---
title: "setuping up simple fileserver"
date: 2007-02-18
forum: Server Platforms
---

### Post by tronica on 2007-02-18
I'm setting up a simple fileserver, however my question is, people use samba to share between windows machine, but what if you setting up a linux server for linux boxes. what do i use in that case?

---

### Post by Mike'sHardLinux on 2007-02-18
The "standard" would be NFS, but you could use Samba if that's what you are more comfortable with.

---

### Post by tronica on 2007-02-18
thanks for the reply, i have used samba, and it can be a pain to setup, could point me to a guide on setting up nfs?

---

### Post by jtc on 2007-02-18
Well, there is always the official documentation...

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html)

---

### Post by nix4me on 2007-02-18
system->administration-> shared folders ought to help.  Just select a folder and share with NFS.  Be sure to install the portmap package as well because it will speed up the mounts.

nix4me

---

