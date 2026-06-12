---
title: "Virtualbox on Ubuntu 12.04 lts"
date: 2013-08-08
forum: Virtualisation
---

### Post by dovah on 2013-08-08
Hello everyone ):P

for working purposes I had to install a Windows 2000 virtual machine on my Ubuntu 12.04. 

For the moment, everything's working fine, but I can't understand how to connect to the Internet, something like enabling the same wifi connection that's running now on the main machine and make it working even for Win in virtualbox... if it's possible, of course! 

Thank you for your answers

---

### Post by TheFu on 2013-08-08
Virtual machines don't see the real hardware, so whatever network connection your Ubuntu machine uses doesn't matter to any virtual machine.  There are network connection settings for each VM. Just be certain to select the PRO/1000 NIC for best performance inside the VM.  Does an old version of Windows like that support a PRO/1000 NIC?  If not, I guess you can use an older AMD 10/100 virtual NIC instead.

You can use either NAT or Bridge settings for the virtual machine. Completely up to you.  Bridge means your normal network address space will be used - DHCP or static IPs.  NAT means a new subnet just for VMs under VirtualBox will be created ... another internal network layer. These work too and are a great option for out-of-date OSes like Windows 2000.

Wifi is a bad way to connect any server, BTW. But for testing and non-production uses, I suppose it will be fine.

---

### Post by papibe on 2013-08-08
Hi dovah.

By default VMs can access the Internet without a problem as the VB software acts a router for them. The other way around it's different.

There's a couple of options for accessing your VMs:
[LIST]
[*]safest: mapping ports from the host machine to the guest.
[*]easiest but not recommended: change the way the NIC is set from NAT to bridge.
[/LIST]
Hope it helps. Let us know if you need more help with that.
Regards.

---

### Post by SchnappiJedi on 2013-08-09
> **papibe said:**
> Hi dovah.

By default VMs can access the Internet without a problem as the VB software acts a router for them. The other way around it's different.

There's a couple of options for accessing your VMs:
[LIST]
[*]safest: mapping ports from the host machine to the guest. 
[*]easiest but not recommended: change the way the NIC is set from NAT to bridge. 
[/LIST]
Hope it helps. Let us know if you need more help with that.
Regards.

I like bridged mode better myself. But this is the key point to making a virtual machine connect to the internet. You need to right click your virtual machine after it is created and shutdown and click "settings" in virtualbox and then go to network. But better seen than read. Take a look here: [http://www.youtube.com/watch?v=NBFtjAzMmUM](http://www.youtube.com/watch?v=NBFtjAzMmUM)

I didn't watch it but if you do you can see how to get to the network settings menu and change the network settings on a virtualbox virtual machine.

---

