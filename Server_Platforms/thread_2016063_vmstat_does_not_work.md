---
title: "vmstat does not work"
date: 2012-07-04
forum: Server Platforms
---

### Post by MitsuTomoe on 2012-07-04
Hi all,
I'm a newbie on Ubuntu Server 12.04, so my problem may seem obvious to you experts, but I can't find a solution.
I take care of 2 servers (Ubuntu 12.04) and on one of them, the account I use for administration (no root allowed, all with sudo) seem to lack some privileges.
When I try vmstat, it says :
Error: /proc must be mounted
  To mount /proc at boot you need an /etc/fstab line like:
      /proc   /proc   proc    defaults
  In the meantime, run "mount /proc /proc -t proc"

Of course, mount /proc ... say that proc is already mounted. sudo vmstat works .
Another symptom is that w does not display anything except header. sudo w works.
On the other server, I have no problem an I installed both same .
The account which has problem is member of sudo, admin and www-data groups.
I replaced real account name with myacc for security reasons.
Some info that may help :
myacc:x:1000:1000:Administrateur cOnclavis,,,:/home/myacc:/bin/bash
sudo:x:27:myacc
www-data:x:33:myacc
myacc:x:1000:
admin:x:115:myacc

Thank you for helping

---

### Post by MitsuTomoe on 2012-07-05
Nobody has an idea ?

---

### Post by hawkmage on 2012-07-05
DO you get any output when you run the following commands:
```
ls -l /proc
mount | grep -i "^proc"
cat /etc/fstab | grep -i "^proc"
```

---

### Post by MitsuTomoe on 2012-07-06
First command (ls) works, second (mount) does not display anything, third (cat) displays :
proc		/proc	proc	defaults		0	0

---

### Post by hawkmage on 2012-07-06
If you grep /var/log/dmesg and /var/log/messages for proc and mount are there any errors?

When you did the "ls" of /proc were there files/directories listed?

The entry in the fstab look OK but you do not seem to have it mounted.  What do you get with the following command:
```
mount | grep -i "proc"
```

---

### Post by MitsuTomoe on 2012-07-07
Here what it says :
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)

---

### Post by MitsuTomoe on 2012-07-07
Here is what I found in /var/log/dmesg :

EXT3-fs (sda1): error: couldn't mount because of unsupported optional features (240)
EXT2-fs (sda1): error: couldn't mount because of unsupported optional features (240)
EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)

---

### Post by CharlesA on 2012-07-07
Run fsck on /dev/sda1:

```
sudo shutdown -rF now
```

[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

---

### Post by MitsuTomoe on 2012-07-07
I'll give it a try when nobody on the server.

---

### Post by CharlesA on 2012-07-07
> **MitsuTomoe said:**
> I'll give it a try when nobody on the server.
In the mean time, can you post the output of this:

```
mount
```

---

### Post by MitsuTomoe on 2012-07-07
Here it is :
```
/dev/root on / type ext4 (rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev on /dev type devtmpfs (rw,relatime,size=1016912k,nr_inodes=254228,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620)
none on /run type tmpfs (rw,nosuid,noexec,relatime,size=203448k,mode=755)
none on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
none on /run/shm type tmpfs (rw,nosuid,nodev,relatime)
/dev/sda2 on /home type ext4 (rw,relatime,user_xattr,acl,barrier=1,data=ordered)

```

---

### Post by CharlesA on 2012-07-07
Is this a VPS or physical server?

/dev/root is an unusual device to use to mount /

---

### Post by MitsuTomoe on 2012-07-07
Physical server on hosting service provider.

---

### Post by MitsuTomoe on 2012-07-07
I did the fsck on boot, nothing changed.

---

### Post by MitsuTomoe on 2012-07-09
Nobody knows a solution ?

---

### Post by CharlesA on 2012-07-09
I don't know why it is acting that way. Perhaps try contacting your hosting company and asking about it?

I checked my mounted devices and it looks like this on my 12.04 server:

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)

```

---

### Post by MitsuTomoe on 2012-07-10
I went in /etc/mtab and found this:
```

rootfs / rootfs rw 0 0
/dev/root / ext4 rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev /dev devtmpfs rw,relatime,size=1016912k,nr_inodes=254228,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620 0 0
none /run tmpfs rw,nosuid,noexec,relatime,size=203448k,mode=755 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
/dev/sda2 /home ext4 rw,relatime,user_xattr,acl,barrier=1,data=ordered 0 0
```

If I try to do a dummy modification, it says "invalid format" on save unless I delete first line.
Is this the culprit ?  Should I delete this line ? Should I replace the line : ```
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
``` by ```
proc /proc proc rw 0 0
``` ?
I am no Ubuntu expert, so I don't want to make my system unbootable.
Your advices would be appreciated.

---

### Post by CharlesA on 2012-07-10
Have you contacted the hosting company yet? It could be that they have their images configured differently. They would be able to tell you for sure.

---

### Post by hawkmage on 2012-07-10
In general the /etc/mtab is a file that the system creates/updates based on what is mounted.  Editing it is probably not the best idea.

If you want to edit the file that controls the mounted volumes you should edit /etc/fstab.

The rootfs entry you indicated from your /etc/mtab is an artifact of the boot process.  As the kernel is loaded a ram disk is created and a temporary root file system is created in it and the init processes is started from it.  The rootfs should be replaced by the real root files sytem as the init processes proceeds.  It can be left behind especially if you are using an encrypted volume or the init precesses doesn't finish.

---

### Post by MitsuTomoe on 2012-07-11
Thank you for the information .
So, it seems something prevents /proc to be mounted on boot ?
Here is /etc/fstab :
```
# <file system>	<mount point>	<type>	<options>	<dump>	<pass>
proc		/proc	proc	defaults		0	0
/dev/sda1	/	ext4	errors=remount-ro,relatime	0	1
/dev/sda2	/home	ext4	defaults,relatime	1	2
/dev/sda3	swap	swap	defaults	0	0
sysfs		/sys	sysfs	defaults		0	0
dev		/dev	devtmpfs	rw	0	0

```

and the result of mount command :
```
/dev/root on / type ext4 (rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
none on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev on /dev type devtmpfs (rw,relatime,size=1016912k,nr_inodes=254228,mode=755)
none on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620)
none on /run type tmpfs (rw,nosuid,noexec,relatime,size=203448k,mode=755)
none on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
none on /run/shm type tmpfs (rw,nosuid,nodev,relatime)
/dev/sda2 on /home type ext4 (rw,relatime,user_xattr,acl,barrier=1,data=ordered)

```


In var/log/dmesg , here is what I found :
```
EXT3-fs (sda1): error: couldn't mount because of unsupported optional features (240)
EXT2-fs (sda1): error: couldn't mount because of unsupported optional features (240)
EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
VFS: Mounted root (ext4 filesystem) readonly on device 8:1.

```

Do you understand what's happening ?

---

### Post by CharlesA on 2012-07-11
The proc line doesn't look right.

This is what mine says:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ef8c919f-7222-4883-ae69-e25ba2cb8f00 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=af5ce030-eefe-491f-b760-88e8b40d0d6e none            swap    sw              0       0

```

---

### Post by MitsuTomoe on 2012-07-11
I carefully looked at /etc/fstab and found extraneous tabs on 2 or 3 lines.
I deleted these and rebooted. Now mount says :
```
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
/dev on /dev type devtmpfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /home type ext4 (rw,relatime)

```

But vmstat still complains that /proc is not mounted :confused:

---

### Post by hawkmage on 2012-07-11
If you run vmstat as root or using sudo does it work?

Can you run the following with the /proc unmounted.
```
stat /proc
```

I have not see the issue in Linux but in Solaris the directory permissions on the mount point before the volume is mounted can cause phantom permissions issues.

---

### Post by MitsuTomoe on 2012-07-12
sudo vmstat always worked . 
Here is stat /proc : ```
 stat /proc
  File: `/proc'
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d	Inode: 390145      Links: 2
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2012-06-20 04:09:35.000000000 +0200
Modify: 2012-06-20 04:09:35.000000000 +0200
Change: 2012-06-20 04:09:35.000000000 +0200
 Birth: -

```

---

### Post by hawkmage on 2012-07-12
Since running vmstat works when running with sudo tells me that it is not an issue with the proc filesystem being mounted.  It is a permission issue.  

What are the permissions on:
/proc/version
/proc/meminfo
/proc/stat
/proc/vmstat

---

### Post by MitsuTomoe on 2012-07-13
You found it ! Here is the culprit :
```

0 -r-------- 1 root root 0 juil. 13 17:51 vmstat

```

I chmod'ed 444 vmstat and now it works .

Thanks a lot

---

### Post by hawkmage on 2012-07-13
Great, sorry it took so long.  This is odd, with standard Ubuntu you should have access to /proc/vmstat as a regular user.

Do you have a 3rd party procps package installed?

Is there anything in /etc/init/procps.conf that updates the permission in /proc?  

What about in /etc/init.d/procps?  (I know that this should not be used in 12.04 but just want to be through)

---

### Post by MitsuTomoe on 2012-07-14
I rebooted and the problem surfaced again. So sth is changing permissions on /proc/vmstat on boot. I didn't see anything special in the files you listed. 
 I can't remember having installed sth special, but it could be that ?

---

### Post by hawkmage on 2012-07-14
There are versions of procps like procps-ng that will allow hardening of the /proc but I have not found anything for the default package that comes with Ubuntu to do this.  

You could try adding the chmod command to the /etc/sysctl.conf between the "script" and "end script" lines.  This is a workaround snot a solution.

---

