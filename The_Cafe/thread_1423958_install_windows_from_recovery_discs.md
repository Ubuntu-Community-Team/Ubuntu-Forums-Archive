---
title: "install windows from recovery discs"
date: 2010-03-07
forum: The Cafe
---

### Post by sandyd on 2010-03-07
I have a little problem here.... A few months ago, I wiped windows from my dell laptop cause it was being extremely slow. I need it back now cause my other laptop just got sent into dell for repairs. Is there some way I can get windows vista (or newer) on there without deleting my linux partition? I currently do not have a restore partition, but have the window xp oem (corperate) discs, the recovery discs for vista, and the dell windows 7 upgrade disc.

---

### Post by MooPi on 2010-03-07
You could clone the drive to backup , then reinstall XP. Send it to dell for repair then use your clone to repopulate the drive? Sorry did notice the Vista or newer. Ooops

---

### Post by lindsay7 on 2010-03-07
Use Gparted and make a partition for Windows then add windows.  This web site should tell you what you need to do. You may need to look around to find you particular situation.


[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Post Monkeh on 2010-03-07
> **carlee said:**
> I have a little problem here.... A few months ago, I wiped windows from my dell laptop cause it was being extremely slow. I need it back now cause my other laptop just got sent into dell for repairs. Is there some way I can get windows vista (or newer) on there without deleting my linux partition? I currently do not have a restore partition, but have the window xp oem (corperate) discs, the recovery discs for vista, and the dell windows 7 upgrade disc.

what version are you looking to install, and what type of disk is it?

my dell xp recovery disk is actually just a full xp install disk so i can install it without wiping anything other than the install partition and the boot loader.

however, my vista recovery disk for my asus laptop requires the vista recovery partition (that is hidden) on the laptop, and this totally resets my laptop to factory default.

if it's a full windows install disk you're looking to use you should be able to do it ok, but if it's a specified restore disk, they normally wipe everything

---

### Post by sandyd on 2010-03-07
its vista im installing... which is a problem... as dell did not provide me w/ an OEM disc.
I created the recovery disc, which will wash out everything on the HD.
maybe if I beg my supervisor, she can give me an OEM vista disc.....

---

### Post by blueturtl on 2010-03-07
The license key printed on your computer might not work with an OEM disc.

Just giving you a heads up because I had to use a recovery disc once but for some reason it failed so I tried to use an OEM media from my employer (same OS, no difference I thought) but it did not accept the key printed on the bottom of the laptop.

---

### Post by Post Monkeh on 2010-03-07
> **carlee said:**
> its vista im installing... which is a problem... as dell did not provide me w/ an OEM disc.
I created the recovery disc, which will wash out everything on the HD.
maybe if I beg my supervisor, she can give me an OEM vista disc.....

do you have an external hard disk you could clone your current hd to?

if so, you could clone your current disk, reinstall vista, repartition, then clone your old partitions back to the newly created ones (if that makes sense) with the dd command (i think) but i know nothing about that command except that it can erase your entire file system if used incorrectly, so i'll allow someone else to instruct you there, but it SHOULD be possible.  you would likely have to fiddle with your fstab file but i don't think it'd be too difficult, just time consuming.

---

### Post by Post Monkeh on 2010-03-07
> **blueturtl said:**
> The license key printed on your computer might not work with an OEM disc.

Just giving you a heads up because I had to use a recovery disc once and once it failed I tried to use an OEM media from my employer (same OS, no difference I thought) but it did not accept the key printed on the bottom of the laptop.

dunno about vista, but my xp install disk is a dell oem, and my pc isn't dell.

it wouldn't accept the licence key even provided with the disk, but a call to the automated phoneline sorted it in 5 minutes.  it maybe depends on the disk.

---

### Post by blueturtl on 2010-03-07
> **Post Monkeh said:**
> do you have an external hard disk you could clone your current hd to?

if so, you could clone your current disk, reinstall vista, repartition, then clone your old partitions back to the newly created ones (if that makes sense) with the dd command (i think) but i know nothing about that command except that it can erase your entire file system if used incorrectly, so i'll allow someone else to instruct you there, but it SHOULD be possible.  you would likely have to fiddle with your fstab file but i don't think it'd be too difficult, just time consuming.

That's good advice. I complement with this: [Clonezilla]("http://clonezilla.org/")

It's a Linux live (text menu based) solution built for just occasions such as this.

---

### Post by sandyd on 2010-03-07
> **Post Monkeh said:**
> dunno about vista, but my xp install disk is a dell oem, and my pc isn't dell.

it wouldn't accept the licence key even provided with the disk, but a call to the automated phoneline sorted it in 5 minutes.  it maybe depends on the disk.

> **blueturtl said:**
> The license key printed on your computer might not work with an OEM disc.

Just giving you a heads up because I had to use a recovery disc once but for some reason it failed so I tried to use an OEM media from my employer (same OS, no difference I thought) but it did not accept the key printed on the bottom of the laptop.
VLK corperate keys override everything.
One of my desktops at home has a corperate winxp installed on it with the company's VLK key. 

Works perfectly, but I need something higher than XP.

The problem is that I **cant** squish vista/7 that much. Which means that im going to be wasteing tons of space because im only going to be installing like.... 1-2 applications on there.

---

### Post by sandyd on 2010-03-07
> **Post Monkeh said:**
> do you have an external hard disk you could clone your current hd to?

if so, you could clone your current disk, reinstall vista, repartition, then clone your old partitions back to the newly created ones (if that makes sense) with the dd command (i think) but i know nothing about that command except that it can erase your entire file system if used incorrectly, so i'll allow someone else to instruct you there, but it SHOULD be possible.  you would likely have to fiddle with your fstab file but i don't think it'd be too difficult, just time consuming.
dont have an external hard disk.
or anything that can store 520 GB (which is my current disk usage)

---

### Post by blueturtl on 2010-03-07
Is there enough space to install Windows into a virtual machine then?

[www.virtualbox.org](www.virtualbox.org)

That would allow you to use the applications you need without breaking your current installation of Linux.

---

### Post by sandyd on 2010-03-07
> **blueturtl said:**
> Is there enough space to install Windows into a virtual machine then?

[www.virtualbox.org]("http://www.virtualbox.org")

That would allow you to use the applications you need without breaking your current installation of Linux.
the applications directly interface with non-virtualbox supported hardware and this processor does not have VT.

---

### Post by blueturtl on 2010-03-07
You're not going to let us off the hook very easy. :)

I'm out of ideas this very instant. :-k

---

### Post by Post Monkeh on 2010-03-07
> **blueturtl said:**
> You're not going to let us off the hook very easy. :)

I'm out of ideas this very instant. :-k
i was out of ideas after my second post :D
> **carlee said:**
> dont have an external hard disk.
or anything that can store 520 GB (which is my current disk usage)

well i'm not an expert, but personally i can't see how you can use a restore disk that is deigned to reset your laptop to factory settings without losing your files.
is this a dell recovery disk?
if so, it MAY be the same as my dell xp disk in that it says recovery disk but in actual fact is a full install disk.

stick it in and try installing it in virtualbox. if you can, then it's a full install disk, and technically all you should need to do is use gparted to make a partition big enough for vista, install it, and restore grub.
but at 520gb of files, i'd be trying to find a way to back that up before i do anything.

btw 520gb? on a laptop? i didn't even know they made 2.5" drives that size.

---

### Post by Daveski on 2010-03-07
You really need to get a drive big enough to backup your important data - even if you weren't going through this particular issue.

---

### Post by sandyd on 2010-03-15
And heres why I love dell so much.
The "upgrade" cd they gave me was actually an OEM disc.
The serial they gave me was actually an oem serial that could also function as an upgrade serial.
 
Insert disc into dvd drive, install, insert serial = profit :)

---

