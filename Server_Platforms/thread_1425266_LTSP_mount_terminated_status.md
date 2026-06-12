---
title: "LTSP mount terminated status"
date: 2010-03-08
forum: Server Platforms
---

### Post by map7 on 2010-03-08
I've just installed Ubuntu 9.10 64bit on my new server and then built a 32bit image.  When I try and boot my thin clients I get the following error on VT7:

```
mount: according to mtab, aufs is already mount on /

mountall: mount / [416] terminated with status 1.
mount: according to mtab, none is already mounted on /proc

mountall: mount /proc [409] terminated with status 1.
mount: according to mtab, none is already mounted on /sys

mountall: mount /sys [410] terminated with status 1.
mount: according to mtab, udev is already mounted on /dev

mountall: mount /dev [411] terminated with status 1.
mount: according to mtab, /dev/nbd0 is already mounted on /rofs

mountall: mount /rofs [412] terminated with status 1.
mount: according to mtab, tmpfs is already mounted on /cow

mountall: mount /cow [413] terminated with status 1.

```

What could this be?

If I try and start the nbd server manually I get warnings:
```

** (process:2112): WARNING **: Could not parse config file: Could not open config file.
** Message: Nothing to do! Bye!
 nbd-server.

```

If I do a ps -wax | grep nbd I do see a nbd-server running 'nbd-server 0 /opt/ltsp/images/i386.img -r -C /dev/null'.  My i386.img file does exist and it's about 205MB which seems big enough.

---

### Post by Digital Treehouse on 2010-03-09
We've had a similar bother with this today... a brand new install on a test environment.  What we found was that the RAM hadn't cleared correctly from one shutdown to another.

Shutting down the terminal, pulling out the power cable and waiting a good 10 seconds cleared the old mounted filesystems from RAM and it booted correctly.

I hope it's that simple for you too... it certainly was a headache!

---

### Post by map7 on 2010-03-09
I unplugged my thin client and removed the power for a good 30seconds and I still get the same error.  If I reconfigure my DHCP server I can successfully boot onto my old 9.04 32bit server.  

Could this be an Ubuntu 9.10 64bit issue?

I built this Ubuntu 9.10 64bit system from scratch and then installed the ltsp server and openssh packages, built my 32bit client, updated the ltsp kernels and tried running my client.

---

### Post by dionblundell on 2010-03-27
I have a similar issue, I'm using Ubuntu Netbook Remix 10.04 Beta1.
Once again I get the errors about device "none" being already mounted elsewhere, which of course it is, but it shouldn't throw up an error.
I have a notebook with of 2GB of RAM and run a RAM Drive, I'll try leaving my notebook off, the battery out, and seeing what happens and will post again.

Here is my fstab
```
proc        /proc            proc    nodev,noexec,nosuid        0    0
/dev/sda8    /            ext4    nodiratime,errors=remount-ro    0    1
/dev/sda5    none            swap    sw                0    0
ramtmp        /tmp            tmpfs    defaults,noexec,nosuid        0    2
/dev/sda6    /home            ext4    defaults            0    2
/dev/sdb1    /media/sdcard        ext3    defaults            0    2

```

I don't know how to get the exact text from the startup screen though,
but it complaims about
/sys being mounted on none

---

### Post by goscuter1 on 2011-04-24
*edit: lol just realised this is about a different issue - I think. I wouldn't really know. Sorry if it is. I'm just on a chicken hunt looking for answers...sorry. *


> **Digital Treehouse said:**
> We've had a similar bother with this today... a brand new install on a test environment.  What we found was that the RAM hadn't cleared correctly from one shutdown to another.

Shutting down the terminal, pulling out the power cable and waiting a good 10 seconds cleared the old mounted filesystems from RAM and it booted correctly.

I hope it's that simple for you too... it certainly was a headache!

Thanks for the suggestion DT, unfortunately it didn't work in my case. 

```
[COLOR=#000000][FONT=Verdana]**ubuntu@ubuntu:~$ sudo umount /dev/loop0**[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]umount: /rofs: device is busy.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]        (In some cases useful info about processes that use[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]         the device is found by lsof(8) or fuser(1))[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**ubuntu@ubuntu:~$ sudo fuser /dev/loop0**[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Cannot stat file /proc/3193/fd/35: Stale NFS file handle[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Cannot stat file /proc/3193/fd/36: Stale NFS file handle[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Cannot stat file /proc/3193/fd/40: Stale NFS file handle[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Cannot stat file /proc/3193/fd/41: Stale NFS file handle[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Cannot stat file /proc/3193/fd/42: Stale NFS file handle[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Cannot stat file /proc/3193/fd/43: Stale NFS file handle[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Cannot stat file /proc/3456/fd/35: Stale NFS file handle[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Cannot stat file /proc/5388/fd/23: Stale NFS file handle[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Cannot stat file /proc/5388/fd/24: Stale NFS file handle[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]**ubuntu@ubuntu:~$ sudo lsof**[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]lsof: WARNING: can't stat() tmpfs file system /cow[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]      Output information may be incomplete.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ubuntu/.gvfs[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]      Output information may be incomplete.[/FONT][/COLOR]
```But golly gosh what do you know, I've just cracked the 100th post on ubuntuforums where far more proficient IT / computer minds than I"ll ever have, have no answers. 

It seems to me, and ABSOLUTELY NOT criticising the users (I"m contributing no answers, obviously), but it seems to me....that this is a pecularity that is too consistent :confused:

---

