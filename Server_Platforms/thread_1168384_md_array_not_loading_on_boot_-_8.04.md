---
title: "md array not loading on boot - 8.04"
date: 2009-05-24
forum: Server Platforms
---

### Post by ScottRose on 2009-05-24
Hi,

I've been banging my head against the wall on this one for 2 days -- I've googled it every which way and can't find a solution.

**Short story:**

fsck throws an error and I'm dumped into a shell on boot because it can't check a LVM logical volume that sits on a md RAID1 array.  The array does not exist.  If I execute "mdadm --assemble --scan" and exit the shell, boot continues normally and all my volumes are there.

I tried explicitly defining my array in mdadm.conf to no avail.  The only change was that the devices from which the array is assembled got renamed from sdb, sdc  to sda, sdb.

**Long story:**

Original configuration:

Ubuntu 8.04 AMD64 (server)

Dell T605 w/ SAS6/iR controller  (Dual Quad-core Opteron)

250gb **hardware **RAID1 (from the SAS6 controller) at /dev/sda
2 x 1 TB disks attached to on-board SATA controller at /dev/sdb  /dev/sdc
/dev/sdb and /dev/sdc are md RAID1 at /dev/md0

LVM:

/dev/vg01/lv01-root  mounted at  /  (on /dev/sda4)
/dev/vg01/lv02-vm at /var/vm-disks/01/  (on /dev/sda4)
/dev/vg01/lv03-vm at /var/vm-disks/02/  (on /dev/md0)

The system ran fine and went through a couple of reboots over the course of 3 days.  I copied about 200gb of data to VMs that had their disks on both logical volumes lv02-vm and lv03-vm.  Completely stable.

Yesterday I installed a new Silicon Image SATA card (for a snapshot volume I was going to add -- wanted to keep it off of the other controllers), but I did not attach any disks.  I also installed 2 Intel NICs (probably irrelevant).

Booted up and got dumped to initramfs shell, with errors that vg01 was incomplete and the root volume could not load.  The UUID of /dev/md0 was not found.  I removed the Silicon Image card and rebooted.  Same deal.

I did..

vgreduce --removemissing
vgchange -a y
exit

..and boot continued normally (without lv03-vm, which sat on md0 and was removed by the previous commands).

I created a new volume group, vg02, in which to stick lv03-vm so that I could get through a boot.  Did..

mdadm --assemble --scan

mdadm --detail /dev/md0

..showed that the array was clean, and I was able to add the pv (/dev/md0) to vg02. I used vgcfgbackup to get the current config of vg02, and copied the physical_volumes section for lv03-vm from an old backup (correct UUID was in there, but I had to change the pv).  I used vgcfgrestore on that file, and then had lv03-vm available under vg02.

mount -a

..and my data was all there.

The weird thing is that /dev/md0 was now on /dev/sda and /dev/sdb, and my 250gb disk was now at /dev/sdc.   (The 250gb was previously at /dev/sda, and the 2x1tb disks were at /dev/sdb and /dev/sdc).

I thought perhaps it was fixed, and I rebooted.  This time fsck threw an error whilst trying to scan lv03-vm and dumped me to shell.  If I run..

mdadm --assemble --scan
exit

..then the system starts normally.  VMs start OK, all data is there.

Soooo, my question is: **Why is my md array not starting on boot (or at least not starting before lvm)?**

My mdadm.conf was system default the entire time.  

DEVICE partitions
[I](No arrays defined.)

[/I]I tried changing it to..

DEVICE /dev/sda  /dev/sdb
*(Output of *[I]mdadm --detail --scan)

[/I]..with no change in behaviour.

Any help would be hugely appreciated.  My system is running, but I have to manually intervene on boot (obviously not cool).

Regards,

Scott

---

### Post by sloggerkhan on 2009-05-24
My only thought is that somehow something is depending on device locations instead of uuids. (IE Somehow your LVM is looking to particular device addresses instead of uuids.)

I'm not very experienced in this though I do run a mdadm RAID. I don't use LVM with mine.

---

### Post by ScottRose on 2009-05-24
Thanks for the quick reply!

But if that were the case, then LVM would be pointing to /dev/md0, which hasn't changed.  The components of md0 changed (/dev/sdb, /dev/sdc), but since mdadm --assemble --scan works, I'm assuming that's somewhat OK.

If you (or anyone else) would find confs or logs helpful, please let me know what I should post..

---

### Post by sloggerkhan on 2009-05-24
> **ScottRose said:**
> Thanks for the quick reply!

But if that were the case, then LVM would be pointing to /dev/md0, which hasn't changed.  The components of md0 changed (/dev/sdb, /dev/sdc), but since mdadm --assemble --scan works, I'm assuming that's somewhat OK.

If you (or anyone else) would find confs or logs helpful, please let me know what I should post..

My hypothetical is that LVM is calling madadm --assemble on specific devices instead of using the --scan option or doing it by UUID, which would explain why you could manually assemble but lvm would error on boot.

However, like I mentioned, not experienced with LVM

---

### Post by ian dobson on 2009-05-24
Hi,

Do you have the mdadm modules in /etc/initramfs-tools/modules so that they're loaded in the initramfs?

I have :-
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
md
raid1

which is enough to load my boot/RAID 1 partition.

You need to run mkinitramfs to regenerate the root ramfs.

Also do you have your partitions/raid array setup in /etc/mdadm.conf?

Maybe you need to add the following to your init scripts with (I'm not sure as my RAID1 boot partition "just worked"):-
echo "mdadm --assemble --scan" > /etc/initramfs-tools/scripts/init-premount/mdadm
chmod 755 /etc/initramfs-tools/scripts/init-premount/mdadm
mkinitramfs -o /boot/initrd.img-2.6.22-14-raid (change to your image)

Regards
Ian Dobson

---

### Post by ScottRose on 2009-05-24
> **ian dobson said:**
> Do you have the mdadm modules in /etc/initramfs-tools/modules so that they're loaded in the initramfs?

Nope.  I'll give it a try, but I never had those entries and the array was working previously.  (AFAIK I'd only need md loaded in initramfs if my root fs was on software RAID; my root is h/w RAID, and it inits/mounts OK.   Please let me know if I'm wrong on that, just for my own edification..)

> **ian dobson said:**
> Also do you have your partitions/raid array setup in /etc/mdadm.conf?

Yes (comment lines removed for brevity):

```
root@hm-vm01:/etc/initramfs-tools# cat /etc/mdadm/mdadm.conf

DEVICE /dev/sda /dev/sdb

CREATE owner=root group=disk mode=0660 auto=yes

HOMEHOST <system>

MAILADDR root

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=ec259fae:96c5ab45:e7bffb3d:decd191d devices=/dev/sda,/dev/sdb
```..the ARRAY line was generated from the output of [FONT=Lucida Console]mdadm --detail --scan[/FONT].  I added the "devices=" portion manually, but I tried it both with and w/o that argument.

Here's the details on the array (executed with the array mounted, so it's gotta be the correct UUID and /dev/ entries (?)):

```
root@hm-vm01:/etc/initramfs-tools/scripts# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu May 21 11:52:53 2009
     Raid Level : raid1
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun May 24 12:19:36 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : ec259fae:96c5ab45:e7bffb3d:decd191d (local to host hm-vm01)
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
```
> **ian dobson said:**
>  Maybe you need to add the following to your init scripts with (I'm not sure as my RAID1 boot partition "just worked"):-
echo "mdadm --assemble --scan" > /etc/initramfs-tools/scripts/init-premount/mdadm
chmod 755 /etc/initramfs-tools/scripts/init-premount/mdadm
mkinitramfs -o /boot/initrd.img-2.6.22-14-raid (change to your image)

I tried that, painfully.  I wasn't sure which script dir to put it in so I tried many of them, including init-premount.

BTW - the reason I tried adding [FONT=Lucida Console]mdadm --assemble --scan[/FONT] to the initramfs scripts was b/c someone mentioned it in another forum (found while googling, I've only posted here).  That seems a little kludgy; any idea why the array would stop automatically initializing?

I ask both because I'm undoubtedly going to face this problem again (adding a new disk and/or controller to a system with a md array), and IMO adding disks should not break an otherwise-functioning system (hence should it be raised as a bug?).

Thanks!

---

### Post by fjgaude on 2009-05-24
What is the line in your fstab file that loads the array on bootup?

---

### Post by ScottRose on 2009-05-24
Eheheheheh..

I added md and raid1 to [FONT=Lucida Console]/etc/initramfs-tools/modules[/FONT] .

[FONT=Lucida Console]update-initramfs -u

reboot[/FONT] 

And got:

[FONT=Lucida Console]L 99 99 99 99 99[/FONT] [etc for about 10 lines]

That one's new to me, but goog has plenty of help.  I'll be back in a few.  :\

---

### Post by ScottRose on 2009-05-24
> **fjgaude said:**
> What is the line in your fstab file that loads the array on bootup?

Oh shizzbot.  I'm booting into a recovery shell right now, but I'm pretty sure fstab has

[FONT=Lucida Console]/dev/vg02/lv03-vm  /opt/vm-disks/02/  [/FONT][Don't know options offhand].

I changed it from UUID at some point during my original troubleshooting.  Maybe change it back to UUID?

Although I should point out that[FONT=Lucida Console] mount -a [/FONT]works fine after [FONT=Lucida Console]mdadm --assemble --scan[/FONT] .

---

### Post by alastair on 2009-05-24
I'm using 8.04 along with LVM2 and MD RAID1. I definitely sympathise with you because I've had personal experience of my own RAID funnies. It can be scary on some machines.

I have 2x MD volumes, each a PV for LVM2 : md0 md1

I had a problem a while ago (soon after install) when LVM failed at boot because the 2nd MD array was missing. I had to add the 2nd "ARRAY" line to the mdadm.conf - and this seemed to fix it. No idea why it worked originally.

My mdadm.conf file is now :

DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=dabb207f:fbc82719:f7353090:c805d08f
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=782f31fa:1ce094da:f22c7d85:8af54e96

LVM uses both md0 and md1. The UUID's are as reported for each MD device using :

mdadm --detail /dev/mdN

The MD partitions ate set to type "fd".

Maybe the "partitions" line helps? Good luck.

Alastair

---

### Post by ScottRose on 2009-05-24
> **alastair said:**
> 
My mdadm.conf file is now :

DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=dabb207f:fbc82719:f7353090:c805d08f
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=782f31fa:1ce094da:f22c7d85:8af54e96

Maybe the "partitions" line helps? Good luck.

Thanks Alastair, but I'm afraid my mdadm.conf looked just like that (with just md0 and my own UUID, of course) at some point when it wasn't working..

Unfortunately, I got my LILO "fixed", but now I get..

[FONT=Lucida Console]"checking if image is initramfs...it isn't (bad gzip magic numbers); looks like and initrd"[/FONT]

..during boot.  ::sigh::  Someone reported a similar problem (my initramfs image got bigger when I added md and raid1 to modules): [https://bugs.launchpad.net/ubuntu/hardy/+source/lilo/+bug/221664](https://bugs.launchpad.net/ubuntu/hardy/+source/lilo/+bug/221664)

I added [FONT=Lucida Console]large-memory[/FONT] to my lilo.conf, ran [FONT=Lucida Console]lilo[/FONT] with no errors, rebooted and got the same message (at which boot halts).  I was able to gunzip the initramfs image with no errors.

I tried re-creating [FONT=Lucida Console]initrd.img-2.6.24-23-server[/FONT] (no errors on creation), but same deal:

[FONT=Lucida Console]update-initramfs -c -v -k 2.6.24.23-server[/FONT]

Rolled back to my old initrd.img-2.6.24-23-server, and **still getting the error**.

I'm assuming I've now f'd something up in my lilo.conf.  lilo.conf points to /initrd.img which is symlinked to the correct /boot/initrd.img-2.6.24-23-server .
[I]
Sorry for being so verbose here, but I'm hoping that once this is solved the thread might help someone going down the same path as myself.[/I]

---

### Post by ScottRose on 2009-05-24
**SOLVED!**

I just booted straight through, and had all of my volumes online and correctly mounted.

I just don't know why it was solved.

The last thing I had done before completely breaking my boot sequence was add [FONT=Lucida Console]md [/FONT]to [FONT=Lucida Console]/etc/initramfs/modules[/FONT] and run [FONT=Lucida Console]update-initramfs-u[/FONT] .  That broke the system.

I restored a backup of [FONT=Lucida Console]initrd.img-2.6.24-23-server[/FONT] and rebooted, but had not re-run [FONT=Lucida Console]lilo [/FONT](so it did not work).

I re-ran [FONT=Lucida Console]lilo[/FONT], rebooted, and now am OK.

The problem I have with this is that I'm [AFAIK] back to a condition where the md array previously did not load -- but it does now!
[B]
Anyone have any ideas on what I did to solve this????[/B]

Here are some configs and outputs that may be helpful..  This is the **working **state:

Note: the LILO mbr is on /dev/sda .  My BIOS explicitly defines that /dev/sdc should be first, both in boot order and "disk order" (two different settings).

fdisk -l
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b211aea

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39ee015c

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 249.3 GB, 249376538624 bytes
255 heads, 63 sectors/track, 30318 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           9       72261   de  Dell Utility
/dev/sdc2              10         271     2104515    b  W95 FAT32
/dev/sdc3           29096       30318     9823747+   5  Extended
/dev/sdc4   *         272       29095   231528780   8e  Linux LVM
/dev/sdc5           29096       30318     9823716   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/md0: 1000.2 GB, 1000204795904 bytes
2 heads, 4 sectors/track, 244190624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x7b211aea

    Device Boot      Start         End      Blocks   Id  System
```blkid
```
/dev/mapper/vg01-lv01--root: UUID="ee65919c-f4a6-47f5-b364-50ee440bca53" TYPE="ext3" SEC_TYPE="ext2"
/dev/mapper/vg01-lv02--vm: UUID="7cd2f57c-57b9-4804-b44a-99ad2ed8bba6" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda: UUID="ae9f25ec-45ab-c596-3dfb-bfe71d19cdde" TYPE="mdraid"
/dev/sdb: UUID="ae9f25ec-45ab-c596-3dfb-bfe71d19cdde" TYPE="mdraid"
/dev/sdc1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-050F" TYPE="vfat"
/dev/sdc2: LABEL="OS" UUID="07D9-050F" TYPE="vfat"
/dev/sdc4: UUID="8SiUaM-fbj2-5Pgo-y0TC-54tx-zKi8-Gl3gfC" TYPE="lvm2pv"
/dev/sdc5: TYPE="swap" UUID="7aeff811-9401-4f96-97ac-b09c525f333c"
/dev/md0: UUID="T2Ioi2-0U2V-paRM-WTlA-DbPe-G2ZZ-fFSMf1" TYPE="lvm2pv"
/dev/mapper/vg02-lv03--vm: UUID="3f9f7227-fcf7-4fc7-9dfa-6b47f57e5a57" TYPE="ext3"
```ls -l /dev/mapper
```
total 0
crw-rw---- 1 root root  10, 63 2009-05-24 15:30 control
brw-rw---- 1 root disk 254,  0 2009-05-24 15:30 vg01-lv01--root
brw-rw---- 1 root disk 254,  1 2009-05-24 15:30 vg01-lv02--vm
brw-rw---- 1 root disk 254,  2 2009-05-24 15:30 vg02-lv03--vm
```ls -l /dev/disk/by-uuid/
```
total 0
lrwxrwxrwx 1 root root 10 2009-05-24 15:30 07D9-050F -> ../../sdc2
lrwxrwxrwx 1 root root 26 2009-05-24 15:30 3f9f7227-fcf7-4fc7-9dfa-6b47f57e5a57 -> ../../mapper/vg02-lv03--vm
lrwxrwxrwx 1 root root 10 2009-05-24 15:30 7aeff811-9401-4f96-97ac-b09c525f333c -> ../../sdc5
lrwxrwxrwx 1 root root 26 2009-05-24 15:30 7cd2f57c-57b9-4804-b44a-99ad2ed8bba6 -> ../../mapper/vg01-lv02--vm
lrwxrwxrwx 1 root root 28 2009-05-24 15:30 ee65919c-f4a6-47f5-b364-50ee440bca53 -> ../../mapper/vg01-lv01--root
```cat /etc/mdadm/mdadm.conf
```
DEVICE /dev/sda /dev/sdb

CREATE owner=root group=disk mode=0660 auto=yes

HOMEHOST <system>

MAILADDR root

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=ec259fae:96c5ab45:e7bffb3d:decd191d devices=/dev/sda,/dev/sdb
```mdadm --detail /dev/md0
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu May 21 11:52:53 2009
     Raid Level : raid1
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun May 24 15:31:47 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : ec259fae:96c5ab45:e7bffb3d:decd191d (local to host hm-vm01)
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
```cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/vg01-lv01--root
UUID=ee65919c-f4a6-47f5-b364-50ee440bca53   /               ext3    relatime,errors=remount-ro 0       1
# /dev/mapper/vg01-lv02--vm
/dev/vg01/lv02-vm  /opt/vm-disks/01 ext3    relatime        0       2
# /dev/sdb5
/dev/sdb5  none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/mapper/vg01-lv03--vm
/dev/vg02/lv03-vm  /opt/vm-disks/02 ext3   relatime     0       2
```cat /etc/lilo.conf
```
boot=/dev/sdc
large-memory

map=/boot/map

delay=20

default=Linux

image=/vmlinuz
        label=Linux
        read-only
#       restricted
#       alias=1
        append="root=/dev/mapper/vg01-lv01--root  "
        initrd=/initrd.img

image=/vmlinuz.old
        label=LinuxOLD
        read-only
        optional
#       restricted
#       alias=2
        append="root=/dev/mapper/vg01-lv01--root  "
        initrd=/initrd.img.old
```Thanks for reading.. ;)

---

### Post by alastair on 2009-05-24
Nothing jumps out at me, but it's late and it's been years since I even thought about LILO as a boot loader. I hope you figure it out, but make sure you've got back-ups I think ...

---

### Post by ScottRose on 2009-05-24
Ubuntu Server  (6.06-8.10 AFAIK) uses LILO by default on a single-OS system (as most servers are apt to be).  I don't even remember if GRUB is an option in the install UI.

I give the installer image credit though; it was able to mount my root partition every time in rescue mode.

Backups?  What are those??

Seriously though, I don't think this will ever be a data loss issue.  More of a descriptor problem [*knocks on wood*].

Fortunately the 2 VMs that I'm running on this machine thus far are brand new and they hold ~200GB of data just copied from an old Windows server.  Fortunately I didn't wipe the disks on the old server (I learned a loonng time ago to leave that part until absolute last ;) ) so I wasn't too rattled by the whole experience..

---

