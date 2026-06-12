---
title: "Networking problem in virtual environment"
date: 2009-03-11
forum: Virtualisation
---

### Post by chiggins1066 on 2009-03-11
I have loaded the latest version of Ubuntu into VMWare as a virtual machine. The install went fine, but I am having a problem with my network settings (I am also having this problem in Virtual Box--so it appears to be something with Ubuntu).

If I use the GUI networking tools in Ubuntu to set a static address, gateway, name servers, etc. this information is not retained when I reboot the virtual machine. In other words, the system goes right back to DHCP.

I then tried to edit the interfaces file by:

sudo vi /etc/network/interfaces

auto eth0
iface eth0 inet static
address 192.168.200.50
netmask 255.255.255.0
network 192.168.200.0
broadcast 192.168.200.255
gateway 192.168.200.1
:w!

and then typing

sudo /etc/init.d/networking restart

This is an attempt to keep the network settings--but it isn't working. I am doing something wrong.  Does the above procedure look correct? 

The network settings in VMWare are set to bridged.

---

### Post by dmizer on 2009-03-12
Moved this to the virtualization section.

I believe that bridged networking in VMWare is DHCP, not static, and that's why NetworkManager is defaulting to DHCP.

What version of Ubuntu are you using as your guest?

---

