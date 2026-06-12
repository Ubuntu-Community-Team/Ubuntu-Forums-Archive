---
title: "Upgrade and replace disks in a RAID5-array"
date: 2009-01-06
forum: Server Platforms
---

### Post by jonta on 2009-01-06
I am using Ubuntu 8.04 server edition 32-bit and on it running a RAID5 with 5 disks, all on 200GB.
Now the time has come to uppgrade the storage space a bit and since i don't have room for more disks in the server i need to replace them. Can i buy 5 new 1TB disk and replace them one and one? Replace on, sync up the raid, replace anotherone, sync up the raid without loosing data?

---

### Post by Cracauer on 2009-01-06
Assuming you use Linux' md:

I have done that.

In fact I recently expanded a raid-5 that has LVMs on top.

Just drop one disk, replace, add.

Be warned that during this re-sync period you run a higher risk. Obviously a second disk failing will kill your data. But the re-sync is extremely stressful for the disk. At the very least you want to make sure that the disks stay under 40 degrees Celsius in smartctl.

---

### Post by jonta on 2009-01-06
Thanks for the excellent reply! Then i'll just buy me 5 new disks and soon have a 5TB array. And yes i use mdadm.

Am i right that the array will still have the same small size until i replace the last of the 5 disks?

---

### Post by Cracauer on 2009-01-07
> **jonta said:**
> 
Am i right that the array will still have the same small size until i replace the last of the 5 disks?

You could make temporary partitions or arrays out of the extra space.

---

### Post by joeinbend on 2009-01-07
Thought I would chime in on this, I recently wrote up a complete how-to document on this subject, to make it easy for anyone who knows very little about Linux, to build a RAID5 server. The document also covers doing the disk upgrade you describe. To my knowledge, your previous statement is correct: Your RAID size will remain the same until you have upgraded all physical disks. At that point, you can grow the block-volume, then expand the file system on top of it. have a look-see, and if anyone has any critique on this guide, I would appreciate the feedback!

[http://www.bishoptechnology.com/content/pdf/raid.pdf](http://www.bishoptechnology.com/content/pdf/raid.pdf)

---

### Post by jonta on 2009-01-07
Just read the document you wrote. Exactly what i need! :)) Thank you very much! My first step was to check if it could be done, my second one would have been googeling for how it could be done.

---

### Post by joeinbend on 2009-01-07
Thanks Jonta! I wrote this a few weeks ago, when I discovered that it was possible to do this. I tested fully in VM's first, then on a test physical server, and now I am running MDADM as my 'production' NAS, with 4x 1TB drives in RAID5, +1 hot-spare.

The reason I wrote this is I was not able to find a single how-to setup guide like this, start to finish, for MDADM, and its' supporting counterparts. I had to piece this together from a dozen or more documents and forum threads.

---

### Post by fjgaude on 2009-01-07
> **joeinbend said:**
> Thanks Jonta! I wrote this a few weeks ago, when I discovered that it was possible to do this. I tested fully in VM's first, then on a test physical server, and now I am running MDADM as my 'production' NAS, with 4x 1TB drives in RAID5, +1 hot-spare.

The reason I wrote this is I was not able to find a single how-to setup guide like this, start to finish, for MDADM, and its supporting counterparts. I had to piece this together from a dozen or more documents and forum threads.

After looking over your .pdf file for **how-to** for raid5, Joe, it is easy to understand why nothing covering the complete range for **mdadm** useage has shown up yet. One of these days... maybe a book!

---

### Post by joeinbend on 2009-01-07
Ha... I think that was a compliment :)  What I would REALLY like to do is team up with some people (hint hint) who know how to build a scripted installer, so I can make a "Ubuntu RAID Server" distro, so others can just download the .ISO, and install on their hardware, without having to do all the backend work described in the document.

---

### Post by fjgaude on 2009-01-07
> **joeinbend said:**
> Ha... I think that was a compliment :)  What I would REALLY like to do is team up with some people (hint hint) who know how to build a scripted installer, so I can make a "Ubuntu RAID Server" distro, so others can just download the .ISO, and install on their hardware, without having to do all the backend work described in the document.

Well that might be useful but I tell you, from experience with **mdadm**, it is best to know exactly how to do each little task in advance of needing to do it. The area still open is bootable raid1, what to do when a drive has actually failed, knowing which drive it is physcially, etc. Get my drift.

With hardware raid all this is easy, very easy, even a caveman can do it!

What you have done with your write-up is a start to a complete book on how to handle all the bells and whistles of software raid. Thanks for the start!

---

### Post by joeinbend on 2009-01-07
yes I agree with this as well. It took me almost a solid week to learn how to comprehensively work with MDADM, and this is only on the RAID5 level. I havent touched RAID1 for OS drives yet. It would be dangerous to give a "no brains required" distro, which would just be setting people up for failure.

I'm continuing to revise and expand this document. It seems to me that learning how to build your own from command-line, and therefore providing a reference manual as well, will teach people how to work with it, and not be scared of command-line!

I am just about to bring my "Documentation Repository" website online, which houses many similar documents I have created over the years, on various subjects. I'll make sure this thread gets a link to it when it's up and running.

---

### Post by fjgaude on 2009-01-07
Okay, and as you update the raid document please keep us in mind, letting us see your progress.

---

### Post by Cracauer on 2009-01-07
Everybody who sets up a RAID to put important data on needs to simulate and practice dropping and re-adding disks, see what it does when you reboot during a re-sync and all these things. While the array is still empty of course.

That applies no matter what RAID product you use.

---

### Post by windependence on 2009-01-07
...And never EVER use RAID as a substitute for good backups.

-Tim

---

### Post by fjgaude on 2009-01-07
Amen!

---

### Post by joeinbend on 2009-01-07
I agree wholeheartedly! Even though I state that in the documentation, I will stress and stress it again on my next revision! RAID is for High Availability, NOT a replacement for backups!!

---

### Post by fjgaude on 2009-01-08
> **joeinbend said:**
> I agree wholeheartedly! Even though I state that in the documentation, I will stress and stress it again on my next revision! RAID is for High Availability, NOT a replacement for backups!!

Availability and speed! <smile>

---

### Post by joeinbend on 2010-07-13
Hey guys, i know this is a very old thread, but I wanted to update my link to the guide. It is available at:

[www.BishopTechnology.com](www.BishopTechnology.com)  under the Linux section, click on "Linux RAID-5 How-To Guide"

---

