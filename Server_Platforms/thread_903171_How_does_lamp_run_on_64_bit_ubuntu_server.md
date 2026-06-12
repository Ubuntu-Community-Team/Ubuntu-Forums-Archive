---
title: "How does lamp run on 64 bit ubuntu server?"
date: 2008-08-28
forum: Server Platforms
---

### Post by muramura on 2008-08-28
I am looking to buy a fancy new dual processor machine to replace my existing one, and am curious about the 64-bit Ubuntu server.  How compatible is it?

What I need is a great LAMP server - no GUI.  It has to replace what I have perfectly.  I need it for Apache, PHP, MySQL, SSL support, etc.

For example, if I "apt-get install apache", will it automatically install the correct 64-bit version?  Will all the apache modules work?  Will mysql work exactly the same?

I'm hesitant to switch to 64 if there are going to be issues, or if it's just going to be running these programs in a 32-bit emulated state.

Thanks in advance!

---

### Post by Rhubarb on 2008-08-28
64bit ubuntu server runs the same as 32bit.
Same apt-get, same everything.
It's easy to get going, and runs the same, just in 64bit goodness.

---

### Post by muramura on 2008-08-28
Thanks for the quick reply.  :)

As for the forums where people have complained about 64bit, was that mostly a GUI issue?  My understanding is that emulation is needed for many programs.  Are there really no issues that affect a 64bit non-gui server?

---

### Post by Rhubarb on 2008-08-28
I haven't come across any issues on 64bit server.
Most problems with 64bit Ubuntu arise from: Flash and Java in firefox.
And that's only in a few cases.
It's true that occasionally sometimes some programs (not in the ubuntu repos, like Quake4, Unreal Tournament) need to use 32bit libraries.
But they work fine in a 64bit environment.


When you install ubuntu 64bit, all the apps in the ubuntu repos (apart from the non-platform specific files, like bash scripts and python scripts) are made for the 64 bit architecture.
There are just as many apps to choose from in the 64bit repos as with the 32bit repos.

To sum it up:  Run 64bit, there's no problems with it, it runs just the same as 32bit, there's no differences - except of increased speed when doing some maths related applications, and being able to address more than 4GB of memory without sacrificing performance with PAE in 32bit.

---

### Post by muramura on 2008-08-28
:guitar: Sweet!  Thanks!  I can't wait now!

---

### Post by windependence on 2008-08-28
No issues here at all. I run my VMware server guests on Ubuntu server 64 bit, and it has been fine.

You won't see much difference though in speed unless you are running really huge databases or you are rendering graphics or something like that. In some cases, 64 bit will actually be a bit slower than 32 bit, but you probably won't notice it.

-Tim

---

### Post by muramura on 2008-08-28
LMAO at your pic!

I do in fact have a huge database - or at least plan to.  I'm surprised to hear you say it's slower in some cases.  That's definitely not desirable...  Is that just with programs that use 32bit emulation?

---

### Post by Sef on 2008-08-28
> Most problems with 64bit Ubuntu arise from: Flash and Java in firefox.

With Java, there is OpenJDK (Open Java Development Kit) that runs on 64-bit systems.   Almost all sites are work with it.

With Flash, there are Gnash and SWFDec, which is often compatible with version 9 Flash.   

All three are in the respositories:  For add/remove, be sure and change show to 'All Available Applications'.

---

### Post by insane_alien on 2008-08-28
i've often found the areas where 64-bit is slower than 32-bit to be trivial and the drop in performance can really only be detected by multiple benchmarks and taking an average. even then i'd be hard pressed to call the difference significant.

64-bit is better at handling large files and data sets than 32-bit, especially as you can use more RAM.

---

### Post by mellowd on 2008-08-28
I've run into a few compatibility issues when I was running 64bit server (and no, I don't have a gui)

This was back with 7.04 though, things could've changed by now.

---

### Post by mellowd on 2008-08-28
> **insane_alien said:**
> 
64-bit is better at handling large files and data sets than 32-bit, especially as you can use more RAM.

32bit server can handle 64gb of memory with PAE installed, which is default with server edition

---

### Post by windependence on 2008-08-28
> **insane_alien said:**
> i've often found the areas where 64-bit is slower than 32-bit to be trivial and the drop in performance can really only be detected by multiple benchmarks and taking an average. even then i'd be hard pressed to call the difference significant.

64-bit is better at handling large files and data sets than 32-bit, especially as you can use more RAM.

Indeed, that's why I said you probably wouldn't notice the difference. I certainly am not in any way saying 64 bit is "bad" or anything close to that, just that not everyone <needs> 64 bit and some 32 bit apps actually run a tad slower. The problem is some folks think 64 bit will automatically make their server "blazing fast" and they might be disappointed when the results are less than stellar. Incidentally, I run most all my web servers on 64 but OSs, but I haven't really noticed much difference other than the fact that it will be more stable than 32 bit running PAE with large amounts of memory which I typically run in my VMware boxes. PAE works, but the OS still can't address more than 4 GB at one time, while 64 bit natively uses the memory.

-Tim

---

