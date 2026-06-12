---
title: "Virtual box permissions...no access to VM"
date: 2009-11-14
forum: Virtualisation
---

### Post by jotto! on 2009-11-14
Hopefully an easy one for you guys, I know I need to do change permissions but am unsure how.

I had VB OSe running but had a problem when I uninstalled it in that I could not boot in to ubuntu.
Clean install of ubuntu and have installed CB PUEL version but when I try to start the virtual machine I get the following.

 p, li { white-space: pre-wrap; }  Failed to start the virtual machine xp.
 Cannot open host device '/dev/fd0' for read/write access. Check the permissions of that device ('/bin/ls -l /dev/fd0'): Most probably you need to be member of the device group. Make sure that you logout/login after changing the group settings of the current user (VERR_ACCESS_DENIED).
 Unknown error creating VM (VERR_ACCESS_DENIED).


If I run /bin/ls -l /dev/fd0 it tells me its a floppy????

Any ideas?

---

### Post by jotto! on 2009-11-14
OK, so I just disabled the floppy support in the settings and it boots fine now.

---

