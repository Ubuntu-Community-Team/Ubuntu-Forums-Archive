---
title: "[SOLVED] Koala Mini, Wireless not working"
date: 2007-12-22
forum: System76 Support
---

### Post by tgs1952 on 2007-12-22
Bought a Koala mini for my mother a year ago.

When I set up the computer the wireless worked perfectly. It found all the wireless networks in the area and connected easily to the correct local one.

However, they soon had some connection difficulties - unrelated to the mini - and a couple of local 'computer repairmen' came by to help with the issue.

The next time I visited the wireless had ceased to work - it doesn't see any wireless networks at all - nothing listed.

Can the wireless card be turned off or disabled? The computer has not had a great deal of use and I can't see why the card go non-functional.

Any ideas?

---

### Post by tgs1952 on 2007-12-24
I should mention that there is no problem with the router. Other computers can see the network and connect just fine.

The computer repairmen were indeed professional computer repairmen, though neither knew much about Linux.

Is there something else I am missing here?

---

### Post by thomasaaron on 2007-12-24
Sounds like your interfaces file might be thoroughly hosed.

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

---

### Post by tgs1952 on 2007-12-25
Thanks,

that worked.

---

