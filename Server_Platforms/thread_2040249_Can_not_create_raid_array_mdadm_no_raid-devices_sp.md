---
title: "Can not create raid array: mdadm: no raid-devices specified."
date: 2012-08-10
forum: Server Platforms
---

### Post by emil.s on 2012-08-10
Hello!

I'm trying to setup a software raid on my server, but I fail already at the first step:
```
root@sandnabba:/root# mdadm -C /dev/md0 -c512 -l5 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: no raid-devices specified.
```

What am I doing wrong!? :confused:

---

### Post by darkod on 2012-08-10
Are you sure -C is equivalent to the --create?

Also, I think you need space after the -c and -l options, the value shouldn't be together with the command, or it should have = between.

Look at the man pages for mdadm and double check the spelling.

---

### Post by emil.s on 2012-08-10
> **darkod said:**
> Are you sure -C is equivalent to the --create?

Also, I think you need space after the -c and -l options, the value shouldn't be together with the command, or it should have = between.

Look at the man pages for mdadm and double check the spelling.

Thanks for the answer!

But it didn't help. :(
Feels like I have been trying everything, without any success... 

```
root@sandnabba:/root# mdadm --create /dev/md0 --level 5 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: no raid-devices specified.

```

---

### Post by darkod on 2012-08-10
Are the partitions sdc1, sdd1 and sde1 of raid type? You need to create them as partitions first and set them up the physical raid devices. Is that done?

Also, have you tried like:
```
mdadm --create /dev/md0 --level=5 /dev/sdc1 /dev/sdd1 /dev/sde1
```

EDIT PS. It seems the command needs to be modified as:
```
mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdc1 /dev/sdd1 /dev/sde1
```

---

### Post by mikaelcrocker on 2012-08-10
Yes you will need --raid-devices.  Also look into chuck size and metadata for further increase in performance.

Also if you're using this as a root partition, be sure to create a /boot sector and point the lilo conf at it too.

This guidline is very well written 
[http://erikugel.wordpress.com/2011/04/14/the-quest-for-the-fastest-linux-filesystem/](http://erikugel.wordpress.com/2011/04/14/the-quest-for-the-fastest-linux-filesystem/)

---

### Post by rubylaser on 2012-08-10
> **mikaelcrocker said:**
> Yes you will need --raid-devices.  Also look into chuck size and metadata for further increase in performance.

Also if you're using this as a root partition, be sure to create a /boot sector and point the lilo conf at it too.

This guidline is very well written 
[http://erikugel.wordpress.com/2011/04/14/the-quest-for-the-fastest-linux-filesystem/](http://erikugel.wordpress.com/2011/04/14/the-quest-for-the-fastest-linux-filesystem/)

That guide is nice, but doesn't cover partitioning for advanced format drives (or drives over 2TB). Also, I've had nothing but problems with XFS at work and home with large datasets, so I use ext4 for everything now (much easier now that the tools support filesystems > 16TB).  My mdadm guide covers both of these aspects.

[http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm")

---

### Post by emil.s on 2012-08-10
> **darkod said:**
> ```
--raid-devices=3
```

And there we have the missing magical words! :)

I have a separate disk for / and /boot, these 3 disks will only work as file storage (XFS on top of cryptsetup/dmcrypt on GPT table).
It's for mostly big files, but there is a few smaller ones, so I think the default chunk at 512kb will be fine. 

Actually, I don't care so much about performance. The machine is mostly working as a NAS and the disks will easily max out the Gbit/s ethernet without RAID anyways.
So this is mostly just for optimizing the storage efficiency.

Thank you very much!

---

### Post by rubylaser on 2012-08-10
Please make sure that you have you /etc/mdadm/mdadm.conf setup so your array assembles correctly after a reboot. Good luck and happy fileserving :)

---

