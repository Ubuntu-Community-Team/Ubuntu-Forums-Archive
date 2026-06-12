---
title: "Network File Systems"
date: 2009-02-14
forum: Server Platforms
---

### Post by keebler411 on 2009-02-14
I have a simple home network consisting of all linux computers.  I use cups for shared printing right now.

What is the best way to share directories if you don't care about microsoft compatibility? 

The main computer which now shares the printer (others are laptops) will eventually be serving up media files to an htpc (not yet built) so throughput is a consideration.

What are the options and pros/cons?  So far I can only think of 2: samba and NFS

Thanks

---

### Post by HermanAB on 2009-02-14
In terms of easyness:
1. FTP (works out of the box)
2. NFS (needs two lines of configuration, one line on server, one line on client)
... ?
100. Samba (requires hundred lines of configuration and hours of debugging)

Cheers,

Herman

---

### Post by perlluver on 2009-02-14
I use NFS, and it is pretty simple to maintain, and to keep running.  I also have Samba on the server, but NFS seems to be less of a hassle.  NFS also seems to be a little quicker between Linux computers.

---

### Post by handy on 2009-02-15
I use NFS also, simple & reliable on my tiny home LAN.

---

