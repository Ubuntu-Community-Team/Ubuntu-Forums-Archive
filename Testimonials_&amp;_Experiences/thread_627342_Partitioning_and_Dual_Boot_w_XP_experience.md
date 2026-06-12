---
title: "Partitioning and Dual Boot w/ XP experience"
date: 2007-11-30
forum: Testimonials &amp; Experiences
---

### Post by airjaw on 2007-11-30
Ok here is my experience with setting up a dualboot XP and ubuntu on a Dell Inspiron shipped with Vista installed.

First I formatted the drive with WinXP Setup and wiped Vista completely.  This went smoothly, although I did have to track down the drivers for my SATA drive and slipstream them onto a custom winxp install CD.

Then I installed Ubuntu.  Worked perfectly, grub, everything, even the wireless card was automatically detected and i was on the internet instantly!

1 Problem: The ubuntu partition does NOT work properly.  I don't even care if it really did what it was supposed to - if I really did read the directions wrong and set my partition size to 20 gb instead of 80gb.  I don't care because the way the partition question and option are worded are counterintuitive.  I've noticed several other people mentioning that the partitioner did the opposite of what they wanted with their drives and this should be something that is changed.

I wanted WinXP to be 20GB and Ubuntu to be 80.  I move the slider bar over to the right... at what is intuitively 80%.
Well, winXP ends up being 80GB and ubuntu ends up being 20GB.  HuH?

Also, this has also been mentioned (the separate /home option 
during installation), but I have a question about it.
I created the partitions already.  I resized my 80gb NTFS to 20gb.  I created a 60gb drive to use for /home and 20GB to use for /root and swap.
The problem is that I already have a swap drive from the previous ubuntu install and in LiveInstallCD gparted I cannot unmount it and delete it.  
I want everything to be clean... I don't want extra swap drives floating around.  Is there a way to clean all these drives up?
Also... I don't get how to set the partition I created for /home to actually be /home.  Meaning... I have the partitions created in Gparted.  I go to Ubuntu Install.  And I'm not sure how or where I'm supposed to tell the Install that I have a partition for /home and a partition for my root.  It seems like it will just go ahead and use the 20GB I have right now for /root and use it for the normal ubuntu install with home and root on the same drive.

Ok thats it I hope I was clear.  If anyone could help me with my questions that would be great... I'm on my 5th day trying to get my laptop setup.

Oh and my hard drive order is like this:

NTFS (20GB) ----- EXT3(60GB - planned for /home) ---- EXT3(20GB- planned for root) ----- (EXT3 - SWAP, EXT3- SWAP)

I'm pretty sure the new ubuntu install will create another swap giving me a total of like 6 partitions.

---

### Post by logos34 on 2007-11-30
> **airjaw said:**
> I don't get how to set the partition I created for /home to actually be /home.  Meaning... I have the partitions created in Gparted.  I go to Ubuntu Install.  And I'm not sure how or where I'm supposed to tell the Install that I have a partition for /home and a partition for my root.

[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html)

If the version of gparted on the livecd won't let you unmount swap to delete it, and you've tried

sudo swapoff -a 

try the [gparted livecd]("http://gparted.sourceforge.net/livecd.php").

---

### Post by Sef on 2007-11-30
Read Psychocat's [installing Ubuntu]("http://psychocats.net/ubuntu/installing").

---

### Post by erfahren on 2007-11-30
when the partition has already been created I get this: [http://img216.imageshack.us/my.php?image=feistydual12tj0.png](http://img216.imageshack.us/my.php?image=feistydual12tj0.png)
(from [psychocats](http://psychocats.net/ubuntu/installing) guide.)

---

### Post by armandh on 2007-11-30
I like parted magic live cd to do partitioning. [and resizing]
it gives a nice graphic representation.  
it is similar to partition magic but linux and with more file types.
[http://www.partedmagic.com/](http://www.partedmagic.com/) download
this is an area where a good gui makes it easy to understand wtf is going on.

---

### Post by airjaw on 2007-11-30
Thanks guys.  one of the articles someone posted helped.
I created swap of 2GB.  I couldn't modify the existing swap (it was locked in Gparted).  I'm not sure if I am in liveCD mode.  I am in the Ubuntu CD install mode and that swap drive was locked.

I am installing ubuntu right now... I am going to have 2 swap drives now.  I want to fix this later...

---

### Post by logos34 on 2007-12-01
> **armandh said:**
> I like parted magic live cd to do partitioning. [and resizing]
it gives a nice graphic representation.  
it is similar to partition magic but linux and with more file types.
[http://www.partedmagic.com/](http://www.partedmagic.com/) download
this is an area where a good gui makes it easy to understand wtf is going on.

Same here.  Been using it for some time now as my preferred utility live cd.  Even have set up so I can boot it straight off the hard drive.  Not as many features as SystemRescueCD, but it has all the important stuff, plus latest gparted, disk mounting tool, usb utility and cd burning app (after it loads into the ram the disc kicks out, freeing up the drive).
> 
I created swap of 2GB. 

airjaw, 

that's overkill.  1 GB is more than enough (and you can use all the space you can get with only an 80gb drive).

---

### Post by baxterdog on 2007-12-01
I too had this problem with a dual boot on a new box with an asus mbd and an amd chip. Just decided to wipe it all clean and reinstalled MS to just keep moving. Got tired of having to choose the MS OS when Ubuntu would never run right anyways. 

Ubuntu is running fine as the only OS on a travelmate 2480 laptop.

Plan to add another hard drive to the desktop to see if this helps with the dual boot.

---

