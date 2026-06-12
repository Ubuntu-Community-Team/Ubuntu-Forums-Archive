---
title: "A VNC alternative for Rdesktop"
date: 2010-12-20
forum: Virtualisation
---

### Post by dboy1612 on 2010-12-20
Hi there,

I'm currently in the works of completing [this tutorial]("http://ubuntuforums.org/showthread.php?t=939183") in order to set up a seamless desktop with Ubuntu and Windows XP. Due to the version of windows I'm using, remote desktop has been removed from the version.

Is it possible to use the same method from the tutorial, but in exchange use a VNC client? Or possibly a third party windows desktop connection client for Windows XP that rdesktop can connect to?

I've googled this idea several times but could never seem to find a good answer. Any help is appreciated. Thanks a lot!

---

### Post by dgoosens on 2010-12-20
seems hard to believe the default RDP client is not installed...
try Win > Run and type "mstsc" > "OK"

---

### Post by CharlesA on 2010-12-20
> **dgoosens said:**
> seems hard to believe the default RDP client is not installed...
try Win > Run and type "mstsc" > "OK"
The "home" editions of Windows XP/Vista and 7 don't have Remote Desktop capability. They have the client, but they don't have the server portion enabled.

@OP: VNC might work, but it would probably be more of a pain then not, as seamless mode has the start button/task bar above the bottom panel, does it not?

EDIT: If you have the "non-free" version of VirtualBox installed, you can use VRDP instead of The RDP server built into Windows. It'll be a little slugging, but it should work fine locally.

---

