---
title: "cannot execute files from other partition"
date: 2006-06-14
forum: Server Platforms
---

### Post by panzi on 2006-06-14
Hi.

I cannot execute any files from my /dev/hda1 disk. The exec option is set, but when I mount it, the noexec option is set! :confused: 

```

mount
/dev/hdb1 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda1 on /mnt/data type reiserfs (rw,noexec,nosuid,nodev,notail)

```

This is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>      <options>                                <dump> <pass>
proc            /proc           proc        defaults                                  0     0
/dev/hdb1       /               reiserfs    notail,atime,auto,rw,dev,exec,suid,nouser 0     1
/dev/hdb5       none            swap        sw                                        0     0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto                               0     0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto                               0     0
/dev/fd0        /media/floppy0  auto        ,atime,noauto,rw,dev,exec,suid,user       0     0
/dev/sda1       /media/usb0     auto        ,atime,noauto,rw,dev,exec,suid,user       0     0
/dev/hda1       /mnt/data       reiserfs    notail,atime,auto,rw,dev,exec,suid,user   0     0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0

```

what the hell is going on an how can I fix that crap?

---

### Post by Sutekh on 2006-06-14
The only thing I can think of is the fact that **user** implies the options **noexec, nosuid, nodev** unless you specify otherwise.  

Seeing as you have specified **exec, suid, dev** the only thing I can think of the *order* of the options.   

It could possibly be that setting **user** *after* **exec** over-rides it with **noexec**?

Try placing the **user** option before specifying the other options
>  /dev/hda1       /mnt/data       reiserfs    **user,**notail,atime,auto,rw,dev,exec,suid   0     0 

---

