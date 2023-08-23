## Interface segregation principle

This principle says that many specific interfaces are better than a single interface in order not to force a class to implement a method that it is not going to use. We need to create small, more specific interfaces instead of having a single generic one.

Let's exemplify to understand better, let's create some interfaces and bird classes to help us.

```php
<?php
interface Bird
{
    public function walk();
    public function fly();
    public function swim();
}
```
```php
<?php
class Duck implements Bird
{
    public function walk()
    {
        //logic
    }

    public function fly()
    {
        //logic
    }

    public function swim()
    {
        //logic
    }
}
```
```php
<?php
class Penguin implements Bird
{
    public function walk()
    {
        //logic
    }

    public function fly()
    {
        //logic
    }

    public function swim()
    {
        //logic
    }
}
```
```php
<?php
class Swallow implements Bird
{
    public function walk()
    {
        //logic
    }

    public function fly()
    {
        //logic
    }

    public function swim()
    {
        //logic
    }
}
```

In this structure we are forcing some birds to implement some methods that they shouldn't have. That's because there are birds that don't fly and birds that don't swim. Like Penguin, which implemented the fly method since penguins don't fly. And the same for Swallow, who doesn't swim.

Let's see how to create a structure that follows the principle of interface segregation.

```php
<?php
interface Bird
{
    public function walk();
}
```
```php
<?php
interface BirdThatFly
{
    public function fly();
}
```
```php
<?php
interface BirdThatSwim
{
    public function swim();
}
```
```php
<?php
class Duck implements Bird, BirdThatFly, BirdThatSwim
{
    public function walk()
    {
        //logic
    }

    public function fly()
    {
        //logic
    }

    public function swim()
    {
        //logic
    }
}
```
```php
<?php
class Penguin implements Bird, BirdThatSwim
{
    public function walk()
    {
        //logic
    }

    public function swim()
    {
        //logic
    }
}
```
```php
<?php
class Swallow implements Bird, BirdThatFly
{
    public function walk()
    {
        //logic
    }

    public function fly()
    {
        //logic
    }
}
```

Now yes. We have the BirdThatFly, BirdThatSwim interfaces instead of just one Bird interface.