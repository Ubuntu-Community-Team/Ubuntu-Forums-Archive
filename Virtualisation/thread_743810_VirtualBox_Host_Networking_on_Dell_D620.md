---
title: "VirtualBox Host Networking on Dell D620"
date: 2008-04-03
forum: Virtualisation
---

### Post by rgrashel on 2008-04-03
For context, I have a Dell D620.  It has a hardwire network interface (eth0) and a wireless network interface (eth1).  

I have an image of Windows XP created with VirtualBox.  What I am wanting to do is use host networking on both eth0 and eth1.  Sometimes I am connected hardware (eth0) and sometimes wireless (eth1)... therefore  I'd like the guest to consume both bridge connections.   

I am connected to a corporate network, so I want my Windows XP guest to acquire an IP address through DHCP from my corporate network.  This will allow my guest to be on the same subnet as the host.

Up to this point, I have tried seven different how-tos for creating a bridge network.   In all cases, I would just repeat the steps for eth0... using eth1.  So in my case, I'd end up with tap0 pointing to br0 and tap1 pointing to br1.  I set up the VirtualBox configuration for Interface 1 to look at tap0 and interface 2 to look at tap1.

In all cases, my guest XP image will not acquire an IP address.  They just fail out and end up with a 169.x.x.x IP address.

Has anyone out there done a successful host networking install with VirtualBox on a laptop which has both hardwire and wireless network interfaces?  If so, please help me out and let me know what you've configured to get this to work.  At this point, I'm getting ready to jump to VMWare to see if they can handle this situation more elegantly and with more ease.

Thanks!

---

### Post by Amorget on 2008-04-08
Did you ever get this working?

---

### Post by rgrashel on 2008-04-15
No, I never did get this working on VirtualBox, unfortunately.  So, I gave up on it and moved to VMware.

I think VirtualBox has some decent potential, but when it comes to networking, it needs to mature.  This is where VMware shines.  You can actually do a fair amount of complicated networking setups using VMware tools without ever hitting the command line and becoming a routing expert.

I look forward to seeing how VirtualBox grows in the future.

---

