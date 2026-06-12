---
title: "Virtual network adapter"
date: 2010-03-14
forum: Virtualisation
---

### Post by RasterBurn on 2010-03-14
hey i am planning to set up a server on my computer using VirtualBox, the installation of the software is simple and straight forward as well as the configuration of it (for me anyways) but what i am not sure of is how to setup the network interface that VirtualBox will use, i would like to give the VirtualBox net interface its own IP address on the physical network instead of a virtual network IP

                        ```

         |-- wifes computer
         |
router --|-- my computer
         |
         |----- VirtualBox (Running on my computer) 
```

In the network settings i have 5 available choices: Not Attached, NAT, Bridged Adapter, Internal Network, Host Only Adapter

Bridged Adapter shows: eth0 & wlan0
Internal Network shows: intnet
Host Only Adapter shows: vboxnet0

so what i want to do is give the virtual machine a physical address on the network to be accessable from all the computers on the network while it is running.

the second thought on this idea is to setup multiple virtual machines and run them simultaniously with each visible and connected to each other while being accessible from the network (just an in theory thought)

so what i want to know is, what do i need to do this and how do i do this

I dont want to go and setup a physical computer just to run the services just for my purposes

---

### Post by RasterBurn on 2010-03-15
ok i have gotten the Virtual system working and on the network (aka 192.168.0.x) so it is visible on the network from any of the physical computers now i guess the next problem i am having is with giving the VM a static IP on the network.

My router is a DLink DIR-615 wireless N router, they have replaced the Static IP address system with a DHCP Reserve system (acts like Static but uses DHCP) this is a lot less configuration for setting a static IP address but unfortunately it gives me an error when i try to give the VM a reserved IP address, claims that the mac address isn't valid i was testing playing with the configurations of the VM in the network section using Bridged Adapter -> eth0 which also happens to be the interface i use as my primary connection, does anyone have any experience with giving virtual interfaces a physical static IP address on the DLink DIR-615 router?

---

### Post by dcstar on 2010-03-16
> **RasterBurn said:**
> ok i have gotten the Virtual system working and on the network (aka 192.168.0.x) so it is visible on the network from any of the physical computers now i guess the next problem i am having is with giving the VM a static IP on the network.

My router is a DLink DIR-615 wireless N router, they have replaced the Static IP address system with a DHCP Reserve system (acts like Static but uses DHCP) this is a lot less configuration for setting a static IP address but unfortunately it gives me an error when i try to give the VM a reserved IP address, claims that the mac address isn't valid i was testing playing with the configurations of the VM in the network section using Bridged Adapter -> eth0 which also happens to be the interface i use as my primary connection, does anyone have any experience with giving virtual interfaces a physical static IP address on the DLink DIR-615 router?

[LIST=1]
[*]Simply set up a Static IP address in the VM.
[*]Post all VM questions in the Virtualization forum.
[/LIST]

---

### Post by RasterBurn on 2010-03-16
oops, i must have missed seeing the virtualization forum

---

