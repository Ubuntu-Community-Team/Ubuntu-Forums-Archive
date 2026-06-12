---
title: "scsi disks and fstab"
date: 2007-10-01
forum: Server Platforms
---

### Post by koenn on 2007-10-01
I'm playing with a VMware virtual machine where I'm using
2 IDE disks
2 SCSI disks

it's part of an LVM config, but this question is not about LVM. 
I seem to have a bit of trouble with the scsi disks.

I noticed that when I mount a scsi volume through /etc/fstab (eg mount /dev/sdb1 to /srv or //dev/sda1 to /home), it causes trouble during boot.

Apparently, the system tries to mount the volumes as given in fstab, but the scsi disks are not available yet so I get errors about corrupt/missing filesystems. 

I could work around that by not mounting any scsi volume from fstab, and mount them from an init script later in the process, 
although that seems a bit tricky, in case the files are needed by daemons that start earlier in the boot process. 

So I'm wondering
1/ is it normal for scsi disks to work this way ? Is this a vmware side effect or does it happen in real live as well

2/ what's the best way to deal with it ?

---

