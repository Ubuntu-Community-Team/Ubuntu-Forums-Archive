---
title: "VMWare Server 2 - Best bridge solution?"
date: 2009-11-09
forum: Virtualisation
---

### Post by ol1v3r on 2009-11-09
Hello everyone,

I've recently upgraded to 9.10 x64 and it is lovely! Goes like a rocket and haven't had any problems at all with it.. Except this one..

I have a Linux firewall as a guest on my host machine. The host setup for this looks like this:

eth0 -(bridge)-> vmnet4 - LAN
eth1 -(bridge)-> vmnet5 - WAN

The LAN interface works a treat and I can access it fine from the network. The WAN interface however, does not. It's not picking up a DHCP address from my ethernet modem, but when plugged into my local network, it does pick up a DHCP address from my firewall

A little digging discovers that my modem doesn't really like more than one interface on the network and generally refuses to give out an address when asked by more than one device.

When I had this setup on Windows XP with VMWare server, I removed the protocol stacks on the network interface and my guest then picked up an IP address. However, I can't see where I can do this in Ubuntu 9.10. 

Is there anyway I can transparently pass this device through Ubuntu straight into my VMWare guest?

Any help would be really appreciated.

Thanks everyone,
Ollie

---

### Post by dcstar on 2009-11-11
> **ol1v3r said:**
> Hello everyone,

I've recently upgraded to 9.10 x64 and it is lovely! Goes like a rocket and haven't had any problems at all with it.. Except this one..

I have a Linux firewall as a guest on my host machine. The host setup for this looks like this:

eth0 -(bridge)-> vmnet4 - LAN
eth1 -(bridge)-> vmnet5 - WAN

The LAN interface works a treat and I can access it fine from the network. The WAN interface however, does not. It's not picking up a DHCP address from my ethernet modem, but when plugged into my local network, it does pick up a DHCP address from my firewall

A little digging discovers that my modem doesn't really like more than one interface on the network and generally refuses to give out an address when asked by more than one device.

When I had this setup on Windows XP with VMWare server, I removed the protocol stacks on the network interface and my guest then picked up an IP address. However, I can't see where I can do this in Ubuntu 9.10. 

Is there anyway I can transparently pass this device through Ubuntu straight into my VMWare guest?

Any help would be really appreciated.

Thanks everyone,
Ollie

If you problem is that the host is getting the WAN IP address, simply set that interface to use a Static IP.

---

### Post by ol1v3r on 2009-11-12
> **dcstar said:**
> If you problem is that the host is getting the WAN IP address, simply set that interface to use a Static IP.

Hi dcstar, thanks for the reply!

The host has a static ip of 192.168.2.1 already set (just something I made up .. No other devices on this network). 

Cheers,
Ollie

---

### Post by amadib on 2010-01-18
@ ol1v3r 

Were you able to figure this out?  I'm having the same issue with no luck :(

---

### Post by ol1v3r on 2010-01-18
Hey amadib,

Well I worked out *a* solution. Wasn't quite what I was looking for though.

I ended up purchasing a USB ethernet adapter, enabled the USB controller on my host and then attached it to my guest. Unfortunately for me, I bought one with no Linux drivers (yay!).. So I had to use ndiswrapper to get mine working.

Not the best solution in the world .. But it worked.

What sort of a setup are you looking for, amadib? The particular setup I had seemed to have issues getting a new IP address from DHCP every time I reset the modem I had it hooked up to. In the end, I purchased a Linksys WRT54GL router and put DD-WRT on there. It's been solid since I turned it on!

Good luck,
Ollie

---

### Post by amadib on 2010-01-18
Thanks for your reply.  Yeah this Bridging issue is driving me mad...

I'm running ubuntu 9.10 (2.6.31) on an AMD Athlon 64 Duel Core Processor with VMware Server v2.0.2 installed.  My wireless card is a USB Linksys WUSBGS54.

I am able to successfully bridge via eth0 and connect via NAT.  Bridging over wlan is my problem.  
I just tried this patch.
[http://blog.mymediasystem.net/uncategorized/vmware-server-2-0-1-installation-howto-for-karmic-koala-x86_64/](http://blog.mymediasystem.net/uncategorized/vmware-server-2-0-1-installation-howto-for-karmic-koala-x86_64/)
Then patched to fix the vsock problem during installation.  I don't wanna keep messing around with all these patches.  

At first I thought it was my VMs (moved over from my Windows machine), but I have been using a clean VM.  I tried modifying the .vmx file.  I have VMware Tools installed and even went as far as disabling my eth connections (I have two).  It doesn't seem to change anything.  A static IP doesn't show the VM receiving any traffic and setting to DHCP gives me the LIMITED OR NO CONNECTIVITY message with a local host only ip of 169.254.x.x.

It seems that this is a very common problem...

---

### Post by ol1v3r on 2010-01-20
Hey again,

So, is your Ubuntu box completely wireless then? Whats the plan for the VM?

Cheers,
Ollie

---

### Post by amadib on 2010-01-20
Hey there, thanks for the reply and keeping my *dream *of getting wireless to work on vmware

Not sure, would like some direction in terms of where to go from here....
It's really not practical to stretch my 40 ft cable across the house and into my box.  It's ideal to be able to make use of my existing hardware and be able to connect wirelessly.  

I have been speaking to the author of the following site and script, Radu, in hopes of helping direct me to a solution.  
[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/)

I just completed a clean install of Ubuntu on my box along with VMware 2.0.2 with a new Guest OS (Win2k3) with no luck.  I don't know if there is a recommended USB Wireless Card for VMware running on a Linux Kernel, but the whole ordeal is quite frustrating and holding me back from accomplishing any productive work.

Radu's conclusions is that I would need to incorporate my network adapter's its interfaces into VMware Server’s networking code.  

Anyone else can feel free to jump in.

---

### Post by ol1v3r on 2010-01-21
Crikey, you really have explored all the options here.. I really don't know what else to suggest.

Are you bothered about whats on your machine at the moment? If not, see if VMWare ESX supports your wireless NIC out the box.. It might not, but its worth a go!

Ollie

---

### Post by amadib on 2010-01-22
lol, just about...

I bit the bullet went to Microcenter and picked up a TRENDnet TEW-421PC card.  Works like a charm...

Thanks

---

### Post by ol1v3r on 2010-01-22
Good news! That's what I like to hear :) 

Glad you got it all sorted! :guitar:

---

