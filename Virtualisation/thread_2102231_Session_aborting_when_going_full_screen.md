---
title: "Session aborting when going full screen"
date: 2013-01-06
forum: Virtualisation
---

### Post by fakedave on 2013-01-06
Hello,

I have a big problem with Virtualbox.

I had installed ubuntu 12.10 and virtualbox 4.2.4, installed W7 64-bit. I struggled to install guest additions because I did not get the way it was working but in the end, no issue.
I saved the VM files.
Reinstalled 12.10 and so on from scratch to make sure I could restart my work easily in case of problem. All went well.

Then for long term support and some graphics card driver questions, I decided to go for ubuntu 12.04.
I installed everything again (no error at all) except that now, the VM always aborts when I switch to full screen (or the other mode).
I don't understand why. I had once an error message making my think that there is an issue graphics driver but I'm not sure nor I know how to get a hold of logs.

Does anybody have a clue about that ??? How to move on?

I may try to reinstall 12.10 but for work purpose I would have preferred 12.04 for LTS but I'm not very knowledgeable about Ubuntu/Linux.

Thanx a lot in advance.

Nicolas

---

### Post by fakedave on 2013-01-08
Hello, anybody has a clue about that?

Thanx.

---

### Post by fakedave on 2013-01-13
Some more information:

It might have been due to the fact that I've declared 2 screens. I declared only one and it's not aborting anymore.
For now it's ok, but it 's limiting for the future.
I'm not yet sorted with my other graphic card and displays so I can wait for some help.

I think I'm gonna try reinstalling everything on a new hard drive with 12.10 and see what it gives.

In the mean time, I take any advice :D

---

### Post by Ms. Daisy on 2013-01-15
You need to install the version of Virtualbox that corresponds to your host operating system.  So you need to download the Ubuntu 12.04 AMD64 version from [here]("https://www.virtualbox.org/wiki/Linux_Downloads") and reinstall it on your host.

---

