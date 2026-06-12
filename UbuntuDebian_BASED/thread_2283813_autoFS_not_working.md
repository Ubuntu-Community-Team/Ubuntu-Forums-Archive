---
title: "autoFS not working"
date: 2015-06-24
forum: Ubuntu/Debian BASED
---

### Post by mat25 on 2015-06-24
Hey automount is not working here. Here is my log when I do automount -f -d

```
Starting automounter version 5.0.7, master map /etc/auto.masterusing kernel protocol version 5.02
lookup_nss_read_master: reading master file /etc/auto.master
parse_init: parse(sun): init gathered global options: (null)
spawn_mount: mtab link detected, passing -n to mount
spawn_umount: mtab link detected, passing -n to mount
lookup_read_master: lookup(file): read entry /ftp
lookup_read_master: lookup(file): read entry +dir:/etc/auto.master.d
lookup_nss_read_master: reading master dir /etc/auto.master.d
lookup(dir): dir map /etc/auto.master.d missing or not readable
lookup(file): failed to read included master map dir:/etc/auto.master.d
lookup_read_master: lookup(file): read entry +auto.master
lookup_nss_read_master: reading master files auto.master
parse_init: parse(sun): init gathered global options: (null)
lookup(file): failed to read included master map auto.master
master_do_mount: mounting /ftp
automount_path_to_fifo: fifo name /var/run/autofs.fifo-ftp
lookup_nss_read_map: reading map file /etc/auto.ftp
parse_init: parse(sun): init gathered global options: (null)
spawn_mount: mtab link detected, passing -n to mount
spawn_umount: mtab link detected, passing -n to mount
remount_active_mount: trying to re-connect to mount /ftp
mounted indirect on /ftp with timeout 60, freq 15 seconds
remount_active_mount: re-connected to mount /ftp
st_ready: st_ready(): state = 0 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983317104 path /ftp
expire_cleanup: got thid 1983317104 path /ftp stat 0
expire_cleanup: sigchld: exp 1983317104 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983317104 path /ftp
expire_cleanup: got thid 1983317104 path /ftp stat 0
expire_cleanup: sigchld: exp 1983317104 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983317104 path /ftp
expire_cleanup: got thid 1983317104 path /ftp stat 0
expire_cleanup: sigchld: exp 1983317104 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
pst_expire: state 1 path /ftp
expire_proc: exp_proc = 1983317104 path /ftp
expire_cleanup: got thid 1983317104 path /ftp stat 0
expire_cleanup: sigchld: exp 1983317104 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp

```

My auto.master
```
/ftp    /etc/auto.ftp    --timeout=60
+dir:/etc/auto.master.d
+auto.master

```

My auto.ftp
```
ftpserver    -fstype=curl,rw,allow_other,nodev,nonempty,noatime    :ftp\://myusername\:mypw\@myhost
```

Thank you for your effort.

---

### Post by Toz on 2015-06-24
The automounter will not understand "fstype=curl". Did you create the /sbin/mount.curl and /sbin/umount.curl files?

See:
- [https://wiki.archlinux.org/index.php/Autofs#Remote_FTP]("https://wiki.archlinux.org/index.php/Autofs#Remote_FTP")
- [http://gentoo-en.vfose.ru/wiki/Mounting_SFTP_and_FTP_shares]("http://gentoo-en.vfose.ru/wiki/Mounting_SFTP_and_FTP_shares")

---

### Post by mat25 on 2015-06-25
Yes I did and and checked them again.

---

### Post by Toz on 2015-06-25
Just setup remote ftp autofs on my system and ran into an issue. With "automount -v -f -d", I got:
> >> fuse: unknown option `-o'

So the info on the Arch wiki page is incorrect (for ubuntu). If you use the sample /sbin/mount.curl script from the gentoo wiki page:
```
#! /bin/sh
curlftpfs $1 $2 -o allow_other,disable_eprt $3
```
...it works.

---

### Post by mat25 on 2015-06-25
okay I use raspbian.. I don't know if this can be the problem. I joined this forum because I found many related autofs problems. I already did the change from gentoo.

---

### Post by Toz on 2015-06-25
I'm sorry but I don't have any experience with raspbian. The above _will_ work with Ubuntu though.

One other comment: how do you know that the mount isn't working? Do you get any error messages when you go to the mount directory? Have you tried with the "--ghost" option in auto.master?

---

### Post by howefield on 2015-06-25
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by mat25 on 2015-06-25
> **Toz said:**
> I'm sorry but I don't have any experience with raspbian. The above _will_ work with Ubuntu though.

One other comment: how do you know that the mount isn't working? Do you get any error messages when you go to the mount directory? Have you tried with the "--ghost" option in auto.master?
I don't see my added "ftpserver" map in /ftp, so I suppose it's not working?

---

### Post by Toz on 2015-06-25
Either add the "--ghost" option:
```
/ftp    /etc/auto.ftp    --timeout=60 --ghost
```
...to /etc/auto.master or from a terminal, list the contents blindly:
```
ls -l /ftp/ftpserver
```

The "ghost" option will display the mapped directory even if its not yet mounted. Otherwise, it is not displayed until mounted.

---

### Post by mat25 on 2015-06-25
Okay, I see the map, but can't open it ("no such file"). I don't find any errors in my logs. Are there no more debug options?

---

### Post by Toz on 2015-06-25
Try:
```
automount -v -f -d
```
...followed by:
```
ls -l /ftp/ftpserver
```

Post back what is displayed.

---

### Post by mat25 on 2015-06-25
```
root@raspberrypi:~# automount -v -f -dStarting automounter version 5.0.7, master map /etc/auto.master
using kernel protocol version 5.02
lookup_nss_read_master: reading master file /etc/auto.master
parse_init: parse(sun): init gathered global options: (null)
spawn_mount: mtab link detected, passing -n to mount
spawn_umount: mtab link detected, passing -n to mount
lookup_read_master: lookup(file): read entry /ftp
lookup_read_master: lookup(file): read entry +dir:/etc/auto.master.d
lookup_nss_read_master: reading master dir /etc/auto.master.d
lookup(dir): dir map /etc/auto.master.d missing or not readable
lookup(file): failed to read included master map dir:/etc/auto.master.d
lookup_read_master: lookup(file): read entry +auto.master
lookup_nss_read_master: reading master files auto.master
parse_init: parse(sun): init gathered global options: (null)
lookup(file): failed to read included master map auto.master
master_do_mount: mounting /ftp
automount_path_to_fifo: fifo name /var/run/autofs.fifo-ftp
lookup_nss_read_map: reading map file /etc/auto.ftp
parse_init: parse(sun): init gathered global options: (null)
spawn_mount: mtab link detected, passing -n to mount
spawn_umount: mtab link detected, passing -n to mount
mounted indirect on /ftp with timeout 60, freq 15 seconds
st_ready: st_ready(): state = 0 path /ftp
ghosting enabled
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
statemachine:1363: got unexpected signal 28!
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
st_expire: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /ftp
^Cdo_notify_state: signal 2
master_notify_state_change: sig 2 switching /ftp from 1 to 5
st_prepare_shutdown: state 1 path /ftp
expire_proc: exp_proc = 1983132784 path /ftp
expire_cleanup: got thid 1983132784 path /ftp stat 0
expire_cleanup: sigchld: exp 1983132784 finished, switching from 5 to 7
st_shutdown: state 5 path /ftp
umount_multi: path /ftp incl 0
rm_unwanted_fn: removing directory /ftp/ftpserver
umounted indirect mount /ftp
automount_path_to_fifo: fifo name /var/run/autofs.fifo-ftp
shut down path /ftp
autofs stopped

```

```
root@raspberrypi:/ftp# dir
ftpserver
root@raspberrypi:/ftp# ls -l /ftp/ftpserver
ls: kan map /ftp/ftpserver niet openen: Bestand of map bestaat niet
root@raspberrypi:/ftp#

```
file or map doesn't exist..

---

### Post by Toz on 2015-06-25
Halfway through your log file, you get:
> statemachine:1363: got unexpected signal 28!
I've googled this error message but haven't found anything yet. I don't get this message on my system.

It would be interesting if you could determine if this error gets generated when you "ls -l /ftp/ftpserver".

EDIT: One other thing to try is to mount the ftp share manually via:
```
curlftpfs ftpserver /ftp/ftpserver -ouser=user:password,allow_other
```
...and see if it works.

---

### Post by mat25 on 2015-06-26
The manual mount just works, but I'm one step further now because I added the map ftpserver in /ftp and now I see errors

```
handle_packet: type = 3handle_packet_missing_indirect: token 1, name ftpserver, request pid 3049
attempting to mount entry /ftp/ftpserver
lookup_mount: lookup(file): looking up ftpserver
lookup_mount: lookup(file): ftpserver -> -fstype=curl,rw,allow_other,nodev,nonempty,noatime     :ftp\://user\:pw\@hosturl/
parse_mount: parse(sun): expanded entry: -fstype=curl,rw,allow_other,nodev,nonempty,noatime     :ftp\://user\:pw\@hosturl/
parse_mount: parse(sun): gathered options: fstype=curl,rw,allow_other,nodev,nonempty,noatime
parse_mount: parse(sun): dequote(":ftp\://user\:pw\@hosturl/") -> ftp://user:pw@hosturl/
parse_mount: parse(sun): core of entry: options=fstype=curl,rw,allow_other,nodev,nonempty,noatime, loc=:ftp\://user\:pw\@hosturl/
sun_mount: parse(sun): mounting root /ftp, mountpoint ftpserver, what :ftp\://user\:pw\@hosturl/, fstype curl, options rw,allow_other,nodev,nonempty,noatime
do_mount: ftp://user:pw@hosturl/ /ftp/ftpserver type curl options rw,allow_other,nodev,nonempty,noatime using module generic
mount_mount: mount(generic): calling mkdir_path /ftp/ftpserver
mount_mount: mount(generic): calling mount -t curl -s -o rw,allow_other,nodev,nonempty,noatime ftp://user:pw@hosturl// /ftp/ftpserver
spawn_mount: mtab link detected, passing -n to mount
>> fuse: unknown option `-n'
mount(generic): failed to mount ftp://user:pw@hosturl/ (type curl) on /ftp/ftpserver
dev_ioctl_send_fail: token = 1
failed to mount /ftp/ftpserver



```

---

### Post by Toz on 2015-06-26
> >> fuse: unknown option `-n'
mount(generic): failed to mount [ftp://user:pw@hosturl/](ftp://user:pw@hosturl/) (type curl) on /ftp/ftpserver
What versions of fuse and curlftpfs do you have installed?

---

### Post by mat25 on 2015-06-26
Both the latest ones, because I coudn't upgrade them anymore.

---

### Post by Toz on 2015-06-26
But what version numbers?
Try:
```
apt-cache policy fuse
apt-cache policy curlftpfs
```

---

### Post by mat25 on 2015-06-26
fuse: 2.9.0-2+deb7u2
curlftpfs: 0.9.2-5

---

### Post by Toz on 2015-06-26
I'm sorry but I can't seem to find anything directly relevant to your situation. From what I understand, if autofs sees that /etc/mtab is a symlink, it passes the "-n" parameter to fuse, but fuse is choking on it. Since its not happening on regular Ubuntu, it must be somehow related to the raspbian install you have. More than that I do not know. 
Perhaps you should file a bug report.

---

### Post by mat25 on 2015-06-27
ok, the reason why I want to use autoFS is because my mounting with fstab didn't work very well. Problem with fstab is that it mounts on boot while my OpenVPN isn't ready yet (so no connection). Maybe it's easier for me to fix this problem.

---

