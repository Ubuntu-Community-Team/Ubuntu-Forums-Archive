---
title: "Adding dhcp server duties to a standard install?"
date: 2008-06-01
forum: Server Platforms
---

### Post by shultzjr on 2008-06-01
I just installed U8.04ServerAMD64 on a machine with the cd in the cdrom drive and no Internet connection.  I need to add the dhcp process to this machine to add to its' duties the task of dhcp server.  Can I do this from the cd or do I have to get on another machine, download something, burn it to a cd and then put the cd I just made into the server drive and install from that.  I realsize this would be easy if the computer had an Internet connection and KDE/Gnome but it doesn't so I have to work with what I have.  Any help is appreciated.

thanks,
charles

---

### Post by quelx on 2008-06-01
download the **dhcp3-server** and **dhcp3-common** deb from your repo of choice > throw it on a flash drive or cd > install with **dpkg**

---

