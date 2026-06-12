---
title: "Recover Striped Array"
date: 2008-08-13
forum: Server Platforms
---

### Post by aaron_summer on 2008-08-13
Good Day and thanks for reading!

I recently made a huge mistake when using VirtualBox and rebooted my server with a self booting ghost image of XP! I lost all my data before I realized what happened.

I was running Ubuntu 8.04 Server and created a md0 (using mdadm) of two external USB harddrives as a striped array.

Is there any documentation on how to recover the raid?

Any help is greatly appreciated!

---

### Post by dacorr on 2008-08-13
if memory serves the stripped array details are stored the primary drive.

in this case if i read it right the Ubuntu server on VirtualBox what happeed to it virtua hard drive when you booted te XP image?

was te XP image a seperate drive or hhas it over written the Ubuntu server Virtual Drive?

---

### Post by psusi on 2008-08-15
Assuming nothing got corrupted on the disks, you can use the mdadm command scan the array, store the detected configuration, and activate the array.  I'm not sure exactly how off the top of my head, but the man page should have all the info you need.

---

### Post by fjgaude on 2008-08-16
Yes, it's easy if you do the right things... re-install Ubuntu, install **mdadm**, then:

```
sudo --assemble --scan
```

A new **mdadm.conf** file will be auto creating and you are ready to mount your array, add a line in **fstab** and you are good to go.

The important thing is to make sure you don't already have an old /etc/mdadm/mdadm.conf or a mdadm file before you do the assemble. If you do, delete them.

---

