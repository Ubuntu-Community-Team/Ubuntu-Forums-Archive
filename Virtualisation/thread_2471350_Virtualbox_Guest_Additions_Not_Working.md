---
title: "Virtualbox Guest Additions Not Working"
date: 2022-01-27
forum: Virtualisation
---

### Post by KenUBF on 2022-01-27
I'm using Ubuntu 20.04.3. I have installed Virtualbox 6.1, installed via their installer from the Oracle website (I like having the updated software). I recently upgraded my kernel and it appears that the guest additions no longer work. I'm guessing because the kernel modules are not present in the new kernel. OK. Simple enough, I thought. I went to install virualbox-dkms but it tells me it's going to remove VB 6.1 and install the version from the repos. Is it possible to just install the modules without removing my preferred version?

---

### Post by KBar on 2022-01-27
Why not install it from the Ubuntu repositories? Focal 20.04 has version 6.1.26. 

If you insist on installing from Oracle VM VirtualBox site, which currently sits at 6.1.32, you need to install Guest Additions included in the deb package, which is placed in host's */usr/share/virtualbox*.

You also need to prepare your **guest** for building external kernel modules. Install the *gcc*, *make* and *perl* packages, click on Devices, then select **Insert Guest Additions** and point to */usr/share/virtualbox/VBoxGuestAdditions.iso* if asked. It should be mounted automatically and prompt you.

---

### Post by KenUBF on 2022-01-27
Thanks! That worked.

---

