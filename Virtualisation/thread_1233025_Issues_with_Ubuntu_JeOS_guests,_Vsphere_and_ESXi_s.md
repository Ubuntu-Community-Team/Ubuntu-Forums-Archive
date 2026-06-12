---
title: "Issues with Ubuntu JeOS guests, Vsphere and ESXi server"
date: 2009-08-06
forum: Virtualisation
---

### Post by supervaca on 2009-08-06
Hi all!


I'm just starting to deal with virtualization and networking. First of all, i'll try to explain the scenario i'm working on. I have a Dell host running ESXi server for virtualization and one WinXp machine that remotly connects to the server through VSphere. 

 For the virtualization project, i've set up two VMs with Ubunt Server JeOS. I've also created two vswitches, one that has connectivity to the pNIC and the other one which not. The last one implements a vLAN (10.0.0.x).I'm trying to have external access with the first one (internet sessions run through a corporative proxy). 

 Therefore i've modified the guest files /etc/networking/interfaces and /etc/resolv.conf. I've also set the HTTP_PROXY variable. I get no ping answers this way (network is unrecheable). In fact, sometimes, when i edit those files i loose vSphere connection. Cheking the host everything seems to be allright, and the only way to recover the remote connection is restarting the ESXi server. 

Previously, i had worked with VMware Workstation and getting the VM connectivity was quite simple and transparent. Just setting in the virtual machine properties the NAT option everything worked.



Any tip or comment will help. Hope to get some answers...

 
 

Thanks in advance and kind regards,

 Eduardo

---

