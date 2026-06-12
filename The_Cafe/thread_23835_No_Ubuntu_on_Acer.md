---
title: "No Ubuntu on Acer"
date: 2005-04-04
forum: The Cafe
---

### Post by Dragonfly_X on 2005-04-04
I've tried to install Ubuntu on Acer machines at work but grub fails to load and finish the setup. I don't know if this is a problem specific to Acer, but it seems that way.

I've also tried to install SUSE 9 and it does the same thing!Has anyone experienced the same problem?  ](*,)

---

### Post by HungSquirrel on 2005-04-04
Have you tried installing LILO instead?  (To have more options during the install, such as using LILO over GRUB, type 'expert' and hit Enter when the CD first boots.)

---

### Post by defkewl on 2005-04-04
Can you please post any message to give us a clue?

---

### Post by kb00heda on 2005-04-04
My installation, on a Acer laptop (Ferrari 3000), worked nicely. No problems at all. Not that it helps for you to hear it...?  :-?

Anyway, I had some trouble getting Ubuntu up and running on my stationary machine, even though not an Acer. I was able to run the installation until the CD popped out, and GRUB was to be loaded. Later I discovered my issue to be a boot order set wrongly in BIOS (I have multiple HDDs). Perhaps that could be the case for you too?

/David

---

### Post by Dragonfly_X on 2005-04-05
I managed to figure it out! When installing Ubuntu create a separate partition about a 100MB big, it must be a "exp3" file system, then set the mount point to /boot. 

When installation is finished grub should load normally! :lol:

---

### Post by kb00heda on 2005-04-05
Glad to hear it!

When I installed I didn't change the default partitioning; just erased all old data and wrote two new partitions, the first being a larger bootable ext3, and the second a smaller swap.

---

