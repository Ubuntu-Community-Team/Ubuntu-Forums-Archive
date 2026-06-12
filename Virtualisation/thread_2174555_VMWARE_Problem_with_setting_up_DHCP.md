---
title: "VMWARE Problem with setting up DHCP"
date: 2013-09-15
forum: Virtualisation
---

### Post by mast3rmind2 on 2013-09-15
Hi, all

This is my first topic i started i'm a beginner with ubuntu i tried allot followed allot of tutorials but cant figure it out now i need you help guys.

This is my problem.

I need to gave Windows 7 a dhcp adress from ubuntu but its not working i followed all the steps from setting up dhcp but i cant get it work.

I get a error of job failed to start

I'm using VMware

---

### Post by TheFu on 2013-09-22
Which vmware product? They make 6 of them - server, workstation, vdi, player, ESX, ESXi and probably a few others.

I don't understand what you mean by "setting up dhcp" - as a client or server? Do you need/want static leases?
Usually, clientOS DHCP works using whatever the network DHCP server provides ... as long as you didn't configure NAT. That network server can be any normal DHCP server ... router, Windows-AD or any of the DHCP servers that run under Linux.

Is there anything in the log files?  Warnings, errors?  Copy/paste please.

Also, which is the hostOS and which is the guestOS?  I can't figure that out from the OP and don't want to assume.

---

### Post by mast3rmind2 on 2013-09-25
Already fixed i my fault was the subnet it was not right so he didnt can restart it.

---

