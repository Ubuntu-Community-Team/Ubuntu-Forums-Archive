---
title: "[Q] Automatically start vmware-tools on Ubuntu 12.04"
date: 2013-04-10
forum: Virtualisation
---

### Post by nocode on 2013-04-10
I'm not very experienced with Linux and I'm having a hard time finding a script that will allow me to automatically start vmware-tools on Ubuntu 12.04 on the command line (no GUI).  The only thing I've came across was this:

echo "/usr/bin/vmware-toolbox - -minimize" > ~/.kde/Autostart/vmware-toolbox.sh

and that appears to be for the GUI or kubuntu.  I'd like the service to automatically start if the server reboots.

Thanks

---

### Post by stevecrawl on 2013-04-12
Vmware Virtualization Machine 
Ip Address

---

### Post by nocode on 2013-04-12
uh what?

---

### Post by dcstar on 2013-04-18
/etc/rc.local

Why do you want to start a GUI tool on a non-GUI system anyway?

---

### Post by nocode on 2013-04-18
There's not a whole lot, but being able to reboot from vSphere and copy/pasting from the console.  It also sends some server info into vSphere

---

