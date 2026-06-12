---
title: "Cannot share folder - Win7 host,  Ubuntu 10.10 guest"
date: 2011-01-09
forum: Virtualisation
---

### Post by Tdonohue on 2011-01-09
I have been working on this for more than 6 hours and just cannot share a folder between Ubuntu 10.10 running in a virtual box on a Windows 7 desktop.

I have installed DKMS and guest additions. 

"winshare' is a folder on my host desktop.  "share" is a folder in the home folder on the ubuntu guest.

I type:

```
mount -t vboxsf winshare /home/share
```

and get:

```
/sbin/mount.vboxsf: mounting failed with the error: No such file or directory 
```

I cannot see what I'm doing wrong.

---

### Post by Tdonohue on 2011-01-12
As a workaround I've installed teamviewer on both host and guest and the file transfer feature works okay. What a PITA though

---

