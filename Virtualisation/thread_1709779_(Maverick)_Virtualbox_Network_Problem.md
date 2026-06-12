---
title: "(Maverick) Virtualbox Network Problem"
date: 2011-03-18
forum: Virtualisation
---

### Post by tessio on 2011-03-18
Hello,
I can't ping the host from the guest, and vice versa, using virtualbox-ose. I'm using bridged adapter and iptables -L shows it is accepting everything. 

Prints: [http://www.flickr.com/photos/23267339@N02/5538659448/](http://www.flickr.com/photos/23267339@N02/5538659448/) [http://www.flickr.com/photos/23267339@N02/5538659554/](http://www.flickr.com/photos/23267339@N02/5538659554/)

Ps. I can ping from one guest to another just fine.

---

### Post by tessio on 2011-03-19
Apparently the problem is that my notebook need to be physically connected (cable plugged) in the chosen bridged (eth0) interface. Only using ifconfig (ifconfig eth0 192.168.1.200/24) to give an address to that interface is not enough.
Is there something I can do to circumvent this?

Ps. I'm not trying to connect the INTERNET.. I only want to communicate my guest from the host (and vice versa) and from any guest to another.

---

### Post by lmarmisa on 2011-03-19
Your problem is related to DHCP. If you do not connect physically the computer to your LAN, no IP address will be assigned to your network interfaces and you will have no communication between the host and the guest.

If you need only internal communication among the host and the different guests consider to use the VirtualBox internal networking mode:

[http://www.virtualbox.org/manual/ch06.html#network_internal](http://www.virtualbox.org/manual/ch06.html#network_internal)

Use the command VBoxManage dhcpserver if you wish to activate the DHCP server built into VirtualBox:

[http://www.virtualbox.org/manual/ch08.html#vboxmanage-dhcpserver](http://www.virtualbox.org/manual/ch08.html#vboxmanage-dhcpserver)

---

### Post by tessio on 2011-03-21
Imarmisa: I was using ifconfig to give static ip address to my virtual adapters, not DHCP.

The problem was that the bridged interface (eth0) needed be plugged (ethernet cable attached in it). When I was using virtual box in a desktop I did not have such a problem.. but in my notebook, it occurs all the time. The solution to this problem was to switch from bridged to host-only network.
Everything is OK now.. :)

---

