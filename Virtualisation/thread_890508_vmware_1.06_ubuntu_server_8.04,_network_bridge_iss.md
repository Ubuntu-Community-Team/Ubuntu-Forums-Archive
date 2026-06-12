---
title: "vmware 1.06 ubuntu server 8.04, network bridge issu"
date: 2008-08-15
forum: Virtualisation
---

### Post by Mr_Whippy on 2008-08-15
Hi all,

I have managed to get vmware running, with access via the mui and the server console, however i cant get the bridged network to work i have 2 network cards in the server and would like to use on for my virtual machines and one for the server itself or something similar,

however i can not get the bridged network to work i get the following error

The network bridge on device /dev/vmnet0 is temporarily down because the bridged Ethernet interface is down.  The virtual machine may not be able to communicate with the host or with other machines on your network.

thanks for any help

---

### Post by veloce on 2008-08-16
Have you got the right interface bridged?

Are they both connected to your network?

Perhaps you should bridge both (using vmware-config.pl) then, when you can see them both, eliminate the one you don't want to use.

---

