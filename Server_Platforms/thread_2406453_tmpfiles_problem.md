---
title: "tmpfiles problem"
date: 2018-11-21
forum: Server Platforms
---

### Post by loki2100 on 2018-11-21
After last update there is become a problem: systemd-tmpfiles not starts (so there is no temp dirs and some services can't be started).

```
root@myserver:/# journalctl -b 0 -u systemd-tmpfiles-setup.service
-- Logs begin at &#1057;&#1088; 2018-11-21 01:00:51 MSK, end at &#1057;&#1088; 2018-11-21 11:45:01 MSK. --
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd[1]: Starting Create Volatile Files and Directories...
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/log, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/lib, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/sendsigs.omit.d, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/lock/subsys, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/lock/lvm, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/lvm, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/cache, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/cache/man, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/php, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/rpcbind, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/rpcbind/rpcbind.xdr, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/rpcbind/portmap.xdr, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/samba, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/run/screen, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/run/sshd, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/run/sudo, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/run/sudo/ts, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/nologin, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/user, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/utmp, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/systemd/ask-password, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/systemd/seats, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/systemd/sessions, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/systemd/users, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/systemd/machines, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/systemd/shutdown, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/systemd/netif, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/systemd/netif/links, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/systemd/netif/leases, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /run/log, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/lib/systemd, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/lib/systemd/coredump, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/log/wtmp, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd-tmpfiles[1040]: Unsafe symlinks encountered in /var/log/btmp, refusing.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd[1]: systemd-tmpfiles-setup.service: Main process exited, code=exited, status=1/FAILURE
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd[1]: Failed to start Create Volatile Files and Directories.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd[1]: systemd-tmpfiles-setup.service: Unit entered failed state.
&#1085;&#1086;&#1103; 21 01:01:04 myserver systemd[1]: systemd-tmpfiles-setup.service: Failed with result 'exit-code'.
```

I was trying to run separate config files
```
root@myserver:/# systemd-tmpfiles --create /usr/lib/tmpfiles.d/sshd.conf
Unsafe symlinks encountered in /var/run/sshd, refusing.
```
/var/run/sshd is empty. There is no symlinks at all.

I've no idea what its means and how to fix it. So I will be glad to any advice.

```
root@myserver:/# uname -a
Linux myserver 4.4.0-139-generic #165-Ubuntu SMP Wed Oct 24 10:58:50 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by loki2100 on 2018-11-21
Well. Problem is the root folder has user as an owner.
```
root@myserver:~# stat -c "%U %G" /
user user
```
Solution is:
```
root@myserver:~# chown root:root /
root@myserver:~# stat -c "%U %G" /
root root

root@myserver:~# systemctl start systemd-tmpfiles-setup
root@myserver:~#

```

---

### Post by howefield on 2018-11-21
Thread moved to the "*Server Platforms*" forum.

Congrats on solving.

---

### Post by mystadm on 2018-12-18
Any chance you might share how you got from point A  to point B here. I encountered the same issue and while glad for the fix do not understand how you identified that problem.. or was it a lucky catch?

---

### Post by xdracco on 2019-01-31
> **mystadm said:**
> Any chance you might share how you got from point A  to point B here. I encountered the same issue and while glad for the fix do not understand how you identified that problem.. or was it a lucky catch?

for me, it was not root dir that had incorrect ownership permission, rather it was /var/lib. It was owned by user dhcpd.

very much agree. would be nice to learn how they managed to figure it out. either way, thank you for the solution.

---

### Post by richud on 2019-02-25
amazing , non root ownership of root / was cause of my problem with php-fpm having died and not restarting. How on earth did that happen??

php-fpm7.2[15693]: [25-Feb-2019 15:50:55] ERROR: unable to bind listening socket for address '/run/php/php7.2-fpm.sock': No such file or directory


$ ll
total 2097264
drwxrwxr-x  24   1002     1001       4096 Feb 17 20:27 ./
drwxrwxr-x  24   1002     1001       4096 Feb 17 20:27 ../
drwxr-xr-x   2 root   root           4096 Feb 19 06:32 bin/
drwxr-xr-x   3 root   root           4096 Feb 19 06:32 boot/
...

---

### Post by hacksaw-hacksaw on 2019-09-02
I just had this problem, but the affected directory was /run, which was suddenly owned by clamav. Thanks for the solution, now to check on clamav...

---

