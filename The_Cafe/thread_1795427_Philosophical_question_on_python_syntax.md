---
title: "Philosophical question on python syntax"
date: 2011-07-02
forum: The Cafe
---

### Post by leandromartinez98 on 2011-07-02
I'm used to Fortran programming, and starting to adventure me with python, as so many people speak so well about it. Now I have just made my first toy program, which opens a file, reads its content, and then closes it. For closing it, one uses:

file.close()

in Fortran it would be something like 

close(file)

How did work the mind of the people developing python such to think that the python syntax is more readable or clear than the other one? Or there is any FUNDAMENTAL reason for using that which prevents the fortran-style syntax being used? Really, I'm asking that from the bottom of my heart, in hope to understand.

For instance, in python one writes something with 

print 'something'

with that logic, it should be

'something'.print()

or something like that. I just find that very strange.

---

### Post by ibuclaw on 2011-07-02
```

close(file)

```
Is a function call passing 'file' as the first argument.

```

file.close()

```
Is a method call. 'file' is the object, and 'close' is a property of that object.

You need a OOP damaged brain to understand that basic concept. Any previous knowledge of C++ would help you there... :)

Regards

---

### Post by cgroza on 2011-07-02
The paradigms are different. The python syntax expresses OOP while Fortan is procedural (not sure...).

---

### Post by red_Marvin on 2011-07-02
> **leandromartinez98 said:**
> I'm used to Fortran programming, and starting to adventure me with python, as so many people speak so well about it. Now I have just made my first toy program, which opens a file, reads its content, and then closes it. For closing it, one uses:

file.close()

in Fortran it would be something like 

close(file)

How did work the mind of the people developing python such to think that the python syntax is more readable or clear than the other one? Or there is any FUNDAMENTAL reason for using that which prevents the fortran-style syntax being used? Really, I'm asking that from the bottom of my heart, in hope to understand.

For instance, in python one writes something with 

print 'something'

with that logic, it should be

'something'.print()

or something like that. I just find that very strange.

That it is called somefile.close() is standard for object oriented languages;
since close operates on the file object alone, it makes sense to make
it a method of the File class, the syntax is standard.

The fact that it is not called somestring.print() is because printing
is not an operation on the string object, but on the output stream object.*
E.g. in java, where this is forced to be explicit it would be System.stdout.println(somestring).

edit: *This is not neccesarily true for python, but more generally why it in the
object oriented paradigm would make sense to not have print as a method of the String
class. It is possible that some language designers would have another opinion
and that other languages actually do have somestring.print()...

---

### Post by in-dust-rial on 2011-07-02
OOP 
object oriented programming.

just for clearification.

historically:
the issue mainly can be understood by understanding the change from c to c++ - as it is well discussed and documented

learning:
(for fortran see:
[http://fortranwiki.org/fortran/show/Object-oriented+programming](http://fortranwiki.org/fortran/show/Object-oriented+programming))
within c++ it is very simple to use both ways of programming.
so c++ is a classical environment to learn how to use and understand the paradigm shift.
i liked this tutorial:
[http://www.tenouk.com/Module12.html](http://www.tenouk.com/Module12.html)


philosophical issue:
for ppl with some background in programming it seems to be quite clear, that one notion is object oriented, while the other is not.
but philosophical this is not straight forward. it might be possible to implement object oriented or 'normal' BEHAVIOR in both syntax ways:
print 'something'
'something'.print()

or more precise:
function(object)
function(argument)
or
object.function
argument.function

indeed this is archived in many libraries/languages to avoid the confusion you are in.
i.e. sometimes the functions are overloaded to handle objects as 'traditional' inputs. 
the two concepts here are 'overloading' and 'wrapping'.


why use the OO way to manipulate data?
- there are many reasons.
two reasons are very important. one reason is the use of 'interfaces'. interfaces can be quite clean when using objects.
interfaced 'decleare' what inputs and outputs a function (or object) has. so one can understand the function (object) by reading the interface alone, without having a look at the complex implementation.
the other reason is very thighly associated with interfaces. when projects are quite complex it is easy to appraoch everything as an object. so one can very easily think of the instances that are instanciated by the program code in a straight forward way.

the different syntax now just makes the programmer see 'THIS IS AN OBJECT'. this can tell him several things. most likely he will look at the interface immediately - to learn about these kind of objects.

conclusion:
different kinds of programming languages are associated with different syntax. for example functional programming(haskall) has a different syntax from logical(prolog) or imperative programming(c++).
however - most likely each programming language can immitate the syntax of another paradigm. (there are for example functional libraries for c++)
so syntax does not tell you something fundamental about WHAT is actually going on. 
especially in higher programming languages (like python) the implementation of the syntax(compiler) can be quite complex and hidden from the user.

but it doesent mean you cannot have a look at it!
see for example object oriented fortran... 
this might look very odd to you:
THERE is always some code -somewhere- which implements how to come from
the normal way of fortran]
to the OO fortran. 
if you are lucky the code is written in fortran itself.
(i guess this can not easily done in phyton.)

and there it is written in fortran code WHAT ACTUALLY IS THE DIFFERENCE BETWEEN:
object.function
and 
function(object)

so it is no magic at all!

good luck

---

### Post by Cheesehead on 2011-07-02
'close' is like a verb in fortran. But like an adjective in python.

---

### Post by forrestcupp on 2011-07-02
> **Cheesehead said:**
> 'close' is like a verb in fortran. But like an adjective in python.

Not really. It's a verb in python, too. It's just a member of the class that 'file' is an instance of.

+1 to the people saying that the OP needs to think with an object oriented mindset. 'file' is an object. An object is an instance of a class, which is kind of like the blue prints of what you want those types of objects to be like. Each object can have any number of members, which can be variables, functions (called methods if they're inside a class), or whatever. Close() is a method that is part of that class, so you access it through the object that you are wanting to run that function on.

And just remember, I doubt if they had Fortran in mind when they were creating Python.

---

### Post by leandromartinez98 on 2011-07-02
Uhm... I see... Ok, the OOP way of think is such that things are organized in such a way that a function (an operation) is something within the object (or the class of that object?). Thus, the class of objects is something on a lower level (I'm thinking of something like a tree) than the functions. The functions are part of that class... makes sense. That is, 

close(file)

could make one interpret that the operation close() could be applied to something other than something of the class of files. Of course that cannot be done, but it is not explicit on the syntax (in this case it may be obvious, but it is true that the other way around can be more clear in other cases, now I realize). While

file.close()

is saying: look, the object is a file, and within the operation of such a class of objects, I'm applying this close() one.

So, one question, within these OOP languages (python among them), I suppose that, for example, one can have a "close()" operation for a file and a "close()" operation for something else, with a totally different meaning, correct? If that is the case (well, I imagine, now, obviously it is), indeed the flexibility of the syntax is enormously greater...

Uau, this is the first time I understand any advantage of OOP.

Thanks for the discussion!

---

### Post by in-dust-rial on 2011-07-02
hey,
cool!
what you are saying sounds valid and sound to me.

:) 
so you developed seemingly by yourself the idea of overloading functions.

> **leandromartinez98 said:**
> Thus, the class of objects is something on a lower level (I'm thinking of something like a tree) than the functions. The functions are part of that class... makes sense.

here I hope you actually have a model where this is true. 

however on the level of machine code i would tend to disagree. 
maybe i would even go further and challenge this model of a tree construct? (flow charts are the classical way)

likewise other data types also complex data types (like objects) are 'normally' given before run-time. in case you would like to instanciate a OBJECT from a CLASS you would search the part in the code where the class is defined. 
and there you find what functions are bound to the class.

in any case:
program entry -> complex data structure -> function
(if there was a hierarchic tree)
this relation ship is quite nicely resembled in the term mentioned above: 
functions are 'class members'
if functions are members of a class the programmer has to ensure that they actually work with objects of 'this' class. more precisely this means, that those member-functions are often  defined (or overloaded) just within the class itself.

for me in general it is:
data types > functions

have fun with python

---

### Post by Lucradia on 2011-07-02
PHP also uses file.open('file') and file.close() << Note, nothing on close.

But that's just OOP as per normal. Have fun with python indeed.

---

### Post by Bandit on 2011-07-02
> 
```

file.close()

```
Is a method call. 'file' is the object, and 'close' is a property of that object.

You need a OOP damaged brain to understand that basic concept. Any previous knowledge of C++ would help you there... :)

Regards

LOL damaged brain.. No wonder it made perfect since to me.. I use Javascript and PHP a lot.. Those are object oriented also. Plus my experience using VB.

---

### Post by forrestcupp on 2011-07-02
> **leandromartinez98 said:**
> 
So, one question, within these OOP languages (python among them), I suppose that, for example, one can have a "close()" operation for a file and a "close()" operation for something else, with a totally different meaning, correct? If that is the case (well, I imagine, now, obviously it is), indeed the flexibility of the syntax is enormously greater...

That's right. When you start creating your own classes, you're limited only by your imagination. You can even define your function to have several methods that are all named the same thing but can have different numbers and types of parameters, each doing something different. That's called overloading. I could create methods all called Append() that could do different things depending on whether I pass an int or string parameter. The sky's the limit.

Welcome to the world of OOP. :)

---

### Post by 3Miro on 2011-07-02
Objects, that's the whole issue.

In Fortran and C, you have data structures (i.e. some array or struct) and you have functions working on them:

scale( vector, alpha )

In C++ and Python (and all object oriented languages), you can create classes which combine the data structure and the functions that go with it:

vector.scale( alpha )

Basically, the function "scale" is part of the structure "vector".

Or you can think of the above as calling "scale" with "vector" passed by default.

---

