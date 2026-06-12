---
title: "Ca't mount shared folder"
date: 2012-04-28
forum: Virtualisation
---

### Post by Borneq on 2012-04-28
I install Precise Pangolin 12.04 under Virtual Box. I installed Guest Additions. 
I can't mount share folder: sudo mount -t vboxsf VBshare ~/host 
/sbin/mount.vboxsf: mounting failed with the error: Protocol error
In old Ubuntu I can mount.

---

### Post by Borneq on 2012-04-28
Problem solved - VBshare is not global for VirtualBox and it was for only one machine.:guitar:

---

