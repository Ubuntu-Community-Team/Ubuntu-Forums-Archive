---
title: "Kubuntu 9.04, VirtualBox 3.04 and Freenas"
date: 2009-08-07
forum: Virtualisation
---

### Post by emamm on 2009-08-07
Hello

I am trying to get freenas under Virtualbox to work with my pc box running kubuntu 9.04.  As far as I know VirtualBox doesn't need any more messing around with the network interfaces, so the only thing I did was to sudo usermod -a -G vboxusers username.

Then I have downloaded the lastest stable version of freenas (livecd with the option of full install) and gone through the  installation process. 

As part of the installation, there is an option to set LAN Ip address which gives the option of using dhcp (which I did). Unfortunately the result was 0.0.0.0  .   The network settings on VB are:
a) PCNet-PCI II
b) bridged adaptor ->  I need this one (not NAT)
c) eth0

I have no idea of what could be wrong.  Any suggestions?

Many thanks

Ed

---

