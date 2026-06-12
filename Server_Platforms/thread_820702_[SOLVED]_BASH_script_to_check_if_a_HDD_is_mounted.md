---
title: "[SOLVED] BASH script to check if a HDD is mounted"
date: 2008-06-06
forum: Server Platforms
---

### Post by Titan8990 on 2008-06-06
I am looking to add to my backup script something that will check to see if a disk is mounted and if it is not, mount it. I had been looking at some example scripts and I am having a bit of trouble understanding it. I am no newb to Linux but definatly a newb to scripting of all kinds. 

So here is what I am looking at:

```
MNT_POINT=/backup

MNT_INFO=$(mount | awk -v mnt=$MNT_POINT '{if ($3 == mnt) print $0}')

if ["$MNT_INFO" == ""]; then
echo "not mounted"
fi
```

The line that I am having trouble grasping is this one:

> MNT_INFO=$(mount | awk -v mnt=$MNT_POINT '{if ($3 == mnt) print $0}')

I looked at the man pages for mawk (assuming that it is the same as awk command) but it still didn't help me get it as the man pages didn't go over the -v arguement hardly at all.

So anyways.... Does "mnt" refer to the mnt directory? How does this line use an integer value to comapare in order to find if the drive is mounted? I would this 1=true 0=false but 3? I also notice that this script does not rever to a specfic drive which I would like my script to do. Any suggestions on how to implement that would be excellent.

For those looking to help, I am as much interested in understanding this script as I am getting it modified and functioning.

As always I appreciate any help I can get.

Thanks

---

### Post by Monicker on 2008-06-06
There is no integer comparison in that line.  The -v is being used to assign the value of /backup to an awk variable which is called mnt.  Awk uses whitespace as the default field separator.

```
anthony@localhost ~ $ mount
/dev/sda3 on / type ext3 (rw,noatime)
```


With the above output of the mount command, the 3rd field would be "/".  The line from the script would compare each line of the mount command output, looking for /backup in the 3rd field.

To mount a specific parition just specify it in your mount command in your script, if you find that it is not mounted.  You could assign another variable if you want to check if its mounted at the right partition; but that seems unnecessary, since I would think that has already been determined in /etc/fstab.

---

### Post by Titan8990 on 2008-06-06
Alright, i appreciate your post. I now have a much better understanding of the script. I think that I need to go about this a different way. This is the output of my mount list (which is done when not all my disks are mounted). The drive I am trying to check if is mounted is at the bottom (sda1). 

With this script it would check the mount on my first drive (sdb1). 

```
jordan@einstein:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/hda on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=jordan)
/dev/sda1 on /media/sda1 type ext3 (rw)
```


I need approach this from a different direction. Any suggestions?

Here is my /etc/fstab if this helps:

```
jordan@einstein:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a9d41ccf-5fff-46c5-883d-4988b8f7461e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=07b7524d-1a82-4a0e-8453-fdbc70be7741 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by dje on 2008-06-06
Couldn't you just check that a file or directory which is on the drive is there:
```
#!/bin/bash

if [ ! -d /backup/mydir ]; then
     echo "drive not mounted"
fi
```
or
```
#!/bin/bash

if [ ! -f /backup/myfile ]; then
     echo "drive not mounted"
fi
```
Of course choose a directory or file which is always on the drive. I think this is a much simpler way of doing it?

hope that helps,
dje

---

### Post by Martin Witte on 2008-06-06
For mount I get this
```
martin@toshibap200:~$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```
So modifying your script a little you get the information you want isn't it, or am I missing something?
```
martin@toshibap200:~$ MNT_POINT=/media/sda1
martin@toshibap200:~$ MNT_INFO=$(mount | awk -v mnt=$MNT_POINT '{if ($3 == mnt) print $0}')
martin@toshibap200:~$ set|grep MNT
MNT_INFO='/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)'
MNT_POINT=/media/sda1
martin@toshibap200:~$ if [[ -z "${MNT_INFO}" ]]; then
> echo "not mounted"
> else
> echo "mounted"
> fi
mounted
martin@toshibap200:~$ 


```

---

### Post by Martin Witte on 2008-06-06
> **Titan8990 said:**
> 
I looked at the man pages for mawk (assuming that it is the same as awk command) but it still didn't help me get it as the man pages didn't go over the -v arguement hardly at all.

A good book on awk is available online, although it is an old print it is still usefull, see [the o reilly bookshelf]("http://www.unix.com.ua/orelly/unix/sedawk/index.htm")

---

### Post by hal10000 on 2008-06-06
this would be my script to test a mountpoint:
> 
#!/bin/bash
#filename mounttest.sh

mnt_point=/media/sda1
command=$(mount | grep $mnt_point | cut -d\  -f3)
#NOTE: in the above line there must be **two** spaces after cut -d\ 

if [ "$command" != "$mnt_point" ]
  then
    mount $mnt_point
  else
    echo "$mnt_point already mounted"
fi
exit 0



Make the script executable (chmod a+x mounttest.sh).
Depending on the settings in /etc/fstab (wether the device is mountable as normal user or only as root you may run it with sudo ./mounttest.sh or ./mounttest.sh

---

