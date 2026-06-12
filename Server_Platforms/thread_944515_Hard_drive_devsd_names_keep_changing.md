---
title: "Hard drive /dev/sd? names keep changing"
date: 2008-10-11
forum: Server Platforms
---

### Post by timandjulz on 2008-10-11
The hard drive device names often change when I reboot Ubuntu 64bit 8.04 kernel 2.6.24-19.  e.g. /dev/sdi becomes /dev/sda.

I have been ignoring this for a long time but today I accidently deleted a partition on the wrong hard drive.  Needless to say, I now have an incentive to solve this problem.

How can I tell Linux to stop moving things around?

Thanks,
Tim

---

### Post by timandjulz on 2008-10-13
bump

---

### Post by lykwydchykyn on 2008-10-13
I'm no expert on this, but I believe you can use udev rules to map drive names to UUIDs.  See this link (it's redhat, but udev should work the same in ubuntu):

[configuring persistent storage](http://www.centos.org/docs/5/html/5.2/Virtualization/sect-Virtualization-Virtualized_block_devices-Configuring_persistent_storage_in_a_Red_Hat_Enterprise_Linux_5_environment.html)

You might also assign disk labels to the drives and access them using labels instead of the sd* nomenclature.

---

### Post by promodus on 2008-10-13
UUIDs are great.

If you're wanting persistent naming with /dev/sda, sdb, sdc, etc...
The only problem with UUID's is that it applies to partitions, not the whole device.

I would think the drive serial number would be a good place to track what drive is attached to what device name.

Example:
```
hdparm -I /dev/sda | grep -A 2 Model
```

To find what partitions have which UUIDs, use blkid

---

### Post by timandjulz on 2008-10-14
> **lykwydchykyn said:**
> I'm no expert on this, but I believe you can use udev rules to map drive names to UUIDs.  See this link (it's redhat, but udev should work the same in ubuntu):

[configuring persistent storage](http://www.centos.org/docs/5/html/5.2/Virtualization/sect-Virtualization-Virtualized_block_devices-Configuring_persistent_storage_in_a_Red_Hat_Enterprise_Linux_5_environment.html)

You might also assign disk labels to the drives and access them using labels instead of the sd* nomenclature.

Thanks lykwydchykyn.  This looks like a good approach and udev is probably the culprit for moving things around.

I would like to keep the same naming convention (e.g. /dev/sd*).  I already use labels on the partitions in fstab so that part should work fine.  But I am a bit concerned I might get a collision by renaming the drives (sdc becomes sdb) and cause unforeseen problems (sdb already existed).  Any ideas if this is a risk or does udev automatically deal with it?

Thanks in advance,
Tim

---

### Post by timandjulz on 2008-10-14
I can't get udev rules to work.  I tried this:

```
#Add ID_SERIAL and other variables into the environment
ACTION=="add", KERNEL=="/dev/[sh]d[a-z]", IMPORT{program}="ata_id --export $tempnode"
#Add symlink to hard drive
KERNEL=="/dev/[sh]d[a-z]", ENV{ID_SERIAL}=="WD-WCANU1937055", SYMLINK+="timsdisks/500gb_a"

```
My understanding is this should create a symlink in /dev/timdisks named 500gb_a.  The timdisks folder isn't created and there is nothing in the syslog nor /var/log/udev.  ???

Do I have a problem with my udev rule?

Output of udevtest:

```
sudo udevtest /dev/sda
parse_file: reading '/etc/udev/rules.d/05-options.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-udev-early.rules' as rules file
parse_file: reading '/etc/udev/rules.d/20-names.rules' as rules file
<snip>
parse_file: reading '/etc/udev/rules.d/50-TimSymlinks.rules' as rules file
<snip>
parse_file: reading '/etc/udev/rules.d/95-udev-late.rules' as rules file
unable to open device '/dev/sda'

```

---

### Post by dmizer on 2008-10-14
I had this same problem.

All I had to do was modify /etc/fstab to mount the drive by UUID instead of /dev/sd* like so:

From this:
```
/dev/sdc1       /media/backup   ext3    defaults        0       1
```

To this:

```
#/dev/sdc1
UUID=47ff66d6-786b-4a9d-a75c-a93f9be07639       /media/backup   ext3    defaults        0       1
```

---

### Post by forger on 2008-10-14
In case you're looking for the uuid of your partition:
```
ls -l /dev/disk/by-uuid
ls -l /dev/disk/by-id
```

or:
```
sudo vol_id /dev/sda1
```

Here's my /etc/fstab for example:
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=84dd1fef-48f2-4aa9-badf-dea59ac58e39 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=f5c288aa-acd3-48e7-9217-e2dc412f3de3 /home           ext3    relatime        0       2
# /dev/sdb1
UUID=1ba5ca25-f700-4aad-990f-7d1875ebc173 /media/300gb    ext3    relatime        0       2
# /dev/sda2
UUID=e4c071a0-9ed3-49ca-9c4e-54cd3a1abee0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by cariboo on 2008-10-14
I never reboot my server, so I never run into that problem, :) the only reason I would reboot is if there is a new kernel with a security update. I also invested in an inexpensive ups so I have no problems with power fluctuations.

If you do want problems with drive id's change use the blkid to identify your drives, I had a problem with that early on in Intrepid desktop testing, where it was sying that /dev/sda had a problem and I needed to run fsck on the drive. The problem was that /dev/sda is my windows drive and Hardy was on /dev/sdb and  /dev/sdc was Intrepid. Changing to using blkid I never had the problem again. They fixed the problem around alpha 4, So I look forward to the final release, I will then install Intrepid server.

Jim

---

### Post by phoinx on 2010-05-04
forger, your post was very useful to me. Thanks!

---

