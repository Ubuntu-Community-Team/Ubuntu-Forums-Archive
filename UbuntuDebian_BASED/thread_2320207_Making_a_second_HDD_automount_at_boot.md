---
title: "Making a second HDD automount at boot"
date: 2016-04-11
forum: Ubuntu/Debian BASED
---

### Post by frogotronic on 2016-04-11
Hello,

   I have a 1 TB HDD where my system is, and the data.  This is a machine running Bio-Linux 8 (Ubuntu 14.04 LTS), and has about 15 user/logins.  I would like to make a second 1 TB HDD available as an automount at/on boot.  Would the best approach be editing FSTAB?

Thanks,
Andor

---

### Post by howefield on 2016-04-11
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by frogotronic on 2016-04-11
Why would you move this?  It's Ubuntu 14.04, not a derivative.

---

### Post by QIII on 2016-04-11
Bio-Linux is *based* on Ubuntu, but it is an independent distribution.  It is not a recognized member of the Ubuntu flavors.  Hence "Ubuntu/Debian BASED".

And yes, I believe modifying fstab would be the best course of action.

---

### Post by Dennis N on 2016-04-12
> **cement_head said:**
> Hello, I have a 1 TB HDD where my system is, and the data.  This is a machine running Bio-Linux 8 (Ubuntu 14.04 LTS), and has about 15 user/logins.  I would like to make a second 1 TB HDD available as an automount at/on boot.  Would the best approach be editing FSTAB?


If you use an entry in fstab to mount the 2nd drive, then it can be mounted at start up regardless of which user logs in.

To mount my data partition on my 2nd hard drive, I use this line in fstab:

[FONT=Courier New]UUID=d97e2feb-1bf6-429b-bba5-943264ec1474 /mnt/data ext4 defaults 0 2[/FONT] 

Access to the mounted file system depends on the owner and permissions of folders and files - everyone by default has a basic level of access to folders and files given to 'other' users.

---

