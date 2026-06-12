---
title: "Sun xVM VirtualBox and MacPro"
date: 2008-08-05
forum: Virtualisation
---

### Post by L1PA17 on 2008-08-05
I am using VirtualBox to run ubuntu on my MacPro. Everything worked fine after the basic installation. I also installed guest additions because I would like to use shared folders. After the reboot I have run into window adjusting problems. Everything is fine until the logging screen appears. Before the logging screen, I am loosing the windows frame and can not be adjusted anymore. It seems the window shows only the left upper corner of the logging screen. I tried to use different settings but the result was the same.

Any suggestions ???

---

### Post by Oldsoldier2003 on 2008-08-05
Moved from Apple to Vitualization for better visibility to those that might be able to help you.

---

### Post by bodhi.zazen on 2008-08-05
Not with the video, but ...

IMO "Shared folders" are over rated. If you can not fix your video problem, re-install then use either a shared USB device or a network share protocol such as samba, NFS, ftp, http, ssh (sshfs).

---

### Post by cyberdork33 on 2008-08-05
> **bodhi.zazen said:**
> Not with the video, but ...

IMO "Shared folders" are over rated. If you can not fix your video problem, re-install then use either a shared USB device or a network share protocol such as samba, NFS, ftp, http, ssh (sshfs).

Just a little detail, Virtualbox on OS X doesn't support anything but NAT right now, so most filesharing protocols won't work nicely. The "shared folders" functionality basically creates an accessible samba share within the guest.

---

