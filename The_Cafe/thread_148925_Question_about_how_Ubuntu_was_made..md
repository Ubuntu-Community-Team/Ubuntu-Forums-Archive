---
title: "Question about how Ubuntu was made."
date: 2006-03-22
forum: The Cafe
---

### Post by ReviewSpin on 2006-03-22
I am learning HTML and other languagfes right now, but a ways down the road -- maybe 5 years or so -- when I have mastered all the ineternet languages, i would like to know how to make software. OS is one of them. Since I all ready know its going to be hell to do, I would like to start from linux and build it to what I would like. Anyway, what language is Ubuntu? Pearl? Or...what? (And is i the same for Linux...?)

Thanks.

---

### Post by briancurtin on 2006-03-22
C and/or C++

---

### Post by Kerberos on 2006-03-23
HTML isn't a computer language technically.  PHP is a language that generates HTML and is definatley worth a look if you want to get into programming, and is certainly much less hardcore than C/C++.

---

### Post by Iandefor on 2006-03-23
Lots of different languages. The Linux kernel itself is composed of C/ASM (I believe... I'm probably wrong, though), but some tools are based on Perl, some on C++, etc. The way a Linux distribution is structured, you should know, is that it's basis is the Linux kernel and everything else is built around that. There isn't any such thing as the Linux "OS". Beyond the kernel, it's all just software selection, which can be written in a variety of languages- from bash scripting to C.

And writing an OS is a *huge* undertaking. I don't believe that there is a single person on earth capable of writing an OS.

---

### Post by stuporglue on 2006-03-23
> I don't believe that there is a single person on earth capable of writing an OS.

Sure there are. Computer Science students have to do it all the time. Of course it would be an extremetly limited OS, but it is quite possible. 

In this one they write an emulated OS, but I believe they have to write the device drivers, file system drivers (for FAT 12, I think) etc. 
[http://ilab.cs.byu.edu/cs345/](http://ilab.cs.byu.edu/cs345/)

At the end of the course any decent student could write a basic OS by them selves.

Edit: Replying to the original posters question...
> I would like to start from linux and build it to what I would like. Anyway, what language is Ubuntu? Pearl? Or...what? (And is i the same for Linux...?)

Sounds like what you're really trying to do is create your own distribution of Linux. IF you're after that, what you probably want to do is set up a test box, and put Linux From Scratch on it. You'll get familiar with all the guts of Linux, and have your own custom setup when you're done.  LFS has lots of tutorials on how to do it, with plenty of room for deviation and customization.  [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)   And I don't think you actually need any programming experience to set up LFS, just good instruction following capabilities.

---

### Post by s|k on 2006-03-23
[QUOTE=ReviewSpin] when I have mastered all the ineternet languages,.[/QUOTE]I suppose this is possible, but not in a few years, and you don't really need to. Just find something you enjoy. As for 'internet language' I don't if you're talking about client side stuff like HTML, JavaScript, or CSS. That's probably a good start. Get a good book, those are really helpful when you're beginning.

---

### Post by sebast on 2006-03-23
ReviewSpin,

I would recommend you to start by reading the [How to Become a Hacker]("http://www.catb.org/~esr/faqs/hacker-howto.html") text by [Eric S. Raymond]("http://en.wikipedia.org/wiki/Eric_S._Raymond")

The text does a great job at trying to explain the different programming languages and operating systems and with what to start when you want to master all those things.

HTML is a good thing to learn when beginning to help become familiar with structuring things.

Has for creating an Operating System, you first have to know that it's a complicated task and that you should become a good programmer before even thinking about building an OS. But, what you can and should do is learn the basics of [Operating Systems]("http://en.wikipedia.org/wiki/Operating_system"), their job and how they work in general.

---

### Post by Iandefor on 2006-03-23
[quote=stuporglue]Sure there are. Computer Science students have to do it all the time. Of course it would be an extremetly limited OS, but it is quite possible. 

In this one they write an emulated OS, but I believe they have to write the device drivers, file system drivers (for FAT 12, I think) etc. 
[http://ilab.cs.byu.edu/cs345/]("http://ilab.cs.byu.edu/cs345/")

At the end of the course any decent student could write a basic OS by them selves.[/quote] I made the implicit assumption that OS means full operating system- like a typical Linux distro today. My bad. 

And before this goes any further, there's a big difference between the operating systems CS students write and operating systems that could be deployed on a significant scale- like Windows, Mac OS X, and Linux/Unix, and by "full operating system", I mean an operating system that could be deployed on a significant scale.

---

### Post by IYY on 2006-03-23
If you really want to understand your operating system, Gentoo would suit you better than Ubuntu.

---

### Post by Kvark on 2006-03-23
As stuporglue said. You don't program a Linux distribution like Ubuntu. You take a lot of software such as the Linux kernel, GNU toolchain, X server, Gnome, Open Office and anything else you want. Then you compile it all and configure it to work together and form a complete system that is customized exactly the way you want it. A lot of people say installing Linux From Scratch is the best way to learn how to do that.

As for programming languages, don't worry about learning them all. Once you are good at a couple languages you can start programming in any language in a matter of hours with a good reference book by your side. You'll know that for example "here I need a loop" and check in the reference what the exact syntax for loops are in the new language. The first program you write in a new language will not make full use of that language's potential but it will work. So once you know one language in each area learn the rest if/when you need them.

The best way to learn programming is IMO to play programming games like [Robocode]("http://robocode.sourceforge.net/") plus undertake challanges like "write a program that finds prime numbers" or "write a program that can play tic tac toe".

---

### Post by ReviewSpin on 2006-03-24
First off, sorry I haven't been on. I haven't had time to do much replieng, just glancing at everything.


Thank you guys for all the advice you have given me. I'll take this in and consider it as I am learning the langauges I want to learn (And, I actually want to learn XML, HTMl and CSS -- not in the order, btw). Then I'll go onto computer languages.


And I didn't plan to do all this by myself -- theres no chance in heaven I could design it all (I want to change the looks a bit, make it more 'flashy'...so long it doesn't slow the OS down).

Anyway, I will be reading those pages and I will be trying out that Linux from Scratch. Gatta start somewhere. And, btw, I will be switching to Gentoo once I learn the basics of Linux -- someone on Gentoo's forum mention Ubuntu being a good transition distro. And so far, it has been easy to use. Besides this installing thing..but I am getting a handle on it (I also want to change that, too). 

Anyway....thats me. Thanks.

---

### Post by briancurtin on 2006-03-24
[QUOTE=IYY]If you really want to understand your operating system, Gentoo would suit you better than Ubuntu.[/QUOTE]
Arch is also in this category, and something to check out.

---

### Post by Kvark on 2006-03-25
[QUOTE=sebast]I would recommend you to start by reading the [How to Become a Hacker]("http://www.catb.org/~esr/faqs/hacker-howto.html") text by [Eric S. Raymond]("http://en.wikipedia.org/wiki/Eric_S._Raymond")[/QUOTE]
That is some great advice, I'm bookmarking that to show to anyone who wants to become a good programmer. Specially the recommendation on which languages to learn is a good path to take.

[QUOTE=ReviewSpin]And I didn't plan to do all this by myself -- theres no chance in heaven I could design it all (I want to change the looks a bit, make it more 'flashy'...so long it doesn't slow the OS down).[/QUOTE]
There are plenty of howtos in this forum on how to add flashy effects and stuff to change the looks of Ubuntu. Playing around with those is a must if you want to make a Linux system look flashy.

---

