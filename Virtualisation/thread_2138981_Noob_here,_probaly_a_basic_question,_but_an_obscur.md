---
title: "Noob here, probaly a basic question, but an obscure one."
date: 2013-04-25
forum: Virtualisation
---

### Post by ERRRIMMAD on 2013-04-25
When I install windows in virtual box will it recognize ext4 drives, so what I'm wondering is this, the install drive will be formatted in ext4, then I will install the VM, will the VM be able to read off that drive in ext4 through the windows VM or will I have to partition the drive to have like a fat32 to swap files.

Anyone see where I'm going with this, so if I download something in windows and later want to import in into Ubuntu, will the disk formats be an issue?

---

### Post by CharlesA on 2013-04-25
If you are running a VM, it only cares about what the file system of the guest's hard drive is. It doesn't seen the host's file system.

You would need to set up some kind of file sharing, usually Samba if you are using Windows in order to share files between the guest and host.

---

