---
title: "Windows 7 random restarts when 3D enabled"
date: 2012-05-03
forum: Virtualisation
---

### Post by OliverHaslam on 2012-05-03
I have a Windows 7 client running in Virtualbox on an Ubuntu host. The client runs fine, so long as I do not enable 3D acceleration by installing the 3D driver via Virtualbox Additions.

As soon as I do, I begin getting random reboots of the client. Any ideas what could be causing this, other than the state of the drivers?

Cheers.

---

### Post by Dedoimedo on 2012-05-03
Did you try collecting a minidump (bsod) info in your Windows box? Is the option enabled to collect a memory core in case of a kernel panic?
Dedoimedo

---

### Post by OliverHaslam on 2012-05-03
> **Dedoimedo said:**
> Did you try collecting a minidump (bsod) info in your Windows box? Is the option enabled to collect a memory core in case of a kernel panic?
Dedoimedo

I don't get a BSOD, just a reboot. I'll check though.

---

