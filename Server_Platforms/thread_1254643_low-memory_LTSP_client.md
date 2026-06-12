---
title: "low-memory LTSP client"
date: 2009-08-31
forum: Server Platforms
---

### Post by Perkins on 2009-08-31
My grandfather is one of those people who doesn't like to waste anything.  He has one, somewhat nice, computer. (Which I stuffed full of as many pc-133 memory sticks as I could get my hands on and upgraded to Ubuntu when Windows ME started misbehaving for him.)  

He also has an older 75Mhz machine, for which I have managed to scrounge 24Mb of ram.  He would like a second computer for my Grandmother to do her word-processing type stuff on so that she won't be messing up his desk, but he doesn't really want to buy a new computer if he can avoid it.

I believe the nice machine is robust enough to act as an LTSP server.  It's good enough to be worth a try anyway, especially where they don't do anything that's particularly memory or processor intensive.

Unfortunately, 24Mb of ram does not seem to be enough for the thin client to boot.  I turned on NBD swap, and switched out the client kernel for the 386 version instead of the generic (it's smaller), but it still can't manage to boot.  It loads the initrd.img, and then I get "Kernel panic - Not Syncing: Out of memory and no killable processes.

The LTSP project page lists the performance of a machine with these specs as acceptable, but the instructions for paring down the image to work on one don't match with the way the Ubuntu installation is laid out.

Can anybody offer me any pointers for how to make it work?  Or do I need to scrap using the pre-installed Ubuntu LTSP and install it from scratch myself?

---

