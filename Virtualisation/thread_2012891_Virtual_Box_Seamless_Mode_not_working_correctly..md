---
title: "Virtual Box Seamless Mode not working correctly."
date: 2012-06-30
forum: Virtualisation
---

### Post by MrBalloonHands on 2012-06-30
So I'm running Ubuntu Studio 12.04 as my main operating system, and Windows 7 as virtual machine using Virtual Box. I installed Guest Additions to the Windows 7 VM. But when I put the Widnows 7 VM in to Seamless mode, the Windows 7 desktop background and icons disappear showing my Ubuntu desktop and all it's icons. The even more screwed up thing is the Windows 7 task bar appears, but not the actual desktop. 

Any ideas?

Thanks

---

### Post by rai4shu2 on 2012-06-30
I think that fits the category of "It's a feature":

> After seamless windows are enabled (see below), VirtualBox suppresses the display of the Desktop background of your guest, allowing you to run the windows of your guest operating system seamlessly next to the windows of your host...

[https://www.virtualbox.org/manual/ch04.html#seamlesswindows](https://www.virtualbox.org/manual/ch04.html#seamlesswindows)

---

### Post by mlentink on 2012-06-30
AFAIK that's exactly as it should behave. Seamless mode is designed to allow you to run windows programs as if they were linux programs.  It cannot show the windos background while in seamless mode.

---

### Post by peter1489 on 2012-06-30
My mistake...

---

