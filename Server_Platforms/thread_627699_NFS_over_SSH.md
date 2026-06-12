---
title: "NFS over SSH"
date: 2007-11-30
forum: Server Platforms
---

### Post by kooseefoo on 2007-11-30
Okay, I'm trying to tunnel an NFS share from a closed network through the internet to my laptop via SSH.

Here's what I'm doing:
```

user@local$ ssh -gCL localhost:2050:localhost:2049 remote_host

```
And in another terminal
```

user@local$ sudo mount -t nfs -o port=2050 localhost:/path/to/share /path/to/mount/point

```

My laptop returns this:
```

mount.nfs: mount to NFS server 'localhost' failed: RPC Error: Program not registered

```


I checked to see if the nfs server is running, and that is fine. Netstat on the server shows that it is listening on port 2049. Netstat on my laptop shows that it is listening on port 2050. The NFS mounts work perfectly fine through the local network, so it seems to be a tunnel problem. Tunnelling other ports (such as port 80) works totally fine.


Thanks,
Chris

---

### Post by scrooge_74 on 2007-11-30
See if any of this helps

[http://www.howtoforge.com/nfs_ssh_tunneling](http://www.howtoforge.com/nfs_ssh_tunneling)

---

### Post by kooseefoo on 2007-11-30
Thanks for the quick reply.

I went through the howto you posted. As far as I can tell, everything that pertains to what I need I have done. The majority of it is about setting up the sleeper user to create the tunnel automatically. I'm just trying to do this as a manual on-demand mount.

---

### Post by HermanAB on 2007-11-30
Well, the problem is RPC.  You either need to restrict NFS to fixed ports or you need a connection tracker.

HTTP is different, since it uses a single port, it doesn't use random RPC ports.

Cheers,

Herman

---

