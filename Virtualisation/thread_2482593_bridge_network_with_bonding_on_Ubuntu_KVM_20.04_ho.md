---
title: "bridge network with bonding on Ubuntu KVM 20.04 host"
date: 2023-01-05
forum: Virtualisation
---

### Post by devangamsunil on 2023-01-05
I have setup KVM on Ubuntu 20.04. The config i have is 2 physical NIC's, created as bond. I have used brctl to add bridge br0 and mapped to bond0. As soon as i reboot, i will loose br0. Like in vmware, i need to setup 100 VLAN's for different VM's, how can i get bridges setup for all 100 VLAN's to assign to VM's. Do we need to configure bridge details in /etc/network/interfaces or /etc/netplan? Also, how can we configure these interfaces without IP's configured for each VLAN. I'm really confused because don't find any doccumentation on setting up bond, bridge network for ubuntu for many VLANs. please help.

---

### Post by TheFu on 2023-01-05
The interfaces file is deprecated and shouldn't be used.

Netplan is how to configure networking on Ubuntu Servers since around 19.04, but don't quote me.  Best to just delete the /etc/networking directory, since leaving it will just confuse someone.  I think the only way it would still exist in 20.04, is if someone did an "upgrade", not a fresh install or if they installed the ifupdown package, which has been unsupported since 2011, even though everyone kept using it for about a decade.

Stick with 'ip' commands, not ifconfig, route, arp, which are all deprecated.

I don't use vlans nor do I bond multiple NICs into 1, so I cannot help with that.  netplan.io has examples for almost anything you might want to do.  Is there no example config for your needs?

BTW, I'd place each bond and each vlan/subnet into a separate netplan config file.  That way, if you need hundreds to **** off your customers, you can automate the creation of each config file using bash or ansible or any scripting language you like.  One of the first things I used scripts for was generating other scripts.  Nearly 30 yrs later and that is still a very common thing.

Perhaps I'm dumb, but what's the point of a vlan without any IP?  Do you not want to actually route packets into the vlan?

---

### Post by MAFoElffen on 2023-01-05
+1 with TheFu. But an answer isn't just solely concerning configuration options.

The first question is what is your basic goal for your "network plan"? What is your experience and skills with networking? (Both physical and virtual.) What is your network layout and requirements? ...Meaning who is connecting to those VM's external to the server and what is the planned network load?

AFAIK, you are going to need 1 more NIC and a Level 3 switch that supports bonding and VLAN. AND, a basic network switch from a Normal Big Box store is not going to support it physically. 

When you bond NICs it needs bonded ports to connect to on the network switch side. Does that make sense? It needs to be thought of as multiple concurrent paths bound as one path. Both the Server PC and the network switch need to understand that for that to work. A basic switch cannot handle that with a MAC table alone. The same goes for VLAN, when it come to basic switches and Level 3 switches that can read a VLAN tag and handle VLAN routing. 

A Server with a service as a Virtual Host, needs it's own NIC, then if a bridge is configured, another NIC (or NIC's if bonded) configured as that bridge. You are looking for that broadband throughput for your VM's right?

VLAN still uses IP addresses in the stack. Just a different level of control, by adding a vlan tag into the stack. The question you need to ask yourself, is if your networking requirements would be better suited with VLAN or subnetting your network to isolate traffic into segments, in your network plan... And do you have Level 3 network devices, and possibly some SR-IOV NIC's(?). The later would open up other virtual networking options.

---

