---
title: "VirtualBox 3.2.8 not working"
date: 2011-05-01
forum: Virtualisation
---

### Post by Rlemontw on 2011-05-01
I can not get Virtualbox to work. I think the iso is missing but not sure. This what I am running: Linux rlemontw-EL435AA-ABA-SR1720NX-NA610 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux

The error I get is no bootable medium found. What am I doing wrong or missing.

Thanks in advance for any help.

:D

---

### Post by CharlesA on 2011-05-01
You need to mount an ISO of the install CD in order to install a guest OS.

---

### Post by Rlemontw on 2011-05-01
> **CharlesA said:**
> You need to mount an ISO of the install CD in order to install a guest OS.

I downloaded it from the internet so I do not have an install CD. I am trying to figure out how to install the ISO and where would I find the ISO since I got this from the internet.

Thanks for help.:)

---

### Post by CharlesA on 2011-05-01
VirtualBox is virtualization software, it can run another OS as a "guest"

You need the install disk or iso for the OS you want to install.

Also see here: [http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

---

### Post by Rlemontw on 2011-05-09
> **CharlesA said:**
> VirtualBox is virtualization software, it can run another OS as a "guest"

You need the install disk or iso for the OS you want to install.

Also see here: [http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

Thanks for the link. However I am a little confused about which installation to use, VB on windows host or VB on Linux host. I have a dual boot Ubuntu and Windows and trying to get away from Windows. SO I would like to use VB on Ubuntu so that I can still use certain windows programs. Mainly games from the net for my kids. I am using Wine for most things though. 

Thanks for the help.:D

---

### Post by wilee-nilee on 2011-05-09
There is a more update version of virtualbox from oracle, there is a windows and Linux version use what you think fits your needs.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Personally I load the ISO as this picture will show, this is Vbox 4 but I believe the settings are are basically the same in your version.
[ATTACH]191709[/ATTACH]

---

### Post by CharlesA on 2011-05-12
There are a few interface changes between Vbox 3.2 and VBox 4.0, but nothing too major. You still mount ISOs and whatnot in the VM properties of that specific VM.

---

