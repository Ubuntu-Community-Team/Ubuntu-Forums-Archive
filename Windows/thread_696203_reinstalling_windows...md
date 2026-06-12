---
title: "reinstalling windows.."
date: 2008-02-13
forum: Windows
---

### Post by Scaraba on 2008-02-13
I know that this a typical question but, as much as I love Ubuntu, I need to reinstall windows because of my new job...  When I installed Ubuntu, I had completely formatted my hard drive for it, because I didn't think 'd need XP on my laptop anymore.

Can you guys help me in my quest to either dual boot XP with ubuntu, or uninstall Ubuntu from my laptop, and then reinstall windows on it??

Thank you guys.

---

### Post by mrsteveman1 on 2008-02-13
Did you install ubuntu using all the drive space? If so you can use the ubuntu livecd to shrink ubuntu to make space for windows.

After that you just install windows to the free space, then boot the ubuntu livecd again and fix grub.

But start with the drive space part first. Fire up the ubuntu livecd and run gparted, and let it resize ubuntu for you.

---

### Post by Scaraba on 2008-02-13
Thanks!

I installed Ubuntu from a live CD, but I am not so technically savvy on partitioning.

yes it's on all the drive space.

and how do i configure gparted??  I'm having some problems after attempting to install wine, so I have to fix that before anything else.

---

### Post by mrsteveman1 on 2008-02-13
Since the drive is all being used you'll have to shrink the ubuntu part before installing windows.

You must do this from the ubuntu CD because it has to be done while your main installation isnt being used. 

Gparted is pretty easy to use you just start it from the ubuntu CD and then select your ubuntu installation from the window and click resize, then drag the slider over a bit to make it smaller.[This]("http://gparted.sourceforge.net/screens/gparted_1_big.jpg") is what it looks like, you may only see one big section when you use it on your system.

After you do that you should have free space for windows.

---

### Post by Scaraba on 2008-02-13
okay, okay. I am still lost, as I have the CD running, but all the files are of the .exe extension..  many appolges for my newbshness, but do i need to download a new CD or do I need to do something elsE?

---

### Post by mrsteveman1 on 2008-02-13
When you are IN windows thats all you will see. You have to boot from the ubuntu cd to run gparted :D

---

### Post by Scaraba on 2008-02-13
Ahh. so i should try getting my laptop to boot from disk before trying any of this?

Edit:  Gotcha!! Start Ubuntu from the Disk!

---

### Post by Scaraba on 2008-02-13
by the way, thank you!

I'm currently partitioning the hard drive.  Wll windows start automatically when I put it in?? or is there something else I need to do?

---

### Post by mrsteveman1 on 2008-02-13
Once you resize ubuntu, then install windows, windows will boot as if it were the only OS on the system, so you will have to use the ubuntu CD again to fix things up a bit, but its not terribly hard to do.

Hows the partitioning going? Did it resize correctly?

---

### Post by Scaraba on 2008-02-13
Well, I am finally understand what the heck I'm supposed to be dong, so it all is working fine.

Sadly, my laptop ddn't come with an XP disk, so most likely I'll have to torrent an image of an XP install disc so i can use my own product key.

Ridiculous, no?

---

### Post by mrsteveman1 on 2008-02-13
Yea its ridiculous, but it's what i had to do. I've never gotten a real windows disc with any computer I've purchased, always those restore discs which always seem slower after installation because of the stuff installed.

Just make sure the image you get is of a real XP disc and not something that has been messed with.

---

### Post by igknighted on 2008-02-15
> **Scaraba said:**
> Well, I am finally understand what the heck I'm supposed to be dong, so it all is working fine.

Sadly, my laptop ddn't come with an XP disk, so most likely I'll have to torrent an image of an XP install disc so i can use my own product key.

Ridiculous, no?

Good luck... driver hell with a fresh XP install can be the most frustrating thing in computing, especially on a laptop.

---

