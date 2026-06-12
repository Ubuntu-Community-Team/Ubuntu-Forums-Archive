---
title: "nfs nlockmgr timed out"
date: 2013-01-09
forum: Server Platforms
---

### Post by testestt on 2013-01-09
Hi all, thanks for reading me and helping me !

I got a NFS problem. It's not a permanent problem it comes and goes. 
Sometimes (very often), the clients using the mounted partitions are frozen when they're trying to open a new program like eclipse or kde.
I think it's a lock problem due to maybe a network problem or optimization problem, but I don't know what to do, I tried  a lot of thing but I failed....

The ubuntu version
```

cat /etc/issue
Ubuntu 10.04.4 LTS \n \l
```When Everything is OK :
```

Every 2.0s: rpcinfo -u 10.10.10.2 nlockmgr              Wed Jan  9 13:50:41 2013

rpcinfo: RPC: Program/version mismatch; low version = 1, high version = 4program
 100021 version 1 ready and waiting
program 100021 version 2 is not available
program 100021 version 3 ready and waiting
program 100021 version 4 ready and waiting

```When the problem happens 
```
Every 2.0s: rpcinfo -u 10.10.10.X nlockmgr              Wed Jan  9 13:58:39 2013

rpcinfo: RPC: Timed out
program 100021 version 0 is not available

```
No problem with others like mountd or status
Server log :
```
Jan  9 14:02:25 dallas kernel: [95801.650031] statd: server rpc.statd not responding, timed out
Jan  9 14:02:25 dallas kernel: [95801.650044] lockd: cannot monitor topalbum

```client log :
```
kernel: lockd: server 10.10.10.X not responding, timed out
``````
Jan  9 13:22:24 topalbum kernel: [6464607.366966] lockd: server fileserver OK
Jan  9 13:23:24 topalbum kernel: [6464667.367109] lockd: server fileserver OK
Jan  9 13:24:24 topalbum kernel: [6464727.520031] lockd: server fileserver not responding, still trying
Jan  9 13:24:24 topalbum kernel: [6464727.520115] lockd: server fileserver not responding, still trying
``````
avahi-daemon[3890]: Invalid query packet.
```I tried to increase the RPCNFSDCOUNT in /etc/default/nfs-kernel-server using 
```
echo "512" > /proc/fs/nfsd/threads
```I tried to mount client partitions with no lock, tcp....

I tested the network performance  with iperf, got 936 Go/s
I got statd enabled
server is up to date

I am exhausted...

---

