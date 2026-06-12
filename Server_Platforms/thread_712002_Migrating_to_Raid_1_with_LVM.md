---
title: "Migrating to Raid 1 with LVM"
date: 2008-03-01
forum: Server Platforms
---

### Post by KTamas-esp on 2008-03-01
Hi

So... yeah... I do realize that there are a couple guides out there on the internet on how to migrate an existing system to RAID1 using mdadm. However, I couldn't find any that includes LVM -- Which, I guess, makes things a wee bit harder... My partition table is sth like this:

/dev/sdc1: /boot
/dev/sdc2: Extended
/dev/sdc5: /

(yeah right now even though I'm using LVM I only have one partition)
I'm using Gutsy Server x64.

Help please..
Thanks,
KTamas

---

### Post by Sam Lars on 2008-03-01
Here's what looks to be a nice guide to setting up RAID...
[http://ubuntuforums.org/showpost.php?p=4391983&postcount=2](http://ubuntuforums.org/showpost.php?p=4391983&postcount=2)

---

### Post by KTamas-esp on 2008-03-02
> **Sam Lars said:**
> Here's what looks to be a nice guide to setting up RAID...
[http://ubuntuforums.org/showpost.php?p=4391983&postcount=2](http://ubuntuforums.org/showpost.php?p=4391983&postcount=2)
Thanks, however I already know these steps... I still dont know that where does LVM comes into the picture.

---

### Post by koenn on 2008-03-02
raid 1 is a mirrored set, right ? 
that requires 2 disks (or possibly 2 volumes)
you only mention 1 disk  - /dev/sdc, so what exactly is it you want to do ? where do you want to mirror to ? what do your LVM volumes consist of physically ?

---

### Post by Sam Lars on 2008-03-04
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=raid&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=raid&titlesearch=Titles)
All the help sections on RAID... a few about it with LVM.

---

