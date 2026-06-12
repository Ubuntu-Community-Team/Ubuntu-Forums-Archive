---
title: "No internet on brand new install in Vmware?"
date: 2016-01-06
forum: Virtualisation
---

### Post by cincibluer6 on 2016-01-06
I already have one Ubuntu server set up on our VMware doing IPAM but I installed a DE on it so my other cohort could use it (he's not savvy with the terminal.)
I'm setting up a new one though that he shouldn't need to deal with and I can't get internet even with leaving DHCP on. I can request and receive a lease but I can't ping anything (gateway, google, etc.)
I set it to static in /etc/network/interfaces and it takes but still no dice on internet or anything else.

I really don't want to have to install a DE simply to use networking. Just not sure where the issue is. Right now I'm ruling out VMware as this setup is working fine on the other VM (and a whole slew of others with this vmnic.)

Edit- forgot to include I can't ping out and nothing can ping to it. I saw it had a DHCP lease and when I moved to static, that address is in an exclusion range.

---

### Post by darkod on 2016-01-06
Just "follow the route"... How is your setup, which device is doing the main routing and internet access? Did you select correct type of virtual network adapter (compare with the other VM) and is that virtual adapter part of the correct vSwitch (if you have more than one)?

This is not about whether you have DE or not. Something is missing/wrong with the networking setup/layout...

---

### Post by MAFoElffen on 2016-01-06
RE: Ubuntu server installed as a VM in VMware ____ (<-- OP did not specify which VMware "product" was used for hypervisor)

Most hypervisors are basically the same virtual networking concepts, but different names and nomenclature for those same concepts.

In the case of VMWare hypervisor products, the 3 basic options of their vlan are:

(1) Bridged Networking - Bridged networking connects a virtual machine to a network using the host computer's Ethernet adapter. Note that the Vm's will be on the same NID as the host so can communicate between VM, Host, and anything that host can communicate with.


(2) Network Address Translation (NAT) - NAT gives a virtual machine access to network resources using the host computer's IP address. All VM's using this option will be assigned a NAT IP address if dhcp or use a static address of the same NID. Note that the VM's using this option will be on another network segment (different NID) than the host computer. It uses NAT translation though the hosts NIC...

(3) Host-Only Networking - Host-only networking creates a network that is completely contained within the host computer. These will get a dhcp IP of the default vlan NID (or static if manual set to that same NID), but does not have access to the outside world ... 


That is the basics. 

*** Like other virtual hypervisors, you can get very detailed in a "custom" virtual networking where you could create an enterpise vlan. Option #3 does not have access to the outside world, but ... you can create a bridge or route across from that that NID to the hosts NID through one of thosee VM's (with a second virtual NIC) or through a virtual network switch... (or other virtual network appliances).

If you do not set/reset any networking options when you create your VM, it's default selected networking option is #3. (access to other VM's, but not the outside world...) So, (the short answer) out of the box, VMwares default option to get to the outside world is to select VM network setting "NAT." Limited, but gets you to the internet. Optimal would be to do further configuration to create a bridge (virtual switch) and use bridged networking.

As virtual networks go... If you are just do testing and need to protect from your own network, then #3 is good. If you are just trying out a VM and need an internet connection, option #2 is enough. If you need to connect to the VM from your own network, then you need #1 or a custom virtual networking solution.

If you need further specifics and info:
[VMware Virtual Networking Concepts (pdf)]("https://www.vmware.com/files/pdf/virtual_networking_concepts.pdf")
[VMware Workstation - Configuring virtual networks]("https://www.vmware.com/support/ws55/doc/ws_net.html")

EDIT-- A moderator should please move this thread to the Virtualization Section to get more exposure there.

---

### Post by cincibluer6 on 2016-01-07
So dumb. Booted it up this morning (no changes) and it works. I swear, VMware sometimes...
Thanks for the help guys. Apparently I had it right but leaving it sit all night has helped (as I had rebooted it a few times prior with no luck.)

---

### Post by MAFoElffen on 2016-01-07
Congratulations.

Please revisit this thread, and use the Thread Tools link in the upper right of the page to mark this thread as solved.

---

