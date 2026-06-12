---
title: "[SOLVED] k3b only works in sudo"
date: 2008-12-31
forum: Ubuntu Studio
---

### Post by afeasfaerw23231233 on 2008-12-31
I installed k3b from add/remove. I clicked Application > Sound and video > K3b but no response. So I ran k3b in terminal and these showed up: 
```

k3b
trying to create local folder /home/wong/.kde/share: Permission denied
trying to create local folder /home/wong/.kde/share: Permission denied
trying to create local folder /home/wong/.kde/share: Permission denied
trying to create local folder /home/wong/.kde/tmp-wong-desktop: Permission denied
trying to create local folder /home/wong/.kde/share: Permission denied
trying to create local folder /home/wong/.kde/share: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/wong/.kde/tmp-wong-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/wong/.kde/tmp-wong-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/wong/.kde/tmp-wong-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/wong/.kde/tmp-wong-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/wong/.kde/tmp-wong-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/wong/.kde/tmp-wong-desktop/startkdeinitlockXXXXXX.tmp: Permission denied
trying to create local folder /home/wong/.kde/share: Permission denied
trying to create local folder /home/wong/.kde/share: Permission denied
trying to create local folder /home/wong/.kde/share: Permission denied
trying to create local folder /home/wong/.kde/socket-wong-desktop: Permission denied
trying to create local folder /home/wong/.kde/socket-wong-desktop: Permission denied
kdeinit: Aborting. No write access to '/home/wong/.ICEauthority'.
startkdeinitlock: ERROR: KUniqueApplication: Can't setup DCOP communication.
```

How to fix it? Thanks!

My system is Ubuntu 8.04 64-bit.

---

### Post by afeasfaerw23231233 on 2009-01-01
bump

---

### Post by afeasfaerw23231233 on 2009-01-01
I googled around and found out it's a permission problem. Just run ```
 sudo chown -hR yourname:yourname /home/yourname 
```in the terminal and the problem is solved.

---

