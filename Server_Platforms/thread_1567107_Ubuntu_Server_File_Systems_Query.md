---
title: "Ubuntu Server File Systems Query"
date: 2010-09-03
forum: Server Platforms
---

### Post by kris90mnu on 2010-09-03
Hey everyone,

As a project i'm interested in setting up a home server using Ubuntu 10.04 server edition. I plan to install the OS to a 20gb hard drive and use a 500gb hard drive for personal data.

Right now i only plan to use it to share files with Windows computers on my network using Samba and stream media files to my Playstion 3, although i may add more functionality in the future.

Could anyone offer any advice on which file system i should use for the 500gb data drive. Will Windows recognize Linux file systems or should i use NTFS (I'm not sure how well Linux supports NTFS). I haven't found anything that can help me and i want to be more clear on this issue before i proceed.

Thanks in advance.

---

### Post by gobbledigook on 2010-09-03
ntfs is supported out of the box, prob an easier option if you are gonna be hot-swapping the disk between windows and linux boxes as windows doesn't natively support ext3/4 :)

i'd see [this how-to]("https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting") and the links there for fstab and mountingwindowspartitions... ubuntu server doesn't automount so you will have to add a line in /etc/fstab to mount the drive on boot.

---

### Post by kris90mnu on 2010-09-04
Thanks for the info and links - i may go with NTFS for the sake of convenience.

Is it possible to defragment the drive from Windows or can i do it Ubuntu?

---

### Post by koenn on 2010-09-04
using ntfs is completely unnecessary - you're sharing though Samba, so only samba needs access to that disk; the windows clients will talk to samba, and don't read the disk directly. So any linux filesystem will do just fine.

also, you might want/need to set filesystem security on your shares.
I don't know how well ntfs deals with linux-style file permissions.

---

### Post by FuturePilot on 2010-09-04
Yes, as said above, you don't need to use NTFS for a Samba share. I have a Samba share on an Ext3 disk and it works just fine.

> **koenn said:**
> 
I don't know how well ntfs deals with linux-style file permissions.

Horribly.

---

