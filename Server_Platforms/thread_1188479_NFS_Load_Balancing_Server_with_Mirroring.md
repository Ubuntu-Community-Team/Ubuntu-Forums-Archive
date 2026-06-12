---
title: "NFS Load Balancing Server with Mirroring"
date: 2009-06-15
forum: Server Platforms
---

### Post by Benismyhorse on 2009-06-15
Hi, Everyone.
I am trying to set-up a NFS Load Balancing Server using round robin DNS,
The problem I have now is how to Mirror the 2 servers.:confused:
Does anyone have an idea of how to do this?

Thanks

---

### Post by gombadi on 2009-06-15
Are the two servers using the one file storage system?

i.e. can user a, edit file a, on server a, and at the same time user b, is editing file a, on server b or is file a the same file on both servers?

---

### Post by Benismyhorse on 2009-06-16
Hi,
Trying to find out a way that the servers with have the same files on,
so they will always be the latest, then using Round Robin DNS for the load balancing.
Trying to do this because the volume of users are slowing down the NFS server. Also the NFS Shares are using kerberos.

Thanks

---

### Post by HermanAB on 2009-06-16
Rsync is your friend.
;)

---

