---
title: "64 bit Server 11.10 and MDADM problem"
date: 2012-02-04
forum: Server Platforms
---

### Post by Krupski on 2012-02-04
Hi all,

I tried to upgrade my file server box running 11.04 64 bit server with 5 drives in a array to 11.10 server.

Now, my RAID array is /dev/md0 and composed of 5 drives **with no partitions.** That is, I created the array, formatted /dev/md0 with EXT4 and that's it. Worked fine.

Now MDADM for 11.10 complains that I have a "degraded array" and wants me to fix it or hit ctrl-D to continue (kinda difficult for a headless server box). It complains because it sees no "valid partition table".

If I do ctrl-D out of it and mount the array manually, it works fine. But the system won't boot without complaining first.

I see no reason why I should have to back up terabytes of data and rebuild my array only to add partitions to the drives so MDADM doesn't complain.

Is there any way around this problem? Or do I have to make my 11.04 my final version?

Thanks...

-- Roger

---

### Post by rubylaser on 2012-02-04
What's the output of these commands?

```
cat /proc/mdstat
```
```
cat /etc/mdadm/mdadm.conf
```
```
mdadm --detail /dev/md0
```

There's really no need for a partition on top of an mdadm array, so I'm betting it's not liking your mdadm.conf file.

---

### Post by Krupski on 2012-02-05
> **rubylaser said:**
> What's the output of these commands?

```
cat /proc/mdstat
```
```
cat /etc/mdadm/mdadm.conf
```
```
mdadm --detail /dev/md0
```

There's really no need for a partition on top of an mdadm array, so I'm betting it's not liking your mdadm.conf file.

mdstat:
```
root@storage:/# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdd[3] sdb[1] sdc[2] sde[4] sda[0]
      2930284032 blocks super 1.2 level 6, 512k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>

```

mdadm.conf:
```
cat /etc/mdadm/mdadm.conf
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
MAILADDR [email]krupski@roadrunner.com[/email]

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=311b8a28:5619dd16:d41b3874:59f9a3d7

```

mdadm --detail /dev/md0:
```
root@storage:/# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Dec 23 21:52:01 2011
     Raid Level : raid6
     Array Size : 2930284032 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976761344 (931.51 GiB 1000.20 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Sun Feb  5 17:18:17 2012
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : storage:0  (local to host storage)
           UUID : 311b8a28:5619dd16:d41b3874:59f9a3d7
         Events : 45

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd
       4       8       64        4      active sync   /dev/sde

```


All looks normal to me. Note that this is running on my old 11.04 system. I yanked 11.10 because of the need to hit ctrl-D to boot.

(oh and please nobody yell at me for using the root account... I disabled UAC in Windows 7 too... and the world is still turning).  :)

(p.s.: The boot drive is /dev/sdf - a 40GB SSD card which is not part of the array).

---

### Post by rubylaser on 2012-02-06
This looks correct, but I'm betting that you needed to recreate your /etc/mdadm/mdadm.conf file on 11.10 to get it to startup correct.  Or, you could have run dpkg-reconfigure mdadm, and selected the all option for arrays to startup automatically.

---

### Post by Krupski on 2012-02-07
> **rubylaser said:**
> This looks correct, but I'm betting that you needed to recreate your /etc/mdadm/mdadm.conf file on 11.10 to get it to startup correct.  Or, you could have run dpkg-reconfigure mdadm, and selected the all option for arrays to startup automatically.

Well, what worries me is in the past, when I've upgraded Ubuntu versions, I just did a fresh re-install (to the separate SSD drive which is not part of the RAID array), then installed MDADM and it found my existing array, generated the mdadm.conf file with the proper data and it all just worked.

Now, doing the same thing (moving from 11.04 to 11.10), upon installing MDADM I get the message that the array is "degraded" because "no valid partition table" is found.

Since what USED to always work now suddenly does NOT work, I have to assume that the problem lies elsewhere than my "upgrade technique".

It seems to me intuitively wrong that I now need to change some configuration to make it work when in the past I never had to.

If it had something to do with a fundamental change in the 2.6 -> 3.0 kernel design, then I could accept it.

Is it possible that an array without any partition table was "always wrong but ignored" in the past and now "being enforced as necessary"?

Thanks for all your input so far!

-- Roger

---

### Post by rubylaser on 2012-02-07
You don't need to change your configuration, but you do need to ensure that it exists otherwise mdadm won't know how to assemble the array.  Finally, there's no need for a partition on top of mdadm unless, you're using LVM to create smaller volumes on top of mdadm, but you haven't mentioned that, so that's not the case.

On 11.04 what's the output of these?
```
mount
```
```
fdisk -l
```
```
cat /etc/fstab | grep md0
```

---

### Post by Krupski on 2012-02-07
> **rubylaser said:**
> You don't need to change your configuration, but you do need to ensure that it exists otherwise mdadm won't know how to assemble the array.  Finally, there's no need for a partition on top of mdadm unless, you're using LVM to create smaller volumes on top of mdadm, but you haven't mentioned that, so that's not the case.

On 11.04 what's the output of these?
```
mount
```
```
fdisk -l
```
```
cat /etc/fstab | grep md0
```

mount:
```

root@storage:/# mount
/dev/sdf1 on / type ext4 (rw,noatime,discard,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,noatime,mode=1777)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/md0 on /home/shared type ext4 (rw)

```

fdisk -l:
```

root@storage:/dev/shm# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/sdf: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ab996

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        4866    39081656   83  Linux

Disk /dev/md0: 3000.6 GB, 3000610848768 bytes
2 heads, 4 sectors/track, 732571008 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

cat /etc/fstab | grep md0:
```

/* nothing  (I typed this) */

```

/etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                <mount point>    <type>  <options>                                   <dump>  <fsck>

# proc
proc                            /proc           proc    defaults                                    0       0

# /tmp
tmpfs                           /tmp            tmpfs   defaults,noatime,mode=1777                  0       0

# root
/dev/disk/by-label/linux-boot   /               auto    defaults,noatime,discard,errors=remount-ro  0       1

# shared raid drive
/dev/disk/by-label/linux-raid   /home/shared    auto    defaults                                    0       2

# swap
/home/shared/swapfile           swap            swap    defaults                                    0       0

```


My fstab mounts stuff via volume label which is why the "grep /md0" failed.

Also note from fdisk -l that some drives are 512 byte and some are newer 4096 "advanced format" drives. Since the /dev/md0 device is formatted without a partition table, the drive starts at cylinder 0 which is "optimal" for both 512 and 4096 byte alignments.

Drive /dev/sdf is the 40gb SSD boot drive.

The "discard" option for the root drive activates "[_TRIM_]("http://en.wikipedia.org/wiki/TRIM")" for solid state drives (makes the drive internally zero out unused and relinquished sectors to speed writes).

Again... it all looks good to me. What do you think?

By the way, you said: > but you do need to ensure that it [mdadm config] exists otherwise mdadm won't know how to assemble the array.

If I boot ***11.10*** and manually ctrl-D past the error, then the "/dev/md0" device exists and can be mounted manually and it works. Also in 11.10, a "cat /proc/mdstat" shows no resync activity (i.e. the array is happy). And of course, /etc/mdadm/mdadm.conf DOES exist. :)

-- Roger

---

### Post by rubylaser on 2012-02-07
This looks okay as well.  The error it gives you is that the partition is missing or is it saying the filesystem is not available?

---

### Post by Krupski on 2012-02-07
> **rubylaser said:**
> This looks okay as well.  The error it gives you is that the partition is missing or is it saying the filesystem is not available?

OK, here's what I did step by step and what happened:

(1) Have a working RAID-6 array using MDADM and Ubuntu 11.04

(2) Shutdown the machine, unplugged the HDD power cables leaving only the SSD alive

(3) Booted into 11.10 server **installer** from a USB stick (created with "Startup Disk Creator" and the 11.10 ISO image).

(4) Installed 11.10 to the 40GB SSD (formatted as EXT4).

(5) Shut down and plugged HDD power cables back in

(6) Boot the server, then "apt-get install mdadm"

(7) The install goes fine, "/etc/mdadm/mdadm.conf" is created by the installer. It shows the correct UUID.

(8) Sync, then reboot the server.

(9) The server hangs during the startup, saying "array is degraded" and waits for me to hit ctrl-D to continue booting.

(10) Hit ctrl-D, bootup finishes.

(11) "ls /dev/md0" - it's there.

(12) cat /proc/mdstat - it's there and not doing anything (i.e. it's already sync'ed).

(13) Manually type "mount /dev/md0 /home/shared" - command completes successfully. All the content at /home/shared is there and accessible - no errors.

(14) Edit /etc/fstab to mount the array at boot time (i.e. the fstab you saw a few posts ago).

(15) Reboot. Same thing. It says "degraded array" and will not continue until I hit ctrl-D


Sorry I don't have the *exact* text of the error message as I'm doing it from memory (and the server is back to 11.04 for now).

Hope this shows you something that I'm missing... and thank you again for all your help and patience.

-- Roger

---

### Post by rubylaser on 2012-02-07
Booting degraded (even though it isn't) from a non system array should not stop the booting process. I'll have to setup an array in 11.04 tomorrow in Virtualbox and then migrate to 11.10.  I'll follow the same steps that you did.  I could understanding it stalling the boot process if it tried to mount the array and it wasn't available, but that should give you the "S" option to skip, so it's not that.

I'll try to set a test up and see if I can recreate your problem. Maybe I can figure out what the issue is.

---

### Post by Krupski on 2012-02-10
> **rubylaser said:**
> Booting degraded (even though it isn't) from a non system array should not stop the booting process. I'll have to setup an array in 11.04 tomorrow in Virtualbox and then migrate to 11.10.  I'll follow the same steps that you did.  I could understanding it stalling the boot process if it tried to mount the array and it wasn't available, but that should give you the "S" option to skip, so it's not that.

I'll try to set a test up and see if I can recreate your problem. Maybe I can figure out what the issue is.

I tried it again and this time took pictures of the boot screens (since I couldn't capture the text any other way). Let me know if it would help you to see the text... and please let me know if there are any tests you would like me to perform.

Thanks...

-- Roger

---

### Post by rubylaser on 2012-02-10
Sorry, I forgot to run the test.  I'll try it today.

---

### Post by rubylaser on 2012-02-10
Okay, I just ran the tests and everything works great for me here.  I installed 11.04 on a single OS disk and setup a simple (3) disk RAID5 array and mounted it at /storage.  Here are the steps I followed.

**11.04**

```
root@mdadm-test:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

root@mdadm-test:~# fdisk -l

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000da21b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         784     6290432   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             784        1045     2095105    5  Extended
/dev/sda5             784        1045     2095104   82  Linux swap / Solaris

Disk /dev/sdb: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x92c7d68c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         130     1044193+  fd  Linux raid autodetect

Disk /dev/sdc: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b8bfd17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         130     1044193+  fd  Linux raid autodetect

Disk /dev/sdd: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde26680a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         130     1044193+  fd  Linux raid autodetect
root@mdadm-test:~# apt-get install mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  postfix ssl-cert
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin dovecot-common resolvconf postfix-cdb mail-reader openssl-blacklist
Recommended packages:
  default-mta mail-transport-agent
The following NEW packages will be installed:
  mdadm postfix ssl-cert
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,477 kB of archives.
After this operation, 4,407 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main mdadm i386 3.1.4-1+8efb9d1ubuntu4.1 [298 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ natty/main ssl-cert all 1.0.28 [12.2 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main postfix i386 2.8.5-2~build0.11.04 [1,167 kB]
Fetched 1,477 kB in 8s (178 kB/s)                                                                                                                   
Preconfiguring packages ...
Selecting previously deselected package mdadm.
(Reading database ... 48243 files and directories currently installed.)
Unpacking mdadm (from .../mdadm_3.1.4-1+8efb9d1ubuntu4.1_i386.deb) ...
Selecting previously deselected package ssl-cert.
Unpacking ssl-cert (from .../ssl-cert_1.0.28_all.deb) ...
Selecting previously deselected package postfix.
Unpacking postfix (from .../postfix_2.8.5-2~build0.11.04_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Setting up mdadm (3.1.4-1+8efb9d1ubuntu4.1) ...
Generating mdadm.conf... done.
 Removing any system startup links for /etc/init.d/mdadm-raid ...
update-initramfs: deferring update (trigger activated)
 * Starting MD monitoring service mdadm --monitor
   ...done.
Setting up ssl-cert (1.0.28) ...
Setting up postfix (2.8.5-2~build0.11.04) ...
Adding group `postfix' (GID 113) ...
Done.
Adding system user `postfix' (UID 104) ...
Adding new user `postfix' (UID 104) with group `postfix' ...
Not creating home directory `/var/spool/postfix'.
Creating /etc/postfix/dynamicmaps.cf
Adding tcp map entry to /etc/postfix/dynamicmaps.cf
Adding group `postdrop' (GID 114) ...
Done.
setting myhostname: mdadm-test
setting alias maps
setting alias database
mailname is not a fully qualified domain name.  Not changing /etc/mailname.
setting destinations: mdadm-test, localhost.localdomain, , localhost
setting relayhost: 
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: all
/etc/aliases does not exist, creating it.
WARNING: /etc/aliases exists, but does not have a root alias.

Postfix is now set up with a default configuration.  If you need to make 
changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix
   ...done.
 * Starting Postfix Mail Transport Agent postfix
   ...done.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic-pae
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

root@mdadm-test:~# mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[bcd]1
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: size set to 1043968K
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

root@mdadm-test:~# watch cat /proc/mdstat
 
root@mdadm-test:~# echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
root@mdadm-test:~# echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
root@mdadm-test:~# echo "MAILADDR  youruser@gmail.com" >> /etc/mdadm/mdadm.conf
root@mdadm-test:~# mdadm --detail --scan >> /etc/mdadm/mdadm.conf
root@mdadm-test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Feb 10 13:40:48 2012
     Raid Level : raid5
     Array Size : 2087936 (2039.34 MiB 2138.05 MB)
  Used Dev Size : 1043968 (1019.67 MiB 1069.02 MB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Fri Feb 10 13:41:05 2012
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : mdadm-test:0
           UUID : 5cb9b746:450d257f:00fb7bd6:854bcb2b
         Events : 18

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1

root@mdadm-test:~# mkfs.ext4 -b 4096 -E stride=128,stripe-width=256 /dev/md0
mke2fs 1.41.14 (22-Dec-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=128 blocks, Stripe width=256 blocks
130560 inodes, 521984 blocks
26099 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=536870912
16 block groups
32768 blocks per group, 32768 fragments per group
8160 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912

Writing inode tables: done                            
Creating journal (8192 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 27 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
root@mdadm-test:~# tune2fs -m 0 /dev/md0
tune2fs 1.41.14 (22-Dec-2010)
Setting reserved blocks percentage to 0% (0 blocks)
root@mdadm-test:~# nano /etc/fstab
root@mdadm-test:~# mkdir /storage
root@mdadm-test:~# mount -a
root@mdadm-test:~# df -h /storage
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              2.0G   35M  2.0G   2% /storage
```


After verifying that works correctly, rebooted and installed 11.10 on the OS disk.  Ubuntu automatically installed mdadm for me, and configured an mdadm.conf file, but I like to have it in a consistent format, so I redid that, but here's my steps.

**11.10**

```
root@mdadm-test:~# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

root@mdadm-test:~# fdisk -l

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00072036

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    12582911     6290432   83  Linux
/dev/sda2        12584958    16775167     2095105    5  Extended
/dev/sda5        12584960    16775167     2095104   82  Linux swap / Solaris

Disk /dev/sdb: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x92c7d68c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     2088449     1044193+  fd  Linux raid autodetect

Disk /dev/sdc: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b8bfd17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     2088449     1044193+  fd  Linux raid autodetect

Disk /dev/sdd: 1073 MB, 1073741824 bytes
255 heads, 63 sectors/track, 130 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde26680a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63     2088449     1044193+  fd  Linux raid autodetect

Disk /dev/md0: 2138 MB, 2138046464 bytes
2 heads, 4 sectors/track, 521984 cylinders, total 4175872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

root@mdadm-test:~# echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
root@mdadm-test:~# echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
root@mdadm-test:~# echo "MAILADDR  youruser@gmail.com" >> /etc/mdadm/mdadm.conf
root@mdadm-test:~# mdadm --detail --scan >> /etc/mdadm/mdadm.conf
root@mdadm-test:~# nano /etc/fstab
root@mdadm-test:~# mkdir /storage
root@mdadm-test:~# mount -a
root@mdadm-test:~# df -h /storage
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              2.0G   35M  2.0G   2% /storage
root@mdadm-test:~# reboot

```

Here's a reboot, and following that, my machine booted and automounted the array just fine.
```
root@mdadm-test:~# df -h /storage/
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              2.0G   35M  2.0G   2% /storage
```

So, it looks like the fresh install method works fine and continues to work as it has for years.  Maybe this will help you see a step that you missed :)

---

### Post by Krupski on 2012-02-10
> **rubylaser said:**
> Okay, I just ran the tests and everything works great for me here.

Here's a "screenshot" of the error I get:

[img]http://three-dog.homelinux.com/other/images/boot_screen.jpg[/img]

Note: I combined 2 photos together to show all of it.

Does that tell you anything?

---

### Post by Krupski on 2012-02-10
> **rubylaser said:**
> Okay, I just ran the tests and everything works great for me here.

Your RAID array is made of /dev/sdb1, sdc1 and sdd1 (all partitions of a disk).

My array was initially created like this:

mdadm -C -n5 -l6 /dev/md0 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde

(something like that) - note that I used /dev/sda, /dev/sdb etc... NOT /dev/sda1, /dev/sdb1, etc...

---

### Post by rubylaser on 2012-02-10
Partitions vs. raw disks wouldn't be causing this issue, that's just how I like to setup mdadm arrays, but either way is fine.  In this case the partition message doesn't mean anything and isn't the problem.  The issue is that all the disks aren't available yet when it tries to assemble the array, so it thinks the array is degraded.

I would set up the boot degraded option first like this (this shouldn't be necessary, but this will get you around the error).
```
nano /etc/initramfs-tools/conf.d/mdadm
```
change "BOOT_DEGRADED=false" to "BOOT_DEGRADED=true"

Then, I would try to reconfigure mdadm
```
dpkg-reconfigure mdadm
```

Make sure when it asks you to autostart arrays, that you leave that field as **all**.  That should startup your array early in the boot process and avoid this.  The other option is to remove the mount line from /etc/fstab and write an init script that mounts your array at the end of the boot sequence, but I'll wait to hear from you about the results from trying the above.

---

