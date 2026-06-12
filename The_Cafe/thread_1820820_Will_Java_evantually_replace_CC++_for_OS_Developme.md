---
title: "Will Java evantually replace C/C++ for OS Development"
date: 2011-08-08
forum: The Cafe
---

### Post by darthvader39560 on 2011-08-08
A couple of rumors are going round the Internet saying Java will replace C and C++ for OS programming. I was just wandering if its true. My take on this is that Java isn't Low level enough for stand-alone OS development.

---

### Post by Legendary_Bibo on 2011-08-08
No.

---

### Post by RoflHaxBbq on 2011-08-08
LMAO!

I actually LOL'd.

---

### Post by NovaAesa on 2011-08-08
I would guess that kernel architectures and kernel design methodologies will have to change drastically before a higher level language can easily be used to implement them.

Keep in mind that as Java technology stands at the moment (and into the foreseeable future), Java code cannot run on bare silicon.

---

### Post by Noz3001 on 2011-08-08
> **NovaAesa said:**
> I would guess that kernel architectures and kernel design methodologies will have to change drastically before a higher level language can easily be used to implement them.

Keep in mind that as Java technology stands at the moment (and into the foreseeable future), Java code cannot run on bare silicon.

I thought ARM chips could run Java bytecode?

---

### Post by 3Miro on 2011-08-08
> **Noz3001 said:**
> I thought ARM chips could run Java bytecode?

[http://en.wikipedia.org/wiki/Java_processor](http://en.wikipedia.org/wiki/Java_processor)

Very few CPUs can run Java bytecode. In short, Java is designed to be independent from the hardware. An OS is all about the Hardware. An OS will never be coded in Java (unless Java changes big time).

---

### Post by cgroza on 2011-08-08
There is GCJ which can compile Java into native machine code. I wonder if that could be used to develop a kernel.
Their homepage: [http://gcc.gnu.org/java/](http://gcc.gnu.org/java/)

---

### Post by Majorix on 2011-08-08
> Will Java evantually replace C/C++ for OS Development

No way.

---

### Post by Bandit on 2011-08-08
> **Legendary_Bibo said:**
> No.

++ Second This ++

Reason being, Java is slower. C++ is faster and supports if not more just as many platforms.

Now what the OP may have heard is about C# which is a blend of the good things from multiple languages (Java, C++, even VB and few others), but not having programmed in it yet I will leave that open for discussion.

---

### Post by Thewhistlingwind on 2011-08-08
> **Bandit said:**
> 
Now what the OP may have heard is about C# which is a blend of the good things from multiple languages (Java, C++, even VB and few others), but not having programmed in it yet I will leave that open for discussion.

C# is proprietary Java.

So the answer is still no.

---

### Post by Lucradia on 2011-08-08
No, it won't.

i'd sooner see python replace java.

---

### Post by Bandit on 2011-08-08
> **Thewhistlingwind said:**
> C# is proprietary Java.

So the answer is still no.

Wrong..

> Anders Hejlsberg has argued that C# is "not a Java clone" and is "much closer to C++" in its design.
Being he is the lead developer, I'll take [his word]("http://windowsdevcenter.com/pub/a/oreilly/windows/news/hejlsberg_0800.html") over yours..

---

### Post by ve4cib on 2011-08-08
> **darthvader39560 said:**
> A couple of rumors are going round the Internet saying Java will replace C and C++ for OS programming. I was just wandering if its true. My take on this is that Java isn't Low level enough for stand-alone OS development.

Replace?  Probably not.  Augment/compliment?  Possibly.

With hardware-implemented JVMs being worked on and continually improved we may see limited instances of pure Java OS development.  Right now Java's big limitations for OS development are:

1- reliance on a software JVM which in turn requires:
2- an existing OS in place that the JVM can use
3- the JVM + existing OS acts as a middle layer between the byte code and the hardware, resulting in generally slower performance

If one were to create hardware specifically designed to run java byte code then we could conceivably mitigate (or possibly even eliminate) all these problems.  A hardware-level JVM would be much faster than a software one, and it would remove the "middleware" nature of the JVM + host OS entity.

But in order for Java to fully replace C and C++ for OS development such a hardware JVM would need to be widely adopted, to the point where it is the standard.  I don't see that happening any time soon on a global scale.

There is likely some interest in creating an all-java OS/hardware combination for specific niche industries though.  Mobile devices comes to mind.  We might also see this sort of thing on embedded systems like DVD players, car radios, microwaves, and suchlike.  Not for general-purpose computing -- the standard C/++ based OSs are too firmly entrenched there -- but for smaller, specific-purpose devices we may see more pure-java implementations in the future.

Another likely possibility -- at least to my mind -- is to continue along the Android route, where we have a very minimal underlying OS (the Linux Kernel + a few supporting binaries in the case of Android) with a JVM running on top of it to manage all of the UI and most of the executables.  We haven't eliminated the need for C/++ in this case, but it's been reduced to a very small -- yet very important -- piece of the larger whole.

---

### Post by Thewhistlingwind on 2011-08-08
> **Bandit said:**
> Wrong..


Being he is the lead developer, I'll take [his word]("http://windowsdevcenter.com/pub/a/oreilly/windows/news/hejlsberg_0800.html") over yours..

Regardless, it's from .net, so the answer will always be no.

---

### Post by psusi on 2011-08-08
Java is both a language, and a platform independent VM.  Microsoft divided the two concepts and made .NET to be the bytecode interpreting VM part, but allowing several languages to be compiled into that bytecode.

C# was born as a C++ that was modified to fit nicely in the .NET VM model, using the java concepts of managed memory and garbage collection.  IIRC it borrows a few more java concepts like only allowing single inheritance, having a universal common base class, and an exception model that is closer to java than C++.

So while saying C# is a knock off of Java misses the mark a bit, it is not that far off.

---

### Post by 3Miro on 2011-08-08
> **ve4cib said:**
> 
If one were to create hardware specifically designed to run java byte code then we could conceivably mitigate (or possibly even eliminate) all these problems.  A hardware-level JVM would be much faster than a software one, and it would remove the "middleware" nature of the JVM + host OS entity.

Wouldn't that be doing things backwards. People usually first build the hardware and then put the software on top to allow you to fully use it. This would be the opposite approach of making the software first and then trying to create hardware that would run it.

> 
Another likely possibility -- at least to my mind -- is to continue along the Android route, where we have a very minimal underlying OS (the Linux Kernel + a few supporting binaries in the case of Android) with a JVM running on top of it to manage all of the UI and most of the executables.  We haven't eliminated the need for C/++ in this case, but it's been reduced to a very small -- yet very important -- piece of the larger whole.

That is definitely possible.

---

### Post by Simian Man on 2011-08-08
> **NovaAesa said:**
> Keep in mind that as Java technology stands at the moment (and into the foreseeable future), Java code cannot run on bare silicon.
Of course it can.  As someone already mentioned, Java is both a language and a software platform.  They normally go together, but there is nothing stopping anyone from compiling Java code directly to machine code, or building a hardware implementation of the Java platform.  Indeed people have done both.

> **Thewhistlingwind said:**
> C# is proprietary Java.
So the answer is still no.
C# is not a Java clone and is not proprietary, so you're waaay off the mark.

> **psusi said:**
> IIRC it borrows a few more java concepts like only allowing single inheritance, having a universal common base class, and an exception model that is closer to java than C++.
Most of what you said is totally correct, but these features are not new things to Java.  Java itself borrowed them from languages like Smalltalk and Eiffel.

There actually have been several Java operating systems, most notably [JavaOS]("http://en.wikipedia.org/wiki/JavaOS"), so it's definitely possible.  I don't think Java is a great fit for systems level programming and don't expect it to take off.

---

### Post by Linux_junkie on 2011-08-08
Java is a language that is independent of hardware it is designed to be written once but run anywhere.  In order to run Java apps you need to have the Java runtime environment (JRE) installed.  In theory you could develop an OS kernel and apps with Java but without the JRE it would be no good.

---

### Post by Bandit on 2011-08-08
> **Thewhistlingwind said:**
> Regardless, it's from .net, so the answer will always be no.
It may not always be no. It may not be the best option now, but saying "will always be no" means you know the future of all programming development. You must be the all knowing one.. I'll make sure I send you my 10%!!

Guess Mono is a Nogo..

---

### Post by Thewhistlingwind on 2011-08-08
> **Simian Man said:**
> 

C# is not a Java clone and is not proprietary, so you're waaay off the mark.



The former I will not comment on. The latter however, is interesting. 

C#/ the .net framework in general. Are not proprietary in the traditional sense.

(Here are the standards for the CLI (Common language infrastructure) and the C# programming language:

[http://www.ecma-international.org/publications/standards/Ecma-335.htm](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

[http://www.ecma-international.org/publications/standards/Ecma-334.htm](http://www.ecma-international.org/publications/standards/Ecma-334.htm))

If you'll notice, attached are two "Patent statements." Which are valid as long as the standard is valid. 

Actually I was way off the mark, it's other parts of .net that are troublesome, not C#.

It's still not becoming an OS language anytime soon.

> **Bandit said:**
> It may not always be no. It may not be the best  option now, but saying "will always be no" means you know the future of  all programming development. You must be the all knowing one.. I'll make  sure I send you my 10%!!

Guess Mono is a Nogo..

C# in it's current form, will never be a language you write an OS in. I don't think it could become one even if it were retooled specifically for this purpose. Theres more factors at work here than just C#'s suitability as an actual language.

1. As far as I know, .net implementations are about bytecode, not compiling to machine op codes. This would mean you would require a compiler that compiles to machine code, or hardware that uses .net bytecode for it's op codes.

2. If the above hardware existed, it would need to become popular in some application. In addition, operating systems written in C# would need to be in some way more desirable than ones written in C/C++.

3. There would need to be a desire for this development in the first place. 

As much as I'd love to be omniscient, I'm not and I probably never will be. However, I highly doubt (To the point of calling it an outright impossibility.) The development of C# becoming a programming language it is fashionable to write operating systems in.

---

### Post by ve4cib on 2011-08-08
> **3Miro said:**
> Wouldn't that be doing things backwards. People usually first build the hardware and then put the software on top to allow you to fully use it. This would be the opposite approach of making the software first and then trying to create hardware that would run it.

Basically, yes.  But it's been done before.  Way back in the day there were terminals that used hardware implementations of Lisp interpreters as one example.  And there are some hardware implementations of simple JVMs that already exist out in the wild.

Most systems are built with the assumption that people will write software in some combination of C, C++, and/or assembly, and use those tools to implement compilers and interpreters for other languages.

But I see nothing wrong with picking a different language -- like Java -- and having a hardware designer say "This is going to be the standard language for this system instead of C" and implement the hardware accordingly.  It's uncommon, but not inconceivable.

---

### Post by forrestcupp on 2011-08-08
> **ve4cib said:**
> 
Another likely possibility -- at least to my mind -- is to continue along the Android route, where we have a very minimal underlying OS (the Linux Kernel + a few supporting binaries in the case of Android) with a JVM running on top of it to manage all of the UI and most of the executables.  We haven't eliminated the need for C/++ in this case, but it's been reduced to a very small -- yet very important -- piece of the larger whole.

I'm surprised people aren't getting this, as popular as Android is. Android's methods are most likely the source of this rumor.

One thing people here are misunderstanding is that an operating system does not equal the kernel. Just like with Android, it is possible to have major parts of an OS being programmed in Java with the underlying parts being programmed in assembly and C/C++.

So in my opinion, it has already been done with Android, which is a very popular OS. But will Java replace C/C++ in the majority of desktop OSs? No way. You'll never see Windows or MacOS or even the major parts of a desktop Linux distro being programmed in Java.

Also, keep in mind that Android doesn't use the full Java Virtual Machine; it uses a very streamlined version of it.

---

### Post by psusi on 2011-08-08
> **ve4cib said:**
> Basically, yes.  But it's been done before.  Way back in the day there were terminals that used hardware implementations of Lisp interpreters as one example.  And there are some hardware implementations of simple JVMs that already exist out in the wild.

That's not a CPU that executes lisp in hardware; that's a bios with a built in lisp interpreter, much like how the commodore 64 had a built in BASIC interpreter.

---

### Post by ve4cib on 2011-08-08
> **psusi said:**
> That's not a CPU that executes lisp in hardware; that's a bios with a built in lisp interpreter, much like how the commodore 64 had a built in BASIC interpreter.

Apparently I was mis-informed then.  Thanks for correcting me.

---

### Post by NovaAesa on 2011-08-08
> **Simian Man said:**
> Of course it can.  As someone already mentioned, Java is both a language and a software platform.  They normally go together, but there is nothing stopping anyone from compiling Java code directly to machine code, or building a hardware implementation of the Java platform.  Indeed people have done both.

I stand corrected! :)

---

### Post by 3Miro on 2011-08-08
> **ve4cib said:**
> 
Most systems are built with the assumption that people will write software in some combination of C, C++, and/or assembly, and use those tools to implement compilers and interpreters for other languages.


I think it is actually the other way around. Originally people designed hardware and programmed in binary. Then they developed languages to help them write software, first came assembler then higher order languages like C. Basically the language is designed to give you access to the functionality of the hardware and that is why a hardware implementation of JVM will be doing things "backwards".

I guess today it is more of a chicken and egg question, who comes first, the hardware or the software.

---

### Post by RoflHaxBbq on 2011-08-09
C will always be superior for programming an OS, regardless of how much people may prefer Java.

---

### Post by BrokenKingpin on 2011-08-09
Not at the kernel level. I can see it being used in the layers above the Kernel... look at Android for example. At this point Java just seems to slow to write an OS in (which probably contributes to the poor battery life in Android).

---

### Post by directhex on 2011-08-09
> **Thewhistlingwind said:**
> The former I will not comment on. The latter however, is interesting. 

C#/ the .net framework in general. Are not proprietary in the traditional sense.

(Here are the standards for the CLI (Common language infrastructure) and the C# programming language:

[http://www.ecma-international.org/publications/standards/Ecma-335.htm](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

[http://www.ecma-international.org/publications/standards/Ecma-334.htm](http://www.ecma-international.org/publications/standards/Ecma-334.htm))

If you'll notice, attached are two "Patent statements." Which are valid as long as the standard is valid. 

Actually I was way off the mark, it's other parts of .net that are troublesome, not C#.

It's still not becoming an OS language anytime soon.



C# in it's current form, will never be a language you write an OS in. I don't think it could become one even if it were retooled specifically for this purpose. Theres more factors at work here than just C#'s suitability as an actual language.

1. As far as I know, .net implementations are about bytecode, not compiling to machine op codes. This would mean you would require a compiler that compiles to machine code, or hardware that uses .net bytecode for it's op codes.

2. If the above hardware existed, it would need to become popular in some application. In addition, operating systems written in C# would need to be in some way more desirable than ones written in C/C++.

3. There would need to be a desire for this development in the first place. 

As much as I'd love to be omniscient, I'm not and I probably never will be. However, I highly doubt (To the point of calling it an outright impossibility.) The development of C# becoming a programming language it is fashionable to write operating systems in.

[http://en.wikipedia.org/wiki/Singularity_%28operating_system%29](http://en.wikipedia.org/wiki/Singularity_%28operating_system%29)

---

### Post by Thewhistlingwind on 2011-08-09
> **directhex said:**
> [http://en.wikipedia.org/wiki/Singularity_%28operating_system%29]("http://en.wikipedia.org/wiki/Singularity_%28operating_system%29")

[http://en.wikipedia.org/wiki/Cosmos_%28operating_system%29](http://en.wikipedia.org/wiki/Cosmos_%28operating_system%29)

[http://en.wikipedia.org/wiki/SharpOS_%28operating_system%29](http://en.wikipedia.org/wiki/SharpOS_%28operating_system%29)

Do those really change anything?

I could say that microkernels won't ever gain mainstream acceptance, and you can point me to some microkernel operating systems, and it still won't invalidate my statement.

Or, I could say that Lisp will almost surely never be a fashionable language to write operating systems in, and you can point me to the Lisp machines/Emacs (Emacs is described on their website as being, in a sense, an operating system.), we can play that game all day.

As long as an language is turing complete, a "operating system" is possible. If a language has a large enough following, one will inevitably be attempted. That STILL doesn't change that C# is NOT a language for writing operating systems.

EDIT: Also, Singularity still uses C and C++, according to the article.

---

### Post by DangerOnTheRanger on 2011-08-10
I don't know if any of you have attempted to make an OS from scratch, but let me tell you, it's hard enough to write VGA drivers and memory allocation alone. A JVM on top of that? *faints*

---

### Post by JDShu on 2011-08-10
> **RoflHaxBbq said:**
> C will always be superior for programming an OS, regardless of how much people may prefer Java.

At one time, people said this about ASM :P

---

### Post by disabledaccount on 2011-08-10
> **JDShu said:**
> At one time, people said this about ASM :P
And that is still true. C is/can be very close to ASM in terms of data structures management, in C++ You should avoid using classes ( :) )
Java, Basic, even shell scripts were designed to write applications fast and easy, without need to know HW, digital signals relationships, etc.

---

### Post by psusi on 2011-08-10
> **tomazzi said:**
> And that is still true. C is/can be very close to ASM in terms of data structures management, in C++ You should avoid using classes ( :) )

No, you shouldn't.  The only difference between class and struct is the default protection ( private vs public ).  There is no difference between a polymorphic class hierarchy in C++ using virtual methods and the common C approach of using a struct full of function pointers that is commonly used in every kernel including Linux.  Except of course that it is much easier to read and write in C++.

Someone asked yesterday about the difference between sockaddr, sockaddr_in, and sockaddr_un.  You could implement those in C++ with a base class sockaddr, and two derived classes for sockaddr_in and sockaddr_un, and there would be no difference in the generated asm.

There are also some ways where the C++ method can turn out to generate MORE efficient asm than C.  Take the difference between printf( "Hello World" ) and cout << "Hello World";.  The former requires a function call to a library function that has to do a bunch of string parsing and copying before finally calling write().  The latter can be inlined and optimized by the compiler to a direct call to write().

---

### Post by ZaphodFJ on 2011-08-10
> **Thewhistlingwind said:**
> C# is proprietary Java.

So the answer is still no.

Seconded.  Too many patent issues surround C# - see: [http://en.wikipedia.org/wiki/C_Sharp_%28programming_language%29#Standardization_and_licensing](http://en.wikipedia.org/wiki/C_Sharp_%28programming_language%29#Standardization_and_licensing)

---

### Post by disabledaccount on 2011-08-10
> **psusi said:**
> No, you shouldn't.  The only difference between class and struct is the default protection ( private vs public ).  There is no difference between a polymorphic class hierarchy in C++ using virtual methods and the common C approach of using a struct full of function pointers that is commonly used in every kernel including Linux.  Except of course that it is much easier to read and write in C++.

Someone asked yesterday about the difference between sockaddr, sockaddr_in, and sockaddr_un.  You could implement those in C++ with a base class sockaddr, and two derived classes for sockaddr_in and sockaddr_un, and there would be no difference in the generated asm.

There are also some ways where the C++ method can turn out to generate MORE efficient asm than C.  Take the difference between printf( "Hello World" ) and cout << "Hello World";.  The former requires a function call to a library function that has to do a bunch of string parsing and copying before finally calling write().  The latter can be inlined and optimized by the compiler to a direct call to write().
At first, You should have noticed that I've put a smile in brackets at the end of that sentence - right?
In both languages You can do the same, ofc C++ is easier. But, there is still one big advantage of using C - it's much easier to keep ABI unchanged - what can be considered as compiler "feature" together with more "explicit" functions/data relationships.
Printf example is not really relevant, because if You're writting kernel or driver from scratch, then You have to write streaming support from scratch anyway or provide common interface for all input methods.
Classes are very usefull, but I would say not for low-level programming.

---

### Post by cgroza on 2011-08-10
> **tomazzi said:**
> 
Classes are very usefull, but I would say not for low-level programming.
Why not?

---

### Post by DangerOnTheRanger on 2011-08-10
> **cgroza said:**
> Why not?

There *is* some overhead incurred for calling virtual methods, and while it's not large (1ns or less, in most cases), it can really add up for things like bus I/O. Besides, at the lowest level (like raw I/O), classes really don't make sense.

---

### Post by cgroza on 2011-08-10
> **DangerOnTheRanger said:**
> There *is* some overhead incurred for calling virtual methods, and while it's not large (1ns or less, in most cases), it can really add up for things like bus I/O. Besides, at the lowest level (like raw I/O), classes really don't make sense.
You don't really need to use virtual methods. Just look at the C++ standard containers, they all have a common interface, but no common base.

---

### Post by matt_symes on 2011-08-10
"Will Java evantually replace C/C++ for OS Development?"

No.

---

### Post by DangerOnTheRanger on 2011-08-10
> **cgroza said:**
> You don't really need to use virtual methods. Just look at the C++ standard containers, they all have a common interface, but no common base.

That's true, but how will you override behavior otherwise (not to mention the fact you can't pass each of those containers to the same method)? Besides, how would you write a class for raw port I/O? A stand-alone function would be much easier.

---

### Post by disabledaccount on 2011-08-10
> **cgroza said:**
> You don't really need to use virtual methods. Just look at the C++ standard containers, they all have a common interface, but no common base.As I said before, C++ can be used to write low-level software - but this puts limitations on using "convenient features". Standard containers are not good for efficient programming - You have to create dedicated data structures and dedicated functions to deal with them. That means CPP will effectively work/look like pure C, because then it can produce equivalent machine code for different platforms using different compilers, thus giving predictable performance and code size.
You have to consider architecture limitations, data alignment, byte order, etc - this effectively makes most of standard functions unusable (or at least not efficient). Additionally, it's obvious that some portions of code will have to be written directly in ASM to keep proper signals timings and/or allow to use some special HW functions.

---

### Post by cgroza on 2011-08-10
> **DangerOnTheRanger said:**
> That's true, but how will you override behavior otherwise (not to mention the fact you can't pass each of those containers to the same method)?
Templates and iterators can be used to do that.

---

### Post by DangerOnTheRanger on 2011-08-10
> **cgroza said:**
> Templates and iterators can be used to do that.

Slowing the OS that uses it down even further.

---

### Post by cgroza on 2011-08-10
> **DangerOnTheRanger said:**
> Slowing the OS that uses it down even further.
All the template magic happens at compile time. I do not see any penalty other than slightly bigger object code.

---

### Post by DangerOnTheRanger on 2011-08-10
> **cgroza said:**
> All the template magic happens at compile time. I do not see any penalty other than slightly bigger object code.

Templates don't incur a speed penalty; iterators, on the other hand...

---

### Post by ve4cib on 2011-08-10
> **tomazzi said:**
> 
Classes are very usefull, but I would say not for low-level programming.

Clearly written by someone who has never done much low-level programming.

Classes are useful for low-level programming in the same ways they're useful for high-level programming; they provide convenient ways of wrapping variables and functions together into one convenient black-box.  Inheritance and the more convoluted OO concepts are maybe less useful, since low-level programming typically involves simpler objects like queues, heaps, and stacks.  But to say that classes as a whole are not useful is a gross over-statement of the situation.

---

### Post by DangerOnTheRanger on 2011-08-10
> **ve4cib said:**
> Clearly written by someone who has never done much low-level programming.

Classes are useful for low-level programming in the same ways they're useful for high-level programming; they provide convenient ways of wrapping variables and functions together into one convenient black-box.  Inheritance and the more convoluted OO concepts are maybe less useful, since low-level programming typically involves simpler objects like queues, heaps, and stacks.  But to say that classes as a whole are not useful is a gross over-statement of the situation.

Clearly written by someone who hasn't coded their own OS.
Classes just don't make sense for the truly low-level things like various port I/O, and other things along that line.

---

### Post by ve4cib on 2011-08-10
> **DangerOnTheRanger said:**
> Clearly written by someone who hasn't coded their own OS.
Classes just don't make sense for the truly low-level things like various port I/O, and other things along that line.

*cough* [Google code project of the OS I'm working on](http://code.google.com/p/frigos/) *cough*

Yes, I admit it may seem hypocritical of me to have written in in C, and arguing in favour of using classes in an OS.  But I'm forking an existing project that was written in C, so it was easier to keep going with it than to start again from scratch and rewrite everything with classes.

I just don't understand your argument.  You say "classes don't make sense" but don't elaborate as to why.  From my perspective a class is simply a nice container for an entity that has to contain both functions and data, something often re-implemented using structs and function pointers in a C program.  So if C programmers re-implement classes using a struct, why does it not make sense for a C++ programmer to use classes to create an OS?

Also, Haiku, as far as I know, is written in C++ using classes.  And it's not a little toy OS like what you or I probably are working on.

Please elaborate on your perspective, because quite honestly I do not understand it.

---

### Post by MasterNetra on 2011-08-11
No, And why would you...If you thought Windows lagged a OS made of java would most probably be worse. Or at least I would think so.

---

### Post by disabledaccount on 2011-08-11
> **ve4cib said:**
> *cough* [Google code project of the OS I'm working on]("http://code.google.com/p/frigos/") *cough*
What a coincidence, I've written multitasking OS for AVR too - fully in  asm, preemptive, supporting processes (separate stacks, registers state  saving) and threads, crash tracing, I/O and IRQ queues, cpu load  monitor. Whole OS was less than 900bytes - it could easily fit ATmega8  :) You should try AVR ASM - its easy, and faaar more efficient than  C/CPP.

> **ve4cib said:**
> I just don't understand your argument.  You say "classes don't make  sense" but don't elaborate as to why.  From my perspective a class is  simply a nice container for an entity that has to contain both functions  and data, something often re-implemented using structs and function  pointers in a C program.  So if C programmers re-implement classes using  a struct, why does it not make sense for a C++ programmer to use  classes to create an OS?

My point was, that classes are "hiding the truth" about what will happen after compilation (eg constructors/destructors, hidden realocations). Structs and funcions are very close to how the machine code will work/look like (it's very much like advanced macros for ASM). Therefore I see no reason to use or reimplement classes for low level code - it has to be as fast as possible, because this affects whole OS and all applications.

---

### Post by ninjaaron on 2011-08-11
Eh... I don't think a kernel could be coded in Java, but an entire user-space can be.  Android basically does everything with a clone of Java (for which they are being sued by Oracle at the moment).  Course, that is running, as everyone here knows, over a Linux kernel, which is coded in C.

---

### Post by psusi on 2011-08-11
> **DangerOnTheRanger said:**
> Templates don't incur a speed penalty; iterators, on the other hand...

Not necessarily.  An iterator is an abstraction of a pointer.  In many cases, it IS just a pointer.  You can't get much more efficient than that.

> **tomazzi said:**
> You should try AVR ASM - its easy, and faaar more efficient than  C/CPP.

Any decent C compiler will generate ASM that is difficult, if not impossible to beat by hand.

> **tomazzi said:**
> My point was, that classes are "hiding the truth" about what will happen after compilation (eg constructors/destructors, hidden realocations).

At their heart, classes are simply grouping your structure with your functions that manipulate it, and modifying the namespace rules so that referencing the members of the structure requires less typing.  That makes the code easier to write, easier to read, and easier to debug, all without any cost compared to doing the same thing in C or C++.

> **tomazzi said:**
> Structs and funcions are very close to how the machine code will work/look like (it's very much like advanced macros for ASM). Therefore I see no reason to use or reimplement classes for low level code - it has to be as fast as possible, because this affects whole OS and all applications.

The reason is because it is good programming practice.  It is the only way to write large code bodies and maintain readability of the code, and your sanity.  Take a look at the Linux kernel.  It is full of classes.  When you have a dozen different filesystem drivers you can load, you write the VFS to interface with an abstract class that represents a generic filesystem so it can be free of the details of each and every supported filesystem.

The VFS defines struct file_operations, and the fat filesystem driver defines fat_file_operations as an instance of it, filling out the function pointers to point to the fat functions.

You can do that with a C++ base and derived class with virtual methods, and you would get exactly the same ASM.  The difference is that the C++ code is easier to read, write, and debug.

The Linux kernel is FULL of OOP because it's good programming practice.  classes are just C++'s way of doing OOP easier than C, but no less efficient.

---

### Post by DangerOnTheRanger on 2011-08-11
> **ve4cib said:**
> *cough* [Google code project of the OS I'm working on]("http://code.google.com/p/frigos/") *cough*

Yes, I admit it may seem hypocritical of me to have written in in C, and arguing in favour of using classes in an OS.  But I'm forking an existing project that was written in C, so it was easier to keep going with it than to start again from scratch and rewrite everything with classes.

I just don't understand your argument.  You say "classes don't make sense" but don't elaborate as to why.  From my perspective a class is simply a nice container for an entity that has to contain both functions and data, something often re-implemented using structs and function pointers in a C program.  So if C programmers re-implement classes using a struct, why does it not make sense for a C++ programmer to use classes to create an OS?

Also, Haiku, as far as I know, is written in C++ using classes.  And it's not a little toy OS like what you or I probably are working on.

Please elaborate on your perspective, because quite honestly I do not understand it.

Take a look at the code at [http://www.jamesmolloy.co.uk/tutorial_html/3.-The%20Screen.html](http://www.jamesmolloy.co.uk/tutorial_html/3.-The%20Screen.html), and show me how you would put it in a class.

That's just a simple example - I have many more.

---

### Post by cgroza on 2011-08-11
> **DangerOnTheRanger said:**
> Take a look at the code at [http://www.jamesmolloy.co.uk/tutorial_html/3.-The%20Screen.html]("http://www.jamesmolloy.co.uk/tutorial_html/3.-The%20Screen.html"), and show me how you would put it in a class.

That's just a simple example - I have many more.
Actually, you can put that into a class. Classes are perfect for representing concepts such as a monitor in your example.
I am not against functions and I support OOP. Both of them have their own place.

---

### Post by ve4cib on 2011-08-11
> **tomazzi said:**
> What a coincidence, I've written multitasking OS for AVR too - fully in  asm, preemptive, supporting processes (separate stacks, registers state  saving) and threads, crash tracing, I/O and IRQ queues, cpu load  monitor. Whole OS was less than 900bytes - it could easily fit ATmega8  :) You should try AVR ASM - its easy, and faaar more efficient than  C/CPP.

"Efficiency" is one of the most vague, and often misused terms in computer science.  Modern compilers are exceptionally good at optimizing code to run as efficiently as possible from the machine's perspective.  9 times out of 10 compiler-generated assembly code will be as good or better than hand-written assembly, and is easier to maintain since C or C++ source files are inherently more legible.

For my time it's simply not worth writing the whole OS in assembly when I can spend a fraction of the time doing it in C, and having the resulting assembler be as good or better than what I could have written in the first place.


> Take a look at the code at [http://www.jamesmolloy.co.uk/tutoria...%20Screen.html](http://www.jamesmolloy.co.uk/tutoria...%20Screen.html), and show me how you would put it in a class.

That's just a simple example - I have many more.

Please tell me you're joking by somehow using this as an example of something that could not be wrapped up in a class.  As a trivial solution one could take all of the global functions and simply use them as public static members of a class, encapsulating them better with less risk of accidentally clobbering previous function definitions.  Or you could create a singleton class with those same functions as instance members, along with a private constructor/destructor and a static "getUniqueInstance()" function.  Or you could create a Screen class that could be instantiated multiple times -- once for each device -- but is otherwise the same as the singleton design I just mentioned.  Furthermore, a Serial class could be used to contain the cryptically named "outb" "inb" and "outw" serial functions.

---

### Post by 3Miro on 2011-08-11
The Linux kernel is almost entirely (if not entirely) written in C and it does not contain classes. The OOP is a good way to do programming regardless of what you want to code and you can do OOP in any language. However, Classes force OOP thus impose restrictions that do not belong in something that needs to be as optimized as a kernel.

The problem with the Java language is that Classes is the only way to do anything. This makes the language good for what it does, but very rigid for other things. Unless Java sees a major transformation, it will not be used for coding kernels.

---

### Post by disabledaccount on 2011-08-11
> **ve4cib said:**
> "Efficiency" is one of the most vague, and often  misused terms in computer science.  Modern compilers are exceptionally  good at optimizing code to run as efficiently as possible from the  machine's perspective.  9 times out of 10 compiler-generated assembly  code will be as good or better than hand-written assembly, and is easier  to maintain since C or C++ source files are inherently more  legible.
At high abstraction levels there is not much to gain by  writting directly in asm, with the possible exception of some  time-critical fragments. 
But with C/CPP and any other language You just cant do the very basic  thing: control the execution time. By writting in ASM I know exactly how  much time I need to switch process/thread and thus what value is  absolute minimum for time slice at what CPU frequency. This is  especially important in small embedded systems like those based on  low-power/low clock ARMs, AVRs, etc. This is also reason why in C/CPP  it's practically impossible to write efficient hardware emulators (f.e.  software I2C, 1-wire).
Code optimisation: compilers are good in solving **typical** situations  in **typical** programs. Low level programming is far from that, because  every wasted clock cycle moves Your code more and more closer to  trashcan :)

> **ve4cib said:**
> For my time it's simply not worth writing the  whole OS in assembly when I can spend a fraction of the time doing it in  C, and having the resulting assembler be as good or better than what I  could have written in the first place.Simple, real-life example:
 AVR core is 8-bit, but in C/CPP you can write:
 int16_t a, b;
 a+=b; -> 4 asm instructions, 4 clock ticks
 a=a*b; -> 16 asm instructions, 16clk
 a=a/b; -> 24 asm instructions in loop, ~**350**clk - You **have** to know asm implementation of 16 by 16 bit division, because otherwise Your code will be crappy.
 Then You can write:
 a=a*(1/b); -> 32 asm instructions, ~**200**clk - still far from perfection, but if You additionaly know the range of values, then You can modify the asm code and reduce exec. time to ~100-150clk or even less.

---

### Post by ve4cib on 2011-08-11
> **tomazzi said:**
> Code optimisation: compilers are good in solving **typical** situations  in **typical** programs. Low level programming is far from that, because  every wasted clock cycle moves Your code more and more closer to  trashcan :)

Simple, real-life example:
 AVR core is 8-bit, but in C/CPP you can write:
 int16_t a, b;
 a+=b; -> 4 asm instructions, 4 clock ticks
 a=a*b; -> 16 asm instructions, 16clk
 a=a/b; -> 24 asm instructions in loop, ~**350**clk - You **have** to know asm implementation of 16 by 16 bit division, because otherwise Your code will be crappy.
 Then You can write:
 a=a*(1/b); -> 32 asm instructions, ~**200**clk - still far from perfection, but if You additionaly know the range of values, then You can modify the asm code and reduce exec. time to ~100-150clk or even less.

I'll grant you that there are limited instances where inline assembly is desirable (or necessary) to solve specific issues.  Task-switching in a preemptive scheduler is one very good example of when you need access to the assembler's push and pop abilities.  Your example of division is another.  But I fail to see the logic in writing everything in assembler when it comes to low-level programming.  If it was truly "better" to write everything in assembler then C would not have been invented, and the Linux kernel as we know it would not exist.

Another possible solution is to know that division is inherently expensive and design algorithms that work around this problem by not relying on division/modulo operations (or at the very least minimizing their use).

---

### Post by disabledaccount on 2011-08-12
The difference between small multitasking OS for simple microcontroler and something such complex like linux kernel is just *huge*. Of course it doesn't make sense to write such complex sytem fully in assembly, but for devices that have very limitted resources like 8KB Ram, no FPU, no cache, no MMU, no DMA assembly is just the best solution - it's not that hard to write several hundreds lines of ASM.

---

### Post by ZaphodFJ on 2011-08-17
> **3Miro said:**
> The Linux kernel is almost entirely (if not entirely) written in C and it does not contain classes. The OOP is a good way to do programming regardless of what you want to code and you can do OOP in any language. However, Classes force OOP thus impose restrictions that do not belong in something that needs to be as optimized as a kernel.

The problem with the Java language is that Classes is the only way to do anything. This makes the language good for what it does, but very rigid for other things. Unless Java sees a major transformation, it will not be used for coding kernels.

A perfectly fair point.  Something many people overlook in saying "If you can use C++ then Java, which is also OOP should do fine", is that C++ is essentially C on OO-driven steroids.  The first C++ compilers translated the code into C, and passed it onto a C-compiler.

Hence, anything written in C++ can be expressed in C.  It's just a helluva lot quicker to use the classes already defined as part of C++ than to start from scratch.  If you are writing C++ and don't fancy doing OOP, just switch to C and the C++ compiler will understand.

As for dropping regular C in the middle of Java.... nope, not what it was designed for.

Java is good at what it was designed for.  C is good at what it was designed for (and dreadfully cumbersome in other instances).  There are many instances where neither language is required.  Unfortunately many CS courses seem to emphasise Java and VB, thereby conveying the idea that these languages can be used for everything under the sun.  In reality, any big project will use a range of languages, playing to the strengths of each. UI is a much different problem to printer drivers, for example.

Choose the tool that is best for the job you are doing at the time.

FWIW - Windows uses C, C++, C# and..... assembly code.  Now when did you last see assembly code taught to CS majors?  See: [http://social.microsoft.com/Forums/en-US/windowshpcacademic/thread/65a1fe05-9c1d-48bf-bd40-148e6b3da9f1](http://social.microsoft.com/Forums/en-US/windowshpcacademic/thread/65a1fe05-9c1d-48bf-bd40-148e6b3da9f1)

---

### Post by unknownPoster on 2011-08-17
> **ZaphodFJ said:**
> .  Now when did you last see assembly code taught to CS majors? 

Every semester at my University. There are two assembly based classes which are taught every semester and are required classes.

We also learn Java, C, C++, LISP, and Python.

---

### Post by NovaAesa on 2011-08-17
I'm doing CS as well and have taken an ASM subject (programming on a microcontroller). It wasn't a core class, but rather a directed elective.

---

### Post by Thewhistlingwind on 2011-08-17
> **unknownPoster said:**
> Every semester at my University. There are two assembly based classes which are taught every semester and are required classes.

We also learn Java, C, C++, LISP, and Python.

Thats actually not a bad line up.

---

### Post by ve4cib on 2011-08-17
> **ZaphodFJ said:**
> Now when did you last see assembly code taught to CS majors?

How about my honours CS degree that I completed in 2008?  Or my friends who are still undergrads?  Assembler is definitely still taught at my university.  And I refuse to believe that we're the only one that does.

When I was in second-year we had a mandatory course that covered SPARC and Motorolla 68k assembly, a third-year course that used MIPS very heavily (we actually built a MIPS CPU in LogicWorks as the last assignment), and I've had to know various Atmel-family assembly languages for fourth-year and grad-level courses (mainly for the AtMega169 and AtMega128).

(And no, we didn't just learn various assembly languages; we also covered Java, C, C++, Prolog, and Lisp.  Perl, PHP, and C# were taught/used in courses I never took.)

---

