---
title: "To Those Wanting To Make The Next Great Programming Language"
date: 2009-01-18
forum: The Cafe
---

### Post by SuperMike on 2009-01-18
For those of you who think you'd like to make the next great programming language, and who actually might do that and influence my life later on, I'd like to have a word of persuasion here with you, my friend.

**Semicolons**
Please make it so that I can wrap a line of code over several lines, and mail code and know that a mail system may wrap my mails in odd ways, but as long as those semicolons are there, my code will remain intact. For those languages that don't use semicolons -- mail often munches their stuff.

**The Dot**
Let's just keep it simple, shall we? Got a static method? How about a dot as the separator. Got a non-static method. A dot. Got an object property. The dot. You can use & as a concatenator symbol, but please don't make me have to keep typing -> and :: and ::: and / all the time when dealing with object methods and properties.

**Duck Typed**
I like duck typed languages. Less hassle that way. They seem to run just fine. And if not, then I'll build something in C to work my way out of that problem. See my note on C further down.

**No Compilation**
I like scripting languages. I can make a change, try it out, make a change, try it out -- much faster than fighting with compilers and linkers.

**If Control Structure and the Curly Brace**
Look, if it's between the word "if" and a curly brace symbol, don't make me have to wrap my conditions yet again with parentheses. PHP does this and it drives me crazy.

**Curly Braces**
This works well. Keep this in your if/then, do/while, for, etc.

**C Should Be A Good Influence**
C has some great control structures like if/then, for, etc. Many languages already borrow from this. We get it, alright? Please start at least with those. And I love how I can do $i++ and it increments, as well as $i+=1.

**Require Space Before and After Concat Symbol**
PHP drives me nuts. You read a bunch of code and someone does a string like:

$a="Welcome ".$Person.",".$WelcomeMsg;

That stuff drives me nuts. So, if you're going to replace the concat symbol with &, make it require a space before and after it or it won't compile.

**Give Us Active Record**
Whenever you get rocking and rolling with PHP freelancing, you eventually realize that an ORM makes a lot of sense on doing onsey-twosy record updates where you don't want to have to type out all the SQL. And often the simplest ORMs just re-implement what's called an Active Record. So why not make Active Record part of the main language? Sure, it's not suitable for everything, but it can be a timesaver for a lot of parts of an application.

**Give Us the With Statement**
Nothing is more annoying than grabbing an object with dozens of properties, and wanting to set all those properties. It would be great to use something like the following and save keystrokes:

```
with $oObject {
  .name = $sFirstName & ' ' & $sLastName;
  .address = $sAddress;
}
```

**Keep The Parameter Order Consistent**
PHP keeps inverting this stuff. The substr() wants the haystack first. The str_replace() wants the haystack last. And so on. Keep the haystack and needle in a consistent place.

**By Default, It Should Be An Apache Module**
Don't make us have to run your language in CGI mode or with a special web server. It should start as an Apache module.

**Building Modules in C Should Be A Snap**
I should be able to extend the language easily by taking a skeleton module written in C, flesh it out with normal C language stuff, compile it brainlessly easy with GCC, and then include it in my script with a simple one-liner that makes that library into an object namespace with a bunch of functions and properties available to it. And to make our lives easier, please create other skeleton modules that interface with PostgreSQL, MySQL, and SQLite so that we can see how that's done.

In fact, you could make it even cooler that I could just include the myfile.c file and the script could compile it on the fly as neccessary -- giving my C stuff a kind of scripting language feel to it.

**Compiling Your Language Should Not Be A Nightmare**
I have no idea why it's such a pain to compile PHP from scratch. (If you're doing it without an RPM or DEB file.)

**Don't Assume ByRef**
Don't assume that I want to pass something as byval or byref. Force me to use some syntax to make something byref, such as &myvar.

**Get It Right The First Time So It's Not Deprecation City**
Take early Java and compare it to the Java we see today, and it's like a completely different thing. You can't even use old Java books anymore like you can almost do with early PHP books.

**Use ASP-Style Tags**
Okay, since <? seems to have been stolen unfairly by the XML crowd, let's stick with ASP-style tags like:

<% DoSomething(); %>

and

<%= $sMyVar %>

**Keep The Global Namespace Thin**
Sure, I don't like having to grab a String object or namespace in order to do string tasks. Nor do I like to grab a Math object or namespace in order to do math tasks. So, for the most common things we use, give us these things in the global namespace so that I can simply do abs() and substr(). But know your limits and create a namespace arrangement that I have to load a namespace to go beyond a certain range of stuff. Sometimes that's very hard to figure out, so do your best. Ideally it would be great that I only need a namespace to do XML work, database stuff, PDF generation, GD lib interaction, JSON interaction, etc.

**Unicode Should Not Be An After-Thought**
Wide characters do take up a lot of memory, so obviously we don't want them as the default. But if I want to switch a class so that everything it does is in wide character format to accommodate Unicode, please let me do this easily. And then give us various wide-to-regular and regular-to-wide character translations. (Although I realize that regular-to-wide and wide-to-regular can only go so far because one has a much larger character set than the other.) And let us add some parameter in a function or object property to indicate that we're passing a string in wide character format or outputting a string in wide character format.

**Dates And Times Should Work Better**
Just make it that all the time/date stuff doesn't use an epoch and therefore has no risk of screwing up. Make it use UTC as the default timezone. And then give a FAQ to developers with a Javascript code snippet inside so that they can see how to extract the browser's timezone delta and pass that into your programming language so that times can be changed as necessary for each user's context.

**Make It A Templating Language Too**
Because of PHP's alternative syntax and short tags, it is already an outstanding templating language. I'd like to see your language have this feature too.

**Make Extremely Helpful Error Pages**
I should be able to add a statement at the top of my script files so that I can get very pretty error messages coming back along with colored code highlighting. I should also have an editor on that page so that I can leave some summary notes on why such an error would occur -- to help me on the next time I see that error. And then give me a hyperlink I can click where I can see what other people have typed about this kind of error as well.

**Security Should Be Paramount**
This is a never-ending game, but by default the language should do a lot of security fixes for me. I want to effortlessly block 80% of most XSS, URL hacking (going to parts of the site out of sequence or without authentication), and SQL injection. From there on out, the language should have an advice center on how to take this even further.

**Simplistic Filters Should Be Available**
We do a lot of work on our own to ensure our First Name field is a first name, our Last Name field is a last name, to ProperCase these values, and so on. And this applies to Zipcodes, Postal Codes, URLs, Address Line 1, Address Line 2, etc. Your language should provide a lot of these right out of the box.

**Record Pagination Should Be A Snap**
Google-style record pagination should be a snap to implement with your language and the database API, communicating with PostgreSQL, MySQL, or SQLite.


Okay, that's enough. Anyone else got any wishes for such a language? Beats worrying about the economy!

---

### Post by loell on 2009-01-18
> **SuperMike said:**
> 
**No Compilation**
I like scripting languages. I can make a change, try it out, make a change, try it out -- much faster than fighting with compilers and linkers.

even scripting languages are compiled before they are executed.

---

### Post by brunovecchi on 2009-01-18
You are not being ambitious enough.

[**_Here's_**]("http://dev.perl.org/perl6/") your solution. It will more than suffice.

---

### Post by thisllub on 2009-01-18
Another insightful post.
Let me add some things

> **SuperMike said:**
> 
**No Compilation**
I like scripting languages. I can make a change, try it out, make a change, try it out -- much faster than fighting with compilers and linkers.

I would just like something that optionally compiled the code to an executable.

> **SuperMike said:**
> 
**Give Us the With Statement**
Nothing is more annoying than grabbing an object with dozens of properties, and wanting to set all those properties. It would be great to use something like the following and save keystrokes:

```
with $oObject {
  .name = $sFirstName & ' ' & $sLastName;
  .address = $sAddress;
}
```

Watch out. That is very VB like.

> **SuperMike said:**
> 
**Compiling Your Language Should Not Be A Nightmare**
I have no idea why it's such a pain to compile PHP from scratch. (If you're doing it without an RPM or DEB file.)


I have a script that includes all the modules I want and options for the configure line. I modify it as necessary.

> **SuperMike said:**
> 
**Dates And Times Should Work Better**
Just make it that all the time/date stuff doesn't use an epoch and therefore has no risk of screwing up. Make it use UTC as the default timezone. And then give a FAQ to developers with a Javascript code snippet inside so that they can see how to extract the browser's timezone delta and pass that into your programming language so that times can be changed as necessary for each user's context.



If every computer user adopted the standard yyyy/mm/dd there would be no problem. I have spent an irrational amount of time converting dd/mm/yyyy to mm/dd/yyyy. It gets even worse when you are trying to automate data imports from people you have little or no control over.

---

### Post by MaxIBoy on 2009-01-18
> **SuperMike said:**
> For those of you who think you'd like to make the next great programming language, and who actually might do that and influence my life later on, I'd like to have a word of persuasion here with you, my friend.

**Semicolons**
Please make it so that I can wrap a line of code over several lines, and mail code and know that a mail system may wrap my mails in odd ways, but as long as those semicolons are there, my code will remain intact. For those languages that don't use semicolons -- mail often munches their stuff.I dislike mandatory semicolons, because there's no real reason to need them. I tend to restrict my line width to 80 or 120 characters, and so I don't have to horizontally scroll through statements. Restrict yourself to one statement per line, or use parentheses to spread things across multiple lines, or split really complex stuff up. It's easier to read that way, anyway. If you have two really simple statements that just belong together, then **optional** semicolons are great. 

> **The Dot**
Let's just keep it simple, shall we? Got a static method? How about a dot as the separator. Got a non-static method. A dot. Got an object property. The dot. You can use & as a concatenator symbol, but please don't make me have to keep typing -> and :: and ::: and / all the time when dealing with object methods and properties.Total agreement.

> **Duck Typed**
I like duck typed languages. Less hassle that way. They seem to run just fine. And if not, then I'll build something in C to work my way out of that problem. See my note on C further down.Total agreement.

> **No Compilation**
I like scripting languages. I can make a change, try it out, make a change, try it out -- much faster than fighting with compilers and linkers.Total agreement. (Though optional compilation and JIT interpreters are nice, too.)

> **If Control Structure and the Curly Brace**
Look, if it's between the word "if" and a curly brace symbol, don't make me have to wrap my conditions yet again with parentheses. PHP does this and it drives me crazy.I can see both sides of this one. On the one hand, I can see the rationale behind keeping it consistent and treating control structures like functions. However, I pretty much agree.

> **Curly Braces**
This works well. Keep this in your if/then, do/while, for, etc.Curly braces are nice if your intention is to write unreadable code. I prefer consistent indentation, because it doesn't allow people to write crap like this:
```
bool moreWorkNeeded = true
int boltTightness
while moreWorkNeeded { moreWorkNeeded = false; insertBolt; tightenBolt; boltTightness = checkBoltTightness(); if boltTightness < 720 { /*degrees*/
tightenBoltMore} 
if numUnusedBolts < 0 {raise howIsThisEvenPossibleError} else if numUnusedBolts > 0 {
moreWorkNeeded = true}}
```
With indentation, that code would *have* to be written like this:
```
bool moreWorkNeeded = true
int boltTightness
while moreWorkNeeded: 
    moreWorkNeeded = false; insertBolt; tightenBolt; boltTightness = checkBoltTightness() 
    if boltTightness < 720: //degrees
        tightenBoltMore
    if numUnusedBolts < 0: 
        raise howIsThisEvenPossibleError 
    else if numUnusedBolts > 0:
        moreWorkNeeded = true
```
Still not pretty, but it's an improvement.

> **C Should Be A Good Influence**
C has some great control structures like if/then, for, etc. Many languages already borrow from this. We get it, alright? Please start at least with those. And I love how I can do $i++ and it increments, as well as $i+=1.I almost entirely agree with you. However, the increment and decrement statements seem of limited use. Although it's true that you can use it in interesting ways:
```
//will output 8, then 4
i = 3
print (i++)+5, i

//will output 9, then 4
i = 3
print (++i)+5, i
```That kind of stuff is really annoying to modify. In general, the increment and decrement statements do save an entire character of typing, but it's not helpful enough to make it worth the trouble of implementing in an interpreter.

> **Require Space Before and After Concat Symbol**
PHP drives me nuts. You read a bunch of code and someone does a string like:

$a="Welcome ".$Person.",".$WelcomeMsg;

That stuff drives me nuts. So, if you're going to replace the concat symbol with &, make it require a space before and after it or it won't compile.My favorite solution is to use the plus sign:
```
a = "Welcome, " + PersonName + ", " + WelcomeMessage
``` However, I do think that spaces should be required before and after the plus sign, minus sign, multiplication sign, division sign, modulus sign, "to the power of" sign, before and after parenthesis pairs, and after every comma in a sequence. For the sake of tired eyes everywhere!

> **Give Us Active Record**
Whenever you get rocking and rolling with PHP freelancing, you eventually realize that an ORM makes a lot of sense on doing onsey-twosy record updates where you don't want to have to type out all the SQL. And often the simplest ORMs just re-implement what's called an Active Record. So why not make Active Record part of the main language? Sure, it's not suitable for everything, but it can be a timesaver for a lot of parts of an application.Why not implement a "dict" (dictionary) class: ```
dict colors = {'red': [255, 0, 0], 'green': [0, 255, 0], 'blue': [0, 0, 255],
                     'yellow': [128, 128, 0], 'turquoise': [0, 128, 128], 'purple': [128, 0, 128]}

print colors ['red'] // prints "[255, 0, 0]"
```

> **Give Us the With Statement**
Nothing is more annoying than grabbing an object with dozens of properties, and wanting to set all those properties. It would be great to use something like the following and save keystrokes:

```
with $oObject {
  .name = $sFirstName & ' ' & $sLastName;
  .address = $sAddress;
}
```Potential for abuse and unreadability, but I basically agree.

> **Keep The Parameter Order Consistent**
PHP keeps inverting this stuff. The substr() wants the haystack first. The str_replace() wants the haystack last. And so on. Keep the haystack and needle in a consistent place.Total agreement.

> **By Default, It Should Be An Apache Module**
Don't make us have to run your language in CGI mode or with a special web server. It should start as an Apache module.Not every language is intended to be used by web servers. 

> **Building Modules in C Should Be A Snap**
I should be able to extend the language easily by taking a skeleton module written in C, flesh it out with normal C language stuff, compile it brainlessly easy with GCC, and then include it in my script with a simple one-liner that makes that library into an object namespace with a bunch of functions and properties available to it. And to make our lives easier, please create other skeleton modules that interface with PostgreSQL, MySQL, and SQLite so that we can see how that's done.Not to mention C++ and other languages. If it's interpreted, there's no excuse not to do a good job of making it a "glue" language.

> In fact, you could make it even cooler that I could just include the myfile.c file and the script could compile it on the fly as neccessary -- giving my C stuff a kind of scripting language feel to it.Yeah, neat trick. Having your interpreter interface with every C compiler that anyone could possibly have installed in every possible configuration and every possible location is very helpful.

> **Compiling Your Language Should Not Be A Nightmare**
I have no idea why it's such a pain to compile PHP from scratch. (If you're doing it without an RPM or DEB file.)Documentation, people! Provide a simple list of dependencies so you don't have to find them by trial and error. Also, make sure your makefile works properly before you upload.

> **Don't Assume ByRef**
Don't assume that I want to pass something as byval or byref. Force me to use some syntax to make something byref, such as &myvar.Total agreement. Even with arrays.

> **Get It Right The First Time So It's Not Deprecation City**
Take early Java and compare it to the Java we see today, and it's like a completely different thing. You can't even use old Java books anymore like you can almost do with early PHP books.Total agreement.

> **Use ASP-Style Tags**
Okay, since <? seems to have been stolen unfairly by the XML crowd, let's stick with ASP-style tags like:

<% DoSomething(); %>

and

<%= $sMyVar %>This whole business of "blocks" seems to make things needlessly complex.

> **Keep The Global Namespace Thin**
Sure, I don't like having to grab a String object or namespace in order to do string tasks. Nor do I like to grab a Math object or namespace in order to do math tasks. So, for the most common things we use, give us these things in the global namespace so that I can simply do abs() and substr(). But know your limits and create a namespace arrangement that I have to load a namespace to go beyond a certain range of stuff. Sometimes that's very hard to figure out, so do your best. Ideally it would be great that I only need a namespace to do XML work, database stuff, PDF generation, GD lib interaction, JSON interaction, etc.Total agreement.

> **Unicode Should Not Be An After-Thought**
Wide characters do take up a lot of memory, so obviously we don't want them as the default. But if I want to switch a class so that everything it does is in wide character format to accommodate Unicode, please let me do this easily. And then give us various wide-to-regular and regular-to-wide character translations. (Although I realize that regular-to-wide and wide-to-regular can only go so far because one has a much larger character set than the other.) And let us add some parameter in a function or object property to indicate that we're passing a string in wide character format or outputting a string in wide character format.Total agreement.

> **Dates And Times Should Work Better**
Just make it that all the time/date stuff doesn't use an epoch and therefore has no risk of screwing up. Make it use UTC as the default timezone. And then give a FAQ to developers with a Javascript code snippet inside so that they can see how to extract the browser's timezone delta and pass that into your programming language so that times can be changed as necessary for each user's context.The epoch can be helpful for seeding random numbers and so on. However, you should provide alternate ways of doing it too (getSecondsFromEpoch() and getCurrTime() in two different functions?)

> **Make It A Templating Language Too**
Because of PHP's alternative syntax and short tags, it is already an outstanding templating language. I'd like to see your language have this feature too."Type inheritance." 

> **Make Extremely Helpful Error Pages**
I should be able to add a statement at the top of my script files so that I can get very pretty error messages coming back along with colored code highlighting. I should also have an editor on that page so that I can leave some summary notes on why such an error would occur -- to help me on the next time I see that error. And then give me a hyperlink I can click where I can see what other people have typed about this kind of error as well.I would like getting an error name, a traceback, the values of all variables in the current scope. I want that error type to be well-documented too.

> **Security Should Be Paramount**
This is a never-ending game, but by default the language should do a lot of security fixes for me. I want to effortlessly block 80% of most XSS, URL hacking (going to parts of the site out of sequence or without authentication), and SQL injection. From there on out, the language should have an advice center on how to take this even further.Just don't make any mistakes when you create a language, and it should work out fine.

> **Simplistic Filters Should Be Available**
We do a lot of work on our own to ensure our First Name field is a first name, our Last Name field is a last name, to ProperCase these values, and so on. And this applies to Zipcodes, Postal Codes, URLs, Address Line 1, Address Line 2, etc. Your language should provide a lot of these right out of the box.I agree. Regular expressions are great for this kind of thing.

> **Record Pagination Should Be A Snap**
Google-style record pagination should be a snap to implement with your language and the database API, communicating with PostgreSQL, MySQL, or SQLite.This kind of thing is a very good benchmark for how annoying a language is as a whole.





Python does a good job with about 80% of my criteria. It's the best language I have found so far, and I'm very happy with it.

---

### Post by InfinityCircuit on 2009-01-18
R6RS Scheme. Write a functional interpreter/compiler while you're at it.

---

### Post by MikeTheC on 2009-01-19
Meh. You guys are lame. We don't need a new programming language. What's *really* needed is a Great Programming Language Tool. I mean... don't tell me you folks haven't *heard* about this yet... no? Really? Well, this is useful for doing a number of tasks ranging from code review and checking to speeding up optimization and compile time (by at least 50% I'm told), string completion and validation, and a number of other fancy programming things which I don't have the first clue about.

Anyhow, from what I understand, it's about 85%-ish ready, and has entered final trials to sort out a last group of compatibility and driver bugs. As I recall, I think the "biggies" left are:

[list][*] emacs IDE (module is in late beta stage)
[*] Visual Basic.NET
[*] C++
[*] Java 6+
[*] Ruby
[*] Ajax
[*] ASP.net
[*] Objective C (you know how Apple can drag it's feet)
[*] ColdFusion
[*] Mathematica (7.x support pending)[/list]



Here's a photo of this marvelous tool:


[img]http://www.schmoozii.com/upload/easy%20button.jpg[/img]

---

### Post by SuperMike on 2009-01-19
Wow. I guess I'm jealous. That's one big tool there.

---

