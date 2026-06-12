---
title: "RAID Questions"
date: 2006-02-04
forum: Server Platforms
---

### Post by spyke01 on 2006-02-04
i want to get 10 320GB hard drives working in a RAID5 array, does anyone know and cards that i can use that will allow me to do this well in linux? also how hard is it to setup something l;ike this for nix?

---

### Post by spartas on 2006-02-05
I've used a 3ware 9500 series card with breezy.  It has it's own configuration settings, apart from the OS, and after setting up the disks in RAID5, which is what I used, breezy found the RAID without a problem.

---

### Post by spyke01 on 2006-02-06
thanx m8 it looks like a really great product, and its really nice that it comes with all the cables, how long have you had it, and have you experienced any problems with it?

---

### Post by spartas on 2006-02-06
No problems whatsoever.  As I said in the previous post, I'm using RAID5 with the 3ware 9500 series card; I'm using it with 4 74G SATA WD Raptor drives, giving me about 200Gb of space.  I set the RAID up using LVM in case I decide to go with a larger card (more than 4 ports) and more drives.  

I mainly use it to develop applications, with storage space not the main concern.  I only went with the RAID because I wanted the redundancy just in case.  If you look up the specs on the Raptor drives, you'll see they're 10K RPM drives, this is why I chose them.

Here's a look at a few commands on that box:

```

tim@asynjur:~$ uptime
 10:14:27 up 28 days, 20:35,  2 users,  load average: 0.00, 0.00, 0.00

tim@asynjur:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                       33G  1.2G   30G   4% /
tmpfs                1003M     0 1003M   0% /dev/shm
tmpfs                1003M   14M  989M   2% /lib/modules/2.6.12-10-amd64-generic/volatile
/dev/sda1             228M   29M  187M  14% /boot
/dev/mapper/array-home
                      196G   47G  150G  24% /home

```

This is how it shows up using df.  The RAID5 is only on /home.  I'm using a separate disk for /

---

### Post by jimwillsher on 2006-02-14
I'm not using RAID5, just two mirrored SATA drives, but I can vouch for the 3ware kit. The Linux kernel recognises it during the install, so you can have your full setup RAID protected, and it's *rock* solid. Never had ANY issues with it, either on my CentOs install (2 years) or my current Ubuntu Breezy install. Definitely recommended.

Jim

---

