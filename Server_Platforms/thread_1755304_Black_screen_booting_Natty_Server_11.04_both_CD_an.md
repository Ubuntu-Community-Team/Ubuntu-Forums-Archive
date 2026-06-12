---
title: "Black screen booting Natty Server 11.04 both CD and USB install"
date: 2011-05-11
forum: Server Platforms
---

### Post by bababooey on 2011-05-11
I tried booting up natty server on both a unetbootem usb flash drive install and on CD. I get the menu of options to install like Install Ubuntu Server, Install Ubuntu Server 9 expert install, Cloud, etc. Hitting install either the 1st or 2nd option leads to a black screen but not at a frozen state(I can still reboot with ctrl-alt-del). 

The server Im installing on is a ibm system-x rack with a single xeon and a raid5 already setup to be used for installation. Now Im back to using lucid 10.04.2 which I might consider upgrading through Update Manager since I cant get natty to boot correctly with a working display. Anyone having similar problems on Natty server stable release?

Also as I post this, I dont see a ubuntu server prefix, maybe it should be added?

---

### Post by volkswagner on 2011-05-11
It could be screen resolution issue.  You can try hitting F6 for boot options and select nomodeset.

If that does not work, you can try other boot options under F6 menu.

---

