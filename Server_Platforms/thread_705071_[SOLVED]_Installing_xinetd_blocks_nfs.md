---
title: "[SOLVED] Installing xinetd blocks nfs"
date: 2008-02-23
forum: Server Platforms
---

### Post by Peter Howard on 2008-02-23
This is on Ubuntu 7.10 server install.

If I install xinet.d then NFS stops working.  

Attempting to restart NFS (via "sudo /etc/init.d/nfs-kernel-server restart") gives the following errors in /var/log/syslog

[FONT="Fixedsys"]Feb 23 16:16:33 rhuiden kernel: [273140.770000] rpcbind: server localhost not responding, timed out
Feb 23 16:16:33 rhuiden kernel: [273140.770000] RPC: failed to contact local rpcbind server (errno 5).
[/FONT]

I'm guessing this is something simple, but don't know what.

TIA

PJH

---

### Post by Peter Howard on 2008-02-23
OK, it was pretty simple - I just needed to restart portmap :oops:

---

