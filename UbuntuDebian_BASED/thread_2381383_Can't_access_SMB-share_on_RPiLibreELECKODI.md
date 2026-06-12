---
title: "Can't access SMB-share on RPi/LibreELEC/KODI"
date: 2017-12-30
forum: Ubuntu/Debian BASED
---

### Post by zachalexy on 2017-12-30
Hi, upgraded my RPI/LibreELEC which now doesn't accept SMB1 connections anymore. When I change the smb.conf to use a client min and client max protocol I can access the share again through smbclient or by mounting in fstab at boot. What somehow still doesn't work is use Nautilus to "Connect to server": Failed to retrieve share list from server: Connection timed out. Strange?? How can I solve this SMB-issue once and for all? Thx

---

### Post by TheFu on 2017-12-30
I would check that the samba protocol versions are compatible with each other.  Since libreElec isn't Ubuntu, I have no idea what it might have.

Protocol versions aren't the same as client versions, BTW.  You can probably control which version is used on the server-side via a config change, unless the distro uses a cut-down or older version of samba.

---

### Post by QIII on 2017-12-30
Moved to Ubuntu/Debian BASED

---

