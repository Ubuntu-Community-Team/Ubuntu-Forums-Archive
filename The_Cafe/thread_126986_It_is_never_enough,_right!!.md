---
title: "It is never enough, right!?!?"
date: 2006-02-07
forum: The Cafe
---

### Post by Bone Down on 2006-02-07
Well i have finally got the system up and running to the point that 98% of everything is running that I need.

I now would like to upgrade my kernel and I am wondering what I am up against if I take on this task.

I am running 2.6.12-10.26 386.

Now I was told that the above listed will not fully utilize my 1 GB Ram and is limited to 512MB.

I would like to upgrade to at the least the 686 kernel as I believe my P4m is up to it.

I am worried about losing all my network settings, files, and anything else; if I upgrade the kernel will it effect any of this???

I await your replies eagerly.

---

### Post by fuscia on 2006-02-07
am i crazy, or can't you just reinstall the other?

---

### Post by kingsidy on 2006-02-07
not at all. you won t loose anything. you will also have the option to run the other kernel. i too have a gig of ram and the 686 kernel recognized like 960 of it. the rest is probably taken by the integrated graphics. it is just a kernel, it does not really have anything to do with settings and such.

---

### Post by mstlyevil on 2006-02-07
[QUOTE=Bone Down]Well i have finally got the system up and running to the point that 98% of everything is running that I need.

I now would like to upgrade my kernel and I am wondering what I am up against if I take on this task.

I am running 2.6.12-10.26 386.

Now I was told that the above listed will not fully utilize my 1 GB Ram and is limited to 512MB.

I would like to upgrade to at the least the 686 kernel as I believe my P4m is up to it.

I am worried about losing all my network settings, files, and anything else; if I upgrade the kernel will it effect any of this???

I await your replies eagerly.[/QUOTE]

I installed the K7 kernel for my Athlon 64 3200 and it did not break anything. This was before I installed the latest Nvidia graphics drivers. If you just use the legacy drivers from Nvidia, they update automatically during the install of the new kernel. If you have the latest drivers, you will have to reinstall them to get X up and running after installing the new kernel. Other than that it should go pretty smooth.

Edit: I have no clue if the same is true for the ATI drivers. If you have a ATI card just have the drivers and the guide ready just in case or ask others that have a ATI card if there is any special instructions.

---

### Post by towsonu2003 on 2006-02-07
I updated my kernel from 386 to 686 once, and also applied a kernel security update which changed the kernel version. 

I have this same fear with each kernel (security) update. 

Nothing to worry. just don't uninstall your old kernel. grub will give you the option to choose between the two. if one isnt good for you, you can always go back to the other. 

Anything you compiled, you will have to compile again, including proprietary drivers such as ati and nvidia drivers you got from their websites. but that's just some manual exercise... now that you know how to do it... stuff you got from the repos will just comtinue working w/out any effort at all.

---

### Post by Bone Down on 2006-02-08
Thank you all for the replies, I guess I know what I will be doing tonight after work     \\:D/

---

