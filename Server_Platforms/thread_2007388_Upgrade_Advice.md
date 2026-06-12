---
title: "Upgrade Advice"
date: 2012-06-20
forum: Server Platforms
---

### Post by brighty22 on 2012-06-20
About a year ago, I built my first machine using Ubuntu Server 11.04. I made 2 rookie mistakes - not using an LTS release, and secondly putting said OS on the same mdadm RAID5 array as all of the data.

Now I've got a problem where I have a 4TB array containing a soon-to-be EoL OS, with no easy way of doing a clean install (I've heard one should never upgrade a server - only do a clean install). In order to do this, I'd have to temporarily move the 1.8TB of data on it somewhere else - but the sum of all computers in my house doesn't add up to 1.8TB.

The best case scenario would be to create a separate partition within the array for just the data. From what I've read, this would allow the clean OS installs while keeping the data partition safe. The problem is that I'd be mad to do this without backing up the data first, but to do that I'd have to buy another hard drive, which would defeat the purpose - see below.

I think the easiest way to get the server using a clean install of 12.04 LTS might be to buy a small HDD just for it, then somehow get it to recognise the existing RAID5 array. I could then delete 11.04 of the array, and be left with a server where the OS and data are separated. If I were to put 12.04 on a new drive, could it recognise and manipulate an existing RAID5 array?

Any thoughts are much appreciated!

George

---

### Post by arrrghhh on 2012-06-20
It seems the array is managed by MDAM, yes?

I would think then yes, the system could see the RAID5 array if you install 12.04 on a separate hdd.

Always a good idea to have separate physical disks for install and data anyways ;).

---

### Post by brighty22 on 2012-06-20
> **arrrghhh said:**
> Always a good idea to have separate physical disks for install and data anyways ;).

As I've learnt... ](*,)

---

### Post by rubylaser on 2012-06-20
> **brighty22 said:**
> About a year ago, I built my first machine using Ubuntu Server 11.04. I made 2 rookie mistakes - not using an LTS release, and secondly putting said OS on the same mdadm RAID5 array as all of the data.

Now I've got a problem where I have a 4TB array containing a soon-to-be EoL OS, with no easy way of doing a clean install (I've heard one should never upgrade a server - only do a clean install). In order to do this, I'd have to temporarily move the 1.8TB of data on it somewhere else - but the sum of all computers in my house doesn't add up to 1.8TB.

The best case scenario would be to create a separate partition within the array for just the data. From what I've read, this would allow the clean OS installs while keeping the data partition safe. The problem is that I'd be mad to do this without backing up the data first, but to do that I'd have to buy another hard drive, which would defeat the purpose - see below.

I think the easiest way to get the server using a clean install of 12.04 LTS might be to buy a small HDD just for it, then somehow get it to recognise the existing RAID5 array. I could then delete 11.04 of the array, and be left with a server where the OS and data are separated. If I were to put 12.04 on a new drive, could it recognise and manipulate an existing RAID5 array?

Any thoughts are much appreciated!

George
It is not possible to install the OS on an mdadm RAID5, so I would bet your OS is installed on a separate RAID1 mdadm array on different partitions on the same disks.  This would be a good thing and would mean that you could do a fresh install and not impact your RAID5 array.  Can you provide the output of these to verify if what I'm saying is the case?
```
cat /proc/mdstat
```
```
mdadm --detail --scan
```
```
cat /etc/fstab
```

---

### Post by brighty22 on 2012-06-20
Indeed you're right. I'd overlooked it - apologies. /boot is RAID1; swap and the root partition are both RAID5.

```
george@bright2a:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [ra                                                                          id10]
md0 : active raid1 sdc1[2] sdd1[3] sdb1[1] sda1[0]
      96244 blocks super 1.2 [4/4] [UUUU]

md2 : active raid5 sdc3[2] sdd3[3] sdb3[1] sda3[0]
      4394236416 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

md1 : active raid5 sdd2[3] sdc2[2] sda2[0] sdb2[1]
      877056 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>
```

```
george@bright2a:~$ sudo mdadm --detail --scan
ARRAY /dev/md/1 metadata=1.2 name=bright2a:1 UUID=57fe77c5:2baef303:dce5c587:e4aaf449
ARRAY /dev/md/2 metadata=1.2 name=bright2a:2 UUID=b1c8c0be:56670ac0:536b2570:ba1fc479
ARRAY /dev/md/0 metadata=1.2 name=bright2a:0 UUID=0b8f0bf5:c4171cd6:bcada1df:cca5782c
```

```
george@bright2a:~$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md2 during installation
UUID=82723d50-a913-4f18-bbf4-1d05bf4f36df /               ext4    errors=remount-ro,acl 0       1
# /boot was on /dev/md0 during installation
UUID=4f0d4e2d-266d-4642-9f83-e62a7836f12b /boot           ext4    defaults        0       2
# swap was on /dev/md1 during installation
UUID=956882a7-31fe-4367-ac70-72f4df0b467f none            swap    sw              0       0
```

---

### Post by rubylaser on 2012-06-20
You should be able to use the alternate install disk for 12.04 and install on what's currently being used as your swap and / partitions. But, I would seriously consider buying at least a 2TB external disk to backup your data before you did anything.  The benefit would be that you could continue to use it for a backup going forward.

---

