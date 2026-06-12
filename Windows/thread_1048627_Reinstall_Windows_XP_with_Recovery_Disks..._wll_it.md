---
title: "Reinstall Windows XP with Recovery Disks... wll it erase Ubuntu?"
date: 2009-01-23
forum: Windows
---

### Post by the8thstar on 2009-01-23
Well folks the title says it all.

I kept the Recovery disks from when I had Windows XP running on my computer. I ditched XP a long time ago and now I solely run Ubuntu 8.10.

I want to use the Recovery disks to reinstall Windows XP alongside Ubuntu (each on its own partition of course).

But I wonder if the recovery disks will wipe out Ubuntu in the process. What do you guys think? Have any of you tried this before?

---

### Post by Dr. C on 2009-01-24
My understanding is yes. Many Windows OEM recovery disks return the computer to the original state when it was first sold. They will wipe out Ubuntu and anything else on the hard drive.

---

### Post by Ericyzfr1 on 2009-01-24
I used recovery disks on my vaio and there was no partition manager.

---

### Post by jfr1tz on 2009-01-24
> **the8thstar said:**
> Well folks the title says it all.

I kept the Recovery disks from when I had Windows XP running on my computer. I ditched XP a long time ago and now I solely run Ubuntu 8.10.

I want to use the Recovery disks to reinstall Windows XP alongside Ubuntu (each on its own partition of course).

But I wonder if the recovery disks will wipe out Ubuntu in the process. What do you guys think? Have any of you tried this before?

pretty much without exception. However you have options such as [this]("http://www.howtohaven.com/system/createwindowssetupdisk.shtml"), there are a few more guides like this (google for more). It lets you do a clean install rather then remastering(and wiping) your hard drive with recovery disks. Downside is you just get windows, so you have to add all the remaining drivers manually.

---

### Post by Bender the Robot on 2009-01-24
A recovery disc will, normally, consolidate all partitions into one and install Windows in the resultant space.

---

### Post by seanc7 on 2009-01-25
Pretty much yeah, most of them use something like Norton Ghost to restore the OEM recovery disk so it blows away all partitions to make the hard disk the same as it was when you first bought the system.

Rather then just including the Windows install CD with a driver CD for the hardware. Guess that makes too much sense for manufacturers anymore.

---

### Post by shadoweva00 on 2009-01-25
I'm not sure why everyone is saying this stuff, I've never come across any disks that just restore an image. Every one I've come across is just a windows install disk without the need to enter a product key. Most recovery disks are just windows install disks. they can easily select partitions to install to, however they will make the system default boot into the windows partition. If you let Ubuntu use the whole disk, you probably need to change your existing partition sizes and create a new one for windows.

short version: boot your disk to see if it's a windows install disk. you have to see about shrinking existing partition(s), adding new one, and then reconfiguring boot loaders. last 3 things could ruin you're system or make it unbootable if you don't know what you're doing.

(Seriously where are you getting these kinds of disks? is this what they sell at best buy with computers and such or through business contracts? I've really never seen such a thing.)

---

### Post by coffeecat on 2009-01-26
> **shadoweva00 said:**
> I'm not sure why everyone is saying this stuff, I've never come across any disks that just restore an image. Every one I've come across is just a windows install disk without the need to enter a product key.

Previous posters are saying this because it has been their experience. It has certainly been my experience. You've been lucky if you've only ever seen a 'proper' Windows install disk.

> **shadoweva00 said:**
> (Seriously where are you getting these kinds of disks

Out of the big cardboard box that the computer ships in. :wink:

---

### Post by Bender the Robot on 2009-01-26
> I'm not sure why everyone is saying this stuff, I've never come across any disks that just restore an image. Every one I've come across is just a windows install disk without the need to enter a product key.

The only company, I've dealt with, in the UK, that gave anywhere near a full disc were "QTech", and they were highly "customised" discs - ( some of them did have a partitioning facility but most didn't - it probably depended on the price bracket of the system you bought ).  Most others give a restore disc and some don't even give that - you need to burn an image of the "restore partition" and create your own disc.  

> Out of the big cardboard box that the computer ships in. 

Not if you buy an Acer Aspire, you don't - they're one of the companies with a "roll yer own!" attitude ;-)

---

### Post by Kevbert on 2009-01-26
Recovery will format and install Windows over the whole disk with a single partition. You'll then need to shrink this single partition with gparted. Next run up Windows again as it may complain and perform a chkdsk on the Windows partition.  Now you can run up a Ubuntu live CD, installing and formatting the spare space as you like for Ubuntu.

---

### Post by djb6 on 2009-01-26
My vista recovery disc wouldn't touch the other partition if I set it to factory settings.

---

### Post by kspncr on 2009-01-27
Yes, using the recovery disks will definitely eat Ubuntu.

> **shadoweva00 said:**
> (Seriously where are you getting these kinds of disks? is this what they sell at best buy with computers and such or through business contracts? I've really never seen such a thing.)

They come with computers that have Windows preinstalled. Some manufacturers now require the user to create their own recovery disks with a recovery disk-making tool preinstalled on the PC.

---

