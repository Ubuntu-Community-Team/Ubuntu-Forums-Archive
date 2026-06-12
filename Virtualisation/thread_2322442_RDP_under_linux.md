---
title: "RDP under linux"
date: 2016-04-28
forum: Virtualisation
---

### Post by kek3 on 2016-04-28
Hi everyone!
I'm trying to make a lan with  remote desktops with virtual machines. I've done all the configuration  (like improve the video performance, USB redirection, audio  streaming...) and all is working!

But I have a huge problem, I  use a service to make the conections (with service I mean something like  can be remmina for example), that must be in the conection, and if the  conection is from linux as server and linux or windows as remote  desktop, it will close the conection. I've tried doing the same being  windows the server and linux the remote desktop and it does not close  the conection. Soo... it must be some rdp on linux configuration?

The systems are:
1º First Server: Ubuntu 15.10 / thin client / xrdp
2º Second Server: Raspbian jessie and RPiTC project (you should check it, it really rules) / raspberry pi 2 / xrdp
3º Thrid Server: Linux Mint 17.3 / intel nuc / rdesktop

1º First remote desktop: Ubuntu 15.10 / xfce / xrdp
2º Second remote desktop: Lubuntu 15.10 / lxde / xrdp

EDIT: nvm, it looks that is a internal software issue, not rdesktop or xrdp one!:P

Cheers!

---

