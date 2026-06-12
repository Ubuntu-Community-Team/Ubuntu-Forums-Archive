---
title: "NFS and Windows 7 - bad performance"
date: 2010-09-20
forum: Server Platforms
---

### Post by aztekk on 2010-09-20
Hi .. first post here.

Anyway...

As I need to share a folder on my server, to other clients on my network, I set up NFS on my machine.
The main reason is to enable my HTPC to access media on the server and I thought NFS was the way to go, since it usually perform better than Samba.

The HTPC is running Windows 7 and uses the built in NFS package.


This was a real dissapointment, since the whole Windows box froze when listing dirs on the NFS share.

My exports look like:
```
/share 192.168.1.0/24 (rw, async, insecure)
```I'm running Ubuntu Server 10.04 TLS / 2.6.32-24-server x86_64
NFS info ..
```

Architecture: amd64
Source: nfs-utils
Version: 1:1.2.0-4ubuntu4

```Any idéas on what causes the bad performance ?
I really want to fix this, since I can't stream HD-media through Samba to 100%.

---

### Post by sikander3786 on 2010-09-20
This guide might give you some hints.

[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)

I have a mix of Linux and Windows network and I prefer Samba to server the purpose.

---

