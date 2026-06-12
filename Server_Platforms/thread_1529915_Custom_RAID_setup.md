---
title: "Custom RAID setup"
date: 2010-07-12
forum: Server Platforms
---

### Post by LepeKaname on 2010-07-12
I'm setting up a web server but I have no experience with RAID. I would like to try this configuration if possible:

2 x HDD 500GB RAID1
1 x HDD 20GB (logs and tmp)

The old 20GB drive I would like to use it to store logs and temporally files (mounted in /var/log and /tmp respectively). With this I'm trying to reduce some disk usage in the RAID drives. In my idea, it would be better to write the access/error logs of the web server in a separated drive to the one serving the files which may increase speed... sounds crazy?

What do you think?

One problem is that during the installation, If I set the RAID automatically it will try to use my 20GB HDD as well in the RAID... Does it will work if I set the RAID first (removing the 20GB HDD) and then set the mount points in it after the installation? 

Any suggestion?

Thank you

---

### Post by cj.surrusco on 2010-07-12
Well, first you need to start off with the Alternate install CD. When you get to the partitioning part of the installation, (Assuming the RAID 1 is for /) create a partition in each of the larger drives that fills the entire drive. Then choose to create a RAID device, and choose to add only the two partitions that you just made.

Once that is done, set the RAID device to mount as root, and then you can partition the 20GB drive as you wish and set the mount points for each partition.

---

### Post by LepeKaname on 2010-07-12
So it has to be with the "Alternate install CD"? can't be done with the normal server CD?

---

### Post by cj.surrusco on 2010-07-12
> **LepeKaname said:**
> So it has to be with the "Alternate install CD"? can't be done with the normal server CD?

Excuse my ignorance. I had the idea that you were installing a desktop. You *can* use the server CD to install software RAID.

---

### Post by LepeKaname on 2010-07-12
Ok I found it... thank you!
For those interested, this is a way to go:
[https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html)

---

