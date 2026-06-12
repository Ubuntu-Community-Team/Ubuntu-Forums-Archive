---
title: "Performance problems with virtualbox"
date: 2018-11-12
forum: Virtualisation
---

### Post by WimiBuntu on 2018-11-12
Hi

Previously I posted this on a virtualbox forum:

> Dear all

For quite some time I have a problem with my virtualbox.  Right now I am running Version 5.2.10_Ubuntu r121806 on Ubuntu 18.04  (32-Bit, Intel i5, 8Gb RAM) as host. My guest is a Win 10. Previously I  had a Win 7 as guest. With both, but even more with the Win 10 I have  the problem that virtual box uses too much of the CPU. If I do not limit  the virtual box process it takes 100% CPU time. It does not matter if  an application is running in the virtual box or not. Guest additions are  installed and I try to always use the current version.

So, while running VB my battery drains around 2-3% per minute. Using VB only on battery is therefore not an option.

Can you give me a recommendation how to solve this?

Best regards

And I got this response:

> In that case you are not running VirtualBox, you are running the Ubuntu  fork of VirtualBox, support for which is available on the Ubuntu forums.

If  you want support here then you need to be using VirtualBox, not  somebody's forked version of it. I.e. download and install from the downloads area on this site.

Actually I already tried the not-ubuntu-specific version. But this did not help either.

Do you have any recommendations?

---

### Post by deadflowr on 2018-11-12
*Thread moved to **Virtualization***

Is the host really 32-bit?
Seems like you'd be better with 64-bit, since your system is more than capable.

---

### Post by WimiBuntu on 2018-11-12
Yes, it is 32 bit. When I installed it was the better option from my point of view. But that has been a long time ago.

Still, right now I am not thinking about some tweaking, but rather the problem that virtualbox uses all CPU time it can get.

---

### Post by SeijiSensei on 2018-11-13
As a kludgy solution you could reduce VB's demands with the "[renice]("https://linux.die.net/man/8/renice")" command that lets you change the priority of a process. I've not seen this problem myself though.

---

### Post by WimiBuntu on 2018-11-13
Thanks, I already did this. But even when I reduce the cpu time to like 70% then the process still takes the full 70% and VB slows down ...

---

