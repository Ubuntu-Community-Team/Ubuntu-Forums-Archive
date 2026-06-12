---
title: "Problem starting virtualbox"
date: 2016-09-12
forum: Virtualisation
---

### Post by aeronutt on 2016-09-12
Relatively new (a few months ago) install of 16.04.
I installed VirtualBox using synaptic.
I get the following popups when I try to start a Windows XP image (that I had successfully used in an older version of Ubuntu, 14.04 I think).

[img]http://i.imgur.com/M4MwdUv.png[/img]


DKMS is installed, virtualbox-dkms is installed.

If I try to run  "sudo modprobe vboxdrv"   , I get:
```
modprobe: ERROR: could not insert 'vboxdrv': Required key not available
```

---

### Post by &amp;KyT$0P# on 2016-09-12
Is your host a EFI system with Secure Boot enabled?
If so, disable Secure Boot in the EFI and try again.

---

### Post by aeronutt on 2016-09-12
Yep, bingo! That was easy. Thanks!

---

### Post by &amp;KyT$0P# on 2016-09-12
You're welcome! :KS

---

