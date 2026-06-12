---
title: "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the"
date: 2018-07-21
forum: Virtualisation
---

### Post by hopeinformer on 2018-07-21
I have seen similar issues on the forum by others but I was instructed to start a new thread instead of posting on the existing thread. So, if I'm doing it wrong please forgive me.

I'm having a problem after trying to install Virtualbox.  The terminal just stops after "Building initial module for  4.15.0-23-generic" I have waited for it to finish, left it overnight, and it hasn't moved  past it. I have tried entering my password and hitting enter twice, I  have tried simultaneously hitting enter & right arrow, as others have instructed. Nothing  works.

Here's the error:

```
bowlcut3x@bowlcut3x-Inspiron-5559:~$ sudo apt-get install virtualbox
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
bowlcut3x@bowlcut3x-Inspiron-5559:~$ sudo dpkg --configure -a
Setting up virtualbox-dkms (5.2.10-dfsg-6ubuntu18.04.1) ...
Removing old virtualbox-5.2.10 DKMS files...


-------- Uninstall Beginning --------
Module:  virtualbox
Version: 5.2.10
Kernel:  4.15.0-23-generic (x86_64)
-------------------------------------


Status: This module version was INACTIVE for this kernel.
depmod...


DKMS: uninstall completed.


------------------------------
Deleting module version: 5.2.10
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-5.2.10 DKMS files...
Building for 4.15.0-23-generic
Building initial module for 4.15.0-23-generic
```

---

### Post by wildmanne39 on 2018-07-21
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by deadflowr on 2018-07-21
Similar issue here:
[https://ubuntuforums.org/showthread.php?t=2393436]("https://ubuntuforums.org/showthread.php?t=2393436")
Workaround seems to be disable Secure Boot in BIOS.

---

### Post by hopeinformer on 2018-07-23
Thank you deadflowr. I searched for a topic just like this but wasn't able to locate it.

---

