---
title: "Copy from Ext2 drive to FAT drive w/ Ubuntu?"
date: 2006-06-02
forum: The Cafe
---

### Post by Super King on 2006-06-02
Here's the situation:

I have an old hard drive with [OpenLinux]("http://www.theosfiles.com/os_linux/ospg_Linux_Caldera.htm") on it. It was used in a machine at a hotel, with some sort of expensive hotel-type software on it. I need to somehow get this software off the drive and copy it to another one. As you can see from the above link this Linux distro is oooold :cool: It says it supports Ext2 and read/write FAT file systems, so I'm gonna assume this drive is Ext2 formatted to begin with. My basic plan to get the data pff the drive is to:

-Shove the OpenLinux hard drive as well as a blank FAT-formatted drive into my main machine which runs WinXP and Dapper.

-Mount the two drives in Ubuntu (they'll show up right? I'm pretty sure Ext2 and FAT are supported in Ubuntu)

-Copy from the Ext2 drive to the FAT drive.


Is there anything I'm overlooking here? Any suggestions/thoughts?

---

### Post by Virogenesis on 2006-06-02
you could also use windows by using [http://www.fs-driver.org/](http://www.fs-driver.org/) it allows read/write access to ext2 drives.

---

### Post by aysiu on 2006-06-02
Sounds good to me.

You'd be better off with a Knoppix live CD, though, as it will automatically mount partitions of both types.

---

