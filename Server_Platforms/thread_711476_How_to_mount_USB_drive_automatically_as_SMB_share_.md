---
title: "How to mount USB drive automatically as SMB share w/ no authentication?"
date: 2008-02-29
forum: Server Platforms
---

### Post by crazycarlt on 2008-02-29
I've just set up a 7.10 Ubuntu box as a server and I want to mount a USB backup drive, share it on samba, and make it fully, read/write/create accessible to Windows XP users without password prompts.

Could anybody help me out or point me to a tutorial?

---

### Post by rapiscan on 2008-02-29
You would mount the USB drive (usually automatically done when you plug it in).  Just make sure you're aware of the mount path to the USB drive.

You can follow these instructions to operate a samba server:
[https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88](https://help.ubuntu.com/community/SettingUpSamba#head-51f51bea37ef002e8c6d7dbfeeb486a47cdb0f88)

(There are specific instructions in one of the sections about a public share.)

---

