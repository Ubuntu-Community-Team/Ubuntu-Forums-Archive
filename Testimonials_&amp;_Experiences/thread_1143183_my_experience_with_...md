---
title: "my experience with .."
date: 2009-04-29
forum: Testimonials &amp; Experiences
---

### Post by dicairo on 2009-04-29
(sorry about my English)
 first of all I have to say that ubuntu rocks , I just converted from windows to ubuntu from 4 month ago and I was afraid about the difficulty of using Linux , but with ubuntu  I foud it very easyyy. Now I am going to tell you about the positive and negative points I affronted with ubuntu and Linux;
 positive :  
       -     secure no virus
 
[LIST]
[*]very stable no crash
[*] I can personalize it from  a  to     z , thanks to gnome desktop
[*]very fast
[*]I became an anti Microsoft  just      because I cant pay more than 90£ for microsoft office and I am a     student in fact I never paid for a windows app but with the open     source we can donate what we want
[*]as I said ubuntu its very easy t o     use
[*]the open source is very useful for     who study computer science because we can have the source code
[/LIST]
 I know that they are many other points but I cant remember it now
  now with negative points ( don't worry  about it ) :  
 
[LIST]
[*]Linux doesn't support until now     all the hardware or better the hardware manufacture doesn't consider     Linux how many times you buy for example a web cam and on the box     you find the logo of Microsoft??? but its  have to Chang
[*]I hate compile programs so  I was     thinking what about standardizing a package like deb for example I     mean for all Linux distribution have the same extension for the     programs
[*]gaming with Linux is good but not     perfect
[/LIST]
 so thats it I hope that was clear and I am waiting for your answers and  at the end upgrading from ubunu 8.10 to 9.04 many things is better and this means that ubuntu and Linux are going forward   :P:P

---

### Post by garythegoth on 2009-04-29
> **dicairo said:**
> (sorry about my English)
 first of all I have to say that ubuntu rocks , I just converted from windows to ubuntu from 4 month ago and I was afraid about the difficulty of using Linux , but with ubuntu  I foud it very easyyy. Now I am going to tell you about the positive and negative points I affronted with ubuntu and Linux;
 positive :  
       -     secure no virus
 
[LIST]
[*]very stable no crash
[*] I can personalize it from  a  to     z , thanks to gnome desktop
[*]very fast
[*]I became an anti Microsoft  just      because I cant pay more than 90£ for microsoft office and I am a     student in fact I never paid for a windows app but with the open     source we can donate what we want
[*]as I said ubuntu its very easy t o     use
[*]the open source is very useful for     who study computer science because we can have the source code
[/LIST]
 I know that they are many other points but I cant remember it now
  now with negative points ( don't worry  about it ) :  
 
[LIST]
[*]Linux doesn't support until now     all the hardware or better the hardware manufacture doesn't consider     Linux how many times you buy for example a web cam and on the box     you find the logo of Microsoft??? but its  have to Chang
[*]I hate compile programs so  I was     thinking what about standardizing a package like deb for example I     mean for all Linux distribution have the same extension for the     programs
[*]gaming with Linux is good but not     perfect
[/LIST]
 so thats it I hope that was clear and I am waiting for your answers and  at the end upgrading from ubunu 8.10 to 9.04 many things is better and this means that ubuntu and Linux are going forward   :P:P

Linux actually supports more hardware out of the box than any other OS, but yeah, its not perfect.....

---

### Post by Kareeser on 2009-04-30
Your English is much better than some posters' English. Don't you fret!

---

### Post by 3rdalbum on 2009-04-30
> **dicairo said:**
> 
[*]I hate compile programs so  I was     thinking what about standardizing a package like deb for example I     mean for all Linux distribution have the same extension for the     programs

You are certainly not the first person to suggest this, and you won't be the last person either.

If all Linux distributions started using one package format, what would it be? If we announced that Debian packages were now the standard, then the RPM-based distributions would simply ignore it. In fact, RPM is the Linux Standards Base standard, and we don't use RPM.

Oh, there have been attempts to try and make a new package format for everyone, but then you have to convince EVERYONE to adopt your new format rather than stick with their current one... it's not going to happen.

But what if we all adopted a singular package format? Would that solve all the problems? Nope. Lots of distributions use the RPM format, but they often can't use eachother's RPM packages because each distribution names their packages differently. If an RPM package says "I depend on libvorbis" and you try to install it on a system where the package is called "vorbis-lib", it's simply not going to work.

I believe that we need to standardize the naming system for libraries and support infrastructure, so all distributions have a package called "libvorbis" and not "vorbis-lib" or "libaudio-vorbis". Or, alternatively, have your current naming system but also have large metapackages such as "universal-free-audio-support" that packages can list as their 'depends' - and all distributions will have that metapackage.

Because, after all, it's possible and even easy to convert between package formats - there's a program to do it called Alien.

EDIT: I've just re-read your post - you think you have to compile software because there is no standard package format? The reason why source code is distributed rather than a package, is less to do with packaging formats and more to do with the fact that a program compiled on an i386 computer will not run on an Itanium, SPARC, MIPS, ARM, PowerPC, m68k, etc-based computer. Source code can be compiled for any sort of computer, but binaries are not portable.

Binaries are not much of a problem on Windows because Windows only really runs on i386. There is a version of Windows for Itanium, but it's a complete failure because no Windows programs run on it unless they have been compiled specially for Itanium. Most Itanium machines end off running Linux, because most programs that you want are available as source code that you can easily compile into an Itanium-native binary.

---

### Post by dicairo on 2009-04-30
> **3rdalbum said:**
> You are certainly not the first person to suggest this, and you won't be the last person either.

If all Linux distributions started using one package format, what would it be? If we announced that Debian packages were now the standard, then the RPM-based distributions would simply ignore it. In fact, RPM is the Linux Standards Base standard, and we don't use RPM.

Oh, there have been attempts to try and make a new package format for everyone, but then you have to convince EVERYONE to adopt your new format rather than stick with their current one... it's not going to happen.

But what if we all adopted a singular package format? Would that solve all the problems? Nope. Lots of distributions use the RPM format, but they often can't use eachother's RPM packages because each distribution names their packages differently. If an RPM package says "I depend on libvorbis" and you try to install it on a system where the package is called "vorbis-lib", it's simply not going to work.

I believe that we need to standardize the naming system for libraries and support infrastructure, so all distributions have a package called "libvorbis" and not "vorbis-lib" or "libaudio-vorbis". Or, alternatively, have your current naming system but also have large metapackages such as "universal-free-audio-support" that packages can list as their 'depends' - and all distributions will have that metapackage.

Because, after all, it's possible and even easy to convert between package formats - there's a program to do it called Alien.

EDIT: I've just re-read your post - you think you have to compile software because there is no standard package format? The reason why source code is distributed rather than a package, is less to do with packaging formats and more to do with the fact that a program compiled on an i386 computer will not run on an Itanium, SPARC, MIPS, ARM, PowerPC, m68k, etc-based computer. Source code can be compiled for any sort of computer, but binaries are not portable.

Binaries are not much of a problem on Windows because Windows only really runs on i386. There is a version of Windows for Itanium, but it's a complete failure because no Windows programs run on it unless they have been compiled specially for Itanium. Most Itanium machines end off running Linux, because most programs that you want are available as source code that you can easily compile into an Itanium-native binary.
  thanks for you all and now i know another reason of having the source code

---

### Post by Armor Nick on 2009-04-30
Actually, if you know what you're doing, you don't really need source code. Even if you do need source code, there's a lot of good resources on how to compile an app. The README included with the source usually gives great instructions, and ./configure tells you which dependencies are missing. Plus, Ubuntu has so many apps in its repositories that the only time you'd need to compile source is when you want the latest greatest (i.e. version > ubuntu version).

---

