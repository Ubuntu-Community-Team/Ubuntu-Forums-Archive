---
title: "Ubuntu Server: Slow file copy when using Windows client."
date: 2013-09-14
forum: Server Platforms
---

### Post by fredfillis on 2013-09-14
I have a box running Ubuntu server providing media files to several windows 7 clients (SMB) and a HTPC running openelec (share via NFS). From my windows client, if I copy files from one server folder to another, it is quite slow (7MB/Sec).

This is quite painful. I have not done the comparison yet, but I believe the same transfer on my HTPC machine or another lappie I have running Ubuntu 12.10 is MUCH quicker.

Am I expecting too much from SMB? Where do I start with this?

---

### Post by coffeecat on 2013-09-14
*Thread moved to **Server Platforms**.*

---

### Post by scbingham on 2013-09-15
From what I have read, nfs is much, much quicker than samba. Bit tough for windoze users then ;)

---

### Post by fredfillis on 2013-09-16
Have a hard time believing that it's just bad luck for windows users. I expect the world is full of *nix servers and windows clients and samba shares. Performance can't be that bad or it would not be a viable option all over the place.

For what it is worth, my speeds on a file copy using an ubuntu client (NFS share) over a wireless connection are not great but I've yet to measure. A cut and paste is almost instantaneous, even on the windows client.

Guess I need to do some speed tests. But I don't know what performance I should expect with samba. Any ideas? Anyone?

---

### Post by TheFu on 2013-09-18
11MB/s is about the upper limit for a 10/100 network.  If any part of your network is only 10/100base-tx, then you will be limited to that throughput.

OTOH, if everything is GigE - 1000base-tx - then I routinely see 75MB/s throughput in both directions over SMB until the cache gets full, then it drops to 20-40MB/s ... sustained. That's about all my drives can handle, but with excess RAM in a server, moving 1-2G files happens at full wire speed usually. It is only the HiDef mpeg2 videos that hit the limit around here.

---

### Post by Entilza on 2013-09-19
Any results on your tests?

Try to edit smb.conf add this old trick?

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

---

