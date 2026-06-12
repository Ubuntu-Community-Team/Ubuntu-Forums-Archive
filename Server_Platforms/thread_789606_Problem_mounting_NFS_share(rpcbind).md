---
title: "Problem mounting NFS share(rpcbind)"
date: 2008-05-10
forum: Server Platforms
---

### Post by _sAm_ on 2008-05-10
Hi, I am trying to mount a NFS share and get this error:

mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Program not registered
mount.nfs: internal error

This is on Ubuntu 8.04, and mounting NFS on Ubuntu 7.10 was fine. 

Any advice?

---

### Post by _sAm_ on 2008-05-13
I tried the local IP and not the hotsname, and now NFS works.

But I don't understand why I cant use the hostname as before, its like the server cant see the hostname of my desktop pc(?). If I try to ping my desktop from the serverpc, using its hostname, it will say &#8220;ping: unknown host&#8221;. But if I try the local IP it will ping it just fine. On the other hand, I can use both hostname and local IP to ping the server from my desktp. 

Is it possible to update the hostname so the other pc can see it?  Both /etc/hostname and  /etc/hosts has the same hostname.

---

### Post by nizzmarshal on 2009-04-26
well just update the /etc/hosts file by altering the 127.0.0.1 to @ip (ip adress of the actual machine)

that's what i did and it worked fine both ways mount <hostname>:<file> ....

---

### Post by HermanAB on 2009-04-26
You should put the hostname of the machine in the /etc/hosts file:

```
127.0.0.1 localhost.localdomain localhost
192.168.x.y host.example.com
```

Alternatively, you should run a DNS to resolve the hostname.

---

