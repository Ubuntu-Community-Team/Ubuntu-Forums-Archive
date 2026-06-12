---
title: "vista backup problem"
date: 2009-08-21
forum: The Cafe
---

### Post by sandyd on 2009-08-21
I currently have a problem.
My parents are buying a new laptop for me... but they require me to have a backup of vista. a bootable backup. that i can reinstall vista from.

Manufacturers don't provide reinstllation DVDs anymore (its kinda irritating as im used to installing windows a million times)
Im completely unfamiliar w/ windows vista.

how could i do this?

p.s. could i simply grab the recovery partition, make an image and stick it onto a ubuntu cd? then restore it when i blow windows into a million pieces by accident?

---

### Post by sandyd on 2009-08-21
p.s. since im buying from dell, i get a free win7 upgrade disk in october. could i take the bootsector of the win7 install disk from the net and patch it onto a copy of that? (yes, i know that theirs a difference between oem and upgrade)

---

### Post by FuturePilot on 2009-08-21
I know HP does this, I'm not sure about anyone else, but they allow you to make a recovery CD which is basically based off of the recovery partition. If that isn't the case another option would be to use Clonezilla or a  similar program and image the entire disk before you do anything to it.

---

### Post by lisati on 2009-08-21
My Toshiba laptop came with software that let me backup Vista's recovery partition to bootable disks. As far as I'm aware it isn't limited. My Compaq desktop came with similar software for XP but came with a limit of 1 set of disks that could be made (there is a workaround).

---

### Post by JC Cheloven on 2009-08-21
Hi, I assume that you plan to install ubuntu in your new pc. I've installed Ubuntu in about 10 dell computers, most of them with vista preinstalled (all except three mini9's). In my experience, dell is a very good choice and has an excellent post-sales service, at least in my country. I'd bet you'll enjoy it ;-)

As for your question: every dell+vista I've seen comes with a recovery partition. This is caught when installing ubuntu as dual boot, so grub ends up with the usual entries for ubuntu, one for vista, and one more for the recovery partition. If you choose to boot from this and go ahead, your disk will be reformatted to the state of brand-new (as it was when you bought the computer).

So, if you plan to dual boot (and have a minimal idea about you're doing), I wouldn't worry at all: you'll be always able to put your system back to its original state. Also you are -usually- given the choice of burning a set of dvd's out of the recovery partion, so you can use it eventualy for the same purpose.

If you're looking for a backup of the vista partition after updates and software installs, etc, all I can tell you is that the program I use for similar tasks in linux (fsarchiver) doesn't support ntfs. So little help on this point, sorry.

---

### Post by sandyd on 2009-08-21
hmm... guess i wasn't clear enough.
I meant that i wanted to create a CD that could boot up and restore EVERYTHING. 
from scratch.
meaning that im going to completely bomb the windows partition and start all over again.

something that could have the same effect as deleting the partition and using an oem cd to reinstall.

--oh wait, you mean i can create a recovery dvd that can completely reinstall windows even if i do something that completely bombs it over?

---

### Post by cariboo on 2009-08-21
Most laptops come with a utility to create restore dvd's. The utility usually pops up on first boot. Most Windows users ignore it, and manage to find a way to disable the pop up without creating the backup dvd. :)

---

### Post by isotonik on 2009-08-21
A vista recovery disk (iso) can be download from microsoft for free but it's not an installation disk, it will only boot/run from an existing recovery partiton.


> **cariboo907 said:**
> Most laptops come with a utility to create restore dvd's. The utility usually pops up on first boot. Most Windows users ignore it, and manage to find a way to disable the pop up without creating the backup dvd. :)

Recovery installation disks are notorious for not burning right and leave you up the river.

Best thing is to clone the hard drive with something like norton ghost, that will give you a bootable image of your current hard drive,

---

### Post by oboedad55 on 2009-08-21
> **carlee said:**
> hmm... guess i wasn't clear enough.
I meant that i wanted to create a CD that could boot up and restore EVERYTHING. 
from scratch.
meaning that im going to completely bomb the windows partition and start all over again.

something that could have the same effect as deleting the partition and using an oem cd to reinstall.

--oh wait, you mean i can create a recovery dvd that can completely reinstall windows even if i do something that completely bombs it over?

Hi, I use acronis true image to backup my XP system before I install something else. I realize it's not free, but it will allow you to backup everything to an external drive and restore it exactly the way it was when you backed up. It works very well. It will also backup Linux partitions and restore them as well. I may get slammed for this, but here it is: 
[http://www.acronis.com/](http://www.acronis.com/)

Jon

---

### Post by sandyd on 2009-08-21
> **oboedad55 said:**
> Hi, I use acronis true image to backup my XP system before I install something else. I realize it's not free, but it will allow you to backup everything to an external drive and restore it exactly the way it was when you backed up. It works very well. It will also backup Linux partitions and restore them as well. I may get slammed for this, but here it is: 
[http://www.acronis.com/](http://www.acronis.com/)

Jon
Thats actually really what i want... if there was a free version.
or is there an app that does disk imaging/restoring in ubuntu?

if there is, ill simply image my vista system once i get it, make several copies of it onto several disks and leave it somewhere safe. and of course, leave it with a ubuntu livecd.

---

### Post by sandyd on 2009-08-21
> **JC Cheloven said:**
> Hi, I assume that you plan to install ubuntu in your new pc. I've installed Ubuntu in about 10 dell computers, most of them with vista preinstalled (all except three mini9's). In my experience, dell is a very good choice and has an excellent post-sales service, at least in my country. I'd bet you'll enjoy it ;-)

As for your question: every dell+vista I've seen comes with a recovery partition. This is caught when installing ubuntu as dual boot, so grub ends up with the usual entries for ubuntu, one for vista, and one more for the recovery partition. If you choose to boot from this and go ahead, your disk will be reformatted to the state of brand-new (as it was when you bought the computer).

So, if you plan to dual boot (and have a minimal idea about you're doing), I wouldn't worry at all: you'll be always able to put your system back to its original state. Also you are -usually- given the choice of burning a set of dvd's out of the recovery partion, so you can use it eventualy for the same purpose.

If you're looking for a backup of the vista partition after updates and software installs, etc, all I can tell you is that the program I use for similar tasks in linux (fsarchiver) doesn't support ntfs. So little help on this point, sorry.

ah wait. so no matter how badly i damage it, ill still be able to restore it. completely. i don't really care about the rest of the apps that are on there - their reinstallable, im just a little queasy about the functionality of the OS
if i could find an free easy-to-use app for it that is...

and sorry if im dragging this on.
i had a winxp oem cd so im used sticking it into my computer whenever something goes wrong. :P foolproof.

---

### Post by FuturePilot on 2009-08-23
> **carlee said:**
> hmm... guess i wasn't clear enough.
I meant that i wanted to create a CD that could boot up and restore EVERYTHING. 
from scratch.
meaning that im going to completely bomb the windows partition and start all over again.

something that could have the same effect as deleting the partition and using an oem cd to reinstall.

--oh wait, you mean i can create a recovery dvd that can completely reinstall windows even if i do something that completely bombs it over?

Like I said before, usually if there is a recovery partition, there is also a program that lets you create a set of recovery DVDs or CDs that is based off of the recovery partition. Meaning that you can boot these CDs or DVDs and restore everything to how it was when you first got the computer.

> **carlee said:**
> ah wait. so no matter how badly i damage it, ill still be able to restore it. completely. i don't really care about the rest of the apps that are on there - their reinstallable, im just a little queasy about the functionality of the OS
if i could find an free easy-to-use app for it that is...

and sorry if im dragging this on.
i had a winxp oem cd so im used sticking it into my computer whenever something goes wrong. :P foolproof.

Assuming that you don't damage the recovery partition itself, then yes. I've had Windows get screwed up on me a number of times to the point where I thought it would be easier to just reinstall it. All I did was boot up the recovery partition and it restored everything to the way it was when I got the computer.

---

### Post by oboedad55 on 2009-08-23
> **carlee said:**
> Thats actually really what i want... if there was a free version.
or is there an app that does disk imaging/restoring in ubuntu?

if there is, ill simply image my vista system once i get it, make several copies of it onto several disks and leave it somewhere safe. and of course, leave it with a ubuntu livecd.

You can look at clonezilla. I've seen lots of posts about it.

---

### Post by Regenweald on 2009-08-23
how about not bombing the partition ? use the built in vista partitioning tool to shrink the Vista space to a discrete size, Give Ubuntu the rest. With the new boot structure, you won't even have to see vista, unless you hit 'esc' grub will send you straight into Ubuntu.

Vista can be handy for OEM bios and firmware updates and such.

---

### Post by inobe on 2009-08-23
the laptop will be supplied with instructions on how to create the backup dvd from the backup hard drive/ partition, if not check the manufactures site for that specific model.

---

### Post by sandyd on 2009-08-26
this will sound really really stupid, but how do you go about creating a recovery dvd(s)?

i only see an option for backing up files on my computer, not creating a bootable recovery disk.

---

### Post by jpeddicord on 2009-08-26
When you order your laptop, call sales or customer support and ask for a physical installation cd/dvd. They'll usually throw it in free if you just ask. The past two systems I've ordered I was able to do this, though I haven't had to actually use the disks. :)

---

### Post by sydbat on 2009-08-26
> **jacobmp92 said:**
> When you order your laptop, call sales or customer support and ask for a physical installation cd/dvd. They'll usually throw it in free if you just ask. The past two systems I've ordered I was able to do this, though I haven't had to actually use the disks. :)+100 

I was going to suggest this too. They should have no problem sending the disks out when you order.

However, if you have already gotten your computer, they may charge you shipping for the DVD(s).

---

### Post by sandyd on 2009-08-26
aww great.... here goes nothing....

---

### Post by krisarnold on 2009-08-31
Not that I like to give away one of my secrets...but, look up Hiren. Goto the wiki site, and choose the link below where the actual Hiren site is. This is the ultimate iso. You have a choice of several programs to clone hardrives. I suggest using vista to partition the hard drive the way you want it and then clone. I use snapshot, but thats just me. Acronis and ghost are on there along with a buttload of other computational tools.

---

### Post by madjr on 2009-08-31
wow is really this big of a hassle on vista?

and i thought linux was harder... guess not

---

