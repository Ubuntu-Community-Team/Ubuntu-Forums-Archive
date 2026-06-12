---
title: "What Distro should I use?"
date: 2007-08-10
forum: The Cafe
---

### Post by Turboaaa2001 on 2007-08-10
Here is what I'm looking at:

I have Fiesta installed on my everyday machine (the one with all the bells and whistles), but I want to un-install and start over. The problem is that now that I have my feet wet, I'm asking myself what I want to do differently?

Here is what I'm looking for:

1. Relatively good compatibility
2. Ease of erasing data i.e. Really deleting my web cache instead of just letting FF do it.
3. The pure control over where my data is and being able to find where all the temp folders are.

Basically I want to make it secure as possible. This time around I'm going to create the environment I need instead of monkeying around with all the cool apps that come with Ubuntu.

So I need to know if I can get the above out of Ubuntu (the most stable version??) or if I need to go somewhere else.

---

### Post by Epilonsama on 2007-08-10
you could try doing a server install of ubuntu or you could try using Debian Etch cuz is really stable, but keep in mind that Debian etch doesn't do program updates that often.

---

### Post by starcraft.man on 2007-08-10
I don't see a reason to change from Feisty. Ubuntu has 1 for the most part. 2 and 3 can be handled with a bit of learning but I don't think are really tied to any one distro (especially 3, file structure is almost uniform across the distros if I'm not mistaken).

I say stick with what you got. For the record, I use the same copy of Feisty 32 bit for both my day to day work and my messing around :).

---

### Post by seshomaru samma on 2007-08-10
you can do 2 and 3 with Ubuntu , 
you might want to try Debian Etch as well

as for 1 (compatibility) it`s really a hit and miss, depending on your hardware), if Feisty was Ok then stick with it , Debian Etch should offer roughly the same compatibility.

---

### Post by tbroderick on 2007-08-10
**1. Relatively good compatibility**

Don't know what you mean. Does Ubuntu work with your hardware?

**2. Ease of erasing data i.e. Really deleting my web cache instead of just letting FF do it.**

There is a cache folder under ~/.mozilla. Something like ~/.mozilla/firefox/tnph1rq2.default/Cache/


**3. The pure control over where my data is and being able to find where all the temp folders are.**

Do you mean where applications store their preferences/settings or /tmp?

---

### Post by Drate on 2007-08-10
I'd wait till the next LTS, Gutsy Gibon.  Keep with what yo have for now.  When Gutsy hits, I'd wipe clean and start fresh, then keep to it.  I wouldn't take any new Ubuntu releases till the next LTS... I wish I had never upgraded from Edgy.  Grrr... grrr I say.

Also, for educational purposes there is LFS, Linux From Scratch (HLFS for security).  Create your own distro, but it's a bear to get through it all.

Otherwise I'd say these guys know more than me.  Personally I'm using Puppy Linux which is the only thing I can consitently make work.  Not all the utils work up to par, but I can get on the internet and do wordprocessing fine.  Plus it's uber small and uber fast and can be run from a CD, don't even have to put the darn thing on your hard drive.  Ain't that special?

---

### Post by Turboaaa2001 on 2007-08-11
> **tbroderick said:**
> 
**3. The pure control over where my data is and being able to find where all the temp folders are.**

Do you mean where applications store their preferences/settings or /tmp?

I mean the folders in which logs and temporary files are held. I want to be able to find these easily and create a shell script to delete them regularly.

One thing I do need to be more specific on is that I want to make sure the distro I'm using is not linked to a large corporation. Although I'm not paranoid (except those ETs reading my mind) I want my actions on this one machine to be hidden from the world.

---

### Post by tbroderick on 2007-08-11
> **Turboaaa2001 said:**
> I mean the folders in which logs and temporary files are held. I want to be able to find these easily and create a shell script to delete them regularly.


Logs are in /var. I'd recommend using logrotate to clean them out. Temp files could be in /tmp, which you don't want to delete while running. /tmp should clear itself out either at boot or shutdown. There might be some temp files in /var/cache which should be ok to delete. Just don't delete all of /var or you might loose some data.

---

### Post by ssam on 2007-08-11
You might want to look at encrypting you partitions, and swap. there are some howtos in the wiki.

you could run entirely from a live cd. it is possible to customise the live cd to have different apps on it.

you could use virtualisation. (qemu, zen, virtualbox etc). do a clean install in a virtual machine. backup this machine image. then you can revert back to a clean machine when ever you want. (fedora has some good tools for virtualisation)

be aware that deleting files does not always remove the data from your disk. there that properly overwrite the space on the disk where the file used to be. there is a package called secure-delete in the repos, you could look at that.

if you want super secure you might want to look at openbsd instead of linux

---

### Post by Turboaaa2001 on 2007-08-11
> **ssam said:**
> ....

be aware that deleting files does not always remove the data from your disk. there that properly overwrite the space on the disk where the file used to be. there is a package called secure-delete in the repos, you could look at that.

if you want super secure you might want to look at openbsd instead of linux

Hey thanks! I know that the data is still there but just un-attached to the filesystem. I really appreciate the help, I will be sure to look-up that package!:)

---

