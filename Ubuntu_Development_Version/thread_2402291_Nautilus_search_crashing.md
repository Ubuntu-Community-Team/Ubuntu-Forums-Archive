---
title: "Nautilus search crashing"
date: 2018-09-28
forum: Ubuntu Development Version
---

### Post by dino99 on 2018-09-28
gnome-shell on xorg session
nautilus 3.26.4-0ubuntu3

Get a crash when using 'search' feature:

Goto  'Other Locations' -> Computer ->  Search 'tempfile'

Wonder if the last change (only searching into a dir, instead across the whole system as it was) has to be blamed.

Maybe lp:#1795028

Still hope to get 3.30 version.

---

### Post by corradoventu on 2018-09-30
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1795136](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1795136)

---

### Post by P-I H on 2018-09-30
Nautilus has crashed earlier on my system when Nautilus didn't find any match, or the search took a long time. Tried those searches now and they went OK. However some more "complex" searches crashed Nautilus.
Created a bug report
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1795210](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1795210)
and added me to
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1795136](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1795136)

---

### Post by dino99 on 2018-10-02
Latest nautilus  3.26.4-0ubuntu5 fix the previous crash.
So repicking my previous test about searching 'tempfiles.d':
- no crash, and list some related files across the system
- but does not list that subdir 'tempfiles.d' nor any other dir/subdir

Latest version   changelog talks about 'remote' feature. In my case i'm searching on a standalone pc only. 

That is a heavy regression (when nautilus was searching/list everything across the system. Limiting searching only to a local dir/subdir is not user friendly: the previous feature was too wide on some cases, ok, but actual feature is a drawdown. It might allow user to select either searching 'local dir/subdir' or 'whole system' or 'remote' from the search field for a friendly experience.

---

### Post by vanadium on 2018-10-07
This crashing on search also exists in Ubuntu 18.04. Is most likely to happen on first uses, occurs less frequently later in the session. Ubuntu in 18.10 keeps using the older version, so if any of these bugs would have been solved, Ubuntu won't benefit.

---

### Post by P-I H on 2018-10-07
I don't get this crash any longer.
I think it was fixed in this update.
```
Start-Date: 2018-10-02  06:38:38
Commandline: aptdaemon role='role-commit-packages' sender=':1.660'
Install: linux-headers-4.18.0-8:amd64 (4.18.0-8.9, automatic), linux-image-4.18.0-8-generic:amd64 (4.18.0-8.9, automatic), linux-modules-extra-4.18.0-8-generic:amd64 (4.18.0-8.9, automatic), linux-headers-4.18.0-8-generic:amd64 (4.18.0-8.9, automatic), linux-modules-4.18.0-8-generic:amd64 (4.18.0-8.9, automatic)
Upgrade: evince:amd64 (3.30.0-3, 3.30.0-3ubuntu1), linux-headers-generic:amd64 (4.18.0.7.8, 4.18.0.8.9), libevdocument3-4:amd64 (3.30.0-3, 3.30.0-3ubuntu1), yaru-theme-icon:amd64 (18.10.4, 18.10.5), grub-common:amd64 (2.02+dfsg1-5ubuntu4, 2.02+dfsg1-5ubuntu5), linux-image-generic:amd64 (4.18.0.7.8, 4.18.0.8.9), grub2-common:amd64 (2.02+dfsg1-5ubuntu4, 2.02+dfsg1-5ubuntu5), network-manager-gnome:amd64 (1.8.18-1ubuntu1, 1.8.18-2ubuntu1), yaru-theme-gtk:amd64 (18.10.4, 18.10.5), grub-pc:amd64 (2.02+dfsg1-5ubuntu4, 2.02+dfsg1-5ubuntu5), linux-signed-generic:amd64 (4.18.0.7.8, 4.18.0.8.9), grub-pc-bin:amd64 (2.02+dfsg1-5ubuntu4, 2.02+dfsg1-5ubuntu5), evince-common:amd64 (3.30.0-3, 3.30.0-3ubuntu1), 
**NAUTILUS**:amd64 (1:3.26.4-0ubuntu4, 1:3.26.4-0ubuntu5), **LIBNAUTILUS**-extension1a:amd64 (1:3.26.4-0ubuntu4, 1:3.26.4-0ubuntu5), grub-efi-amd64-bin:amd64 (2.02+dfsg1-5ubuntu4, 2.02+dfsg1-5ubuntu5), libevview3-3:amd64 (3.30.0-3, 3.30.0-3ubuntu1), libnma0:amd64 (1.8.18-1ubuntu1, 1.8.18-2ubuntu1), yaru-theme-gnome-shell:amd64 (18.10.4, 18.10.5), libmysqlclient20:amd64 (5.7.22-0ubuntu18.04.1, 5.7.23-2ubuntu1), grub-efi-amd64-signed:amd64 (1.106+2.02+dfsg1-5ubuntu4, 1.107+2.02+dfsg1-5ubuntu5), 
**NAUTILUS-DATA**:amd64 (1:3.26.4-0ubuntu4, 1:3.26.4-0ubuntu5), linux-generic:amd64 (4.18.0.7.8, 4.18.0.8.9), gir1.2-nma-1.0:amd64 (1.8.18-1ubuntu1, 1.8.18-2ubuntu1), yaru-theme-sound:amd64 (18.10.4, 18.10.5)
End-Date: 2018-10-02  06:39:29
```

---

