---
title: "Can Ubuntu Touch tablets run PCSX2 from native x86 source?"
date: 2014-03-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Joe_Magus on 2014-03-24
I heard that Ubuntu Touch supports x86 native desktop apps to some degree, so I figured that, since Intel Atom is x86 and Ubuntu Touch works with x86, and Ubuntu Touch can run x86 desktop apps, theoretically, PCSX2 should work on it, yes?

I wanted to know this before hand because I'm a supporter of Ubuntu and Linux in general; an open-source, free operating system.

Microsoft's Surface Pro tablets are similar to Ubuntu Touch's upcoming ones, and they can run PCSX2 with their specs. My question, however, concerns the **software-side of things **more.

Would Ubuntu Touch be able to run PCSX2, and other compiled x86 desktop apps really?

---

### Post by grahammechanical on 2014-03-25
What is PCSX2? And why would it not run on Linux?

Over the next 12 months the Ubuntu Touch code is going to be converged into the Ubuntu desktop code. So, that there will be but one Ubuntu code base. Software that runs well on Ubuntu desktop may not run well on the small form factor of a phone or tablet due to the need to scale the application to the form factor. There is not a lot that Ubuntu developers can about third party software not scaling correctly. I doubt very much if Ubuntu developers are doing any work to get third party software working acceptably on phone/tablet devices. 

The focus of much of the work of Ubuntu Touch developers is to get the phone apps scaling correctly for the tablet form factor and then to get them scaling correctly for the desktop form factor. 

A retail Ubuntu Superphone that can become a tablet and a desktop PC will only show the Ubuntu desktop user interface when it is connected to a monitor. Otherwise, the phone/tablet user interface will appear. This is my understanding. Think - phone apps for the phone. Think - phone apps + tablets apps for the tablet. Think - phone apps + tablet apps + desktop apps for the desktop. 

You are better off thinking about Ubuntu 14.10 or 15.04. By the release of those two versions  Ubuntu Touch will have disappered. In fact it has already been decided to stop using the name Ubuntu Touch. It is now called Ubuntu.

Regards.

---

### Post by deadflowr on 2014-03-25
If the program is an x86 program and the system is an x86 system, then it should run it.
The only thing to watch out for is Ubuntu is going to use mir as the display server which will have xmir to run xserver applications through. So it will depend on how well xmir works.

---

### Post by Joe_Magus on 2014-03-25
PCSX2 is a Playstation 2 emulator. It runs on native x86 Ubuntu desktop versions, but my question was, since it can run on x86 Ubuntu desktops and the like, shouldn't it run on Ubuntu Touch, whether or not that's converging with Ubuntu OS itself?

In short, should a desktop compiled x86 app for Ubuntu run on the software OS, libraries, and interface of a phone/tablet, taking hardware limitations and form factor into consideration as well; any x86 desktop apps should theoretically run on x86 Intel Atom powered tablets that Ubuntu runs on?

---

