---
title: "My PHP patch for scalar type hinting"
date: 2007-11-15
forum: The Cafe
---

### Post by samb0057 on 2007-11-15
I have written a patch for PHP that allows type hinting for basic variable types (int, float, string, etc.)

It supports:
integers
floats (decimals)
strings
booleans (true/false)
resources (mysql queries, etc)
objects (matches any object)
numbers (matches integers/floats)

This way you can have a function with specific input arguments:

function myFunc(integer $a, number $b, object $c)

I tried to submit it to the PHP internals mailing list but they say that they do not want to implement. I think we should appeal to them to apply the patch. All type hinting is 100% optional and backwards compatible.

If anyone is interested in the patch send me a pm.

---

### Post by maddog39 on 2007-11-15
I don't understand why you would want to even do that in the first place. Plus some type hinting already exists, as used sometimes with the PHP-GTK bindings.

---

### Post by samb0057 on 2007-11-15
Rather than validating data or coming across errors later, i want to know up front that my function that loops through an array is being passed a string. The only type hinting ive been able to find is for arrays and objects

---

