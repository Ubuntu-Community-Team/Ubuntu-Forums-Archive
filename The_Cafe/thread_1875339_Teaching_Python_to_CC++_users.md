---
title: "Teaching Python to C/C++ users"
date: 2011-11-04
forum: The Cafe
---

### Post by P1C0 on 2011-11-04
I have 2 to 3 hours to introduce Python to C/C++, decent,  users. I suppose I have to focus on the main differences between Python and C/C++, but I'm a bit lost..

I was thinking something like:

[LIST]
[*]Showing how you declare variables in Python and what a Python code snippet looks like (indentation, reserved words, function declarations, assignments, e.t.c).
[*]Explaining how everything is an object, and what immutable and mutable objects are.
[*]Introducing them to lists, tuples, dictionaries, sets, and closures.
[*]Showing some looping techniques (also do-while doesn't exist in python), list comprehensions, and generators maybe.
[*]Introducing them to Lambda functions
[*]Showing some OOP features, by constructing some classes and instances, and also demonstrating the link between class methods and closures.
[*]Explaining exception handling.
[*]Closing up with some examples.
[/LIST]

The students will have to write some Python code for a project, but nth extreme, really. 

I would appreciate any advice or comments :)

---

### Post by Lucradia on 2011-11-04
You don't have to teach them outright. Use Python.Boost.

[http://www.boost.org/doc/libs/1_47_0/libs/python/doc/](http://www.boost.org/doc/libs/1_47_0/libs/python/doc/)

if you need to transition them to 3D on top of that, use Python Ogre. Also a note, Python is inherently made and optimized for human-readability.

---

### Post by gsmanners on 2011-11-04
> **P1C0 said:**
> I have 2 to 3 hours to introduce Python to C/C++, decent,  users. I suppose I have to focus on the main differences between Python and C/C++, but I'm a bit lost..

I was thinking something like:

[LIST]
[*]Showing how you declare variables in Python and what a Python code snippet looks like (indentation, reserved words, function declarations, assignments, e.t.c).
[*]Explaining how everything is an object, and what immutable and mutable objects are.
[*]Introducing them to lists, tuples, dictionaries, sets, and closures.
[*]Showing some looping techniques (also do-while doesn't exist in python), list comprehensions, and generators maybe.
[*]Introducing them to Lambda functions
[*]Showing some OOP features, by constructing some classes and instances, and also demonstrating the link between class methods and closures.
[*]Explaining exception handling.
[*]Closing up with some examples.
[/LIST]

The students will have to write some Python code for a project, but nth extreme, really. 

I would appreciate any advice or comments :)

Sounds like an entire semester, to me. How many sessions do you have?

---

### Post by t0p on 2011-11-04
Every coding tuition book or site I've seen starts with a "hello world" program.  So make sure you include a **hello_world.py**.  )

---

### Post by JDShu on 2011-11-04
Probably also something on scoping, which is a bit weird in Python, as well as duck typing, but it looks like a good list to me.

---

### Post by 3Miro on 2011-11-04
Are they C or C++ coders. If they already know C++, then you can skip much of the OOP stuff, they will already know what it is. If they don't know OOP, then spend more time working with that.

---

### Post by Erik1984 on 2011-11-04
I recently jumped into python, just started coding without reading to much docs. What I found most surprising compared to other languages I know such as C++, Java and FreeBASIC, were shared class 'members' between all instances. Has cost me some hours not understanding the 'strange' (as you expect different) behavior of my program :P That's a subject you should touch however I guess you already included it in your list.

---

### Post by P1C0 on 2011-11-04
> **gsmanners said:**
> Sounds like an entire semester, to me. How many sessions do you have?Well, max 3 I'd say, about 1 hour each.

@_[U]3Miro_[/U] They are C and C++ coders and know a great deal of OOP, so I'll keep the Python OOP part short.

@_t0p _import __hello__ :P

---

### Post by Lucradia on 2011-11-05
> **P1C0 said:**
> @_t0p _import __hello__ :P

Make sure to also use __NOTOC__ from MediaWiki ;)

---

