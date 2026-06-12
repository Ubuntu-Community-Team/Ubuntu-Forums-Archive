---
title: "mount: RPC: Timed out"
date: 2006-10-31
forum: Server Platforms
---

### Post by pjbgravely on 2006-10-31
I had a network set up with an Edubuntu server and nfs exports with multiple clients. It worked great and I could max out my network speed.

I moved and at the same time upgraded the server(edmund) to Ubuntu Server 6.06. My desktop ( dutch) has a static IP and mounts it's own shares just fine. My clients which are DHCP IP'd runnng edubuntu 6.06 and ubuntu 6.10 can no longer connect.

 I get this error message every time:  

```
mount: RPC: Timed out
```

This happens no matter if I use DHCP, static IP, or use the same router as the server. I can ssh from the clients to the server and can see the open nfs ports in portmap. 

My /etc/exports file of the server is:

```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/home/torrent/torrents dutch(rw,async)
/home/paul/ dutch(rw,async)
/home/share/ dutch(rw,async)
/home/share/upload 192.168.254.1/24,192.168.1.1/24(rw,no_root_squash,async)
/home/share/download 192.168.254.1/24,192.168.1.1/24(ro,no_root_squash,async)

```

I have changed this many times and am willing to try what I tried before if anyone suggests.


One thing I have found, right after the time out message appears on the client I get this in /var/log/syslog on the server.

```
Oct 31 22:59:30 edmund mountd[13102]: authenticated mount request from 192.168.254.1:797 for /home/share/upload (/home/share/upload)
```

The clients /etc/fstab file looks like this:

```
edmund:/home/share/upload /mnt/upload nfs rw,hard,intr,noauto,users 0 0
edmund:/home/share/download /mnt/download nfs ro,hard,intr,noauto,users 0 0
```


Running the command rpcinfo -p edmund on a client gives me this:

```
 program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32770  nlockmgr
    100021    3   udp  32770  nlockmgr
    100021    4   udp  32770  nlockmgr
    100021    1   tcp  45471  nlockmgr
    100021    3   tcp  45471  nlockmgr
    100021    4   tcp  45471  nlockmgr
    100005    1   udp    660  mountd
    100005    1   tcp    663  mountd
    100005    2   udp    660  mountd
    100005    2   tcp    663  mountd
    100005    3   udp    660  mountd
    100005    3   tcp    663  mountd
    100024    1   udp    722  status
    100024    1   tcp    725  status
```

Paul

---

### Post by pjbgravely on 2007-01-04
I finally found the answer.

To fix it I added the following to /etc/hosts.allow of the server

rpc.mountd: 192.168.254.*

I have no idea why rpc.mountd: ALL didn't work. And I have no idea why this is needed at all. I'm just glad I finally found the answer.

---

