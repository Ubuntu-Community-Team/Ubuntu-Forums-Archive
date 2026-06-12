---
title: "problem at installing XP in VirtualBox"
date: 2009-03-26
forum: Virtualisation
---

### Post by treslunas on 2009-03-26
Just made a fresh install of Intrepid; then installed VirtualBox from virtualbox.org. Everything went well when creating the Virtual Machine and configuring it. However, when starting to install Windows XP in it I get this message:

Cannot open host device '/dev/fd0' for read/write access. Check the permissions of that device ('/bin/ls -l /dev/fd0'): Most probably you need to be member of the device group. Make sure that you logout/login after changing the group settings of the current user (VERR_ACCESS_DENIED).
Unknown error creating VM (VERR_ACCESS_DENIED).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

What exactly this means and how can I fix it?
Please, help!

---

### Post by ubersolid on 2009-03-26
Are you a member of the vboxusers group?

---

### Post by namaku0 on 2009-03-26
..or if you don't have plan to use floppy disk
inside your VM you can disable it.

---

### Post by treslunas on 2009-03-29
Yes. That was it. The XP install went smoothly after disabling the floppy and now I have a working XP environment inside my Intrepid.
Thanks.

---

