---
title: "LVM over RAID5 -- not mounting on bootup"
date: 2008-03-23
forum: Server Platforms
---

### Post by r0biwan on 2008-03-23
Hey all,

I have a computer running Ubuntu 7.10 server and I'm running into a problem. Basically I have LVM set up on top of a software raid5 array.

what's happening is that my volume is not being mounted upon startup

I use LVM elsewhere on the system so I know that's running fine.

When I boot these are the steps I have to take to get things running again.

1) modprobe md
2) mdadm --assemble /dev/md0 /dev/hdc1 /dev/hde1 /dev/hdg1
3) mount /mnt/raid5

number 1 is fixed by putting "md" in /etc/modules
2 & 3 are fixed by writing a shell script, but I know this isn't the proper way to do it, and I'd like things to be done the "proper" ubuntu/debian way :)

FYI the fstab line is /dev/mapper/volGrp2-logVol0  /mnt/raid5 xfs...etc

any ideas?

---

### Post by r0biwan on 2008-03-23
What's odd too is that if I never would have used LVM, and just made a XFS partition on /dev/md0 I wouldn't have this problem.

Except now that I've learned LVM, I like having it around...

:\

---

### Post by ikonia on 2008-03-23
this is nothing to do with lvm.

LVM is not starting / mounting because the meta devices underneigh them is not starting.

the fact that you have to modprove the software raid modules proves this, as does manually starting the arrays

What does your /etc/mdadm.conf say  ?

---

### Post by r0biwan on 2008-03-24
/etc/mdadm/mdadm.conf:

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=8b81ed25:15e565b6:7318fde7:07e99154 devices=/dev/hdc1,/dev/hde1,/dev/hdg1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

---

### Post by ikonia on 2008-03-24
ok, 

that looks solid apart from the fact that your mdadm.conf is made up of hdc/e/g 

I would have expected to see /dev/sdc/e/g on any recent ubuntu install.

do you have device files for /dev/hdc/e/g ??

try rebooting and manually using the raid mdadm init script start up and see if it gives any errors.

something is pretty key that the modules are not being loaded at boot time.

---

### Post by r0biwan on 2008-03-25
This is a small home/office file server with IDE drives, so /dev/hd* is correct.

I assume you're talking about /etc/init.d/mdadm?

With a clean boot, running the command outputs nothing, upon examination it is because of "*test -f /proc/mdstat || exit 0*"

So I load the md module and run it again and get:
 * Starting MD monitoring service mdadm --monitor
   ...done.

However it doesn't assemble the array so I still have to run *mdadm --assemble /dev/md0 /dev/hdc1 /dev/hde1 /dev/hdg1*

As a note, my start raid script was basically the above command then && mount /mnt/raid5 and I got: mount: special device /dev/mapper/volGrp2-logVol0 does not exist

So I added sleep 5 in there to give LVM some time to detect it and it works fine.

This is a fresh installation of Ubuntu Server, for what it's worth.

---

### Post by ikonia on 2008-03-26
you said your running ubuntu 7.10 so hda/b/c is not what's expected, /dev/sda is what's expected, even for ide disks on 7.10 due to the libata changes.

have you by any chance upgraded from a lower version to 7.10 as that may be the problem.

once you have the array running try 

 mdadm --detail --scan

and compare the device details to what you current have in mdadm.conf,

---

### Post by Biochem on 2008-03-26
I have the same problem. It started when I updraded from Gutsy to Feisty. It was working fine a week ago.

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
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=1bd04ac5:84acbc56:345a719c:ee0e83b4

# This file was auto-generated on Mon, 21 Jan 2008 08:20:53 -0500
# by mkconf $Id: mkconf 324 2007-05-05 18:49:44Z madduck $

me@nefuats:~$ sudo mdadm --detail --scan
[sudo] password forme 
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=1bd04ac5:84acbc56:345a719c:ee0e83b4

```

---

### Post by r0biwan on 2008-03-26
sudo mdadm --detail --scan
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=8b81ed25:15e565b6:7318fde7:07e99154

(which does match my mdadm.conf)

As for the hd/sd thing, I am using an old motherboard & controller card, which after some Googling I found that some controllers don't use the new libata if I read correctly. Regardless "dmesg | grep ATA" returns the following:

[   30.365119] hda: ST310212A, ATA DISK drive
[   31.384097] hdc: MAXTOR STM3160812A, ATA DISK drive
[   32.912800] hde: WDC WD2500JB-00REA0, ATA DISK drive
[   33.212546] hdf: ST3320620A, ATA DISK drive
[   33.572225] hdg: MAXTOR STM3160812A, ATA DISK drive
(yes I know it's a random group of drives :p)

I don't have any sd* devices. This is a clean install of 7.10-server as well. The only thing non-Ubuntu on there is NX NoMachine.

I hate these kind of problems, everything looks okay....everything "should" work.

Biochem: Do you run LVM on top of your array? I wonder what effect 8.04 will have on us...

---

