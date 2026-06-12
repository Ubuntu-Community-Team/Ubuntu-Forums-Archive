---
title: "Something wrong with Ubuntu Archive server?"
date: 2006-07-22
forum: Server Platforms
---

### Post by nits_555 on 2006-07-22
Hi All,

I am trying to use the synaptic package manager to download a few files and it times out while connecting the us.archive.ubuntu.com. This happens even when I try to download files using the terminal. Here's a dump of what I get in terminal:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.15), connection timed out

I tried pinging this server and it seems to respond well.

ping statistics ---
12 packets transmitted, 11 received, 8% packet loss, time 11046ms
rtt min/avg/max/mdev = 124.382/129.623/147.112/5.869 ms

Can someone confirm that the it's a problem at the server end and provide a resolution to the same.

Thanks,
Nitin.

---

### Post by Ziox on 2006-07-22
the mirror is down, edit your sources.list file and get rid of the "us." part, just use archive.ubuntu.com

---

