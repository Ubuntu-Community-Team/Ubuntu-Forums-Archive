---
title: "Setup virtual web server on laptop?"
date: 2010-09-20
forum: Server Platforms
---

### Post by AnUUser on 2010-09-20
Hi,

I'm running Ubuntu 10.04 server as a guest on a Windows 7 host using VirtualBox.  I've set the VirtualBox configuration to use a Bridged network connection so that I can access the internet  through the Ubuntu guest and to access the Ubuntu apache server through  my Windows host.

This is all running on my laptop which connects to various routers using dhcp (some ip addresses start with 198. while others start with 10.)

What I need is a single static ip address (or hostname/url) to setup my cms (drupal).  Any ideas how I can accomplish this given the varying routers the laptop connects to?

Thanks in advance for any help.

---

### Post by spynappels on 2010-09-21
Do you want this to be publicly available? Does it have to be accessible at all times? If so, running it in a VM in a laptop is not the best idea. It is fine for testing, but for a production system you may run into problems.

About your original question, can you please diagram your network so we can give some real help rather than just telling you to set up port forwarding to the server IP.

---

### Post by AnUUser on 2010-09-21
This is purely for testing/setup.  Once all set up and working, I will move to dedicated server.

Since this is a laptop, there is no specific network diagram as I will use this setup wherever I go with the laptop (home, work, travel).  The laptop will need to connect to the internet with either a wireless or wired connection, depending on location.  The connection will be almost always be a dhcp connection through a router.

Functionally, I need:
- Ubuntu guest to access external internet to install apps, etc.
- Windows host and any other locally networked machines to be able to access the various servers (web, ssh, etc.) in Ubuntu guest

I don't need external internet access (outside of host machine and local network) to Ubuntu guest.

Thanks.

---

### Post by spynappels on 2010-09-22
I'm not sure of how VirtualBox works with networking, I thought it used NAT, but if your VM does request an IP from whatever DHCP server is on whatever LAN you connect to, and it gets one, you can just use the IP that it gets to connect to the server from a Client computer on the same LAN.

---

### Post by CormoranTick on 2010-09-22
I don't know if VirtualBox can do this, nor if your laptop can handle it, but you can try making a second virtual machine to act as a gateway between the network and your virtual server. So say you connect to a network with a range of 192.168.2.0/24; your laptop get's an IP (192.168.2.100), then your virtual gateway gets an IP (192.168.2.101), and your virtual gateway gives your server a different static IP.

--------------------
|      Router       |
| 192.168.2.0/24|
--------------------
        \
   -----------------------------------------------
   | Laptop - 192.168.2.100 (dynamic)      |
   | --------------------------------------       |
   | | VM Gateway                          |        |
   | | eth0 192.168.2.101 (dynamic) |       |
   | | eth1 172.16.0.1 (static)          |        |
   | --------------------------------------       |
   |         \                                              |
   | ----------------------------------------     |
   | | VM Server 172.16.0.100 (static) |     |
   | ----------------------------------------     |
   -----------------------------------------------

Dunno if this is what you're looking for, but this way your server always has a static IP.

---

### Post by perspectoff on 2010-09-22
Yeah, it can be done, almost. There is a lot of work to do.

A VirtualBox virtual machine appears to the router as an independent system. You can choose to use a static LAN IP address for the virtual Ubuntu machine, but if you are changing routers all the time, this won't work too well unless they all have the same subnet scheme (such as 192.168.0.1).

Otherwise you will have to use DHCP for the virtual Ubuntu machine (always obtaining a new IP address on each LAN you visit), and this won't work for servers very well without an awful lot of tricky customization of the network, which is beyond the scope of most consumer LANs.

(PS -- in the solution in the previous post, in which a virtual gateway is created in a second virtual machine, the problem is merely transferred to the virtual gateway.)

It is very difficult to run a server if the LAN IP for the server is always changed by DHCP. Further, each router has to be configured to forward server traffic to your virtual machine. Are you going to change the port-forwarding configuration for every router you visit?

While I have a web server in a VirtualBox virtual machine on a laptop, I only use it with one router.

If your intent is to demo or work with your server while traveling, then I recommend setting up a server on a box somewhere and merely working with it using SSH/VNC from your laptop while traveling.

---

### Post by AnUUser on 2010-09-23
I ended up going with a workaround:

I setup VirtualBox with 3 network interfaces.  

Interface 1-Host Only Networking.  This is a software interface VirtualBox creates an IP that allows the Windows host and the Ubuntu guest to communicate.  I then updated the hosts file in both Windows and Ubuntu so I could give this ip a static name for Drupal.

Interface 2-Bridged Networking linked to my wired interface which gets it's ip from the dhcp.  Bridged networking allows the guest and host to communicate with each other and the outside world.

Interface 3-Bridged Networking linked to my wireless interface which also get's it's ip from dhcp.

This allows me to fulfill all my needed functionality except I can't use Interface 1 on a local network.  In those cases, I must use the ip from Interface 2 or 3 to communicate through the network.

---

