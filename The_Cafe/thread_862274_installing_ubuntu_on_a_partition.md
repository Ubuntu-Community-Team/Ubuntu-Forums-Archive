---
title: "installing ubuntu on a partition?"
date: 2008-07-17
forum: The Cafe
---

### Post by Uner on 2008-07-17
Well, first of all, I don't know if this is the right section. I tried to post it in the complete Absolute Beginner Talk forum, but it wouldn't let me. I'm more used the traditional Invisionboards look, so I hope you understand me.

Yeah.. to the point.
Last time I tried to install ubuntu, I ran the installer, and after installing, my windows was ****** up. I wonder, what if I make another partition and install Ubuntu on that partition. Will it mess up my Windows any way?

---

### Post by init1 on 2008-07-17
Yeah, the way to keep Windows is to resize the Windows partition, make a partition with that free space, and then install Ubuntu to it. You will also need a "swap" partition (I usually use 1G).

---

### Post by az on 2008-07-17
> **Uner said:**
> Well, first of all, I don't know if this is the right section. I tried to post it in the complete Absolute Beginner Talk forum, but it wouldn't let me. I'm more used the traditional Invisionboards look, so I hope you understand me.

Yeah.. to the point.
Last time I tried to install ubuntu, I ran the installer, and after installing, my windows was ****** up. I wonder, what if I make another partition and install Ubuntu on that partition. Will it mess up my Windows any way?

The installer should do that for you automatically.  Unless you are using Wubi, in which case it install inside a file in windows, but that should not affect your windows install.

I don't know if what you are describing is 
1- that your windows filesystem got corrupted when it was shrunk during the installation
2- you told the installer to use the entire disk, overwriting windows
or
3- everything went fine except that the windows bootloader (or the Ubuntu bootloader) wasn't working properly.

---

### Post by mitso on 2008-07-17
[SIZE="3"]I just finished loading Ubuntu 8.04.1 on the second partition of my primary hard drive using Wubi. It all went without a single hitch.
At boot up I can select Ubuntu or my windows 2000.

One weired element I haven't figured out yet. 

  a) If I select windows after having used Ubuntu, my Haupauge wintv program is not available. 
  b) If I delete the switching option and reboot, the wintv program is OK.

  c) If I reset the switching option and only access W2k the wintv program
     stays activated. 

  d) If I switch to Ubuntu, the next time I use w2k the wintv program is  deactivated and I must go back to step b).

Other than that both programs are running fine. I mention this in the event
that other programs can be similarly affected. At this point I think it's a small price to pay for having both programs so easily available. 

I would appreciate any thoughts on fixing this problem.

I tried to use larger type but couldn't see how.

---

