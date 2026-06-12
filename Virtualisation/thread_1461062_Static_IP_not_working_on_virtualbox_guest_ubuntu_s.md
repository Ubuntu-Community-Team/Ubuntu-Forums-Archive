---
title: "Static IP not working on virtualbox guest ubuntu server"
date: 2010-04-23
forum: Virtualisation
---

### Post by Ravenamp on 2010-04-23
I am trying to set up a server on a virtual machine (Sun VirtualBox). I've set the LAN-adapter in virtual machine settings to "Bridged" so that my virtual machine will not be behind NAT and be reachable from/to my entire network. I really do NOT want to fool around with NAT and port-forwarding as this server should become a DNS/DHCP server for my internal network and should be completely open for practical reasons. I have my reasons for making a virtual machine for this, but I'd like to keep this short, unless someone insists :) 

The server gets a DHCP-address from my router (10.0.0.254) and I can access the internet from it. Ping, update, wget, they all work. But as soon as I enter the static IP settings in /etc/networking/interfaces it refuses to assign those settings to eth0. I've done this many times before in the past and I don't understand what's going wrong this time. Eth0 does not get an IP at all or it just seems to keep the DHCP-address but then refuses to connect to the outside world (my internal network). When I put it back on DHCP it's all fine again...

This is my config:
==================
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Static IP
iface eth0 inet static
address 10.0.0.1
network 10.0.0.0
broadcast 10.0.0.255
netmask 255.255.255.0
gateway 10.0.0.254


# DHCP stuff
#auto eth0
#iface eth0 inet dhcp
=========

I compared these with the DHCP-settings on both the virtual machine as well as my regular desktop. They all match, except for "network" which I can't seem to find anywhere except for in the interfaces cfg-file and on tutorials on the internet about interfaces config. Going on that I assumed it should be 10.0.0.0.
This is not the first time I'm trying to assign a static IP. I remember a long time ago I had a similar problem once. I remember issueing a command to purge something, but I can't seem to find such a command in the ifconfig man-pages. On the other hand, I succeeded many times before on physical machines, this is actually the first server I am trying to run as a virtual machine. It sounds plausible to me that virtualbox is f*cking around with me somehow, somewhere...

I really hope my problem can be solved somehow. Is there anyone here that has some experience with this?

---

### Post by JKyleOKC on 2010-04-24
In your VM settings, when you select bridged, do you have the "Name:" set to the interface name used by the host? I've had similar problems from time to time and most of the time it was because I did not have the VM's network settings properly chosen.

I even have had to use the "NAT" choice from time to time, and on at least one occasion just a few hours ago found that switching to NAT from bridged made things work, and when I then switched back to bridged, they kept working!

---

