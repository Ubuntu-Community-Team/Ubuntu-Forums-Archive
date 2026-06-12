---
title: "After upgrade, VirtualBox won't start"
date: 2010-06-19
forum: Virtualisation
---

### Post by Robotman on 2010-06-19
I've just back to back upgrades from 9.04 to 9.10 to 10.04.  When trying to start Windows XP as a guest, VirtualBox gives me the following error:
```
Failed to start the virtual machine **Windows XP**.

Cannot open host device **'/dev/fd0'** for read/write access.  Check the
permissions of that device ('/bin/ls -l /dev/fd0'): Most probably you
need to be a member of the device group.  Make sure that you
logout/login after changing the group settings of the current user
(VERR_ACCESS_DENIED).

Unknown error creating VM (VERR_ACCESS_DENIED).

_D_etails
Result Code:      NS_ERROR_FAILURE (0x80004005)
Component:        Console
Interface:        IConsole {6375231a-c17c-464b-92cb-ae9e128d71c3}
```
I've tried adding a group of "vboxusers" and adding myself as a member, but that did nothing.  I also added myself as a member to the "disk" group, but that also did nothing.  Can anybody tell me how I can bypass this error and get my XP installation running in VB again?

---

### Post by JustinR on 2010-06-20
Unless you need a floppy drive click on the Settings button for your Windows Vista/7 machine. Go to System, and disable boot from floppy.

---

### Post by Robotman on 2010-06-20
I just figured that out before I saw your reply. ;)  Thanks anyway!  Looks like VB no longer supports physical floppy drives, or they're perhaps handled differently.  In any case, I need it less than rarely, so I can find a workaround.

---

