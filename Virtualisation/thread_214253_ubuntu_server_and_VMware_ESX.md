---
title: "ubuntu server and VMware ESX"
date: 2006-07-12
forum: Virtualisation
---

### Post by Gorante on 2006-07-12
Hi, I'm trying to install Ubuntu Server over a Virtual Machine based on VMWare ESX.

I'm stuck at the first installation steps by the way, Ubuntu infact doesn't recognize the Ethernet card "installed" on the Virtual Machine.

The odd part is that Ubuntu Server installs without any problem under VMWare Workstation.

Anyone knows if there is a reason for that?
The driver that it should use is Pcnet32

I obviously could try to install everything without ethernet support, and to fix the configuration after, but i'm trying to get an installation template usable even by other people.

Thanks

---

### Post by Dragonmantank on 2006-07-20
I am actually setting this up at work. What you need to make sure is that you start with the 'vlance' NIC as the default (it's a standard AMD PCnet32 card that Workstation uses). From there, install the VMWare Tools, and then you can switch the NIC to the vmxnet to use the gigabit card. 

We had this issue with our CentOS installs that we are trying to get going. The IBM guy who is our point of contact stressed to always start with the vlance driver and then switch to vmxnet.

As a side note, I'm using ESX 2.5.3 patch2.

---

### Post by Azzuron on 2008-02-08
How would i go about fixing this type of error once its in a virtual machine? My VM was in vmware-server, we have an esx server now, and i need to get the nic up on the esx server but its not detected, installing VMware tools didnt seem to help, not sure what the process is for this. thanks for any assistance you can provide.

 --Dave

---

