---
title: "Line Is Not an Emulator (Wine for Linux programs)"
date: 2010-03-10
forum: The Cafe
---

### Post by chessnerd on 2010-03-10
For a while I have thought about the idea of a project with the goal of putting Linux application functionality on other operating systems similar to how Wine allows Windows applications to be run on other systems (the name that comes to mind for this is Line). I'm sure others have thought of this, but I don't think that such a project exists. Now, I don't yet have the programming skills to start such an undertaking, but I do think that it would be a good idea.

I know that Linux has far fewer applications for it than does Windows, which is probably why there isn't a project like this, but it seems to me that, compared to Wine, this would be a much simpler undertaking. Because the source code for Linux is available the programmers of Line (or whatever they wanted to call the project) would already know how Linux is making use of the applications. I'm not claiming that I would have the programming skills to create such a thing, but compared to the black-box, clean-room setup that Wine has going, a Linux compatibility layer seems like it would be much easier to make.

Such a project could be useful for systems like OpenSolaris, FreeBSD, and GNU Hurd which have even fewer available applications available for them than Linux. Such a system would be like Wine is for Linux and could greatly increase the number of available applications. In addition, this could be helpful to Windows and OS X users who want to run some Linux applications without using a virtual machine or dual-booting.

I know that many Linux applications can be ported to other Unix-like systems, but a compatibility layer could eliminate that need and smaller applications that people don't feel like porting could then be used on a wider variety of systems.

Thoughts?

---

### Post by phrostbyte on 2010-03-10
[Cygwin]("http://www.cygwin.com/"). :)

The *BSDs have native Linux support for most of Linux's non-POSIX syscalls AFAIK.

---

### Post by Dayofswords on 2010-03-10
yeah, someone beat ya to it =p

like wine, it works ok, not perfect though

---

### Post by chris4585 on 2010-03-10
There is also andlinux

---

### Post by chessnerd on 2010-03-11
> **phrostbyte said:**
> [Cygwin]("http://www.cygwin.com/"). :)

This is kinda what I was thinking, but it seems like Cygwin is really just a way to make it easier to port Linux apps over to Windows. After all, the homepage of the website says:

> Cygwin is not a way to run native linux apps on Windows. You have to rebuild your application *from source* if you want it to run on Windows.

I don't like the idea that you'd need to compile everything from source to run it on Windows. You should just be able to take Linux binaries and run them.

> **chris4585 said:**
> There is also andlinux

This seems closer. From my understanding it is really a seamless, more efficient virtual machine much like XP-mode in Windows 7. If I were in need of a Linux program on Windows, this would probably be what I would go to.

---

### Post by Kimm on 2010-03-11
Actually, there was a project on Sourceforge a couple of years ago called Line, that aimed to do just this. However, I believe the project never got anywhere near maturity and eventually just died (I cant find it anymore, anyway)

---

### Post by phrostbyte on 2010-03-11
> **chessnerd said:**
> This is kinda what I was thinking, but it seems like Cygwin is really just a way to make it easier to port Linux apps over to Windows. After all, the homepage of the website says:

Cygwin includes an admittedly primitive package manager, with most Linux software already precompiled for Windows available for install. The Cygwin people probably do not feel it is worth the effort to design a ELF loader for Windows, because so few relevant applications (eg: closed source Linux-only applications) even exist.

---

### Post by Johnsie on 2010-03-11
KDE for Windows for the win...

[http://windows.kde.org/](http://windows.kde.org/)

There is also X11 for the Mac

---

### Post by Bachstelze on 2010-03-11
> **Dayofswords said:**
> 
like wine, it works ok, not perfect though

Linux binary compatibility on the BSD OSs is as close to perfect as humanly possible. A lot of programs have been reported to run faster in it than in native Linux.

---

### Post by alket on 2010-03-11
Linux apps are mostly Open Source so they can be compiled to run under FreeBSD , Open Solaris , Windows , Mac etc.

---

### Post by Tibuda on 2010-03-11
OP: What Linux app would you like to run on Windows?

---

### Post by cascade9 on 2010-03-11
Cygwin was always a pain in the butt when I tried it. 

I have used a linux program under windows lot though. Python based, which made it pretty easy. Using- 
Python
Gtkwin32
PyGTKwin32 

I even went so far as to use subversion under windows for updating it, the whole lot was pretty easy and very impressive (its probably part of why I changed over to linux).

---

