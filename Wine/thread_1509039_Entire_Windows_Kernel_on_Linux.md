---
title: "Entire Windows Kernel on Linux?"
date: 2010-06-13
forum: Wine
---

### Post by Gelegenheit on 2010-06-13
Wine, while I am glad that there is a program out there that helps to bridge the nearly bottomless chasm between Linux and Windows, is still a very inadequate program.  Admittedly, as soon as you get into the nuts and bolts of why I can't run iTunes 9 in Linux, I can only hear "*wah-wah, wah-wah-wah-wah-wah-wah*" like in Peanuts and am totally lost.  But is it possible for me to look at my brother's Windows 7 guts, get that onto my Linux-box and be able to have a 100% Windows compatibility while maintaining Linux's overall efficiency and feel?  This is, of course, in a method that doesn't have Microsoft hounding me.

Thanks in advance.

---

### Post by amauk on 2010-06-13
Run Windows in a virtual machine

---

### Post by hikaricore on 2010-06-13
You could also blame Apple for not providing a linux version of itunes when it's perfectly within their ability to do so.

---

### Post by Gelegenheit on 2010-06-13
> **amauk said:**
> Run Windows in a virtual machine
Will give it a try.

And I've been screaming that for the past two weeks, hikaricore.

---

### Post by Cavin on 2010-07-14
> **Gelegenheit said:**
> Wine, while I am glad that there is a program out there that helps to bridge the nearly bottomless chasm between Linux and Windows, is still a very inadequate program.
You have to understand, the Wine developers work very hard to make Windows programs work on Linux (and Mac). Windows is a completely proprietary operating system, which means they can't just look at the source and figure out how A works with B. To my understanding, they pretty much had to start from scratch and go through trial-and-error until something worked. Each program uses a variety of specific libraries, many of which are provided by Windows natively. If something doesn't work with Wine, it's because they can't figure out, or they just haven't gotten around to figuring out, how the program interacts with these native libraries.
iTunes probably uses libraries that the Wine developers do not yet know how to make work with Wine. It's a lengthy and difficult process, and that won't change. Maybe eventually, they will figure it out, but for now they just haven't. And that doesn't make Wine inadequate. It just makes iTunes a particularly difficult program to provide compatibility for, when there are things much higher in priority on the developer's to-do list (like MS Office, etc). We are human, it happens.

Also, Wine does not and never will run drivers, so using iPods with iTunes isn't going to be possible in the foreseeable future either, in case you were wondering.

 > Admittedly, as soon as you get into the nuts and bolts of why I can't run iTunes 9 in Linux, I can only hear "*wah-wah, wah-wah-wah-wah-wah-wah*" like in Peanuts and am totally lost.  But is it possible for me to look at my brother's Windows 7 guts, get that onto my Linux-box and be able to have a 100% Windows compatibility while maintaining Linux's overall efficiency and feel?  This is, of course, in a method that doesn't have Microsoft hounding me.
No. There is definitely not a way to take the guts of Windows and put it in Linux. That makes absolutely no sense. You can use VirtualBox or the like as a previous poster suggested, to emulate Windows. But you will still have to deal with license agreements, Microsoft stealing your soul, etc. Not to mention, emulation is pretty resource-hungry. Unless you have a fast system to begin with, your overall system performance will drop when running Windows in an emulator.

Also, I got iTunes 9 running with CrossOver 9.1. But it freezes.

Edit: I realize I may have been like the parents in The Peanuts "wah-wah-wah-wah." Sorry haha

---

