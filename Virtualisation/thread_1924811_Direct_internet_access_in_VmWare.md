---
title: "Direct internet access in VmWare"
date: 2012-02-13
forum: Virtualisation
---

### Post by linuxTest123 on 2012-02-13
[LEFT]Hello,
I currently have Win 7 and VmWare installed on it running latest version of ubuntu. I know when you start the virtual machine you have options for internet connection, that works fine. What I am having trouble with is having the virtual machine connect directly to the router. I am trying to get Wireshark to work(it does not see any packets) and not sure if there are other solutions. I know it is possible to use a USB WiFi for this. But is there any way for the virtual machine to see my ethernet connection, if I have my computer connected?

Thanks all,
Great forum!

[/LEFT]

---

### Post by japzone on 2012-02-13
What you have to do is while the VM is off. Go into it's settings and change the Network Adapter type to "Bridged" then select whatever Network Adapter your Host PC uses to connect to the Router(ie Your Wifi card or Ethernet). Doing this will cause your VM to ask the Router DHCP for connection info instead of the Default Virtual Network. Doing this decreases security because the VM is now exposed to the Network but allows other PCs to do Folder Sharing with the VM and also allows the VM to access things like Network Storage or Wireless Printers. It also allows things like Wireshark to monitor it(which is where the Decreased security comes from).

---

