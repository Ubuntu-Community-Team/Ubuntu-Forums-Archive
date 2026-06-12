---
title: "Ubuntu 8.04 unable to boot"
date: 2008-03-30
forum: Virtualisation
---

### Post by stefangr1 on 2008-03-30
For testing purposes, I have an Ubuntu 8.04 64 bit system installed on a (virtual) RAID-0 array.

Today I got a strange error message at boot:

Could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be
disabled. Please restart GDM when
the problem is corrected.

<OK>

Pressing the OK button didn't do anything.

After that I resetted the machine, the progress bar got to one third, showing this message below it:

Routine check of drives: /dev/md0...
Press ESC to skip

Then it crashes and the computer reboots.


I wonder if anybody has experienced something similar on real or virtual machines, or has any idea what could have caused this. It could be a bug with serious consequences in a normal user environment.

---

### Post by lemmyc on 2008-04-01
I have the same problem with "Routine check of drives". In my case, checking of /dev/hda5 gets to about 9%, then the computer reboots.
This is Hardy Beta. I guess it is finding an error on the drive, but not repairing it. I have to choose ESC to skip every time I boot up.

EDIT: In my case, this is not a virtual installation... Starting a new post in Hardy Development

---

### Post by SneakyWho_am_i on 2008-04-09
I'm having this same problem under Hardy. It's been happening since soon after install but I've only just got around to looking for an answer...

---

### Post by Pheebees on 2008-04-25
Hi!
I'm havin a problem where I'm able to boot and see the kubuntu blue logo then it just shows a black screen and I need to press the post button to reboot my pc.
I'm currently running a dual boot with vista at the other partition.. Does anyone have any idea what's happening?:mad:

---

### Post by huczek on 2008-05-27
**Hardy Heron 8.04 Gnome**
My problem:
routine check of drives: /dev/sda9 *(this is my "/" partition)*

**fstab:**
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=dfa36768-70cd-4733-9d6e-39c227edbefb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=23c3680c-1a07-4c3e-b7a0-41648210b7ab /boot           ext3    relatime        0       2
# /dev/sda8
UUID=ad83b467-beea-4af5-a45d-4898316c71e5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# /dev/sda5
UUID=2C66-0A18       /media/PRACA     vfat     rw,users,utf8,umask=0000 0 0

```
[COLOR="Silver"]now I have fat partition in my fstab, but the problem appeared before I added this part[/COLOR]
```
[COLOR="Silver"]# /dev/sda5
UUID=2C66-0A18       /media/PRACA     vfat     rw,users,utf8,umask=0000 0 0[/COLOR]
```

**mtab**
```
/dev/sda9 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
/dev/sda7 /boot ext3 rw,relatime 0 0
/dev/sda5 /media/PRACA vfat rw,noexec,nosuid,nodev,utf8,umask=0000 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/kononowicz/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=kononowicz 0 0
/dev/scd1 /media/cdrom1 iso9660 ro,nosuid,nodev,utf8,user=kononowicz 0 0
```

different problems with booting i.e.:
can't finish checking
can't start GDM
after boot problems with X no gnome interface etc.

---

