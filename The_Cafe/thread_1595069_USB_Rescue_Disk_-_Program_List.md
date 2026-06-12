---
title: "USB Rescue Disk - Program List"
date: 2010-10-12
forum: The Cafe
---

### Post by ehlodex on 2010-10-12
I'm a Microsoft Technician and Linux is **by far** the **best** utility for troubleshooting and repairing Windows-based systems. That being said, I am in the process of building a new USB "Rescue"  Disk using Ubuntu Desktop as the base. I realize that there are a  couple options that would work better for a bootable USB drive, and if  you're using a smaller drive, you may want to consider Puppy Linux ([http://www.puppylinux.org]("http://www.puppylinux.org/")) or Damn Small Linux ([http://www.damnsmalllinux.org]("http://www.damnsmalllinux.org/")).

I chose Ubuntu Desktop because of the stable environment and my  familiarity with the operating system. Please note that this is not  simply a live CD copied onto a USB drive, but rather a fully installed  OS. I mention this because I had confusion early on. At any rate, here  are my current applications for fixing everything Windows. I'm looking  for more suggestions and a little discussion on this topic overall.  Thanks!

chntpw
gparted
ntfsprogs
avira antivir

---

### Post by ehlodex on 2010-10-13
smartmontools

---

### Post by Spice Weasel on 2010-10-13
I suggest you take a look at [http://www.sysresccd.org](http://www.sysresccd.org). Have fun! :D

---

### Post by capink on 2010-10-14
Make sure to include the package called ntfsprogs. It includes a utility called ntfsclone that will make you able to make and restore ntfs partition images.

gparted is good too.

partimage is another cloning program. But it ntfs support is not reliable.

---

### Post by ehlodex on 2010-10-19
> **Spice Weasel said:**
> I suggest you take a look at [http://www.sysresccd.org](http://www.sysresccd.org). Have fun! :D

Pretty good pre-built rescue utility. Looks to be a great alternative to building your own if you need something in a hurry. Good utility list too! [www.sysresccd.org](www.sysresccd.org) is a great tool.

Their program list appears to be as follows:

sfdisk (backup/restore partition tables)
partimage (backup partition contents)
archivers (gzip, 7zip, etc)
clamav (antivirus)
gparted

Thanks to everyone who's gotten involved so far, this is becoming a great little project.

---

