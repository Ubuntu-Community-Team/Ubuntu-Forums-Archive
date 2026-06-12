---
title: "NFS borked after upgrade"
date: 2007-06-20
forum: Server Platforms
---

### Post by briguy on 2007-06-20
I recently upgraded my 6.06 server to 7.04 (through 6.10) and everything is working well, except for nfs.  When I try to mount from the client, I get:
```
bw@trogdor:~$ sudo mount -a
mount to NFS server '10.50.10.74' failed: server is down.

```
So, I going to the server and restarting /etc/init.d/nfs-kernel-server gets me this:
```
exportfs: /etc/exports [3]: Neither 'subtree_check' or 'no_subtree_check' specified for export "10.50.10.72:/media/files".
  Assuming default behaviour ('subtree_check').
  NOTE: this default will change with nfs-utils version 1.1.0

```
I've tried re-installing nfs-kernel-server, portmap and nfs-common on the server.  Prodding the server with nmap shows that the ports are open that need to be.  What am I missing here?

---

### Post by briguy on 2007-06-20
portmap was bound to lo!  Doh!

Problem solved.

---

