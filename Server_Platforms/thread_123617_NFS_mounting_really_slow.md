---
title: "NFS mounting really slow"
date: 2006-01-30
forum: Server Platforms
---

### Post by djvishnu on 2006-01-30
I am trying to set up NFS on my ubuntu box, but i'm running into problems. I have followed various howtos and got it up and running, but when i mount from my ubuntu desktop pc, it uses about 3-4 minutes (at least) to do a successful mount! I googled a bit and found out that nfs should mount instantaiously, which confirms that i have a problem..

I have read that others have had the same problem, but i havent been able to find any solution that works for me.

Here is my configuration (server: 10.0.0.9, client: 10.0.0.99):

Packages installed:
```
0 vishnu@odin:~> dpkg -l | grep nfs
ii  libnfsidmap1                           0.8-1                      An nfs idmapping library
ii  nfs-common                             1.0.7-3ubuntu1             NFS support files common to client and serve
ii  nfs-kernel-server                      1.0.7-3ubuntu1             Kernel NFS server support

```

/etc/hosts.*:
```
0 vishnu@odin:~> cat /etc/hosts.allow
portmap: 10.0.0.99
lockd: 10.0.0.99
rquotad: 10.0.0.99
mountd: 10.0.0.99
statd: 10.0.0.99
nfs: 10.0.0.99

0 vishnu@odin:~> cat /etc/hosts.deny
portmap:ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL
nfs:ALL

```

/etc/exports
```
0 vishnu@odin:~> cat /etc/exports
/media/download 10.0.0.99(rw,async)

```

Portmap running:```
0 vishnu@odin:~> ps aux | grep portmap
daemon    5011  0.0  0.3   1656   564 ?        Ss   20:52   0:00 /sbin/portmap

```

One of the howtos (for ubuntu) said i had to edit /etc/default/portmap and remove "-i 127.0.0.1" from ARGS to enable others to connect, but as you can se below there is no ARGS in the portmap file. And since i have edited hosts.allow and host.deny, connections apparently are getting through. I dont really know what this portmap file does. here it is:

/etc/default/portmap
```
 0 vishnu@odin:~> cat /etc/default/portmap
# By default, listen only on the loopback interface
OPTIONS=""

```

This is how i try to connect to the NFS share:
```
 sudo mount -t nfs 10.0.0.9:/media/download /media/download
```
(the paths are the same on both machines)


I have read that there are some things that can create such problems: DNS errors (whitch i have no i idea on how to idetify or fix), Portmap not running (the fallback method for nfs apparently is really slow..but i believe my portmap is running)

Finally i attach syslog and daemon.log entries from when i connect:
```
Jan 30 20:53:15 localhost mountd[5083]: authenticated mount request from 10.0.0.99:1021 for /media/download (/media/download)
```
(from the server side, the log files says exactly the same)

I really need this up and running properly, any help would be greatly appreceated!

Thanks!

---

### Post by gruepig on 2006-02-01
What's the output of 'rpcinfo -p 10.0.0.9' run from the client machine?

---

### Post by djvishnu on 2006-02-01
This is what rpcinfo -p 10.0.0.9 outputs:
```
0 vishnu@vishnu:~> rpcinfo -p 10.0.0.9
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp   1024  nlockmgr
    100021    3   udp   1024  nlockmgr
    100021    4   udp   1024  nlockmgr
    100021    1   tcp   1025  nlockmgr
    100021    3   tcp   1025  nlockmgr
    100021    4   tcp   1025  nlockmgr
    100005    1   udp    963  mountd
    100005    1   tcp    966  mountd
    100005    2   udp    963  mountd
    100005    2   tcp    966  mountd
    100005    3   udp    963  mountd
    100005    3   tcp    966  mountd
    100024    1   udp   1004  status
    100024    1   tcp   1007  status
```

---

### Post by habals on 2006-02-25
You need to install package 'portmap'
It will fly.

---

### Post by mous on 2006-03-05
hi!

you need to disable locking. you might do this from the mount-command line, or put it in /etc/fstab:

192.168.66.1:/home      /home   nfs      rw,suid,dev,exec,auto,nouser,async,nolock  0   0

this way i can simply say mount /home
if you don't want to mount this share automatically, add noauto to the options.

hope this helps!

g mous

---

### Post by phentex on 2006-03-09
Hi there,

got the same problem, everything works perfectly well except it's slooww mounting the remote file systems.

On the client side, just do as if you were willing to share directories via the gnome "shared files" graphical frontend. You know the first time you access it, it asks if nfs and/or smb packages are to be installed. Just tick the nfs packages, and let them get installed. Then it all works fine ;)

cheers

---

### Post by patrick295767 on 2006-05-07
[http://ubuntuforums.org/showthread.php?p=992825#post992825](http://ubuntuforums.org/showthread.php?p=992825#post992825)

---

### Post by Zorro on 2006-05-08
as habals suggested.. apt-get portmap.. I had the very same issue... when i installed it.. not a prob... ;)

---

