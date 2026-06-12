---
title: "VBox OSE DHCP hassles- is it that hard, really?!"
date: 2011-04-02
forum: Virtualisation
---

### Post by varelov on 2011-04-02
On an Ubuntu 10.04 host I have installed a VirtualBox 3.1.4 OSE and within it an Ubuntu Server 10.04 VM and Damn Small Linux VM with networking mode of both VM's as "internal". The purpose is to lab some Apache examples without sending actual queries on the real internet but only within the confines of the virtual enviroment.
Of course I could either give static IP's to both machines or have Ubuntu Server VM act as a DHCP server as well and give both machines IP. But I would really like to see VirtualBox do it for me. So far, no juice. I have tried the incantation proposed in the VBox manual, verbose as it is,with VBoxManage dhcpserver add and its proper IP address with proper net name (by default when you switch to internal networking mode your VM is in the "intnet" network) and despite the effort, VM's don't get IP addresses.
How do I get the VBox's own DHCP server hand out IP addresses to internal network VM's???

---

### Post by varelov on 2011-04-03
The mistery is taken up a notch: following the "workaround" proposed in the end- user documentation on VBox's official website, you'd add a second NIC to both machines and put them in NAT mode. Further, make those NAT NIC's default gateways for NIC's that are in the internal mode. That worked in Damn Small Linux VM but not for Ubuntu Server VM (?!) that has both cards with no IP address...
Darn, I wonder how is this solved on other virtualization platforms? Does qemu make more sense in this "VM- only network with DHCP" scenario?

---

