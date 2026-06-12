---
title: "RAID - best practice for mounting existing RAID array on fresh installation"
date: 2011-08-01
forum: Server Platforms
---

### Post by Rincage on 2011-08-01
I'm running 10.04 x86 server with a really simple installation on a single 250GB boot disk. I then have a RAID5 array as /dev/md0 (set up using mdadm with x4 2TB disks). All is working well. My mdadm.conf file looks like this

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
MAILADDR io@bb

# definitions of existing MD arrays

# This file was auto-generated on Fri, 03 Jun 2011 08:53:47 +0100
# by mkconf $Id$
DEVICE /dev/sdb /dev/sdc /dev/sdd /dev/sde
ARRAY /dev/md0 level=raid5 devices=/dev/sdb,/dev/sdc,/dev/sdd,/dev/sde

```My question is, if I was to lose the boot disk and need to remount the RAID array on a fresh installation, what steps do I need to go through. My assumption is that the superblocks on the RAID disks will be used and I don't need to keep any additional information - is this right?

---

### Post by aeiah on 2011-08-01
yes. although to make life easier, you should probably back up your mdadm.conf and /etc/fstab somewhere (not on the raid its self :p)

note that on a new system, your devices and arrays may be seen differently (and not /dev/sdb /dev/sdc /dev/sdd /dev/sde) if you've got additional devices taking up some of those names or something, but it would probably be good to keep it around for reference

---

### Post by rubylaser on 2011-08-01
You definitely, won't want or need to specifically name your devices (/dev/sdb, etc) in your mdadm.conf file.  The partitions line will cover all mdadm RAID devices for you that match the UUID that you're trying to assemble.  You can backup your mdadm.conf file before migrating, but the raid metadata is stored in the superblock on each disk from your array, so even if you forget to back it up, you'll be just fine.

---

### Post by YesWeCan on 2011-08-01
...so the mdadm.conf file needs to be changed to specify the UUID of the array,
for example:

```
# definitions of existing MD arrays
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=86779d62:ae742571:adb101fa:93741ce9
```

And the line
[COLOR="DarkGreen"]DEVICE /dev/sdb /dev/sdc /dev/sdd /dev/sde[/COLOR]
is redundant and can be deleted because it is a subset of
[COLOR="DarkGreen"]DEVICE partitions[/COLOR]

---

### Post by Rincage on 2011-08-02
Thanks. So I assume it's a choice between using (the new style) superblocks to store the RAID meta-data or using (the old style) additional entries in mdadm.conf?

---

### Post by rubylaser on 2011-08-02
YesWeCan, thanks for clarifying what I said, I guess that was a bit vague :)

> Thanks. So I assume it's a choice between using (the new style) superblocks to store the RAID meta-data or using (the old style) additional entries in mdadm.conf?
Not really.  mdadm is going to store it's metadata in the superblock as that's how it works.  DEVICE partitions makes mdadm read all the devices in /proc/partitions and will use those for assembling arrays.  DEVICE partitions works very well, and you shouldn't need to use anything else.

---

### Post by tgalati4 on 2011-08-02
Pretend your machine won't boot.  Put in an Ubuntu LiveCD and see what you need to do to navigate around and manually mount drives.  Write down those procedures.

You could write a script to backup your boot drive to a USB flash drive (say once a month).  Test the backup by booting from the USB flash drive.  Don't run the OS from the flash drive for a long time, because the frequent writes can wear it out, but for backup, it's fine.

---

