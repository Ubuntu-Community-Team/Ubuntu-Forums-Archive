---
title: "nfsd failes to start"
date: 2009-12-28
forum: Server Platforms
---

### Post by olejl on 2009-12-28
Hi
I am having some problems starting nfsd. Here are some information:

```

$ cat /etc/exports
/media/music 192.168.0.0/24(rw,no_root_squash,async,no_subtree_check)
/media/recording 192.168.0.0/24(rw,no_root_squash,async,no_subtree_check)
/media/movie 192.168.0.0/24(rw,no_root_squash,async,no_subtree_check)

$ sudo /etc/init.d/nfs-kernel-server start
 * Exporting directories for NFS kernel daemon... [ OK ] 
 * Starting NFS kernel daemon                           [fail]

$ sudo /etc/init.d/nfs-kernel-server status
nfsd not running

$ cat /var/log/daemon.log | grep nfs
...
Dec 28 23:02:07 mythbackend portmap[7168]: connect from 192.168.0.3 to unset(nfs): request from non-local host
Dec 28 23:02:07 mythbackend portmap[7169]: connect from 192.168.0.3 to unset(nfs): request from non-local host
Dec 28 23:02:07 mythbackend portmap[7170]: connect from 192.168.0.3 to unset(nfs): request from non-local host
Dec 28 23:02:07 mythbackend nfsd[7167]: nfssvc: writing fds to kernel failed: errno 13 (Permission denied)
Dec 28 23:02:07 mythbackend nfsd[7167]: nfssvc: writing fds to kernel failed: errno 13 (Permission denied)
Dec 28 23:02:07 mythbackend portmap[7186]: connect from 192.168.0.3 to unset(nfs): request from non-local host
Dec 28 23:02:07 mythbackend portmap[7187]: connect from 192.168.0.3 to unset(nfs): request from non-local host
Dec 28 23:02:07 mythbackend portmap[7188]: connect from 192.168.0.3 to unset(nfs): request from non-local host
Dec 28 23:02:07 mythbackend nfsd[7167]: nfssvc: Address already in use

```Does anyone have an idea of what could be wrong?

---

### Post by Thocrun on 2009-12-28
sounds like this problem : [**NFS crash and results - rpc.statd won't start??**]("http://ubuntuforums.org/showthread.php?t=629780")

---

