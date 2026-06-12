---
title: "Linux development...from scratch"
date: 2006-08-31
forum: The Cafe
---

### Post by Skyrail on 2006-08-31
Ok, this may seem a noob like quesiton but I am really interesting in being able to develope something. But first thigns first, what language is linux mainly programmed in? I know that there is a kernal that all linux distros use and then different people and companies build upon that and create distros. So what language are distros usually created with? Is there any where that I can learn how to program, a starter tutorial? and then anotehr one to be used after that, At the moment I don't know any programming, and so developing something I'm looking into the future, maybe a year or two.

However I would really like to learn and so I need someone to point me in the right direction, i.e. downloads, tutorials, books and other things that I may need. So please hlep me out and point me in the right direction as I would really lke to eventually develope something :)

---

### Post by Anonii on 2006-08-31
As far as I know, Linux is programmed mainly in C. (the kernel is pure C)
So if you want to do Kernel Hacking, learn C.
KDE applications are programmed in Qt and GNOME applications in Python and GTK.
From what I know Python is the best language to start with, and thats what I'm doing right now. I found this great guide: [http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/)


Also try reading this thread: 
[http://ubuntuforums.org/showthread.php?t=8682](http://ubuntuforums.org/showthread.php?t=8682)

---

### Post by Colonel Kilkenny on 2006-08-31
Someone hopefully will slap me if I talk nonsense but basically gnome is coded with C & python and KDE with C++. Of course there is a lot of other languages (Java, C#, etc) as well.

edit. And yes, Gnome uses GTK for gui and KDE Qt.

---

### Post by Michael_aust on 2006-08-31
As far as I know Linux is mainly programmed in the various C languages and  probably some parts are done in assembly.

A good language to start learning to program with is python.  It's syntax is very simple and generally quite an easy language.  Its certainly easier then starting out with C++ for example.

> but I am really interesting in being able to develop something

Have you considered documentation for a project.  Projects always need documentation and most are lacking some.  Ok so you do not get the glory like programmers do, people don't remember the people who have documented the Linux kernel they remember Linux Torvalds, Alan Cox etc.

---

### Post by Anonii on 2006-08-31
And since you started the participation subject...

[http://www.ubuntu.com/community/participate](http://www.ubuntu.com/community/participate) 

:)

---

### Post by Skyrail on 2006-08-31
Wow thanks people, that is certainly alot of replies and information :). So by the looks of things Python is the language to learn as a starter, I have heard of it which is a bonus :D another good thing is that I prefer Gnome over KDE (not too sure why yet :D) so that is also another good starting place. I'll have to look into the project documentation aswell and see waht needs doing :) I also doubt that I will be able to get anywhere on my own though :S :( but I will try :) thanks for all the links, I will be looking throuhg them and seeing what I can learn, use, understand :D

---

### Post by amo-ej1 on 2006-08-31
If you're really motivated you can start in any launguage that interests you, and the point of open source is that there are many languages, install 20 random applications and you'll have applications written in more than five programming languages.

The Linux kernel itself is programmed in C, while some low level things (interrupt handling, initial boot of the system, ..) is written in architecture dependant assembly.

The best thing is choose a project you'd like to do and choose a language in function of what you want to do. if you want to create web applications learning C won't get you far, learning php/html/javascript/java will get you much further. Also search for the amount of available documentation, you will find a lot more information about php and java than you will find on prolog. 

The sky is the limit, simply find something to do and do it, try some things, fail, try again and learn ;-)

---

### Post by frup on 2006-08-31
Practice makes perfect... sure for a few months you might not be able to do much always but eventually you begin thinking ;)

---

### Post by bernied on 2006-08-31
Without being anti-ubuntu, because really I'm not, can I suggest that if you want to develop in linux you should first try using a distribution that doesn't hand everything to you on a plate. Ubuntu makes using the operating system so easy that you don't see much of what is going on behind the scenes.

Personally I'd suggest a gentoo install. In a gentoo system everything is built on the target system (this is not completely true, but details...), and you get to customise every application (if you want to). So you get to see the building/compiling process. Keep your ubuntu install as well, you will need it for all the times you mess up your gentoo system and can't access the internet. 

The other 'distribution' to try is Linux From Scratch or LFS, though as I understand it, this is not so much a distribution as a masochistic discipline. LFS users build their own custom systems from source and they don't even have a package manager - this means that they have to manage all software dependencies themselves - sounds like a bad dream to me. 

People will tell you that gentoo and (even more so) LFS are not for beginners, but I built a gentoo server after only using Debian for a couple of months. I was slow and made lots of stupid mistakes, but I learnt loads about how linux works.

As for programming, personally I need a purpose before I can do anything. Think of something you'd like to build, then research what tools you'd need to build it. If you want to mess with the kernel, then find a device that isn't supported and write a driver for it. If it works and follows the standards, it will get included in the kernel. Then you will be immortal!

---

### Post by Skyrail on 2006-08-31
lol 

> 
Then you will be immortal


heh wouldn't that just be great :D. I have tried web development, I'm not the greatest at it but there are too many people out there developing web pages for me to even start tto compete, so I thought why not make somehting that would help me out, so I thought I will need to learn a programming language. Naturally I was interested in Ubuntu being it open source, but as bernied said gentoo  mioght be useful or LFS, I'll have to look into those. I have a few ideas of what I would like to create, altyhough in the end when I've leart how to program and how to modify and make things I want I would rather work in a group with some other peope. But thats in the future when I've learnt mroe about linux, how its built and some programming languages. My main aim for now is to be able to create a driver as you said...for a modem? Is that looking at being too hard :( I just need to get to grips with programming, how linux works tehn I can start something :) so I'll try gentoo out then :)

---

### Post by IYY on 2006-08-31
> My main aim for now is to be able to create a driver as you said...for a modem?

Drivers are difficult to code. You need to start small.

I don't think you need to replace Ubuntu with Gentoo just yet. First, learn Python and C. Learn how to make GTK apps (it's quite simple and there are tutorials on its official site) if you want to make graphical applications. These things you can do just as easily in Ubuntu.

Then, when you understand the languages, you should start looking at some source code and figuring out how things are done by the pros. You should be able to modify existing applications, and make some of your own.

Drivers come later. You'll need to go to a book store (or a very good library) and find a book on writing drivers in *nix systems. It will be a big book, and it will take a long time to learn, but once you're done you will have skills that might score you a sweet job in the future (Linux is becoming very big in the embedded market, and writing drivers is the most important part in that field).

---

### Post by Skyrail on 2006-09-01
heh ok thansk for the heads up :) I'll bear that in mind, I guess thats why people don't just code drivers, they aren't taht easy :D. Ok yeh, so stick with Ubuntu, learn Python and C. Learn how to make GTK aps, and then in the end study source code and work from there :D I'll get back to you when I've done it, give me 3-5 years :P

---

### Post by Michael_aust on 2006-09-01
Another problem with writing drivers i you have to have some knowledge of the actual way modems work (the very technical aspects), not just the ability to code in C or assembly etc.

---

### Post by Skyrail on 2006-09-02
ohnoes...ah well, at least I can just learn PYthon and C and then work on something else...hmm :( ah well :)

---

### Post by DoctorMO on 2006-09-02
Drivers arn't _that_ dificult. you can start with abstracted drivers like printers, scaners ect before you move onto more imbedded drivers in the kernel it's self.

see sane (scanners), gutenprint (printers) and kernel.org (Linux kernel)

You also learn ANSI-C much better if you don't learn python, perl first. they may be easyer languages but they obscure the thinking about structure and I know quite a few programmers that get fustrated with the way C is structured and give up.

---

### Post by abbeychase on 2006-10-10
I would get my feet wet with C which, as a lot have mentioned, the kernel is written in.  You can find many sources online.  Also, a lot of current OS's and applications now are done utilizing C and it's successors C++ and now C# for the .NET framework.  ONce you learn a language like C, everything else seems to be cake.  Good Luck!

---

