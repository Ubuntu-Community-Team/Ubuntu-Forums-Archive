---
title: "LTSP some clinets fails to mount root file system - other work"
date: 2006-09-25
forum: Server Platforms
---

### Post by edkey on 2006-09-25
I have a edubuntu 6.06. The lstp server is working on certain connected clients, but not on others. The obvious answer may be hardware differences, but I would like to make sure. On the clients it fails on, it always fails when the system begins mounting root file system...As an added bit of info, on the systems where the mount fails, I later then installed edubuntu on them and the install was successful. I then converted these systems into ltsp servers, and the client connected to them failed at the same mount point.

---

### Post by fnjordy on 2006-09-25
Mounting the root file system is where NFS is started, therefore it would appear some issue with NFS, maybe permissioning is being encountered.  You should be able to tell from /var/log/auth.log or /var/log/messages why an error is occuring.  If these machines have CD drives you should try booting from a Ubuntu CD and trying to manually mount the NFS share on your Edubuntu server.

Permissioning for NFS shares is in the /etc/exports file, you might have tcp wrappers enabled and configured to limit to certain networks or addresses.  Check /etc/hosts.allow and /etc/hosts.deny, but this should be apparent with the live-CD test above.

---

### Post by edkey on 2006-09-26
I checked /var/log/auth.log and /var/log/messages - found nothing about any relevant errors recorded.

I was able to boot with live cd but manual mount failed.

Both my /etc/hosts.allow and /etc/hosts.deny have the default settings that came with install. There is nothing. 

I suspect it has to do with the test system I am using. I am testing on a Toshiba Tecra A3. It appears edubuntu works well on it, but it fails to run strictly as a client or as a server for ltsp clients. All clients that connect to it fail. On my other server, all clients that failed on the Tecra worked on it so, I can only assume it is this (Tecra) system. One hitch though....one AMD client fails on both the Tecra and my other test server (fails to mount). The other test server is a P3.

---

