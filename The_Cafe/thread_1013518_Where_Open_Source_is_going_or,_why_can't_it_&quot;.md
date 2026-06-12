---
title: "Where Open Source is going or, why can't it &quot;Just Work (TM)&quot;"
date: 2008-12-16
forum: The Cafe
---

### Post by Delever on 2008-12-16
Have you ever wondered why can't everything just work? Every program, in every operating system (OS). I mean, looking at programming from user point-of-view, program is just sequence of strict and well-defined instructions, so why is it not possible to make computer **understand unknown** instructions, or **translate** them **to instructions** it can understand? Or, why can't everyone find **the best way to write programs**?

Well, if you thought that way, there is a surprise: basically, that's what programmers do. **Making all things compatible**, that's the ultimate goal. Some take only small part in achieving this goal, some dedicate all their time to it. And **Open Source** is big part of this. Let me explain in more detail.

There are many ways to write a program, many ways it can be executed, any many ways it can be dependent on platform or OS (from now, i will say just "OS").

[INDENT]
**Way 0. "Bare API" programs, using OS directly, or - *incompatible way*.**

Popular operating systems do many things in different way: like memory management, program execution, file system implementation, user interface, etc. If program needs to access these features, it uses libraries, provided by target OS. API (Application Programming Interface) is defined way in which those libraries can be accessed.

Many programs are written for single OS, because it takes time to implement same features on different system, and they may even be incompatible with next version of the same OS.

This category has many commercial and proprietary applications, including games, and the only few ways to run them on different systems are discussed on ways 4 and 5.

**Way 1. Programs using multi-platform libraries, or - *let's hide everything platform-dependent*.**

Put all platform dependent implementation to library and define API, which can be used on any platform. That solves the problem. For a while.

You see, if you use one library, which can work on A and B platforms, and another library for B and C platforms, your final program will only work for B platform. Not only that:
[LIST]
[*]It requires knowledge of target library platforms,
[*]It requires programmer to track libraries and update them to new versions,
[*]Program itself needs to be compiled on different compilers, which are (not) always compatible.
[/LIST]
In other words, programmer still needs to make additional effort to make program compatible, and that effort is not small.

However, situation is rapidly changing. There are more libraries than needed ready to perform any multi-platform task you can think of ([boost]("http://www.boost.org/doc/libs/1_37_0/libs/libraries.htm") is good example)

Furthermore, open source libraries are growing rapidly, and are available for both open and closed projects. So the next time some company finds out that their old proprietary math library is no longer working on next OS version, they might *just* migrate to boost, and by doing that, migrate closer to other platforms.

**Way 2. Programs using virtual runtime platform, or - *so let's make platform which does not exist but is "the best"*.**

How to simplify all work for programmers and force them to make less mistakes? - That probably the question asked by Java designers.

Java was named as "the" solution to incompatibility by many. "Works anywhere" was real buzzword, "slow anywhere" that's what John said (this IS a joke, it is not slow now).

Idea was, that same code could run **on any system**, without checking what system it is running on, and without compiling it for different systems. How could that be done? Well, creating new **virtual system**, and **translating virtual system calls to real system calls**.

Meet Java Virtual Machine (JVM), which can run Your Java program anywhere. Of course, virtual machine itself must be implemented on target platform, and you must use libraries designed by Sun.

There is one large competitor in this area with virtual machine - .NET. The problem is, authors forgot other platforms. Yeah, I am joking - they haven't forgot, .NET is actually **designed** for different platforms, just original **implementation** is only for Windows. And there is Mono implementation of it. What Microsoft did - took Java as example, learned from it's mistakes, and designed clean API with more than one language in mind.

The point is - both Java and .NET/Mono has open sourced implementations, and they are not disappearing anywhere. So why not every .NET program works on Linux? Because it is easy in .NET to use native libraries (so, back to ***way 0***). For example, just for splash screen.

**Way 3. Programs using interpreted language, or - *let's make language do what programmer, not OS needs*.**

This approach got popular when making "simple" scripting languages to do "just task at hand". However, it appears that what is good for task at hand, can be good for big projects too.

Javascript. Humble browser nowadays is actually virtual machine, which can run some amazing applications. From any page with dynamic elements, AJAX, GMail, to "Web <insert number here>" and "cloud computing", it appears to have grown as new trend. Where is it going? I don't know, but it will work not only on any OS, but on any browser. And you can see the source!

Another example of language for programmer, and not for platform, is Python. Implements substantial amount of features as language elements in concise and easy-to-use way, provides huge standard library to cover many aspects of OS, helping with portability.

Approach is different here: 
Instead of compiling program on developers machine (way 0 and 1), it is compiled on user's machine. 
Instead of compiling for virtual system on developer's machine to bytecode, then compiling bytecode for real system on user's machine (way 2), it is compiled once.

Of course, programmer, using Python (or any similar scripting language)  still needs to choose libraries, but they are at much higher level (like GNOME or KDE).

And it is open source.

**Way 4. Programs, which can run on emulation layer, or - *let's remake whole target system libraries*.**

Some programs use direct system calls (way 0), and many of them (for example, DirectX). So, what if we make libraries, which look and behave exactly the same way as program expects, but runs on different OS?

It turned out Wine is more work than ever will be expected. Yes, we have it, it does miracles, but target OS, sadly, is moving target, and will remain such. But it provides needed compatibility in case which otherwise would be impossible.

And it is open source as well.

**Way 5. Programs, which can be used on virtual machines, or - *OS in a box*.**

Probably, ages ago, in some dark dusty university room, surrounded by large math books, some professor said: "it may be possible to create processor which can work, but does not exist." So they did it.

VirtualBox, VMware, .., or some virtualization method built into kernel - all are made to fool OS into thinking that it is alone on computer, while actually it is running inside another OS (emulated).

It is like cheating, because program is not actually running on main OS (host), it is running in it's native environment, so of course it works!

However, if it gets the job done, who cares.
[/INDENT]


So we are solving this "small" compatibility problem on at least 5 fronts, each of them quite different. On each front, open source has indeed strong position, and that position seems to get only stronger with time.

Languages are improving, faster machines change the ways problem is approached ("compiling on user's computer - are you mad??"). And situation is only getting better.

So what actual results can we expect from this? What user will see? Linux victory? Well, not exactly.

All these approaches, when well done (except maybe 5th) make porting application to another system easier, make running not ported applications easier, and in the end **make operating system largely irrelevant, but still necessary component in any case**.

So, next time you see regressions, and ask, why developers are touching things that were working, remember that they are making software more compatible, with anything it can be compatible.

---

### Post by acelin on 2008-12-16
This stinks of copypasta.

---

### Post by Delever on 2008-12-16
> **acelin said:**
> This stinks of copypasta.

Thanks.

---

### Post by cardinals_fan on 2008-12-16
You have some good points, but the "just works" slogan is silly and doesn't really apply to this discussion anyway.

---

### Post by MaxIBoy on 2008-12-16
> **acelin said:**
> This stinks of copypasta.
No, it's legit. Google is a handy tool to refer to before making accusations.


As for the discussion at hand:
The post is a very good observation of the current situation, but I think a few things need elaboration. For an example, you're missing a lot of the *advantages* of "way 0" and "way 1."

---

### Post by Delever on 2008-12-17
> **MaxIBoy said:**
> 
The post is a very good observation of the current situation, but I think a few things need elaboration. For an example, you're missing a lot of the *advantages* of "way 0" and "way 1."

Yes, indeed, native applications will not go anywhere, because there will always be areas where best possible performance is needed, and where architectural differences have to be implemented in different ways.

Mainly graphics, sound, physics and drivers.

---

### Post by Delever on 2008-12-17
> **cardinals_fan said:**
> You have some good points, but the "just works" slogan is silly and doesn't really apply to this discussion anyway.

I was joking a little bit ;)

---

### Post by PryGuy on 2008-12-17
Most programs don't work well out of the box, so I don't like the slogan. Open Source is far more stable compared to the commercial stuff IMHO. The article is defenitely good, but.. too much theory... :)

---

### Post by Takmadeus on 2009-01-04
I find this post brilliant actually, who cares about the title anyway, its the content which is worth ;)

---

### Post by toupeiro on 2009-01-04
To me, the reason all things do not "just work" has nothing to do with libraries, programming languages, or developers..  It has 100% to do with licensing and legal matters... Purely native FOSS "just works" a hell of a lot better with other FOSS than proprietary software because developers have the legal license to add that cross-functionality to other FOSS applications, therefore its usually done from the inception of the FOSS program, and done a lot better than an after-the-fact patch to support a proprietary platform.  In cases like that, cross functionality is usually a one-sided road.

If you really want things to just work, then the Open Source business model needs to better demonstrate how the software industry, can thrive financially while still offering the benefits of Free Software and community development.  Lets face it, when IT is applied to other industries, Intellectual property WILL EXIST, and so long as that happens, you will always have someone believing you need proprietary code to protect proprietary information.  Change that mindset, and do so without sacrificing intellectual property, and then you will have your Utopian software environment.

I think it will happen, but it won't be as fast as most people would like.  Paradigms take time to shift.

---

### Post by Delever on 2009-01-06
> **toupeiro said:**
> To me, the reason all things do not "just work" has nothing to do with libraries, programming languages, or developers..  It has 100% to do with licensing and legal matters... Purely native FOSS "just works" a hell of a lot better with other FOSS than proprietary software because developers have the legal license to add that cross-functionality to other FOSS applications, therefore its usually done from the inception of the FOSS program, and done a lot better than an after-the-fact patch to support a proprietary platform.  In cases like that, cross functionality is usually a one-sided road.

If you really want things to just work, then the Open Source business model needs to better demonstrate how the software industry, can thrive financially while still offering the benefits of Free Software and community development.  Lets face it, when IT is applied to other industries, Intellectual property WILL EXIST, and so long as that happens, you will always have someone believing you need proprietary code to protect proprietary information.  Change that mindset, and do so without sacrificing intellectual property, and then you will have your Utopian software environment.

I think it will happen, but it won't be as fast as most people would like.  Paradigms take time to shift.

Yes, maybe it was mistake to use "Just work" in title, but hey, I added (TM)! :)

I find having code Open both invaluable and overwhelming. Invaluable, because it can provide different pieces of next project you are making, overwhelming, because sometimes it is faster to write your own code than understand how these other pieces work and make them work together.

I am thinking about software which can expose and automatically document different kinds of code blocks, this way helping developers to find what is actually done out there, and most importantly, how. Like an abstraction layer for different tasks, yet easily usable without much hassle. Maybe this would require set of standards for documenting code of any programming language, and standards for creating building blocks in any language. Sort of like common code wikipedia. It's not that writing such code is hard, it's all about writing code that is actually needed for the task, and quickly finding and incorporating code and libraries from other sources, to avoid reinventing the wheel. Therefore I agree and imagine that proprietary software could hardly exist in such environment.

---

