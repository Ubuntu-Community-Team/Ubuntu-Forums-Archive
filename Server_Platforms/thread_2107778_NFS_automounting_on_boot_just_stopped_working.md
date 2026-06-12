---
title: "NFS automounting on boot just stopped working?"
date: 2013-01-22
forum: Server Platforms
---

### Post by Merrattic on 2013-01-22
I run a 12.04 cli server with 5 nfs shares.

My main client is Xubuntu 12.04 LTS with nfs shares setup in fstab

Both machines were setup @ the time 12.04 LTS came out.

Everything has been working fine since then, until the last round of updates this last seven days. Now the nfs shares are not auto-mounting. 

A simple sudo mount -a in a terminal on the client brings them all up, so nothing wrong it seems server side or client side in terms of syntax, but something seems to have gone south during the boot process on the client. Nothing in dmesg to tell me any different.

Running htop on the client I see that:

```
rpcbind -w
rpc.statd -L
rpc.idmapd
```are all running.

An example entry in fstab:

```
192.168.1.1:/media/mynfsmusic               /media/nfsmusic            nfs     rsize=8192,wsize=8192,timeo=14,intr,bg
```As a workaround I put "mount -a" in rc.local, but this didn't mount all the shares, so I created a script using echo "passwd" | sudo -S mount -a, which did the trick. 

AFAIK I am using NFS3, having not specifically set NFS4.

Any ideas what might be wrong?

---

