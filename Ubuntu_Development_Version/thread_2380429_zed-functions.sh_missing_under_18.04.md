---
title: "zed-functions.sh missing under 18.04"
date: 2017-12-17
forum: Ubuntu Development Version
---

### Post by w00sterf1 on 2017-12-17
I'm running 18.04 in Virtualbox with a ZFS setup, running both / and user filesystems as ZFS filesystems.  
  
I stated seeing the zed process running at 100% cpu:
```
ps -ef | grep zed
root     10346     1 99 12:13 ?        00:05:12 /usr/sbin/zed -F

```

I then checked to see what it was doing:
```
# systemctl status zfs-zed.service
&#9679; zfs-zed.service - ZFS Event Daemon (zed)
   Loaded: loaded (/lib/systemd/system/zfs-zed.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2017-12-17 12:13:06 EST; 6min ago
     Docs: man:zed(8)
 Main PID: 10346 (zed)
    Tasks: 1 (limit: 4915)
   CGroup: /zfs-zed.service
           &#9492;&#9472;10346 /usr/sbin/zed -F


Dec 17 12:13:06 Benny-Hill systemd[1]: Started ZFS Event Daemon (zed).
Dec 17 12:13:06 Benny-Hill zed[10346]: Failed to stat "/etc/zfs/zed.d/zed-functions.sh": No such file or directory
Dec 17 12:13:06 Benny-Hill zed[10346]: ZFS Event Daemon 0.6.5.11-1ubuntu5 (PID 10346)
Dec 17 12:13:06 Benny-Hill zed[10346]: Processing events since eid=0



```

Now, what hit me was the following line:
```

 Dec 17 12:13:06 Benny-Hill zed[10346]: Failed to stat "/etc/zfs/zed.d/zed-functions.sh": No such file or directory
```

I then checked to see if the file existed:
```
# ls -l /etc/zfs/zed.d
total 18
lrwxrwxrwx 1 root root    49 Nov 16 17:01 all-syslog.sh -> /usr/lib/x86_64-linux-gnu/zfs/zed.d/all-syslog.sh
lrwxrwxrwx 1 root root    54 Nov 16 17:01 checksum-notify.sh -> /usr/lib/x86_64-linux-gnu/zfs/zed.d/checksum-notify.sh
lrwxrwxrwx 1 root root    53 Nov 16 17:01 checksum-spare.sh -> /usr/lib/x86_64-linux-gnu/zfs/zed.d/checksum-spare.sh
lrwxrwxrwx 1 root root    50 Nov 16 17:01 data-notify.sh -> /usr/lib/x86_64-linux-gnu/zfs/zed.d/data-notify.sh
lrwxrwxrwx 1 root root    48 Nov 16 17:01 io-notify.sh -> /usr/lib/x86_64-linux-gnu/zfs/zed.d/io-notify.sh
lrwxrwxrwx 1 root root    47 Nov 16 17:01 io-spare.sh -> /usr/lib/x86_64-linux-gnu/zfs/zed.d/io-spare.sh
lrwxrwxrwx 1 root root    61 Nov 16 17:01 resilver.finish-notify.sh -> /usr/lib/x86_64-linux-gnu/zfs/zed.d/resilver.finish-notify.sh
lrwxrwxrwx 1 root root    58 Nov 16 17:01 scrub.finish-notify.sh -> /usr/lib/x86_64-linux-gnu/zfs/zed.d/scrub.finish-notify.sh
lrwxrwxrwx 1 root root    45 May 22  2017 zed-functions.sh -> /usr/lib/zfs-linux/zfs/zed.d/zed-functions.sh
-rw-r--r-- 1 root root 11003 Nov 16 17:01 zed-functions.sh.dpkg-new
-rw-r--r-- 1 root root  2554 Aug 22  2016 zed.rc

```


The name is a link:  
```

  lrwxrwxrwx 1 root root    45 May 22  2017 zed-functions.sh -> /usr/lib/zfs-linux/zfs/zed.d/zed-functions.sh
```
and the link does not exist:
```
root@Benny-Hill:~# ls -l /usr/lib/zfs-linux/zfs/zed.d/zed-functions.sh
ls: cannot access '/usr/lib/zfs-linux/zfs/zed.d/zed-functions.sh': No such file or directory
root@Benny-Hill:~# ls -l /usr/lib/zfs-linux/zfs/zed.d
ls: cannot access '/usr/lib/zfs-linux/zfs/zed.d': No such file or directory
root@Benny-Hill:~# ls -l /usr/lib/zfs-linux/zfs
ls: cannot access '/usr/lib/zfs-linux/zfs': No such file or directory

```

There is however, a file that seems to be the one missing:
```
-rw-r--r-- 1 root root 11003 Nov 16 17:01 zed-functions.sh.dpkg-new

```


which again looks like a file from a botched update. Why it was botched, I can not tell nor can I tell if the file is supposed to overwrite the previously existing link or if it was supposed to go into the /usr/lib/zfs/zed.d directory.

Anyone else seen anything similar? Btw, the installation is up to date per today.

The problem was fixed by moving the  zed-functions.sh.dpkg-new to zed-functions.sh and restarting the zed service:
```
root@Benny-Hill:/etc/zfs/zed.d# systemctl restart zfs-zed.service
root@Benny-Hill:/etc/zfs/zed.d# systemctl status zfs-zed.service
&#9679; zfs-zed.service - ZFS Event Daemon (zed)
   Loaded: loaded (/lib/systemd/system/zfs-zed.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2017-12-17 12:38:43 EST; 3s ago
     Docs: man:zed(8)
 Main PID: 9387 (zed)
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/zfs-zed.service
           &#9492;&#9472;9387 /usr/sbin/zed -F


Dec 17 12:38:43 Benny-Hill systemd[1]: Stopping ZFS Event Daemon (zed)...
Dec 17 12:38:43 Benny-Hill zed[9387]: ZFS Event Daemon 0.6.5.11-1ubuntu5 (PID 9387)
Dec 17 12:38:43 Benny-Hill zed[9387]: Processing events since eid=0
Dec 17 12:38:43 Benny-Hill systemd[1]: Stopped ZFS Event Daemon (zed).
Dec 17 12:38:43 Benny-Hill systemd[1]: Started ZFS Event Daemon (zed).



```

Bottom line is whether a botch upgrade at some point has messed it up or if there has been a change in locations of the files and the upgrade scripts in the packages have not been able to handle it. Anyone who can tell?

---

