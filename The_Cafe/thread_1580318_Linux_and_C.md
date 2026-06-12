---
title: "Linux and C"
date: 2010-09-23
forum: The Cafe
---

### Post by limestone on 2010-09-23
Why is most Linux applications and Linux itself written in C and not C++?
Personally I'm not a fan of neither, I like python better. But it would probably be good to know C or other language to.

Could the answer of my question be that according to Wikipedia:
"C is one of the most popular programming languages of all time, and there are very few computer architectures for which a C compiler does not exist."
:)

---

### Post by Sporkman on 2010-09-23
C++ is the same as C, except it has extra features & a different I/O mechanism.

---

### Post by Tibuda on 2010-09-23
[quote="Linus Torvalds"]C++ is a horrible language. It's made more horrible by the fact that a lot of substandard programmers use it, to the point where it's much much easier to generate total and utter crap with it. Quite frankly, even if the choice of C were to do *nothing* but keep the C++ programmers out, that in itself would be a huge reason to use C.[/quote]
[http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918](http://thread.gmane.org/gmane.comp.version-control.git/57643/focus=57918)

EDIT: This is not my opinion. I don't have an opinion at all, as I'm not a programmer.

---

### Post by Paul820 on 2010-09-23
I have just bought 'The C++ Programming Language' by Bjarne Stroustrup and he explains the differences between C and C++ in great detail. Excellent read.

---

### Post by Bachstelze on 2010-09-23
> **Sporkman said:**
> C++ is the same as C, except it has extra features & a different I/O mechanism.

C++ is the same as C, except it is different. :o

---

### Post by limestone on 2010-09-23
> **Paul820 said:**
> I have just bought 'The C++ Programming Language' by Bjarne Stroustrup and he explains the differences between C and C++ in great detail. Excellent read.

I bought the book Learning Python by Mark Lutz, he explains the different in python 2.6 and 3, also his book is really great and easy to understand. Maybe he have a C book to..

---

### Post by Sporkman on 2010-09-23
> **Bachstelze said:**
> C++ is the same as C, except it is different. :o

Correct, with the caveat that the part that is "different" is much smaller than the part that is "the same".

---

### Post by samalex on 2010-09-23
I thought the biggest difference is C++ is Object Oriented and C isn't, but outside of that the basic syntax is pretty much the same as far as I've seen.  Also isn't the Linux Kernel written pretty much in C because Torvalds isn't a fan of C++?

---

### Post by Old Marcus on 2010-09-23
> C++ is a horrible language. It's made more horrible by the fact that a lot of substandard programmers use it, to the point where it's much much easier to generate total and utter crap with it. Quite frankly, even if the choice of C were to do *nothing* but keep the C++ programmers out, that in itself would be a huge reason to use C.
In my opinion that is utter bullcrap. You can be a substandard programmer in any language, and C++ programmers say the same thing about VB/C# programmers. It's nothing more than elitism.

---

### Post by Sporkman on 2010-09-23
> **samalex said:**
> I thought the biggest difference is C++ is Object Oriented and C isn't

True, although you can implement the object-orientedness in C which C++ provides for free, tediously via function pointers.

---

### Post by emanuel.landeholm on 2010-09-23
> **pont.andersson said:**
> 

And should I learn C or is C++ more of my advantage with Linux related applications?

Unless you are going to code drivers, operating systems or graphics/networking libraries, do not bother with C. Trust me, I'm a (recovering) C-programmmer. :-) You are going to spend 99.5 % of your C-time reinventing trivial stuff (strings, lists, hashes etc.) and chasing subtle memory corruption bugs.

C++ is a failed attempt at adding object orientation to C. But OO is not something you slap on to a language as an afterthought, it has to be in from the design of the language.

The reason libraries are written in C is speed (and tradition - C was invented by the original Unix programmers). But once you have bindings to friendlier languages like python, there's really no benefit to using the C api.

---

### Post by koenn on 2010-09-23
> **Sporkman said:**
> C++ is the same as C, except it has extra features & a different I/O mechanism.

That may be true from a "C" point of view.

From a "C++" point of view, the "extra features" are the core of the language, the similarity to C is just backward compatibility  (and sometimes considered a design flaw)

---

### Post by phrostbyte on 2010-09-23
> **Old Marcus said:**
> In my opinion that is utter bullcrap. You can be a substandard programmer in any language, and C++ programmers say the same thing about VB/C# programmers. It's nothing more than elitism.

The bad thing about C is that you need to be reasonably competent to get anything moderately complex to function properly.

The good thing about C is that you need to be reasonably competent to get anything moderately complex to function properly.

---

### Post by tdrusk on 2010-09-23
One reason, GNU strongly recommends it. >> [http://www.gnu.org/prep/standards/standards.html#Source-Language](http://www.gnu.org/prep/standards/standards.html#Source-Language)

---

### Post by Tibuda on 2010-09-23
> **tdrusk said:**
> One reason, GNU strongly recommends it. >> [http://www.gnu.org/prep/standards/standards.html#Source-Language](http://www.gnu.org/prep/standards/standards.html#Source-Language)

so I think you are using [these](http://www.gnu.org/distros/free-distros.html) distros instead of [these](http://www.gnu.org/distros/common-distros.html).

---

### Post by Spice Weasel on 2010-09-23
> **Tibuda said:**
> so I think you are using [these]("http://www.gnu.org/distros/free-distros.html") distros instead of [these]("http://www.gnu.org/distros/common-distros.html").

And it matters why?

---

### Post by lisati on 2010-09-23
And C++ starting life as a preprocessor for C matters because ......? :D
Surely the important thing is to choose the tool that best suits the job. (And stop calling me Shirley. :))

---

### Post by Spice Weasel on 2010-09-23
> **lisati said:**
> And C++ starting life as a preprocessor for C matters because ......? :D
Surely the important thing is to choose the tool that best suits the job. (And stop calling me Shirley. :))

People use the language that suits them or is good for the job. It's pointless to argue which one should be used. Unfortunately, people don't pay any attention to this.

---

### Post by Mr. Picklesworth on 2010-09-23
For applications, the reason is beyond me. I think people are finally starting to realise it's a bad idea, as a few Gnome modules are switching to languages that are actually nice to use, like [Vala]("http://live.gnome.org/Vala"), and build systems that weren't designed to kill people).

For libraries and the like, C is a popular choice because it's (theoretically) possible to optimise it very well, and practically any language can use a library written in C. When you have a library written in C++, you usually need convoluted wrappers to get them to work from other languages because there's all that object oriented stuff to deal with.

In Gnome land, C is always being coupled with glib and gobject, which provides lots of really cool stuff and OOP features on top.

---

### Post by koenn on 2010-09-23
> **lisati said:**
> And C++ starting life as a preprocessor for C matters because ......? :D
Surely the important thing is to choose the tool that best suits the job. (And stop calling me Shirley. :))
Shirley, the OP's question was what would be the best tool for his job, C or C++, and how come one seems  used more often than the other.

relating that to a choice of distro was a bit of a stretch, and I didn't see anyone mentioning C++ being a preprocessor for C, so your analogy there is wrong. 

while we're at it, where does that "C++ starting life as a preprocessor for C" come from? Never heard it before.

---

### Post by GeneralZod on 2010-09-23
> **koenn said:**
> 
while we're at it, where does that "C++ starting life as a preprocessor for C" come from? Never heard it before.

From here, I believe:

[http://en.wikipedia.org/wiki/Cfront](http://en.wikipedia.org/wiki/Cfront)

---

### Post by whiskeylover on 2010-09-23
> **Old Marcus said:**
> It's nothing more than elitism.

^ This.

Besides, if you're getting a degree in Computer Science, chances are that the first language you learn is C. It lays the foundation on which you learn other concepts and languages.

---

### Post by koenn on 2010-09-23
> **whiskeylover said:**
> ^ This.

Besides, if you're getting a degree in Computer Science, chances are that the first language you learn is C. It lays the foundation on which you learn other concepts and languages.

they don't use lisp anymore for that ?

---

### Post by lisati on 2010-09-23
> **koenn said:**
> while we're at it, where does that "C++ starting life as a preprocessor for C" come from? Never heard it before.

Early versions of C++ were as an add-on to C.

[http://www.hitmill.com/programming/cpp/cppHistory.html](http://www.hitmill.com/programming/cpp/cppHistory.html)

---

### Post by koenn on 2010-09-23
> **GeneralZod said:**
> From here, I believe:

[http://en.wikipedia.org/wiki/Cfront](http://en.wikipedia.org/wiki/Cfront)

this is  more about solving the chicken-or-egg problem of compiling a compiler written in C++ on a system without compiler for C++, that about the relation between C and C++.

interesting read, though. thanks

---

### Post by koenn on 2010-09-23
> **lisati said:**
> Early versions of C++ were as an add-on to C.

[http://www.hitmill.com/programming/cpp/cppHistory.html](http://www.hitmill.com/programming/cpp/cppHistory.html)

ah, ok. 
the (mis-)use of the word "[preprocessor]("http://en.wikipedia.org/wiki/Preprocessor")" threw me of, then.

---

### Post by phrostbyte on 2010-09-23
> **koenn said:**
> they don't use lisp anymore for that ?

Well no, MIT has recently moved to Python. :)

---

### Post by matthewbpt on 2010-09-23
> **Tibuda said:**
> so I think you are using [these](http://www.gnu.org/distros/free-distros.html) distros instead of [these](http://www.gnu.org/distros/common-distros.html).
Quote from the second link list 
> Gentoo

Gentoo makes it easy to install a number of nonfree programs through their primary package system.

Apparently GNU believes that a system if NOT free if it gives you the freedom to install whatever you like, including something proprietary. I know that they have another definition of free but, I think in this case they are being a bit extreme, they should be embracing distro's like Gentoo. What's more open source than compiling your entire OS from source code!? (sorry for getting off topic ... )

---

### Post by phrostbyte on 2010-09-23
> **matthewbpt said:**
> Quote from the second link list 


Apparently GNU believes that a system if NOT free if it gives you the freedom to install whatever you like, including something proprietary. I know that they have another definition of free but, I think in this case they are being a bit extreme, they should be embracing distro's like Gentoo. What's more open source than compiling your entire OS from source code!? (sorry for getting off topic ... )

This is a pretty good article to read
[http://www.gnu.org/philosophy/why-free.html](http://www.gnu.org/philosophy/why-free.html)

---

### Post by tdrusk on 2010-09-23
> **whiskeylover said:**
> ^ This.

Besides, if you're getting a degree in Computer Science, chances are that the first language you learn is C. It lays the foundation on which you learn other concepts and languages.
They taught me Java, then C++ in an "Object Oriented Programming" class. Later, classes were introduced where we had to tinker with snippets of C code, but our knowledge of C++ helped us in our endeavors.  I wonder if C++ is becoming more common of a programming class than C.

---

### Post by saulgoode on 2010-09-23
> **matthewbpt said:**
> Quote from the second link list 
> Gentoo

Gentoo makes it easy to install a number of nonfree programs through their primary package system. 

Apparently GNU believes that a system if NOT free if it gives you the freedom to install whatever you like, including something proprietary. I know that they have another definition of free but, I think in this case they are being a bit extreme, they should be embracing distro's like Gentoo. What's more open source than compiling your entire OS from source code!? (sorry for getting off topic ... )

The Gentoo comment you cited is not the reason why Gentoo is included on the list. The comment is an "additional note" about Gentoo besides the fact that it fails to satisfy [the FSF's guidelines]("http://www.gnu.org/distros/free-system-distribution-guidelines.html"). If you are aware of Gentoo satisfying the FSF's guidelines, I'm sure they would be happy to include it on their list of Free GNU/Linux distributions.

---

### Post by Windows Nerd on 2010-09-24
I believe people use C code rather than Python because C code compiles, and is more efficient.

---

### Post by HermanAB on 2010-09-24
There are a few design issues with C++ that have never been fixed. 

In a nutshell:
1. Overloading causes severe test and maintenance problems.
2. There is no mechanism to track Objects and decide when it is safe to free an Object, leading to the most horrible bugs. 

Since the above two things are at the core of C++, the language is best avoided.

Anyhoo, anything that can be done in C++, can be done in C, so there is no point in using C++ really.

---

### Post by emanuel.landeholm on 2010-09-24
> **Windows Nerd said:**
> I believe people use C code rather than Python because C code compiles, and is more efficient.

[ citation badly needed ]

Python also compiles. The result is .pyc. Don't assume C-python, there are other implementations.

Efficiency is a non-trivial measure. Python simply does not have subtle memory corruption bugs that plague C and C++, so you don't need to spend hours of debugging with Valgrind.

If you really need speed (believe me, most people don't!): profile. Write the really slow stuff in C. Keep in mind though that numpy is faster than most C-programmers naive re-implementations. Etc.

---

### Post by matthewbpt on 2010-09-24
I learned C as part of my Physics university degree as well as Matlab programming. In C it was so much more complicated to program algorithms and functions which were trivial in Matlab, though of course Matlab is only useful really for writing code for use in scientific experiments so C has a much wider application. I've never learned C++ but if it makes things more complicated than C then I'd keep away from it... Unless you need to do really low level programming then stick to languages like Python IMO.

---

### Post by tdrusk on 2010-09-24
> **matthewbpt said:**
> I learned C as part of my Physics university degree as well as Matlab programming. In C it was so much more complicated to program algorithms and functions which were trivial in Matlab, though of course Matlab is only useful really for writing code for use in scientific experiments so C has a much wider application. I've never learned C++ but if it makes things more complicated than C then I'd keep away from it... Unless you need to do really low level programming then stick to languages like Python IMO.
I have recently ventured into C. I am learning from "The C Programming Language" by Ritchie and Kernighan. It is old, but I have heard excellent things about it and am really enjoying the process.

In conclusion, I feel any language, no matter how complicated it may look, can be made easy with a good book that really explains what is going on. "The C Programming Language" does this. I have also found "Big Java" by Cay Hortsmann does this well too. With the right teacher, anything can be easy.

I love programming in Python, especially if I want to just whip something together. If I *really* want to understand what I am doing, I like C. If I want portability, I like Java. There is no best language, just something different for a different task/objective.

---

### Post by Windows Nerd on 2010-10-03
> **emanuel.landeholm said:**
> [ citation badly needed ]

Python also compiles. The result is .pyc. Don't assume C-python, there are other implementations.

Efficiency is a non-trivial measure. Python simply does not have subtle memory corruption bugs that plague C and C++, so you don't need to spend hours of debugging with Valgrind.

If you really need speed (believe me, most people don't!): profile. Write the really slow stuff in C. Keep in mind though that numpy is faster than most C-programmers naive re-implementations. Etc.
Thank you for correcting me. I had only heard that as the common misconception spread by the hardcore C programmers that insist that python is not a "real" programming language, only a scripting language.

---

### Post by PurposeOfReason on 2010-10-03
> **Windows Nerd said:**
> Thank you for correcting me. I had only heard that as the common misconception spread by the hardcore C programmers that insist that python is not a "real" programming language, only a scripting language.
As far as I'm concerned that is still true and I'm hardly a real programmer. That isn't to say that you can't do really fantastic things with python (see deluge), but it wouldn't be my weapon of choice to get intensive things done.

---

