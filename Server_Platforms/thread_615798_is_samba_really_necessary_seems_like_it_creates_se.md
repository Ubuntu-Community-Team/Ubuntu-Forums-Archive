---
title: "is samba really necessary? seems like it creates security holes for hackers!"
date: 2007-11-17
forum: Server Platforms
---

### Post by LinuxSoundMan on 2007-11-17
why is samba a required security update. to me IMO it seems like it would create an open security hole allowing windows machines to get to your system. am i way off on this. i did the updates as suggested by the update icon on the taskbar and it said that it was not authenticated. i fear that my system security may be compromised. i installed firestarter and it seemed to work fine but every now and then when i am clicking through the tabs within firestarter it just closes and disappears for no reason. is this a known bug or am i being hacked. thanks in advance.

---

### Post by LinuxSoundMan on 2007-11-17
i also notice whe trying to remove samba with synaptics it is required to remove ubuntu studio desktop as well. the same for openssh. it seems like it is "hardwired" to ubuntu. this is very scary. what gives??? can someone please offer me a simple explanation to all of this? thanks

---

### Post by HermanAB on 2007-11-17
Samba is a Local Area Network protocol.  It should not be allowed to traverse the internet.

Firestarter is a setup script for iptables, which is a front end for netfilter.   Firestarter is also a log reader (the GUI part).  You can quit the log reader without affecting the underlying firewall provided by netfilter.  SO if the log reader terminates, it doesn't mean that your netfilter firewall suddenly stopped working.  The GUI part is quite useless actually and there is not much point in keeping it running.

Cheers,

H.

---

### Post by ddrichardson on 2007-11-17
Samba is not a required update, a security update for Samba is required if it installed and an issue has been found.

The authentication is because of not having the key installed for one of the repositories you have.

I'm not familiar with studio, but the desktop packages are meta packages, linking together a bunch of stuff that doesn't rely on each other. Most of the time you don't need them, often you can remove a component then reinstall the removed desktop package.

---

### Post by LinuxSoundMan on 2007-11-17
ok i understand. i guess i will remove samba because i have no use for it. by the way one of the following is what was unable to be authenticated > gdm (2.20.0-0ubuntu6) to 2.20.1-0ubuntu1
libsmbclient (3.0.26a-1ubuntu2.1) to 3.0.26a-1ubuntu2.2
samba-common (3.0.26a-1ubuntu2.1) to 3.0.26a-1ubuntu2.2
smbclient (3.0.26a-1ubuntu2.1) to 3.0.26a-1ubuntu2.2and the only third party repository i have checked is from [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) thanks for the info

---

