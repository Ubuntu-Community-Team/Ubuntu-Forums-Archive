---
title: "how to virus scan over a network?"
date: 2008-04-30
forum: Security
---

### Post by ikt on 2008-04-30
Hey guys,

I have clamav installed however in the ClamAV GUI it doesn't let you select network shares, and from the command line whether I use 

sudo clamscan smb://fileshare or //fileshare it complains of not finding a file..

so.. how do I scan over a network?

---

### Post by HermanAB on 2008-05-01
Mount the network share using CIFS or NFS.

Cheers,

Herman

---

### Post by ikt on 2008-05-01
cheers

---

