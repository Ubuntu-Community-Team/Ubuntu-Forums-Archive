---
title: "How do I set up the network settings for Ubuntu Server 9.04"
date: 2009-10-11
forum: Server Platforms
---

### Post by sparkyjoe38 on 2009-10-11
Hello everyone,

Let me just say first off that I am a newb to working with Ubuntu servers and I have setup Ubuntu Server 9.04 on my extra pc. I am following the tutorial from the [howtoforge.com]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2-p3") site. It's telling me to configure the network from vi /etc/network/interfaces. I understand how to find and edit the file with vi but I don't know what settings I am supposed to enter for my network. etc...> # The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1I am assuming I would be entering information from my Linksys router (WRT54G) and understand how to access my admin panel for the router but I am unsure of what information I am supposed to enter for the above network interface. Could someone please help me out with this and please dumb it down for me since this is new territory for me? Thank you very much in advance!

---

### Post by Iowan on 2009-10-11
If you have another machine on the network (I noticed the "extra" PC), you might find some useful information from it - otherwise, the router can provide what you need.  The router address will likely be something like 192.168.1.1. (If it happens to be 192.168.0.1, your sample might work OK). The router might also be your DHCP server - in which case, you will need to discover what range of addresses it gives out. Your server address will need to be *outside* this range - so if your DHCP server (router) uses the range 100-200, your server should have address <99 or >200. 
   Another option is to let the server get it's address via DHCP and configure the router to issue it a fixed IP address (static lease). 

Alternately, you can find the IP address on the other PC and (probably) derive much the same information. Details if you wish...

---

### Post by jonabyte on 2009-10-11
in this case use dhcp over a static ip.

---

### Post by sparkyjoe34 on 2009-10-12
Ok I've setup my server to get its address via DHCP from my router. Having done that, if I reboot my server the router will automatically reassign a new address correct?

---

### Post by Iowan on 2009-10-12
Well... maybe.  But it *might* reassign the same address (probably what you want, anyway). To insure that the server gets the same IP address, the router can (probably) be configured to issue the same address (based on MAC address).

---

### Post by f00b on 2009-10-12
Ok, not to hi-jack this thread, but it seems like a waste to start a new one.  I have almost the same question.

My ISP gave me this information about the IPs I have

 WAN:   66.xx.xx.xxx 
        70.xx.xx.xx/xx
 GateWay:   66.xx.xx.xx
 Mask:   255.255.255.xxx
 DNS:	  64.xx.xx.x
 DNS2:   64.xx.xx.x

I am guessing GateWay goes in for "gateway" below, but which of the other ip's go where in the interfaces file:

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

---

### Post by Iowan on 2009-10-12
You may not need the "network" and "broadcast" options - otherwise, they will depend on the address and netmask. DNS addresses will go in */etc/resolv.conf*
I'm not quit sure what to make of the 70.xx.xx.xx/xx address - it doesn't seem to fit with the 66.xx.xx.xx network (I presume the /xx is CIDR notation).

---

### Post by sparkyjoe34 on 2009-10-13
How would I go about that

---

### Post by Iowan on 2009-10-13
Most routers have a configuration page accessible as http://<router-ip-address >. Under the DHCP server settings is (usually) an option to "assign fixed address". The address you choose should be *outside* the range used for leases by the DHCP server (that information should be available in the same general area).  
Sorry to be so generic, but I haven't set up a lot of routers, and don't remember the exact page layout of those I have set up. Good luck, though...

---

