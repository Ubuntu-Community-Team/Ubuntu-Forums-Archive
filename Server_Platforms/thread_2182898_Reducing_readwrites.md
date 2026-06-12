---
title: "Reducing read/writes"
date: 2013-10-22
forum: Server Platforms
---

### Post by nerdtron on 2013-10-22
I have installed ubuntu server on an 8GB USB flash drive. It has no other partitions (no swap) other than / partition. So it is running fine for a few days then I realized I need to minimize read/writes on the flash drive to extend its useful life. I think the /var/log directory writes every log on the system so I added these line on the fstab.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=69d82988-44fd-4907-8936-7d2c6603a3da /               ext4    noatime,nodiratime,errors=remount-ro 0       1
tmpfs   /tmp    tmpfs   defaults,noatime,mode=1777 0 0
tmpfs   /var/tmp tmpfs  defaults,noatime,mode=1777 0 0
tmpfs   /var/log tmpfs  defaults,noatime,mode=0755 0 0


```
I think it is working fine as the server reboots fine and the df -Th shows:
```
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdd1      ext4      7.5G  1.4G  5.7G  20% /
udev           devtmpfs  1.7G  4.0K  1.7G   1% /dev
tmpfs          tmpfs     1.7G     0  1.7G   0% /tmp
tmpfs          tmpfs     677M  236K  677M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.7G     0  1.7G   0% /run/shm
tmpfs          tmpfs     1.7G     0  1.7G   0% /var/tmp
tmpfs          tmpfs     1.7G  448K  1.7G   1% /var/log


```

My question is how do I know that this is working? How can I confirm that log files are no longer written to the flash drive and that read/write are reduced?
Also can I remove read/writes completely on the flash drive? All my important data are on the individual hard drives mounted on the server.

---

### Post by houstonbofh on 2013-10-22
What you may want to do is build a LiveUSB instead.  It is a system that runs fully in memory, but has some persistent storage.

But from what you posted, your logs are in ram, and gone on reboot, so you did what you intended...

---

### Post by nerdtron on 2013-10-23
Thanks for the heads up. Any software/commands to check if there are other "unnecessary" writes on the flash drive?

---

### Post by SeijiSensei on 2013-10-23
Install the **sysstat** package and use iostat.  A command like "iostat -d -h /dev/sdX" will give a useful summary.  See "man iostat" for the lengthy set of options available.

---

