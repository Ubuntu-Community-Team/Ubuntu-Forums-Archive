---
title: "2 TB limit in Ubuntu Server - kernel GPT supported?"
date: 2008-03-06
forum: Server Platforms
---

### Post by Yfrwlf on 2008-03-06
From what I have heard, Ubuntu Server does not support the GPT disk label type by default, and GPT seems to be one of the few disk labels that can support disks and arrays above the 2 TB limit that apparently the MSDOS label format suffers from.  If this is true, it seems strange, since if Ubuntu wants to strive to be a server OS, it should at some point get ready for supporting such sizes as disks continue to get larger.

Or, it already does, and there is some other problem that I'm having. :)  So here goes...

Using Ubuntu 7.10/Kernel 2.6.22, my RAID is seen fine as 2250 GB, the size it should be.  I use parted to create a GPT disk label and have used both parted and gparted to create partitions and they show up as the right size.  Well, they show up as having 2.05 TB free under a reiserfs partition, and about 2.0 TB free under ext3, and parted shows the size of the partition to be 2250, so I'm assuming the missing space is because of the partition's inode table.

Mounts fine, can copy files to them fine, then after a reboot everything goes to hell.  After mounting again, I can see file names but everything else has a ? and they are all unusable, meaning that the inode table has been corrupted somehow.  I assumed that this was due to the kernel not having proper support for GPT, but perhaps there is another issue.

Anyone have any clue, or have any success in getting their Ubuntu Server working with a disk or array of >2TB? :confused:  I'm hoping that my problem is a one-off and that Ubuntu Server can normally easily support >2TB disks/arrays and I simply have a specific problem with my hardware or drivers.  I'd prefer not to have to use CentOS or whatnot instead because I love apt-get too much, and yum just doesn't cut it, and even though one package shouldn't make a difference I don't know if it's possible to use apt-get on an RPM-based distro, which sucks, so I'm left really wishing I could get this working.  Perhaps I'll try Debian instead, or try to recompile the kernel, but I just am amazed this would be a problem for Ubuntu Server.

Also, I'm assuming the Ubuntu Server stock kernel has been compiled with CONFIG_LBD support enabled that is supposed to make the kernel support >2TB sizes, but that's not necessarily the same thing as GPT support of course.

---

### Post by wirelessmonkey on 2008-03-06
I cant' speak to the technical details, but I have a 5TB Raid5 with Feisty...

---

### Post by Yfrwlf on 2008-03-06
> **wirelessmonkey said:**
> I cant' speak to the technical details, but I have a 5TB Raid5 with Feisty...

Oh, wow, OK.  My research led me to think that no one had gotten it working with Ubuntu, so that's good to hear yours is working great!  Perhaps then it's a problem with my drivers, even though it can function to a degree perhaps they aren't fully working.

Going to do some more tests, thanks for your reply, and for anyone else having a similar problem, the server specs:

Compaq Proliant 8000 w/ 8 Pentium 3 Xeons 900 MHz each w/ 2 MB cache, 4 GB RAM, 50 GB old array, 3000 GB new array w/ hardware RAID card (not sure on brand yet).

---

### Post by Yfrwlf on 2008-03-06
> **wirelessmonkey said:**
> I cant' speak to the technical details, but I have a 5TB Raid5 with Feisty...

So you didn't have any problems at all then, you did a format of your RAID and set it up during the Ubuntu install and it worked out of the box after that, with the correct size and everything?  You don't know if it made your RAID use GPT or MSDOS?

After installation, our array showed up as about 50GB.  Very weird.

---

### Post by smileypaul on 2008-03-07
I have a 3TB Raid5 partition setup using ReiserFS..

no issues here?

---

### Post by lespaul_rentals on 2008-03-07
Is it possible that the RAID adapter isn't supported?

---

### Post by Yfrwlf on 2008-03-07
> **smileypaul said:**
> I have a 3TB Raid5 partition setup using ReiserFS..

no issues here?

Thanks for commenting. >.<

Looks like I'm just a one-off then, sorry.  I'm very glad to see Ubuntu Server works normally with >2TB machines and installs fine.

Now to find out why when **I** try to do an install, I wind up with a ~50 GB partition on the 2.25 TB array...

---

### Post by Yfrwlf on 2008-03-07
> **lespaul_rentals said:**
> Is it possible that the RAID adapter isn't supported?

I assumed since I could create the partition and copy files to it just fine that it was OK, I mean, apparently that means it is supported **to a degree**, but either the driver is bad or it's not supported properly (obviously) or *something*, yeah, so I'm going to mess around with compiling drivers and see if that does it.  Thanks for the comment. :)

If it weren't for partial support, and a botched troubleshooting Googling, I wouldn't have assumed it was a GPT-supported kernel issue. :P

---

### Post by smileypaul on 2008-03-07
> or have any success in getting their Ubuntu Server working with a disk or array of >2TB?

sorry, i was just answering this remark :)

Best of luck.

If its any help, I'm using a 3ware 9650-8PML card RAID card. Installation went without a hitch, no additional drivers required, it was beautiful.

Best of luck! make sure you post a resolution if you find it!

---

### Post by dean123 on 2008-03-08
> **Yfrwlf said:**
> From what I have heard, Ubuntu Server does not support the GPT disk label type by default, and GPT seems to be one of the few disk labels that can support disks and arrays above the 2 TB limit that apparently the MSDOS label format suffers from.  If this is true, it seems strange, since if Ubuntu wants to strive to be a server OS, it should at some point get ready for supporting such sizes as disks continue to get larger.

Or, it already does, and there is some other problem that I'm having. :)  So here goes...

Using Ubuntu 7.10/Kernel 2.6.22, my RAID is seen fine as 2250 GB, the size it should be.  I use parted to create a GPT disk label and have used both parted and gparted to create partitions and they show up as the right size.  Well, they show up as having 2.05 TB free under a reiserfs partition, and about 2.0 TB free under ext3, and parted shows the size of the partition to be 2250, so I'm assuming the missing space is because of the partition's inode table.

Mounts fine, can copy files to them fine, then after a reboot everything goes to hell.  After mounting again, I can see file names but everything else has a ? and they are all unusable, meaning that the inode table has been corrupted somehow.  I assumed that this was due to the kernel not having proper support for GPT, but perhaps there is another issue.

Anyone have any clue, or have any success in getting their Ubuntu Server working with a disk or array of >2TB? :confused:  I'm hoping that my problem is a one-off and that Ubuntu Server can normally easily support >2TB disks/arrays and I simply have a specific problem with my hardware or drivers.  I'd prefer not to have to use CentOS or whatnot instead because I love apt-get too much, and yum just doesn't cut it, and even though one package shouldn't make a difference I don't know if it's possible to use apt-get on an RPM-based distro, which sucks, so I'm left really wishing I could get this working.  Perhaps I'll try Debian instead, or try to recompile the kernel, but I just am amazed this would be a problem for Ubuntu Server.

Also, I'm assuming the Ubuntu Server stock kernel has been compiled with CONFIG_LBD support enabled that is supposed to make the kernel support >2TB sizes, but that's not necessarily the same thing as GPT support of course.


The "parted" command you used is probably old or buggy. Check if Ubuntu has a newer version of parted. 
I am using parted v1.8.x and it worked fine for large arrays. 

Good luck.

---

### Post by Yfrwlf on 2008-03-11
> **dean123 said:**
> The "parted" command you used is probably old or buggy. Check if Ubuntu has a newer version of parted. 
I am using parted v1.8.x and it worked fine for large arrays. 

Good luck.

Thanks all, I have resolved this issue after hearing Dean's response and finally confirming this as the cause.

STUPID PARTED 1.7.X!!!!!!!  >.<

If anyone else ever experiences being able to mount a drive, raid array, or whatever just fine after partitioning with Parted 1.7.x and then reboot to find it all screwed up, go download a new Parted version or a bootable Parted Magic CD from [here]("http://partedmagic.com/wiki/PartedMagic.php").

The Ubuntu installer may not have ever had this problem, but while installing to my RAID I was forced to use Parted since the auto-installer did have the problem of only recognizing a small part of the array, strangely it only partitioned the part above the 2 TB mark it seems, which I would have thought it would partition **up to** 2 TB and then stop.  Another Linux distro we tried had worked because it did not use the same version of Parted that was bad.  (I think some of the 1.7.x series may work OK, but just to be safe I recommend 1.8.x).

Also for my Compaq Proliant 8000 server I had to do the following things:

1.  Add the kernel parameters "noacpi i8042.noaux i8042.nomux" to boot it.

2.  Install from Feisty and do an upgrade, because currently Hardy will not recognize the CDROM drive, even after putting in the "load_all_ide" or something similar (can't remember exactly) boot argument.  I hope they fix this in the final, I don't see why loading additional drivers is a bad thing for improved compatibility aside from making the install take sliiiightly longer.

(rant) P.S. Damnit Linux needs to be binary compatible so everyone can easily install 3rd party programs without being **forced** to go through compilation hell and other crap!  We couldn't even install the stupid RAID drivers (even though it turns out we didn't need them) because the included packages on the CD were distro-specific, and the source had horrible instructions for compilation and we ran into lots of dependency hell.  Linux will NOT become the desktop standard unless it resolves this issue.  Having the freedom to see source code is great, but don't force everyone and their mom to compile it, come up with a solid Linux package standard that will work on any distro that supports that package format.  Otherwise, that's not freedom, it's bondage and something most users by far would rather not have to deal with.  The stigma that Linux is free if your time has no value is something that should be a thing of the past.  Computers should compute for you by default unless you **want** to tinker.  (/rant) :)

---

### Post by wquiles on 2008-05-17
Hi there - I am having the same problem as you did!!!

Details here of my 3.2TB partition that works until I reboot, then all goes to h&*$:

[http://ubuntuforums.org/showthread.php?t=794690]("http://ubuntuforums.org/showthread.php?t=794690")


I will go ahead and try the "Parted Magic 2.2" CD to create the partition.  I will report later if this worked for me or not :confused:

Will

---

### Post by wquiles on 2008-05-17
OK, problem solved.  The problem was the "old" parted 1.7, which is buggy!

In this link you can find how to get the latest parted-1.8.8 (note in the comments section by RoundSparrow that you might need to manually copy a lib):
[http://blog.interrupt3h.com/?p=27]("http://blog.interrupt3h.com/?p=27")

Will

---

