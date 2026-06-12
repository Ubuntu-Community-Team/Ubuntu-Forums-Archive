---
title: "Server 8.04.4 image is corrupted on website"
date: 2010-12-11
forum: Server Platforms
---

### Post by doglover56 on 2010-12-11
Hello. I have been having problems installing 8.04.4 and have been assuming it was my hardware.  Certainly I cannot be the first person to experience this, but I have discovered that certain file names on the disc image are corrupted.  I checked the download with the MD5 tool and they match, so it must be the image itself, right?
If you go into the image and navigate to:
\pool\restricted\l\linux-restricted-modules-2.6.24
you will see that the file names are truncated. The deb and udeb file extensions are missing.  If you go ahead and fix the file names as I did, then it installs fine from either CD or USB. So that was the problem all along.  Perhaps someone has reported this before?
Thanks,
Irwin

---

