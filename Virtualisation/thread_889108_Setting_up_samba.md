---
title: "Setting up samba"
date: 2008-08-13
forum: Virtualisation
---

### Post by keefy777 on 2008-08-13
Ok i have followed this tutorial [http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

To try share folders between ubuntu host and xp guest i followed it to the letter and have pinged the ip address from windows and got a full reply.

Now when i try to map the address from xp it states that the ip address is invalid. Also it does some times come up with a window asking for samba username and password but wont allow me to go no further
Any ideas

---

### Post by lisati on 2008-08-13
Perhaps something in the nature of DHCP is changing your IP.

There's a tutorial on samba, which includes connecting with Windows, here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
It also touches on passwords etc.

---

### Post by keefy777 on 2008-08-14
THis is driving me mental no joy still unable to locate network.
And i followed the tutorial to the letter
Arrrrrrrrrrrrrrgggggggggggggggggggggggggghhhhhhhhhhhhhhhhh

Help me please.

---

### Post by HermanAB on 2008-08-14
Well, you have to get networking to work properly BEFORE you play with Samba.  Here is a guide that may help: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Otherwise, visit the Samba web site and read the Official Howto.

Cheers,

Herman

---

