---
title: "Device name does not show in router list"
date: 2010-12-28
forum: Server Platforms
---

### Post by cbarron on 2010-12-28
As the title says the device name does not show in the router attached devices list. I have looked in /etc/hosts as well as /etc/hostname. These are all set the correct way. 2 of my 3 servers show a name and one of those just says ubuntu which is wrong, and the 3rd server shows nothing. Did I miss a file that I should look at? Any help would be great. The router in question is a Netgear Wndr3300. The Distros are Ubuntu Server 10.04, Server 10.10 and Server 10.10.

---

### Post by endotherm on 2010-12-28
well, i;m not sure what naming protocol your router is using to create the list of servers, but do some of your servers have samba/winbindd installed and other don't? how about the AVAHI service? just guessing.

---

### Post by cbarron on 2010-12-28
Nah no samba or anything else....when I set them up they were installed with open ssl thats it pretty much. Its really kinda weird how some show up and some dont when they were all setup the same. Any more ideas?

---

