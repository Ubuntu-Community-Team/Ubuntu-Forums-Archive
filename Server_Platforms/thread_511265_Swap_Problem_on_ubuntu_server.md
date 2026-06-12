---
title: "Swap Problem on ubuntu server"
date: 2007-07-27
forum: Server Platforms
---

### Post by mewt on 2007-07-27
Hi, 

I Have just finished upgrading our LUG server from fedora core 3 to ubuntu server. The following is a printout of  /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md2        /               ext3    defaults,errors=remount-ro 0       0
/dev/md0        /boot           ext3    defaults        0       2
/dev/mapper/VolGroup00-LogVol06 /mirror         ext3    defaults        0       0
/dev/md1        none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


to explain it all.../dev/md2 is root partition, /dev/md0 is /boot and /dev/md1 *should* be the swap partition.

however:

****@mlug-mirror:~$ mount
/dev/md2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/md0 on /boot type ext3 (rw)
/dev/mapper/VolGroup00-LogVol06 on /mirror type ext3 (rw)


the swap partition is not mounted at all..The line starting /dev/md1 was commented out in fstab..I have since removed the commenting and did a sudo mount -a and sudo swapon -av.

mount -a seems to give no problems, however /dev/md1 does not get mounted.

swapon -av gives the following:

******@mlug-mirror:~$ sudo swapon -av
swapon on /dev/md1
swapon: /dev/md1: Invalid argument

We are in sore need of fixing this problem as the server needs swap space. 

If anyone could please help it would be greatly appreaciated.


Thanks

Anton Xuereb
Malta Linux User Group


P.S. It is quite vital that we don't brick the server as the server is co-located at Datacentre..A trip which no-one of the LUG can make right now :)

---

### Post by mewt on 2007-07-29
bump ?

---

### Post by koenn on 2007-07-29
OK, I'll have a go.
I'm not using software raid, never have, so your chances are slim. 

1/ I dont think swap devices get actually mounted, they're turned on/off
here's me verifying that: 
```

root@knix:~# grep swap /etc/fstab
/dev/hda4       none            swap    sw              0       0
/dev/hda7       none            swap    sw              0       0
root@knix:~# mount |grep swap
root@knix:~# mount |grep ext2
/dev/hda3 on /boot type ext2 (rw)
root@knix:~# swapoff -av
swapoff on /dev/hda4
swapoff on /dev/hda7
root@knix:~# swapon -av
swapon on /dev/hda4
swapon on /dev/hda7
root@knix:~# mount |grep swap
root@knix:~#

```


so we ignore your mount output and focus on the swap issue. 

2/
Here's a debian user with the same problem. Hist workaround was to create a swap file. that might be a temporary sollution for your server. 
[http://lists.debian.org/debian-amd64/2006/01/msg00529.html](http://lists.debian.org/debian-amd64/2006/01/msg00529.html)

3/
```
 swapon: /dev/md1: Invalid argument
```
suggests that /dev/md1 doesn't exist. swapon reads the string "/dev/md1"  from fstab (where it got commented out at first ...) but cant find the actual device, or somethin alog those lines. 

This may have something to do with your initial raid setup. Anything strange happen there ? 

Do you know of a way to check that there is indeed a /dev/md1 ?  - fdsik or mdadm or so, or cat /proc/mdstat maybe ?

---

