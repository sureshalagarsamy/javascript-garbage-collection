# JavaScript Garbage collection

Memory management in JavaScript is <b>performed automatically and invisibly to us</b>. We create primitives, objects, functions… All that takes memory.

What happens when something is not needed any more? How JavaScript engine discovers that and cleans up?

### Reachability

The main concept of memory management in JavaScript is reachability.

 “reachable” values are those that are accessible or useable somehow. They are guaranteed to be stored in memory.
 
reachable values cannot be deleted for obvious reasons.
* Local variables and parameters of the current function.
* Global variables.

These values are called roots.

There’s a background process in the JavaScript engine that is called garbage collector. It monitors all objects and removes those that became unreachable.

# A simple example

```javascript
// user has a reference to the object
var user = {
  name: "John"
};
```

![image](https://user-images.githubusercontent.com/6780840/27580833-89c8d2b6-5b49-11e7-9de0-22bce547108b.png)


Here the arrow shows an object reference. The global variable "user" references the object ```{name: "John"}```

The "name" property of John stores a primitive, so it’s painted inside the object.

If the value of ```user``` is overwritten, the reference is lost:

```javascript
user = null;
```

![image](https://user-images.githubusercontent.com/6780840/27584903-9a19196a-5b57-11e7-8e45-9995abd482e1.png)


Now John becomes unreachable. There’s no way to access it, no references to it. Garbage collector will junk the data and free the memory.

# Summary

* Garbage collection is performed automatically. We cannot force or prevent it.
* Objects are retained in memory while they are reachable.

Modern engines implement advanced algorithms of garbage collection.
