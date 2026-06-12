---
title: "New Scripting Language - Mixture of Python and PHP"
date: 2008-05-08
forum: The Cafe
---

### Post by samb0057 on 2008-05-08
My company is releasing a scripting language under an open source license. Its main focus will be full object oriented functionality, as well as ease of use in with the Linux/Apache platform.

The language will include many features taken from Python, but with an easier syntax, based off of PHP and C.

The aim of the language is to be enterprise ready, and support many advanced features currently not available in web scripting languages, such as operator overloading, a mixture of strong/dynamic typing, and better standards for more concrete code.

Examples attached. If anyone is interested in contributing or in more information, send a PM. We will have development servers set up shortly and be open for contributions.

---

### Post by blithen on 2008-05-08
Seems...interesting, how will it compile? etc. More info please.

---

### Post by samb0057 on 2008-05-08
> **blithen said:**
> Seems...interesting, how will it compile? etc. More info please.

It will be interpreted like PHP, but also have bytecode caching functionality (APC for PHP) built in.

---

### Post by gsmanners on 2008-05-08
The important thing is: how much facial hair do the devs have? ;)

[http://entertainment.slashdot.org/entertainment/08/04/29/181249.shtml](http://entertainment.slashdot.org/entertainment/08/04/29/181249.shtml)

---

### Post by LaRoza on 2008-05-08
> **samb0057 said:**
> My company is releasing a scripting language under an open source license. Its main focus will be full object oriented functionality, as well as ease of use in with the Linux/Apache platform.

The language will include many features taken from Python, but with an easier syntax, based off of PHP and C.

The aim of the language is to be enterprise ready, and support many advanced features currently not available in web scripting languages, such as operator overloading, a mixture of strong/dynamic typing, and better standards for more concrete code.

Examples attached. If anyone is interested in contributing or in more information, send a PM. We will have development servers set up shortly and be open for contributions.

[list]
[*] Easier syntax? I doubt it. I looked at the code, it is just PHP syntax with static typing. Static typing isn't easier. Python is dynamically and strongly typed, which is better IMO for this kind of programming.
[*] Python has operator overloading, is strongly and dynamically typed, and has standards. 
[/list]

You should link to the project page.

---

### Post by samb0057 on 2008-05-09
> **LaRoza said:**
> [list]
[*] Easier syntax? I doubt it. I looked at the code, it is just PHP syntax with static typing. Static typing isn't easier. Python is dynamically and strongly typed, which is better IMO for this kind of programming.

[*] Python has operator overloading, is strongly and dynamically typed, and has standards. 

[/list]

You should link to the project page.

What I meant by easier was easier than python. The syntax will be very close to PHP.

Python has most of the features, but it is harder to use than PHP, especially for beginners. What we're hoping to do is combine the power of Python with the ease of use of PHP.

This file is a very early demo, by the time this thing is even in beta it will probably look much different.

We don't have a project page up yet, all of the development is in-house right now. We will soon though, probably within a couple of weeks.

---

### Post by hessiess on 2008-05-09
what open source licence, will it be GPL or something else?
will it have pointers and refarances like C/C++?
will it be able to be used on its own, or is it just for scripting applications?

---

### Post by popch on 2008-05-09
Is there any particular reason for creating the new language?

---

### Post by Christmas on 2008-05-09
Is there some beta interpreter available, or something?

---

### Post by samb0057 on 2008-05-09
> **popch said:**
> Is there any particular reason for creating the new language?

We are trying to combine the intuitiveness of PHP with the strong object oriented architecture of Python.

Python is missing a couple of simple things we would like to see, such as pure abstract classes and protected class members. PHP has these things, but is not an OO language from the ground up, and limits alot of flexibility that is available in Python.

---

### Post by samb0057 on 2008-05-09
> **Christmas said:**
> Is there some beta interpreter available, or something?

No, this is in alpha right now. We are in the planning and architecture stage. Code has been written, but it is not yet in a usable state.

---

### Post by LaRoza on 2008-05-09
> **samb0057 said:**
> What I meant by easier was easier than python. The syntax will be very close to PHP.

Python has most of the features, but it is harder to use than PHP, especially for beginners. What we're hoping to do is combine the power of Python with the ease of use of PHP.

We don't have a project page up yet, all of the development is in-house right now. We will soon though, probably within a couple of weeks.

PHP's syntax isn't easier than Pythons...

It is just syntax. PHP is "easy" because it has a syntax like C that is often taught to in beginner courses (which seem to like C++, Java and C#). To a Lisp programmer, PHP's has a confusing an unintuitive syntax. 

> **samb0057 said:**
> We are trying to combine the intuitiveness of PHP with the strong object oriented architecture of Python.

Python is missing a couple of simple things we would like to see, such as pure abstract classes and protected class members. PHP has these things, but is not an OO language from the ground up, and limits alot of flexibility that is available in Python.
PHP isn't intuitive. If it were, why would every PHP developer has php.net open for function references ;) PHP5 is highly OO and seems to have what you want. 

This seems like a rather pointless project. It isn't fixing anything, nor is it introducing anything new.

If someone is getting paid for this, I envy that someone.

---

### Post by popch on 2008-05-09
> **samb0057 said:**
> Python is missing a couple of simple things we would like to see, such as pure abstract classes and protected class members. PHP has these things, but is not an OO language from the ground up, and limits alot of flexibility that is available in Python.

I can see the need for some of those capabilities. Whether they warrant creating a new language which looks confusingly similar to other already existing ones I really can't say.

A brief inspection of the sample code provided in the first post reveals some statements which appear to be terminated by semicolons while others are not. Is the use of the statement terminator optional or does it follow some rules I could not readily discern?

---

### Post by SunnyRabbiera on 2008-05-09
I hope your company respects the code and contributes back to us at some point, as both PHP and python are open source.

---

### Post by samb0057 on 2008-05-09
> **hessiess said:**
> what open source licence, will it be GPL or something else?
will it have pointers and refarances like C/C++?
will it be able to be used on its own, or is it just for scripting applications?

Definitely an open source license, no decision on which one yet. Probably GPL.

It will have references at the least.

By on its own, do you mean compiled? Probably not, just scripting through CLI, CGI, etc.

---

### Post by LaRoza on 2008-05-09
> **samb0057 said:**
> 
By on its own, do you mean compiled? Probably not, just scripting through CLI, CGI, etc.

Not sure what you mean, but no matter what the intent of what you said, it is already inferior to Python and PHP ;)

---

### Post by samb0057 on 2008-05-09
> **popch said:**
> I can see the need for some of those capabilities. Whether they warrant creating a new language which looks confusingly similar to other already existing ones I really can't say.

A brief inspection of the sample code provided in the first post reveals some statements which appear to be terminated by semicolons while others are not. Is the use of the statement terminator optional or does it follow some rules I could not readily discern?

Semicolons will be used just like in C, these are probably typos.
This does look like most other languages now, but keep in mind this is just a prototype, we do plan to add more than is shown in this example. Our main goal is the power and object oriented features of Python with the easy syntax of PHP.

---

### Post by LaRoza on 2008-05-09
> **samb0057 said:**
> Semicolons will be used just like in C, these are probably typos.
This does look like most other languages now, but keep in mind this is just a prototype, we do plan to add more than is shown in this example. Our main goal is the power and object oriented features of Python with the easy syntax of PHP.

Wouldn't it be easier to just get used to Python's syntax? Most people get used to it very rapidly and start to prefer it.

---

### Post by samb0057 on 2008-05-09
> **SunnyRabbiera said:**
> I hope your company respects the code and contributes back to us at some point, as both PHP and python are open source.

We plan to use PHP and Python's source only for research, we don't plan to take any actual code from either, but either way this will definitely be released under an open source license (probably GPLv3).

---

### Post by samb0057 on 2008-05-09
> **LaRoza said:**
> PHP's syntax isn't easier than Pythons...

It is just syntax. PHP is "easy" because it has a syntax like C that is often taught to in beginner courses (which seem to like C++, Java and C#). To a Lisp programmer, PHP's has a confusing an unintuitive syntax. 


PHP isn't intuitive. If it were, why would every PHP developer has php.net open for function references ;) PHP5 is highly OO and seems to have what you want. 

This seems like a rather pointless project. It isn't fixing anything, nor is it introducing anything new.

If someone is getting paid for this, I envy that someone.

PHP might not be the most intuitive, but it is one of the easiest for beginners. Whether that is because it is similar to C, Java, etc. is irrelevant. Also, it's not only syntax that makes PHP easy. It's easier to set up and make a basic script than most languages I've come across.

PHP 5 is OO, but many people's complaint is that it is not OO from the ground up, OO was tacked on later. This will have fully object oriented data types and things like that.

---

### Post by samb0057 on 2008-05-09
> **LaRoza said:**
> Wouldn't it be easier to just get used to Python's syntax? Most people get used to it very rapidly and start to prefer it.

I don't think Python has a horrible syntax or anything; this is a matter of opinion. I prefer braces around functions for example; but this is not the primary reason for starting this project.

---

### Post by fissionmailed on 2008-05-09
Wait, what? PHP is EASIER than python? :confused:

---

### Post by inportb on 2008-05-09
Having used both, I can say that they are equally easy. You just gotta get in the zone before working.

---

### Post by samb0057 on 2008-05-09
> **fissionmailed said:**
> Wait, what? PHP is EASIER than python? :confused:

That's hard to define, but from my experience I have seen that alot more beginners use PHP than Python.
I found PHP easiest when I started web programming, maybe because I had done C and Java before.

---

### Post by LaRoza on 2008-05-09
> **fissionmailed said:**
> Wait, what? PHP is EASIER than python? :confused:

You know what would happen to this thread if I moved it to the Programming Talk :evil:

---

### Post by fissionmailed on 2008-05-09
> **LaRoza said:**
> You know what would happen to this thread if I moved it to the Programming Talk :evil:

D=

---

### Post by popch on 2008-05-09
> **LaRoza said:**
> You know what would happen to this thread if I moved it to the Programming Talk :evil:

tsk, tsk

---

### Post by LaRoza on 2008-05-11
> **popch said:**
> tsk, tsk

It would be a "Baptism of Fire"...literally.

---

### Post by ZylGadis on 2008-05-11
Am I the only one who did not open the example file because it is a proprietary format (Microsoft Word)? Great start towards an "open-source" language, OP.

---

### Post by LaRoza on 2008-05-11
> **ZylGadis said:**
> Am I the only one who did not open the example file because it is a proprietary format (Microsoft Word)? Great start towards an "open-source" language, OP.

The example file wasn't valid anyway, by any thoughts including the OP's.

---

### Post by popch on 2008-05-11
> **LaRoza said:**
> It would be a "Baptism of Fire"...literally.

That's why I like the Italian word for 'match'. In ancient Greek that term might translate into Pyrphor (or perhaps pyrophor) which by some strange coincidence is an anagram of 'porphyr' which is ancient Greek for the color 'purple' which in turn is the default font color in the pink forum.

Surely there's a message hidden here, albeit perhaps not a very interesting one.

@OP: does a formal syntax exist for the language-to-be?

---

### Post by samb0057 on 2008-05-12
> **ZylGadis said:**
> Am I the only one who did not open the example file because it is a proprietary format (Microsoft Word)? Great start towards an "open-source" language, OP.

Well the forums didnt have txt in the list of allowed file types. i made the file in abiword. thanks

---

