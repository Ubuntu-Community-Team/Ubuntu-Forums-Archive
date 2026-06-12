---
title: "Windows Shares Inaccessible After Couple Days"
date: 2005-12-20
forum: Server Platforms
---

### Post by dk_pa on 2005-12-20
I have a Web Server setup with Ubuntu and another Windows box.  The Windows box has a shared folders for some PHP files and the Ubuntu box has the folder as a mounted drive.  This is so that Apache can make it accessible on the web through the pointer or virtual directory whatever it is called.  All is good for a while and then things become inaccessible.

Any ideas here?  I would seem like the connection is timing out but I'm not sure on which end.  I restarted Apache, Samba, and did a mount -a but none of them seem to have any effect.  The only way I've found for the drive to be accessible again is to reboot the Linux box.  I haven't tried restarting the Windows box tho.

---

