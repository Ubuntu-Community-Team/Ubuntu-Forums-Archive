---
title: "Remote Administration:  Getting By Routers and Port Forwarding"
date: 2009-06-19
forum: Security
---

### Post by Z3ro3X on 2009-06-19
I often times have to administer a family members PC.  Talking them through stuff on the phone is a pain in the butt and takes up loads of my time.  Most of the stuff I say goes over their heads.  So I found it easier to just enable Remote Desktop in gnome.  I have the option enabled to "Configure network..." which works for the most part in using UPnP to forward the necessary ports.  Problem is my sister has been connecting to a router that this isn't working with.  It's not her router (might be a Starbucks or something) so enabling UPnP on the router or doing any manual port forwarding is out of the question.

So the question is, how can I get her computer to connect to mine any time she gets online?  I want to be able to use SSH and Remote Desktop.  Can I have her machine tunnel to mine (which I can open ports for) instead of me trying to connect to her?

---

### Post by bodhi.zazen on 2009-06-20
I have three suggestions (in order what IMO is most to least secure).

1. You can set up an openVPN server.

2. Tunnel over ssh. You set up a ssh server, she ssh in 

[http://blog.bodhizazen.net/linux/how-to-vpn-using-ssh/](http://blog.bodhizazen.net/linux/how-to-vpn-using-ssh/)

With these first 2 you run the openvpn or ssh server and she connects. Once she is connected her computer will be connected to you LAN.

3. Start a VNC server on her computer with -listen. 

[http://www.ubuntuforums.org/showthread.php?t=299489](http://www.ubuntuforums.org/showthread.php?t=299489)
 
[http://www.dotmana.com/index.php/?p=336](http://www.dotmana.com/index.php/?p=336) 

Keep in mind, if you go with VNC, use a strong strong password (VNC is one of the most commonly cracked servers on these forms).

---

### Post by Tamara Perera on 2009-06-20
There are several debugger in windows so the hackers can easily administrate the PC breaking the firewall. For ubuntu it seems to be quite impossible. The routers and port forwarding seems to be comfortable & safe for me. Thanks for the resource.

---

### Post by Z3ro3X on 2009-06-20
I'm trying option 1 mostly just for the learning experience.

I'm using the article at [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN) as a reference on how to do it.  When editing /etc/network/interfaces it says to put...

#####################################
## This is the network bridge declaration
auto lo br0  ## start on boot

iface lo inet loopback

iface br0 inet static 
  address 192.168.1.10 
  netmask 255.255.255.0
  gateway 192.168.1.1
  bridge_ports eth0

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down
#####################################

If I understand it correctly, it's creating a bridge between a virtual adapter interface and the adapter interface that I use for connecting to the Internet.  In my case the cable modem is connected to a wireless router.  Which would make the adapter interface wlan0.  So /etc/network/interfaces should read...

#####################################
auto lo br0
iface lo inet loopback

iface br0 inet static 
  address 192.168.1.10 
  netmask 255.255.255.0
  gateway 192.168.1.1
  bridge_ports wlan0

iface wlan0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down
#####################################

If I'm doing this wrong, please let me know.

Now for /etc/openvpn/server.conf

I need to know (for my case) what to put for...

local <your ip address> ## ip/hostname of server

and...

push "dhcp-option DNS your.dns.ip.here"
push "dhcp-option DOMAIN yourdomain.com"

The goal is to get other computers across the Internet to connect to my system.  My public IP changes every now and then.  So I set up a domain with dyndns and I have ddclient updating my IP when it changes.  Do I need to reflect that when setting up the OpenVPN server or does that only matter on the client side?

---

### Post by kevdog on 2009-06-22
Do you want to create an OpenVPN bridge or route?  I believe in most cases people want to use OpenVPN routing and not bridging.

---

### Post by Z3ro3X on 2009-06-25
> **kevdog said:**
> Do you want to create an OpenVPN bridge or route?  I believe in most cases people want to use OpenVPN routing and not bridging.

I'll try a route.  I tried doing a bridge and nearly messed up my networking configuration.

---

### Post by scorp123 on 2009-06-27
> **Z3ro3X said:**
>  So the question is, how can I get her computer to connect to mine any time she gets online?  I want to be able to use SSH and Remote Desktop.  Can I have her machine tunnel to mine (which I can open ports for) instead of me trying to connect to her? Try "Gitso":
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

What it does: It opens a "reverse VNC tunnel" to your machine. All you have to do is to make sure that the necessary ports are open on _YOUR_ side.

I am using Gitso to support my wife's parents ... they live 1200 km away. And with "Gitso" it just works, I don't have to bother to talk them through any settings, I just need to open the client on my side and voila: I can see their desktop.

---

