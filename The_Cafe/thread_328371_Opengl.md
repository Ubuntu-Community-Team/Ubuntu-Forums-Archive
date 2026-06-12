---
title: "Opengl?"
date: 2006-12-30
forum: The Cafe
---

### Post by haxer on 2006-12-30
Hello i just have to ask this opengl will it ever be good in ubuntu? Why is it so bad deos it cost a lot to use it or is it good or why have i experienced it to be bad?:-k

---

### Post by pmj on 2006-12-30
What exactly is bad with OpenGL in Ubuntu?

---

### Post by haxer on 2006-12-30
Some games dont work :(

---

### Post by pmj on 2006-12-30
I can't say I've had any issues with OpenGL games, including Doom 3 and Quake 4. Are you sure your problems are related to OpenGL and not something else?

---

### Post by haxer on 2006-12-30
No but new games

---

### Post by The Noble on 2006-12-30
The reason many new games are not working in linux is the fact that they are using DirectX instead of OpenGL (as well as being written for windows). Look up openGL and DirectX in wikipedia or try comparing the two in a google search. Nothing is _wrong_ with openGL; hell, it may even be used by UT2007.

---

### Post by Polygon on 2006-12-30
> **The Noble said:**
> The reason many new games are not working in linux is the fact that they are using DirectX instead of OpenGL (as well as being written for windows). Look up openGL and DirectX in wikipedia or try comparing the two in a google search. Nothing is _wrong_ with openGL; hell, it may even be used by UT2007.

hell, it WILL be used forf ut2007, as ive read somewhere that they have confirmed a mac and linux port. It may not come out at the same time as the windows version, but its very nice that at least come companies have already jumped on the linux bandwagon.

 And also the complete doom3 engine was written to use opengl, even in windows. Some games like doom 3, quake 4, prey, all done using open gl :D

---

### Post by slimdog360 on 2006-12-30
As far as I know everything runs on Opengl at a basic level, DirectX is some layer which geos over the top of Opengl and makes some things easier to do, sorta like a programming language like c over the top of machine code. That said, opengl is an industry standard among video card manufacturers and hence all graphics ares must support it or they dont work.

---

### Post by haxer on 2006-12-31
But why doesnt directX work well in linux?

---

### Post by NeoChaosX on 2006-12-31
Can you be more specific about why OpenGL is "bad" in Ubuntu? Are games running slowly? Do you have trouble running newer games? And what's your graphic card?

Really, you're not going to get anywhere unless you're more specific about the problems you're having.

---

### Post by The Noble on 2006-12-31
Linux _can't_ use directX (except through "emulation") and thus is not very good at using it. Simple explanation really.

---

### Post by EdThaSlayer on 2006-12-31
I have to agree with you that OpenGL is VERY slow on Ubuntu. Using FGRXLgears I only get 200 fps, used to be faster in dapper though(1000 fps faster >.>)

---

### Post by Mathiasdm on 2006-12-31
> **haxer said:**
> But why doesnt directX work well in linux?

DirectX was created by Microsoft.

Of course, they don't want to let Linux users use DirectX (they prefer people to buy Windows to use DirectX).

There's a project called 'Wine' that tries to make it possible for Linux users to use DirectX, but this is very complicated.

Have a look at [this explanation](http://www.samba.org/ftp/tridge/misc/french_cafe.txt). It's about another project (Samba), but it explains the difficulty of projects like this.

If you have any more questions, don't hesitate to ask :D

---

### Post by Woodgar on 2006-12-31
> **EdThaSlayer said:**
> I have to agree with you that OpenGL is VERY slow on Ubuntu. Using FGRXLgears I only get 200 fps, used to be faster in dapper though(1000 fps faster >.>)

Odd...

glxgears -printfps 

is reporting around 3200 FPS for me which is pretty much what I have always got with this machine irrespective of the distro installed.

---

### Post by Lord Illidan on 2006-12-31
It depends on the card. NVIDIA cards are notably better with opengl than ATI.

My card for example gives me around 3000 fps with beryl activated and 10000 fps without it. NVIDIA 6800 on Pentium D dualcore.

---

### Post by Sqwishy on 2006-12-31
> **haxer said:**
> But why doesnt directX work well in linux? directX doesn't work will because it's a microsoft product. And it was made for windows, so it's dificult to implement it into wine or cedega or whatever.

---

### Post by Sammi on 2006-12-31
Windows = closed source
DirectX = closed source

DirectX was made to only work on Windows

---

Ubuntu = open source
OpenGL = open source

OpenGL was made to work in as many OS enviroments as possible. Not just Ubuntu and Windows. It works on all sorts of operating systems.

---

Closed source programs have to be reverse engineered to work on other platforms than what they were made for. That's why it's so hard to make DirectX work on Ubuntu. But some projects are trying, including Wine and Cedega.

I fear you are trying to run DirectX games on Ubuntu, and so you are in fact not having problems with OpenGL, but DirectX.

---

### Post by BoyOfDestiny on 2006-12-31
> **Sammi said:**
> Windows = closed source
DirectX = closed source

DirectX was made to only work on Windows

---

Ubuntu = open source
OpenGL = open source

OpenGL was made to work in as many OS enviroments as possible. Not just Ubuntu and Windows. It works on all sorts of operating systems.

---

Closed source programs have to be reverse engineered to work on other platforms than what they were made for. That's why it's so hard to make DirectX work on Ubuntu. But some projects are trying, including Wine and Cedega.

I fear you are trying to run DirectX games on Ubuntu, and so you are in fact not having problems with OpenGL, but DirectX.

Yeah it seems MS gets to dictate which windows can use what directx. XP won't get directx 10 support, correct me if I'm wrong, I've never seen a technical reason for it not being included for XP... So gamers will have to hop on the Vista bandwagon for the latest and greatest...

Although I suppose there could be a technical reason, but judging from other behavior, I doubt it (i.e. vista's wordpad cannot open .doc files even though XP's wordpad can...)

Anyway I wish those WINE guys luck.

---

### Post by The Noble on 2006-12-31
*Offtopic*

I actually saw a qoute from one of the guys that works on wine saying that they could impliment DirectX10 into XP without much trouble. That would put one hell of a wrinkle in Microsofts plan for Vista...

---

### Post by M_the_C on 2006-12-31
> **BoyOfDestiny said:**
> Yeah it seems MS gets to dictate which windows can use what directx. XP won't get directx 10 support, correct me if I'm wrong, I've never seen a technical reason for it not being included for XP... 

I heard that you can't use DirectX 10 in Vista becauase of the new way drivers work.
I don't know if this is true though.

---

### Post by Lord Illidan on 2007-01-01
> **M_the_C said:**
> I heard that you can't use DirectX 10 in Vista becauase of the new way drivers work.
I don't know if this is true though.

DirectX10 is made **for Vista**. Perhaps it cannot work in XP, I don't know about that. But, I doubt it would work in Wine, when it barely supports DX 9 apps.

---

