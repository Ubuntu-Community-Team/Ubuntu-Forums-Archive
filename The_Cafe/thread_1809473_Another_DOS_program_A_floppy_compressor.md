---
title: "Another DOS program: A floppy compressor"
date: 2011-07-21
forum: The Cafe
---

### Post by jjpcexpert on 2011-07-21
UPDATE: Still working on the program. Do not download until I give the "Green Light".
UP2: Wait the whole Summer Holidays - I have a problem to address.
UPDATE 3: I am now ready to declare version 1.0 of flpcmp.

EDIT: It is now safer than ever. Even gets directories now!
Still: USE A UPS or a laptop constantly on AC with a battery in it.
You'll thank yourself during a power cut if you do.

I have actually done some trial/error in compressing on floppies, and I have decided, that the best compressor for turning 1.34MB of space into 1.62MB (try to limit yourself though!) is Info-ZIP ZIP.

Therefore I may now release SquashDISK for DOS.

There are two versions, to unzip to a DOS computer, via CD or whatnot. Make sure you have a blank or unimportant disk with FAT12 format! If you are viewing this on DOS (using Arachne?) you may directly unzip or unlzma then untar the archives provided. The actual thing is less than 128k unzipped. Transfer to your DOS machine for installing on floppies.

When saving the lzma to your DOS, rename in Arachne or Lynx to flpcmp.tlz from flpcmp.tar.lzma.

At the C:\where\you\unzip\ped\flpcmp\to> prompt, type instsqdk and it will install SquashDISK on the floppy in A:. ONLY use that floppy in the A: drive of any DOS or Windows computer from now on. To uncompress to the U: volume, type ```
A:\sqdskuz
``` .
To unmount U: and rezip to update files, type A:\sqdskz at the U:\> prompt, and you should be returned to a C:\some\where> prompt. 

SquashDISK is designed for floppies.
It uses a ramdisk to cache files before unmounting.

Make sure to ONLY use this with a UPS or a laptop. You do NOT want your computer dieing while you still have crucial documents in the RAMdisk. If you have a UPS or battery and the power goes out and you're stuck with battery, save and sqdskz unmount your work as fast as you can and then halt the computer, make sure it powers down.

[flpcmp.zip]("http://jack-gopher.dyndns.org:5000/flpcmp.zip") (for DOS users with PKzip)
[flpcmp.tar.lzma]("http://jack-gopher.dyndns.org:5000/flpcmp.tar.lzma") (for Unix and DOS users with a CD or floppy to spare, this one needs not be copied to HDD if run from CD or the B: drive on your DOS machine, just like the last)

---

### Post by An Sanct on 2011-07-21
Your 11??? :)

Nice prog, tho!

---

### Post by LowSky on 2011-07-21
Who uses floppies anymore?

---

### Post by Dr. C on 2011-07-21
> **LowSky said:**
> Who uses floppies anymore?

I do.

---

### Post by 3rdalbum on 2011-07-21
Would have been handy 20 years ago. Not so much now, unless you make it work with flash drives on Windows.

---

### Post by psusi on 2011-07-21
> **Dr. C said:**
> I do.

Do you also use a telegraph? ;)

Seriously, floppies were obsolete 10 years ago, and oems finally stopped including them in new PCs at least 5 years ago.  People haven't been using DOS since long before that, and of course... this is a forum about a Linux distro... so this thread greatly confuses me.

---

### Post by forrestcupp on 2011-07-21
Wow. I remember DOS and floppies.

I'm thinking the original poster is John Titor and he accidentally set his machine to 2011 instead of 1991. :)

---

### Post by jjpcexpert on 2011-07-22
No. I am not John Titor, this is not 1991 and it's designed for those who really need the extra space available by compressing files piecemeal. 

Thanx 4 the laughs though. 

And for some reason, this is not an Ubuntu support topic.

---

### Post by jjpcexpert on 2011-07-22
> **3rdalbum said:**
> Would have been handy 20 years ago. Not so much now, unless you make it work with flash drives on Windows.
 
 
May I now make it obvious that writing a compressed FS driver for Windows will be a pain?
 
And this driver was just a DOS research project on what really can be done with batch files.
 
But you may use it for non-critical data (NOT YOUR FAMILY PHOTOS) or you may save newsgathered content. It should really be flat text, otherwise Deflate will decide to store the content with less compression, or find that it will be inefficient to compress and store the file flat.
 
I personally don't use it.
 
I need to design a way to uninstall this from floppies. It will copy to your HDD, then give you help on copying the files. Like to stop when dir A: reveals less than 32kB free on the floppy, and to move on to the next floppy after doing that.
 
OK?

---

### Post by psusi on 2011-07-22
> **jjpcexpert said:**
> it's designed for those who really need the extra space available by compressing files piecemeal.

You forgot "and who still use MS-DOS", which is, well... nobody...

I think the last time I even still had an old dos boot floppy collecting dust was around 2003 or so.  I finally threw it out since it was no longer even usable as an emergency rescue method since it didn't understand NTFS or disks larger than 2gb.

---

### Post by RiceMonster on 2011-07-22
Don't copy that floppy.

---

### Post by jjpcexpert on 2011-07-22
> **RiceMonster said:**
> Don't copy that floppy.

I lol'd

But seriously, this is for those who use anyDOS EXCEPT CP/M 86.

I use FreeDOS when I'm dev'ing DOS fsdrvs, I'm just WEIRD!!!!!!!!!

---

### Post by jjpcexpert on 2011-07-22
> **psusi said:**
> You forgot "and who still use [COLOR=Red]MS-DOS[/COLOR]", which is, well... nobody...

I think the last time I even still had an old dos boot floppy collecting dust was around 2003 or so.  I finally threw it out since it was no longer even usable as an emergency rescue method since it didn't understand NTFS or disks larger than 2gb.

Well I use FreeDOS, and so do SO MANY other people out there.

So none of that tosh thank you.

---

### Post by forrestcupp on 2011-07-22
Well, since I can't really test it out, I'll just make an assumption and tell you "Good job". Just because nobody uses it doesn't mean you didn't do a lot of hard work and do a good job.

I once programmed something in BASIC in a C64 emulator just for nostalgia. :)

---

### Post by dh04000 on 2011-07-22
> **Dr. C said:**
> I do.

I use floppies as well. I'm a scientist. A nice HPLC or MS can cost in the hundreds of thousands of dollars. So we used machines for decades. If thier software was written for windows 3.1, or DOS, we kept a windows 3.1 or DOS machine around to run them. So..... I use floppies alot. We even have 8inch disc running machines!!!! But we never use that old spec anymore, so I have never seen anyone even boot up the computer associated with it, thank god! It doesn't even have a harddrive. It boots from a series of 8inch floppies!

---

### Post by jjpcexpert on 2011-08-20
please delete this specific post from your database. thank you.
not the thread, but this specific post in this thread.

---

