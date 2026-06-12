---
title: "How do I make a physical copy of my hard drive"
date: 2008-07-24
forum: Virtualisation
---

### Post by Markissocoollike on 2008-07-24
Hi, what i basically want to do is make a copy of my original windows and virtualize it into a machine, why? Because:

1. Virtual hard drives provide very little space for what i want, I want a hard drive with 200GB for example and the actual size i find out is 7GB when i set it to 200GB and I have about 450GB on my hard drive so, who wouldn't blame me if i want to make windows run on xubuntu, If anyone knows of a way to increase the amount of space on the drive I would REALLY like to know.

2. Activating windows and waiting for it to install is annoying, especially when you had to try again and again because the ubuntu version isn't stable enough and windows gets corrupt on the virtual machine itself because of it, good thing i can dual boot ^^

3. Installing software and hardware is also annoying plus if i could make a simple copy of my original windows I'd be able to get on with things quicker.

Oh and im also having a problem with VirtualBox and its saying its not accessible (again!) I think I asked about this before though, anyway please help as much as you can.
Kind regards,
Markissocoollike

---

### Post by vandorjw on 2008-07-24
Hey, if virtual box is inaccessible, add your user to the "virtualbox" users and groups. That should fix that problem.

I would also like to know how to make a copy of my Hard Drive.
(Just like how Dell and Others give us a restore Image.)

I have Ubuntu set up just how I like it, and if I mess something up, it would be soo nice to restort it from something like a backup image.

At the moment, its about 25gb, so it be best if it could be done with DVDs.


Cheers CC7

---

### Post by Markissocoollike on 2008-07-24
lol forgot about that thanks for reminding me :P

---

### Post by Keithel on 2008-07-24
> **Markissocoollike said:**
> 1. Virtual hard drives provide very little space for what i want, I want a hard drive with 200GB for example and the actual size i find out is 7GB when i set it to 200GB and I have about 450GB on my hard drive

I think I may understand your concern, and, if I understand it, your concern is unfounded.

The following is based on my experiences with VMware VMs, and not with virtual box -- though I believe Virtual Box acts the same in these regards.

When you create a virtual disk, you can specify for it to have a specific size, say, 200GB.  If you create it with default options, you will see that the generated file is *not* 200GB, but instead is just a few hundred kilobytes, or, after doing an install of the OS to it, it may be a few gigabytes.  The reason this is the case is, generally, by default, virtual disks are created so they only take up as much space as is being *used* in the virtual disk (at least initially).  They will grow to fill the 200GBs (the actual size of the virtual disk file will not have a direct correlation to the amount of data stored on the disk).

Now, when you create the virtual disk, you can specify it to pre-allocate the space of the entire virtual disk - in this example, 200GB.  When this is done, you will indeed see that the virtual disk file is 200GB.

Hope that clears up some of your confusion!

---

### Post by Markissocoollike on 2008-07-24
> **Keithel said:**
> I think I may understand your concern, and, if I understand it, your concern is unfounded.

The following is based on my experiences with VMware VMs, and not with virtual box -- though I believe Virtual Box acts the same in these regards.

When you create a virtual disk, you can specify for it to have a specific size, say, 200GB.  If you create it with default options, you will see that the generated file is *not* 200GB, but instead is just a few hundred kilobytes, or, after doing an install of the OS to it, it may be a few gigabytes.  The reason this is the case is, generally, by default, virtual disks are created so they only take up as much space as is being *used* in the virtual disk (at least initially).  They will grow to fill the 200GBs (the actual size of the virtual disk file will not have a direct correlation to the amount of data stored on the disk).

Now, when you create the virtual disk, you can specify it to pre-allocate the space of the entire virtual disk - in this example, 200GB.  When this is done, you will indeed see that the virtual disk file is 200GB.

Hope that clears up some of your confusion!

you know, im more confused by what you said than the problem itself I don't think there is a way to pre-allocate space with virtualbox at least I don't think there is, all it does is just tell me to allocate the space so if you have managed to get more space on your virtual drive then that must mean that there is a way to do it but i don't know of it yet :P

---

### Post by Markissocoollike on 2008-07-24
wait, what would happen if i made 2 seperate partitions on the os? Would that make it so that the original amount of space needed for the actual visualization would be seperated from all that free space? Maybe making two seperate partitions... I'll try it out I really want to get a game on there :)

---

### Post by Markissocoollike on 2008-07-24
ok heres what i've done: I have allocated 5GB for the main windows os and allocated the rest of the space on a seperate drive, I'm not sure whether or not this will work but if im lucky it might do :)

---

### Post by uidb4056 on 2008-07-24
> **cc7gir said:**
> Hey, if virtual box is inaccessible, add your user to the "virtualbox" users and groups. That should fix that problem.

I would also like to know how to make a copy of my Hard Drive.
(Just like how Dell and Others give us a restore Image.)

I have Ubuntu set up just how I like it, and if I mess something up, it would be soo nice to restort it from something like a backup image.

At the moment, its about 25gb, so it be best if it could be done with DVDs.


Cheers CC7

Have a look to Clonezilla [http://www.clonezilla.org/](http://www.clonezilla.org/) it let you backup partitions or entire disk on external media or internal hard disk.

---

### Post by Markissocoollike on 2008-07-24
my idea worked: I basically just created two partitions using C: and D: drive the disk drive used the E: drive just like my laptop ^^ anyway basically for it to be used it must be formatted the best way to do this is to click on start and then run and then simply type D: then you will be prompted on how much you want and so if you did what i did and partitioned two drives one being about 10GB (c) and the other 190GB (d) then you will be able to get the right amount of space required on each drive the prompt menu should give you a load of options but i found the default settings were reasonable and pressed ok (don't pay any attention to this pre-allocating stuff we have been talking about) and to your surprise you will see the d drive will have enough space for all your games and applications now the only problem is getting turok to work :P some idiot had to go too far with anti-cheating on the internet.

---

