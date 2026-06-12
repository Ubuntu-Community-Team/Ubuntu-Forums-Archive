---
title: "hide partitions"
date: 2020-10-17
forum: Ubuntu/Debian BASED
---

### Post by Disabled20241022 on 2020-10-17
When i insert my external harddrive which basicly is just a backup harddrive i get to see 5 different partitions on it but i want to hide 4 of them but i do not know how to do it.

I'm not sure if i will run into problems so let me explain what the other partitions are used for.
One is EFI for grub, i use it to make the entire disk bootable.
One is for files, i go into my bootable partition and run a backup program and i backup drives to this partition.
the 2 other partitions are for different linux bootables/live installs. (not actuall installed)
And then the main partition (the firth) is the one that must remain visible always.

---

### Post by Disabled20241022 on 2020-10-29
Is this possible?

---

### Post by yapidumoac on 2020-10-29
Use Gparted, select partition and 'manage flags' ..

---

### Post by yetimon_64 on 2020-10-29
> **ayudha said:**
> Is this possible?
Yes. See next quote...
> **yapidumoac said:**
> Use Gparted, select partition and 'manage flags' ..
I specifically use the "diag" setting from "manage flags" to hide partitions, though I have never tried it on an EFI boot partition.

I have never set a diag flag on my EFI partition because if the EFI partition is in use by the system that is booted it doesn't show up in the file manager here on Ubuntu Mate 18.04; I've found setting it unnecessary. I don't therefore know if setting it on the EFI partition is "safe" or not for your usage (I suspect it is safe but have not tested such).

I have found setting the "diag" flag very useful over the years in de-cluttering  the interface of excessive partitions with multi-boot set ups eg. ...
[ATTACH=CONFIG]287252[/ATTACH]
You may notice the 4 unused spare partitions, if they weren't tagged with the "diag" flag they would show up in my file manager window.

The storage partition in partition sda12 does show up in the file manager even with the diag flag as it is mounted in my user folder in /media from /etc/fstab. The diag flag in this case stops it showing up in file managers from external drive installations that I sometimes boot from that aren't meant to access it.

Regards, yeti.

---

### Post by Disabled20241022 on 2020-11-08
Thanks the diag worked.

How do i stop my bootable ssd drive from making these new partitions that are writable? (probably when i go into a live linux.. they contain logs)

and how do i change the LABEL and the NAME from my ESP on my external SSD drive using the terminal?

---

### Post by Disabled20241022 on 2020-11-24
Help please......

---

### Post by Disabled20241022 on 2021-01-24
anyone?

When i boot up ubuntu iso image (setup) from my external harddisk (bootable) it automaticly creates this new partition named rewritable that has logs on them. how do i disable this?

---

