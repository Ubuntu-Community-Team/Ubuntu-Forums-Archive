---
title: "Installing Drivers and other required softwares on UBUNTU"
date: 2013-03-03
forum: Ubuntu Studio
---

### Post by gauravdighe on 2013-03-03
I am new to UBUNTU. I was previously a Windows User. I have purchased a new CPU with below details:ASUS motherboard, NVIDIA Graphic Driver, Sound Driver, LAN and WAN Drivers. Is there any way I can find these drivers and install in my Ubuntu. I am also a Java Developer and i want to install JDK, Oracle 11g Database, Weblogic Server, Eclipse Netbeans. I dont know how to install them, as it was easy to install the softwares in Windows. So is there any way to install them in Ubuntu.

---

### Post by carl4926 on 2013-03-03
> **gauravdighe said:**
> I am new to UBUNTU. I was previously a Windows User. I have purchased a new CPU with below details:ASUS motherboard, NVIDIA Graphic Driver, Sound Driver, LAN and WAN Drivers. Is there any way I can find these drivers and install in my Ubuntu. I am also a Java Developer and i want to install JDK, Oracle 11g Database, Weblogic Server, Eclipse Netbeans. I dont know how to install them, as it was easy to install the softwares in Windows. So is there any way to install them in Ubuntu.

Boot the live CD and see what works OOTB

Open a terminal and post the result of
```
lspci -nnk
```That will tell us about your hardware and drivers in use

---

### Post by jejeman on 2013-03-03
Only if something is not working you should look for drivers. There is no must to install the drivers like in windows.
For things you mentioned only properitary drives for nvidia you may want to install, but it is not necesery, if everything is working fine and you don't need 3d support.

---

