---
title: "How Can I Install Realtek 2.5gbe Driver in Ubuntu for My M/B Network Card"
date: 2020-10-17
forum: Ubuntu/Debian BASED
---

### Post by sparks79 on 2020-10-17
I am actually using Zorin OS But have not found anyone to help .
So I figured Zorin is Ubuntu based so perhaps I can get some help here.
My PC, I Built Myself is a Gigabyte B550 Aorus Master, with Ryzen 3 3300x CPU, 64gb RAM, Three Aorus NvMe Gen4 SSD (500gb ).
The OnBoard Network Controller is  Realtek 2.5GBE Family.
The WiFi from this onboard network is working.
But the Cat5 Network is not.
So I need Drivers for this card for linux.
I have downloaded them from realtek.
But I can't get them to install.
When I am in Terminal, I change dir to the decompressed network driver and try to install by install /install autorun.sh.
But I get some message saying ( Permission denied ).
Yet I run terminal as sudo -i .
Any help would be appreciated

---

### Post by coffeecat on 2020-10-17
*Thread moved to **Ubuntu/Debian based** sub-forum.*

---

### Post by CelticWarrior on 2020-10-17
What drivers are you trying to install (link)?
The command seems (very) wrong...

---

### Post by sparks79 on 2020-10-17
I d/l from realtek  ( r8125-9.003.05.tar.bz2 ) ( [https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-pci-express-software) ).
I tried to install with this command ( root@B550-AORUS-MASTER:~# '/home/john/Downloads/r8125-9.003.05/autorun.sh' install /autorun.sh ).
And I get This ( Check old driver and unload it.
Build the module and install
make: *** No rule to make target 'install'.  Stop.
root@B550-AORUS-MASTER:~#  ).
HELP

---

