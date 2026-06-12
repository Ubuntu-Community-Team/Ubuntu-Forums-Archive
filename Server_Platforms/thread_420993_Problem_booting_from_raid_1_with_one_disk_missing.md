---
title: "Problem booting from raid 1 with one disk missing"
date: 2007-04-24
forum: Server Platforms
---

### Post by uengberg on 2007-04-24
I have made a 7.04 server installation using software RAID 1 (and LVM) on a machine with two sata disks. Everything works very well and I can boot without problems with both disks attached. Also, I have had success booting on a live CD (7.04 desktop) and mounting my filesystem by installing mdadm and lvm support, with both or either disk attached.

My problem comes when trying to boot on just one of the disks (emulating a disk failure). It seems as though my RAID arrays are assembled, but not activated, as can be ssen from /proc/mdstat (when the boot process failes I am dumpoed into a initramfs busybox shell):

(initramfs) cat /proc/mdstat
Personalities : [raid1]
md1 : inactive sda2[0](S)
      310351616 blocks
md0 : inactive sda1[0](S)
      248896 blocks

unused devices: <none>

This seems like the standard behaviour for the mdadm assemble command, as mdadm --assemble --help explains (it won't activate unless --run or --scan is given on command line). But surely, a standard ubuntu installation should be able to boot from just one of the disks without need to edit the initramfs manually? Is this a bug or do I miss something?

I include a detailed description of my installation below.

BTW: The standard installation selects lilo as boot loader when I configure my disks as chosen. How can that be, usually grub is used?

  Urban

========================
# Installing Ubuntu 7.04 server

- Install to the hard disk
- English
- Denmark
- No
- Denmark
- Denmark
- eth0
- ampdev1
- Manual
  - Select free space of first disk
  - Create new partition
    - 255 MB
    - Primary
    - Beginning
    - Use as: physical volume for RAID
    - Bootable: on
    - Done setting up the partition
  - Create new partition
    - 317.8 GB
    - Primary
    - Beginning
    - Use as: physical volume for RAID
    - Done setting up the partition
  - Create new partition
    - 2 GB
    - Primary
    - End
    - Use as: swap area
    - Done setting up the partition
  - Repeat exactly same partitioning for disk 2
  - Configure software RAID
    - Yes
     - Create MD device
      - RAID1
      - Continue
      - Continue
      - Select active devices /dev/sda1, dev/sdb1
    - Create MD device
      - RAID1
      - Continue
      - Continue
      - Select active devices /dev/sda2, dev/sdb2
    - Finish
  - Select RAID1 device #0
    - Use as: Ext3 journaling file system
    - Mount point: /boot
    - Done setting up the partition
  - Select RAID1 device #1
    - Use as: physical volume for LVM
    - Done setting up the partition
  - Configure the Logical Volume Manager
    - Yes
    - Create Volume Group
      - ampdev1
      - mark and continue
    - Create logical volume
      - Continue
      - root
      - 20GB
      - (wait for a lomg time, doing lvcreate)
    - Create logical volume
      - return
      - home
      - Continue
      - (wait for three minutes, doing lvcreate)
    - Finish
  - Select LVM VG ampdev1, LV home
    - Use as: XFS journaling file system
    - Mount point: /home
    - Done setting up the partition
  - Select LVM VG ampdev1, LV root
    - Use as: XFS journaling file system
    - Mount point: /root
    - Done setting up the partition
  - Finish partitioning and write changes to disk
- Yes
- Yes
- <user name>
- <initials>
- ******
- ******
- Select LAMP server
- Lilo config: change to /dev/md0
- Continue

---

### Post by uengberg on 2007-04-24
I can make the system boot from the busybox prompt by simply running the command

  mdrun

and pressing control-d. After that, a subsequent boot also works as it should, booting up on just a single disk. But surely, this should not be necessary?

---

### Post by borahshadow on 2007-04-25
I too have this problem I checked a few days ago and didn't find any threads on it so I was about to post another but I decided to check again and this was here here is what I was going to post
> I've looked around and cannot find a fix for the life of me
I set up a new feisty 7.04 server with RAID 1 from the server install(ironically the day after it came out was the day my parts got here and I built it that night and installed the next day) 
due to a reccomendation from my friend I partitioned it like this
/boot 200mb ex2 sda1
swap 1GB(I think mabey 2) sda2
/ rest something like 248GB RAID
He said not to RAID /boot but I see lots of people do it I know why he said not to (the bootloader needing lowlevel access to the drive, but most new bootloaders can understand the filesystem anyway but I want to be able to use an older rescue disk if i need to is what he said) I am tempted to mirror it but that is not important right now there is lots of stuff out there on that

What happens is I boot up fine , cat/proc/mdstat is fine everything is dandy 
When I boot up as soon as the splash screen shows up if I hit alt+F1 then it says mdadm: can't find devices listed in .conf file 
or something real close to that
but then kinit takes over and it boots
when I disconnect one drive to simulate failure kinit never does any thing it just sits at the mdadm error

I think this means that an init script is mounting the drives and that script fails with the lack of one drive but I have no clue how to fix this

I do not have any /etc/raidtab file because the installer created the RAID

please help
ps. I don't have LVM but the rest seems the same
Thanks

EDIT sorry I have no idea what a busybox prompt is 
when it just sits after the mdadm error I tried typing that and hitting ctrl+D but nothing happened

I think this is a feisty problem I saw a bug report somewhere about a similar problem but I tried the fix and it didn't seem to work so I removed it

pps. the server install used grub for me didn't even give a lilo option

EDIT2 ok so I tried again and it didnt work but i was bored soIi started making patterns on the screen with the arrow keys ^[[A ^[[B etc
after a LONG time it dumped me into a busybox shell and I tried cat/proc/mdstat it showed inactive then i tried mdrun and then ctrl+d but it said filesystem doesnot have a /sbin/init so I did cat /proc/mdstat again and my array was running is degraded mode so I rebooted with the drive plugged in and started reconstruction 
ps.I thought on SATA2 drives it would be fast but it is about 30000K/s to like 60000K/s but ususlly getting lower with at first 58min now like 130min ??? that is like 48MB/s or .04 GB/s what happened to SATA's 3GB/s 
pps. I have a 1.9Ghz Dualcore and it isnot taking the processor enough to scale above 1.0GHz so it is not the processor

---

### Post by borahshadow on 2007-04-25
I decided that i'd better not edit my above post anymore but I did echo 50000 >/proc/sys/dev/raid/speed_limit_min and that raised it from 30000k/s to 50000k/s but I'd like to tell it tax the cpu and hdd 100% and get done in 10min err

---

### Post by borahshadow on 2007-04-28
my reconstruction was successfull but I never fixed booting from 1 disk 
Nobody knows anything to do for this?

---

### Post by ndemou on 2007-04-30
> **uengberg said:**
> ...But surely, this should not be necessary?
I would call it a bug. if you have the time file a bug report for this.

---

### Post by borahshadow on 2007-05-07
> **ndemou said:**
> I would call it a bug. if you have the time file a bug report for this.
I believe this is the same as bug #[108971]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/108971/") I have posted a comment there which will hopefully provide some more info for people who can do something about it

---

