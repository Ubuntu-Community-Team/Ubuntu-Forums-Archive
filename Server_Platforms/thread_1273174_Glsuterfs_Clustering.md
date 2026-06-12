---
title: "Glsuterfs Clustering"
date: 2009-09-23
forum: Server Platforms
---

### Post by star3am on 2009-09-23
Hi everyone, I could not find a forum for glusterfs, so I thought I'd start a thread here. 

I am using glusterfs + xen + centos - but it should work fine on *nix

glusterfs is storing my Xen images, my glusterfs currently consists of 4 nodes, soon to become 6, using cluster/distribute and cluster/replicate translators. 

I'm using xen for my VMs, cool, let's start, 

my glusterfs setup can be visualized as, 
[IMG]http://www.riaannolan.com/wp-content/uploads/2009/09/gluster_network_usage.png[/IMG]

my glusterfsd.vol config looks like, 
```
volume posix
  type storage/posix
  option directory /data/export
end-volume

volume locks
  type features/locks
  subvolumes posix
end-volume

volume brick
  type performance/io-threads
  option thread-count 8
  subvolumes locks
end-volume

volume server
  type protocol/server
  option transport-type tcp
  option auth.addr.brick.allow *
  subvolumes brick
end-volume

```

my glusterfs.vol config looks like, 
```
volume node1
  type protocol/client
  option transport-type tcp
  option remote-host node1.domain
  option remote-subvolume brick
end-volume

volume node2
  type protocol/client
  option transport-type tcp
  option remote-host node2.domain
  option remote-subvolume brick
end-volume

volume node3
  type protocol/client
  option transport-type tcp
  option remote-host node3.domain
  option remote-subvolume brick
end-volume

volume node4
  type protocol/client
  option transport-type tcp
  option remote-host node4.domain
  option remote-subvolume brick
end-volume

volume replicate1
  type cluster/replicate
  subvolumes node1 node2
end-volume

volume replicate2
  type cluster/replicate
  subvolumes node3 node4
end-volume

volume distribute
  type cluster/distribute
  subvolumes replicate1 replicate2
end-volume

volume readahead
  type performance/read-ahead
  option page-size 2MB              # unit in bytes
  option page-count 16              # cache per file  = (page-count x page-size)
  subvolumes distribute
end-volume

volume writebehind
  type performance/write-behind
  option window-size 16MB
  subvolumes distribute
end-volume

volume cache
  type performance/io-cache
  option cache-size 512MB
  subvolumes writebehind
end-volume
```

currently I am running, +/- 20 Xen VMs (Windows & Linux) on top of glusterfs with 4 xen servers to manage the VMs from, 

by far the least trouble I have had is with Linux, windows crashed always, but with a bit of sweet talk i generally get windows to the bedroom, 

tools I recommend is, 

- glusterfs
- iftop 
- cacti + some sort of weathermap
- xen
- ntfsprogs
- kpartx
- util-linux (for losetup etc.)

I get pretty decent network performance, 
[IMG]http://www.riaannolan.com/wp-content/uploads/2009/09/gluster_node_eth0.png[/IMG]

so i am pretty happy with gluster and xen thus far, mainly my problem is with NTFS!!! and Windows, yum package manager, and the lack of updates, Ubuntu and Gentoo is always up to date with versions :D but then again, i think portage is the awesomeness!!

my current Xen setup can be visualized like so, 
[IMG]http://www.riaannolan.com/wp-content/uploads/2009/09/weathermap.png[/IMG]

I am seeing a few issues, nothing major, that glusterfs does not share the data evenly across the 2 pair of nodes, rather replicate1 is being used less than replicate2 to the tune of,
[IMG]http://www.riaannolan.com/wp-content/uploads/2009/09/gluster_data_shares.png[/IMG]

but other than that, it's all systems GO !!

I'll update this post as I move along, 

ciao/Riaan

---

### Post by samppah on 2009-09-25
Good to hear that you have got it working. I'm still planning same kind system myself and I'd like to know how big hard disks you are using in DomUs? And how is the performance?

---

### Post by star3am on 2009-09-27
> I'd like to know how big hard disks you are using in DomUs? And how is the performance?

I use a mixed OS, Windows and Linux, the VMs are anything from 5G upwards, with 40G being the biggest. Performance is good, I find that on some Xen srvs the virsh create | xm create commands take unusually long sometimes, whilst the Dom0 is copying data from the glusterfs, other than that, I'm pretty happy

---

### Post by star3am on 2009-11-13
Just an update, ran into a bug with mounting glusterfs within a Xen VM running ontop of glusterfs, 

I have 4 gluster (2.0.6-1.el5) nodes, cluster/replicate 2x2 &
cluster/distribute 2

I have a Xen VM who's Image is hosted on the GlusterFS, 
Inside the VM I installed glusterfs (2.0.8-1) 

#/etc/fstab
/etc/glusterfs/glusterfs.vol  /mnt  glusterfs  defaults,direct-io-mode=disable 
0  0

#grep gluster /proc/mounts 
glusterfs#/etc/glusterfs/glusterfs.vol /mnt fuse
rw,user_id=0,group_id=0,default_permissions,allow_other,max_read=131072 0 0

#ls /mnt/ 
this command hangs .. strace reports, 
lstat("/mnt/ools", 0x2ae537bf4858) = -1 ENOENT (No such file or
directory)
getdents(3, /* 1 entries */, 32768)     = 24
lstat("/mnt/ools", 0x2ae537bf4918) = -1 ENOENT (No such file or
directory)
getdents(3, /* 1 entries */, 32768)     = 24
lstat("/mnt/ools", 0x2ae537bf49d8) = -1 ENOENT (No such file or
directory)
getdents(3, /* 1 entries */, 32768)     = 24
lstat("/mnt/ools", 0x2ae537bf4a98) = -1 ENOENT (No such file or
directory)

###############

Then inside the VM I unmount glusterfs, uninstall it, installe glusterfs
(2.0.7-1) 

#mount -a

now I can use the glusterfs within the VM

#ls /mnt
tools  vm

see with (2.0.8-1) it reported ools not found, ools, does not exist but tools
does,

Link to Gluster bug page
[http://bugs.gluster.com/cgi-bin/bugzilla3/show_bug.cgi?id=379](http://bugs.gluster.com/cgi-bin/bugzilla3/show_bug.cgi?id=379)

---

### Post by roland23 on 2009-12-02
hi, i have seen your post and it looks like very interesting. we use nearly the same scenario. 2 Glusterfs server and 2 xen server. but i have always problems if domU is stored on glusterfs and one glusterfs server goes down. (failover doesnt work.

we use xen-version 3.4.1
and glusterfs 2.0.8

config is the same as yours.

did you ever try a failover with glusterfs, xen and domU. 


Please contact me i need please more information about glusterfs - xen - domU - failover.

Thank you very much
r23

---

### Post by star3am on 2010-01-08
busy testing glusterfs version 3.0.0-1

I am having some problems, more specifically, 

making some progress, here is more log,

**$ mount -a**
**$ df -h**
Filesystem            Size  Used Avail Use% Mounted on
glusterfs#/etc/glusterfs/glusterfs.vol
                      524G  1.9G  495G   1% /opt/domain/mnt

**$ mount**
glusterfs#/etc/glusterfs/glusterfs.vol on /opt/domain/mnt type fuse (rw,allow_other,default_permissions,max_read=131072)

**$ tail -f /var/log/glusterfs/opt-domain-mnt.log**
[2010-01-08 11:37:47] N [glusterfsd.c:1361:main] glusterfs: Successfully started
[2010-01-08 11:37:47] N [client-protocol.c:6224:client_setvolume_cbk] ke-phy-xensrv002.domain.co.ke-1: Connected to 192.168.13.204:6996, attached to remote volume 'brick1'.
[2010-01-08 11:37:47] N [afr.c:2625:notify] mirror-0: Subvolume 'ke-phy-xensrv002.domain.co.ke-1' came back up; going online.
[2010-01-08 11:37:47] N [client-protocol.c:6224:client_setvolume_cbk] ke-phy-xensrv002.domain.co.ke-1: Connected to 192.168.13.204:6996, attached to remote volume 'brick1'.
[2010-01-08 11:37:47] N [afr.c:2625:notify] mirror-0: Subvolume 'ke-phy-xensrv002.domain.co.ke-1' came back up; going online.
[2010-01-08 11:37:47] N [fuse-bridge.c:2931:fuse_init] glusterfs-fuse: FUSE inited with protocol versions: glusterfs 7.13 kernel 7.10
[2010-01-08 11:37:47] E [dict.c:2396:dict_unserialize] dict: count (-2147483648) <= 0
[2010-01-08 11:37:47] E [dict.c:2396:dict_unserialize] dict: count (-2147483648) <= 0
[2010-01-08 11:37:58] E [client-protocol.c:6187:client_setvolume_cbk] ke-phy-xensrv001.domain.co.ke-1: SETVOLUME on remote-host failed: Invalid argument
[2010-01-08 11:37:58] E [dict.c:2396:dict_unserialize] dict: count (-1597773039) <= 0
[2010-01-08 11:38:09] E [dict.c:2396:dict_unserialize] dict: count (-2010475122) <= 0
pending frames:

patchset: 2.0.1-886-g8379edd
signal received: 11
time of crash: 2010-01-08 11:38:09
configuration details:
argp 1
backtrace 1
dlfcn 1
fdatasync 1
libpthread 1
llistxattr 1
setfsid 1
spinlock 1
epoll.h 1
xattr.h 1
st_atim.tv_nsec 1
package-string: glusterfs 3.0.0
/lib64/libc.so.6[0x348e6302d0]
/usr/lib64/libglusterfs.so.0(dict_unserialize+0x2e4)[0x3584211999]
/usr/lib64/glusterfs/3.0.0/xlator/protocol/client.so(client_setvolume_cbk+0x224)[0x2ac1c0175645]
/usr/lib64/glusterfs/3.0.0/xlator/protocol/client.so(protocol_client_interpret+0x25e)[0x2ac1c017609d]
/usr/lib64/glusterfs/3.0.0/xlator/protocol/client.so(protocol_client_pollin+0xb0)[0x2ac1c0176cd3]
/usr/lib64/glusterfs/3.0.0/xlator/protocol/client.so(notify+0x16c)[0x2ac1c017734a]
/usr/lib64/libglusterfs.so.0(xlator_notify+0xf5)[0x358421859b]
/usr/lib64/glusterfs/3.0.0/transport/socket.so(socket_event_poll_in+0x40)[0x2aaaaab1cd9a]
/usr/lib64/glusterfs/3.0.0/transport/socket.so(socket_event_handler+0xb7)[0x2aaaaab1d08f]
/usr/lib64/libglusterfs.so.0[0x358423d185]
/usr/lib64/libglusterfs.so.0[0x358423d35a]
/usr/lib64/libglusterfs.so.0(event_dispatch+0x73)[0x358423d670]
/usr/sbin/glusterfs(main+0xe88)[0x405e10]
/lib64/libc.so.6(__libc_start_main+0xf4)[0x348e61d994]
/usr/sbin/glusterfs[0x4025d9]
---------

... continued ...

hallo GlusterFS list, happy new year

I am busy checking out GlusterFS ver.3 - happily using ver.2.06 already and have no issues, however

with version 3, I get core dumps, here are some info, I hope will help you help me :)

**$ rpm -qa | grep gluster**

glusterfs-server-3.0.0-1
glusterfs-client-3.0.0-1
glusterfs-common-3.0.0-1

**$ cat /etc/glusterfs/glusterfs.vol**

## file auto generated by /usr/bin/glusterfs-volgen (mount.vol)
# Cmd line:
# $ /usr/bin/glusterfs-volgen --name store1 --raid 1 ke-phy-xensrv001.domain.co.ke:/data/export ke-phy-xensrv002.domain.co.ke:/data/export

# RAID 1
# TRANSPORT-TYPE tcp
volume ke-phy-xensrv002.domain.co.ke-1
    type protocol/client
    option transport-type tcp
    option remote-host ke-phy-xensrv002.domain.co.ke
    option transport.socket.nodelay on
    option transport.remote-port 6996
    option remote-subvolume brick1
end-volume

volume ke-phy-xensrv001.domain.co.ke-1
    type protocol/client
    option transport-type tcp
    option remote-host ke-phy-xensrv001.domain.co.ke
    option transport.socket.nodelay on
    option transport.remote-port 6996
    option remote-subvolume brick1
end-volume

volume mirror-0
    type cluster/replicate
    subvolumes ke-phy-xensrv001.domain.co.ke-1 ke-phy-xensrv002.domain.co.ke-1
end-volume

volume writebehind
    type performance/write-behind
    option cache-size 4MB
    subvolumes mirror-0
end-volume

volume readahead
    type performance/read-ahead
    option page-count 4
    subvolumes writebehind
end-volume

volume iocache
    type performance/io-cache
    option cache-size 1GB
    option cache-timeout 1
    subvolumes readahead
end-volume

volume quickread
    type performance/quick-read
    option cache-timeout 1
    option max-file-size 64kB
    subvolumes iocache
end-volume

volume statprefetch
    type performance/stat-prefetch
    subvolumes quickread
end-volume

**$ cat /etc/glusterfs/glusterfsd.vol**

## file auto generated by /usr/bin/glusterfs-volgen (export.vol)
# Cmd line:
# $ /usr/bin/glusterfs-volgen --name store1 --raid 1 ke-phy-xensrv001.domain.co.ke:/data/export ke-phy-xensrv002.domain.co.ke:/data/export

volume posix1
  type storage/posix
  option directory /data/export
end-volume

volume locks1
    type features/locks
    subvolumes posix1
end-volume

volume brick1
    type performance/io-threads
    option thread-count 8
    subvolumes locks1
end-volume

volume server-tcp
    type protocol/server
    option transport-type tcp
    option auth.addr.brick1.allow *
    option transport.socket.listen-port 6996
    option transport.socket.nodelay on
    subvolumes brick1
end-volume

**$ /etc/init.d/glusterfsd restart**

Stopping glusterfsd: [  OK  ]
Starting glusterfsd: [  OK  ]

**$ cat /var/log/glusterfs/-etc-glusterfs-glusterfsd.vol.log**

================================================================================
Version      : glusterfs 3.0.0 built on Dec  8 2009 03:09:12
git: 2.0.1-886-g8379edd
Starting Time: 2010-01-06 14:51:23
Command line : /usr/sbin/glusterfsd -f /etc/glusterfs/glusterfsd.vol
PID          : 16033
System name  : Linux
Nodename     : ke-phy-xensrv002.domain.co.ke
Kernel Release : 2.6.18-164.6.1.el5xen
Hardware Identifier: x86_64

Given volfile:
+------------------------------------------------------------------------------+
  1: ## file auto generated by /usr/bin/glusterfs-volgen (export.vol)
  2: # Cmd line:
  3: # $ /usr/bin/glusterfs-volgen --name store1 --raid 1 ke-phy-xensrv001.domain.co.ke:/data/export ke-phy-xensrv002.domain.co.ke:/data/export
  4:
  5: volume posix1
  6:   type storage/posix
  7:   option directory /data/export
  8: end-volume
  9:
 10: volume locks1
 11:     type features/locks
 12:     subvolumes posix1
 13: end-volume
 14:
 15: volume brick1
 16:     type performance/io-threads
 17:     option thread-count 8
 18:     subvolumes locks1
 19: end-volume
 20:
 21: volume server-tcp
 22:     type protocol/server
 23:     option transport-type tcp
 24:     option auth.addr.brick1.allow *
 25:     option transport.socket.listen-port 6996
 26:     option transport.socket.nodelay on
 27:     subvolumes brick1
 28: end-volume
 29:

+------------------------------------------------------------------------------+
[2010-01-06 14:51:23] N [glusterfsd.c:1361:main] glusterfs: Successfully started

**$ mount -t glusterfs /etc/glusterfs/glusterfs.vol /opt/domain/mnt**
gives no output, apon doing df -h I get,

**$ df -h**
Filesystem            Size  Used Avail Use% Mounted on
df: `/opt/domain/mnt': Transport endpoint is not connected

**$ cat /var/log/glusterfs/opt-domain-mnt.log**

================================================================================
Version      : glusterfs 3.0.0 built on Dec  8 2009 03:09:12
git: 2.0.1-886-g8379edd
Starting Time: 2010-01-06 14:54:04
Command line : /usr/sbin/glusterfs --log-level=NORMAL --volfile=/etc/glusterfs/glusterfs.vol /opt/domain/mnt
PID          : 16101
System name  : Linux
Nodename     : ke-phy-xensrv002.domain.co.ke
Kernel Release : 2.6.18-164.6.1.el5xen
Hardware Identifier: x86_64

Given volfile:
+------------------------------------------------------------------------------+
  1: ## file auto generated by /usr/bin/glusterfs-volgen (mount.vol)
  2: # Cmd line:
  3: # $ /usr/bin/glusterfs-volgen --name store1 --raid 1 ke-phy-xensrv001.domain.co.ke:/data/export ke-phy-xensrv002.domain.co.ke:/data/export
  4:
  5: # RAID 1
  6: # TRANSPORT-TYPE tcp
  7: volume ke-phy-xensrv002.domain.co.ke-1
  8:     type protocol/client
  9:     option transport-type tcp
 10:     option remote-host ke-phy-xensrv002.domain.co.ke
 11:     option transport.socket.nodelay on
 12:     option transport.remote-port 6996
 13:     option remote-subvolume brick1
 14: end-volume
 15:
 16: volume ke-phy-xensrv001.domain.co.ke-1
 17:     type protocol/client
 18:     option transport-type tcp
 19:     option remote-host ke-phy-xensrv001.domain.co.ke
 20:     option transport.socket.nodelay on
 21:     option transport.remote-port 6996
 22:     option remote-subvolume brick1
 23: end-volume
 24:
 25: volume mirror-0
 26:     type cluster/replicate
 27:     subvolumes ke-phy-xensrv001.domain.co.ke-1 ke-phy-xensrv002.domain.co.ke-1
 28: end-volume
 29:
 30: volume writebehind
 31:     type performance/write-behind
 32:     option cache-size 4MB
 33:     subvolumes mirror-0
 34: end-volume
 35:
 36: volume readahead
 37:     type performance/read-ahead
 38:     option page-count 4
 39:     subvolumes writebehind
 40: end-volume
 41:
 42: volume iocache
 43:     type performance/io-cache
 44:     option cache-size 1GB
 45:     option cache-timeout 1
 46:     subvolumes readahead
 47: end-volume
 48:
 49: volume quickread
 50:     type performance/quick-read
 51:     option cache-timeout 1
 52:     option max-file-size 64kB
 53:     subvolumes iocache
 54: end-volume
 55:
 56: volume statprefetch
 57:     type performance/stat-prefetch
 58:     subvolumes quickread
 59: end-volume
 60:

+------------------------------------------------------------------------------+
[2010-01-06 14:54:04] W [xlator.c:655:validate_xlator_volume_options] ke-phy-xensrv001.domain.co.ke-1: option 'transport.remote-port' is deprecated, preferred is 'remote-port', continuing with correction
[2010-01-06 14:54:04] W [xlator.c:655:validate_xlator_volume_options] ke-phy-xensrv002.domain.co.ke-1: option 'transport.remote-port' is deprecated, preferred is 'remote-port', continuing with correction
[2010-01-06 14:54:04] N [glusterfsd.c:1361:main] glusterfs: Successfully started
pending frames:

patchset: 2.0.1-886-g8379edd
signal received: 11
time of crash: 2010-01-06 14:54:04
configuration details:
argp 1
backtrace 1
dlfcn 1
fdatasync 1
libpthread 1
llistxattr 1
setfsid 1
spinlock 1
epoll.h 1
xattr.h 1
st_atim.tv_nsec 1
package-string: glusterfs 3.0.0
/lib64/libc.so.6[0x348e6302d0]
/usr/lib64/libglusterfs.so.0(dict_unserialize+0x2e4)[0x2ac1a48fb999]
/usr/lib64/glusterfs/3.0.0/xlator/protocol/client.so(client_setvolume_cbk+0x224)[0x2ac1a53dc645]
/usr/lib64/glusterfs/3.0.0/xlator/protocol/client.so(protocol_client_interpret+0x25e)[0x2ac1a53dd09d]
/usr/lib64/glusterfs/3.0.0/xlator/protocol/client.so(protocol_client_pollin+0xb0)[0x2ac1a53ddcd3]
/usr/lib64/glusterfs/3.0.0/xlator/protocol/client.so(notify+0x16c)[0x2ac1a53de34a]
/usr/lib64/libglusterfs.so.0(xlator_notify+0xf5)[0x2ac1a490259b]
/usr/lib64/glusterfs/3.0.0/transport/socket.so(socket_event_poll_in+0x40)[0x2aaaaab1cd9a]
/usr/lib64/glusterfs/3.0.0/transport/socket.so(socket_event_handler+0xb7)[0x2aaaaab1d08f]
/usr/lib64/libglusterfs.so.0[0x2ac1a4927185]
/usr/lib64/libglusterfs.so.0[0x2ac1a492735a]
/usr/lib64/libglusterfs.so.0(event_dispatch+0x73)[0x2ac1a4927670]
/usr/sbin/glusterfs(main+0xe88)[0x405e10]
/lib64/libc.so.6(__libc_start_main+0xf4)[0x348e61d994]
/usr/sbin/glusterfs[0x4025d9]
---------

**$ ls -lah / | grep core**
-rw-------   1 root root  30M Jan  6 14:29 core.14511
-rw-------   1 root root  30M Jan  6 14:36 core.15691
-rw-------   1 root root  30M Jan  6 14:39 core.15791
-rw-------   1 root root  30M Jan  6 14:40 core.15894
-rw-------   1 root root  30M Jan  6 14:41 core.15996
-rw-------   1 root root  30M Jan  6 14:54 core.16101

:popcorn:

---

### Post by MACscr on 2011-07-09
So now that were a couple years down the road, are you still using a similar setup and if so, whats your current opinion on it?

---

### Post by corneliusbob on 2011-07-25
I'm not sure if this is the correct place for this, i realize im being THAT guy and kinda kicking an old thread. Ive been trying to come up with a cheap roll your own ha scalable san type thing, which has lead me to glusterfs and zfs, this could be a crazy dream from fantasy land as a co worker suggests.

my ideal setup would look like this
4x storage boxes
     cheapo mb/cpu
     10x 2tb drives
     4x w/egb ssd drives
     5x gb ethernet

configured like
     os on 1 ssd
     10 2tb drives in a raidz2 
       1 ssd as a cache disk
       2 ssds as a mirrored log disk
     2x gb nics lacp
     2x gb nics lacp on 2nd switch
     1x gb nic management?

i would like to start with a cluster of about 4 or so using glusterfs to replicate/distribute across them? (not sure if im using the correct terminology about this im sort of a nub with this stuff)  i would like to be able to expand/grow the setup in the future and present the space as a nfs share for esx to use.  i've been playing with this script to provide free vmware esx HA from this site
 
[http://blog.itoncloud.com/?p=35](http://blog.itoncloud.com/?p=35)

at the moment i have 3 esx boxes connected to a freenas and im using ubuntu server vms to try to simulate this and the results have been mixed, i was able to get the zfs zpools all created and mounted and i followed the glusterfs ubuntu tut on howtoforge which results in me getting the error. 

ls: cannot access glusterfs: Transport endpoint is not connected

so im pretty sure im doing something wrong part of the tutorial mentioned iptables, but the commands gave an error message as well
although i must add vm performance hs been surprisingly good on freenas once i started using a jumpdrive as a zil lol

long story short, im lost, anyone out there using something like this or able to point me in the right direction?


--------
crazy beyond this point

bonus points for a different idea that has lower overhead
it seems that the 4 node glusterfs is similar to raid 0+1 so your overhead is like n/2 i was wondering of theres a way to do something along the lines of striping with parity or raid5/6 but spread across the servers to achieve n-1 or n-2 ha+performance+space

---

