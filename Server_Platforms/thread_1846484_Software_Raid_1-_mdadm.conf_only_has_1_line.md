---
title: "Software Raid 1- mdadm.conf only has 1 line"
date: 2011-09-19
forum: Server Platforms
---

### Post by Smallstack on 2011-09-19
Hi,
 
I have Ubuntu Server 11.04 and its been up for some time.
 
After upgrading packages using the following commands:
```
sudo apt-get update
sudo apt-get upgrade
```
 
The following output was produced:
```
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
Warning: Not updating LILO; /etc/lilo.conf not found

```
 
My file system is setup like this currently
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/md4               31G  2.4G   27G   9% /
none                  3.9G  240K  3.9G   1% /dev
none                  4.0G     0  4.0G   0% /dev/shm
none                  4.0G  152K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
/dev/md1              251M   34M  204M  15% /boot
/dev/md2              2.0G  180M  1.8G  10% /home
/dev/md3              645G  382G  232G  63% /appl

```
 
I did a bit of digging and found my mdadm.conf only had the following line:
cat /etc/mdadm/mdadm.conf
```
 
DEVICES /dev/[hs]d*

```
 
It does not have any array lines, so I ran sudo mdadm --detail --scan
```

ARRAY /dev/md0 metadata=0.90 UUID=b0d7c72f:7f375886:776c2c25:004bd7b2
ARRAY /dev/md1 metadata=0.90 UUID=0a825908:1e676346:776c2c25:004bd7b2
ARRAY /dev/md2 metadata=0.90 UUID=e9e93bcd:1c2e7296:776c2c25:004bd7b2
ARRAY /dev/md4 metadata=0.90 UUID=6be8485e:ccfa5751:776c2c25:004bd7b2
ARRAY /dev/md3 metadata=0.90 UUID=13523099:c9aa2516:776c2c25:004bd7b2
```
 
Is it sufficient for me just to put the output from sudo mdadm --detail --scan into mdadm.conf?
 
Since my boot partition is raided I do not want to restart the server.
 
Edit:
Adding output of sudo fdisk -l
```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000704b
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2089    16777939+  fd  Linux raid autodetect
/dev/sda2            2090        2122      265072+  fd  Linux raid autodetect
/dev/sda3            2123        2384     2104515   fd  Linux raid autodetect
/dev/sda4            2385       91201   713422552+  85  Linux extended
/dev/sda5            2385       87237   681581722   fd  Linux raid autodetect
/dev/sda6           87238       91201    31840829+  fd  Linux raid autodetect
 
Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00028cff
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2089    16777939+  fd  Linux raid autodetect
/dev/sdb2            2090        2122      265072+  fd  Linux raid autodetect
/dev/sdb3            2123        2384     2104515   fd  Linux raid autodetect
/dev/sdb4            2385       91201   713422552+  85  Linux extended
/dev/sdb5            2385       87237   681581722   fd  Linux raid autodetect
/dev/sdb6           87238       91201    31840829+  fd  Linux raid autodetect
 
Disk /dev/md0: 17.2 GB, 17180524544 bytes
2 heads, 4 sectors/track, 4194464 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 
Disk /dev/md0 doesn't contain a valid partition table
 
Disk /dev/md1: 271 MB, 271319040 bytes
2 heads, 4 sectors/track, 66240 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 
Disk /dev/md1 doesn't contain a valid partition table
 
Disk /dev/md2: 2154 MB, 2154954752 bytes
2 heads, 4 sectors/track, 526112 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 
Disk /dev/md2 doesn't contain a valid partition table
 
Disk /dev/md4: 32.6 GB, 32604880896 bytes
2 heads, 4 sectors/track, 7960176 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 
Disk /dev/md4 doesn't contain a valid partition table
 
Disk /dev/md3: 697.9 GB, 697939591168 bytes
2 heads, 4 sectors/track, 170395408 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 
Disk /dev/md3 doesn't contain a valid partition table

```

---

### Post by YesWeCan on 2011-09-19
Your mdadm.conf should look like this
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 metadata=0.90 UUID=b0d7c72f:7f375886:776c2c25:004bd7b2
ARRAY /dev/md1 metadata=0.90 UUID=0a825908:1e676346:776c2c25:004bd7b2
ARRAY /dev/md2 metadata=0.90 UUID=e9e93bcd:1c2e7296:776c2c25:004bd7b2
ARRAY /dev/md4 metadata=0.90 UUID=6be8485e:ccfa5751:776c2c25:004bd7b2
ARRAY /dev/md3 metadata=0.90 UUID=13523099:c9aa2516:776c2c25:004bd7b2

```
And after you change it, run
[COLOR="DarkSlateBlue"]sudo update-initramfs -u[/COLOR]
If there are no errors you are good to go.

---

### Post by Smallstack on 2011-09-19
Thank you very much for that!
 
Can I ignore the following warning due to the fact I'm using GRUB not LILO?
sudo update-initramfs -u
```
update-initramfs: Generating /boot/initrd.img-2.6.38-8-server
Warning: Not updating LILO; /etc/lilo.conf not found
```

---

### Post by YesWeCan on 2011-09-19
You must have installed lilo at some point. You can ignore it or remove lilo.
sudo apt-get remove lilo
Having lilo is useful if you ever want to restore a standard MBR boot code.


Don't forget to mark this solved in [COLOR="Red"]Thread Tools[/COLOR] when you are ready.

---

