---
title: "Multiple drives in Server 6.06"
date: 2006-12-27
forum: Server Platforms
---

### Post by stormchas3r on 2006-12-27
I have a simple question regarding Ubuntu Server 6.06.  I want to install Ubuntu Server on a 40Gb HDD, and have 2 other 120GB HDD with it.  How can I make ubuntu see the other drives as one drive, ie. 40+120+120 = 1 280GB HDD?  

I want to run VMWare server on here and have the max space to use.  

Any thoughts are greatly appreciated.

---

### Post by MrHorus on 2006-12-27
> **stormchas3r said:**
> I have a simple question regarding Ubuntu Server 6.06.  I want to install Ubuntu Server on a 40Gb HDD, and have 2 other 120GB HDD with it.  How can I make ubuntu see the other drives as one drive, ie. 40+120+120 = 1 280GB HDD?  

I want to run VMWare server on here and have the max space to use.  

Any thoughts are greatly appreciated.

Combine it into a RAID array and it can be seen as one volume.

It's not something i've done personally but others here should be able to help you if you don't want to Google for a guide.

---

### Post by Brazen on 2006-12-27
> **stormchas3r said:**
> I have a simple question regarding Ubuntu Server 6.06.  I want to install Ubuntu Server on a 40Gb HDD, and have 2 other 120GB HDD with it.  How can I make ubuntu see the other drives as one drive, ie. 40+120+120 = 1 280GB HDD?  

I want to run VMWare server on here and have the max space to use.  

Any thoughts are greatly appreciated.

You can use LVM.  During the install process, there is an option to partition the harddrives automatically, or partition the harddrives automatically with LVM.  I believe the automatic partitioning will create one big LVM drive.

Personally though, depending on how important your virtual machines are, I would install Ubuntu on the 40 GB drive, and then after installation use Webmin to create a Raid1 drive from the 2 120GB drives.  Then put your virtual machines on the Raid1 drive.  If all you want it a bunch of space though, the automatic with LVM will work for you.

---

### Post by stormchas3r on 2006-12-27
Great, I appreciate the help guys.

---

