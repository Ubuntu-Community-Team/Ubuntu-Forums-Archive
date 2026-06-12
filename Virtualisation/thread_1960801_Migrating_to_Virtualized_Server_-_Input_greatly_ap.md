---
title: "Migrating to Virtualized Server - Input greatly appreciated."
date: 2012-04-18
forum: Virtualisation
---

### Post by mhaedo on 2012-04-18
Hey everyone.  Long time reader first time poster, as the saying goes.  I am in the planning stage of moving several servers into guest OS's within a KVM hypervisor.  Any criticism would be greatly appreciated, since I am not sure if I am going in the right direction.

Here is my plan:  WAN connection goes into Cisco ASA 5505 firewall.  One LAN port goes to hypervisor eth0 (192.168.1.2).  Two PoE (power over ethernet) LAN ports go to IP cameras.  One LAN port goes to eth2 for secure guest OS on an IPSec VPN tunnel.  This guest OS should be isolated from the hypervisor completely.  The hypervisor should not have access to the network it is on.

The other three guest OS's will be on the same subnet as the rest of my LAN, 192.168.1.x.  The hypervisor will have another NIC, eth1, with another IP on the same subnet to connect to a gigabit switch and communicate with the rest of the LAN.  It would make more sense to use the ASA to network everything on the LAN, unfortunately it does not support gigabit ethernet.

Does this setup make sense?  Also, I would like to have a software firewall for additional IDS/IPS purposes.  Does it make more sense for the hypervisor to perform this function, or should I have a separate guest OS as my 2nd firewall?

Once again, any help pointing me in the right direction would be very much appreciated.  I enjoy doing the leg work getting everything set up.  Man pages are my best friend ;)  However, I want to make sure the solution I am attempting makes sense before I spend hours implementing it.

Thanks in advance.  A rough sketch of my plan is below.

[IMG]http://img849.imageshack.us/img849/9057/virtualized.jpg[/IMG]

---

### Post by dcstar on 2012-04-18
> **mhaedo said:**
> Hey everyone.  Long time reader first time poster, as the saying goes.  I am in the planning stage of moving several servers into guest OS's within a KVM hypervisor.  Any criticism would be greatly appreciated, since I am not sure if I am going in the right direction.
..........
Thanks in advance.  A rough sketch of my plan is below.


Over-complicated, just connect the Gig Ethernet switch into the Cisco and everything else into the switch.

---

### Post by mhaedo on 2012-04-18
> **dcstar said:**
> Over-complicated, just connect the Gig Ethernet switch into the Cisco and everything else into the switch.

Thanks for the quick reply.  One of the things I was hoping to accomplish was using one of the guest OS's as a second layer of firewalling with enhanced IDS/IPS functionality.  If I were to continue going in that direction, do you have any other suggestions?

---

### Post by mhaedo on 2012-04-18
I should also mention that I don't mind a complicated setup.  This is not a mission critical project.  I look it as more of a learning opportunity.  I would like it as simple as possible while still accomplishing the following:

- Utilize Cisco ASA 5505 as firewall and use PoE ports of ASA for IP Cameras
- Use Linux for extra layer of firewalling / IDS / IPS and logging.
- It would be preferable to have IP cameras behind the Linux firewall as well, but I'm not sure how I would route from the ASA to Linux box and back to ASA to go through PoE port.  Is this possible?
- Have secure guest OS on VPN completely isolated from hypervisor.  Hypervisor should not have access to its network.  This is necessary to maintain PCI DSS compliance.
- Have separate guest OS's perform separate functions on server.
- Ever node on LAN (with possible exception of IP Cameras on PoE ports) should be behind Linux firewall.


That being said, am I headed in the right direction with my initial chart?  Is there a better way to accomplish this that I have overlooked?

---

### Post by OliverHaslam on 2012-04-19
I'm not here to really offer any meaningful help, other than to say I can't wait to see where this goes!

I get the impression you are very much like me - creating all kinds of weird and wonderful setups in order to learn as much as possible. I know it's odd, but this really gets my juices flowing :)

Be sure to keep us up to date on what you do and how it goes, I'm looking forward to seeing how it pans out.

Good luck!

---

### Post by mhaedo on 2012-04-19
> **OliverHaslam said:**
> I'm not here to really offer any meaningful help, other than to say I can't wait to see where this goes!

I get the impression you are very much like me - creating all kinds of weird and wonderful setups in order to learn as much as possible. I know it's odd, but this really gets my juices flowing :)

Be sure to keep us up to date on what you do and how it goes, I'm looking forward to seeing how it pans out.

Good luck!

Thanks for the encouragement :)  It should definitely be a fun project.  Normally with something like this I just jump in head first and learn as I'm going.  Unfortunately one of the servers I am virtualizing runs runs my IP cameras, all of my lights, and timers for turtles/lizards.  It would be very inconvenient for it to be down for an extended period of time.

I'd hate to start start implementing this setup only to have someone point out there was a better way to do it.

---

### Post by mhaedo on 2012-04-20
Perhaps I should tackle this one step at a time.  My main question: should my firewall be on my hypervisor or on a separate guest OS?

---

### Post by dcstar on 2012-04-20
> **mhaedo said:**
> Perhaps I should tackle this one step at a time.  My main question: should my firewall be on my hypervisor or on a separate guest OS?

You already have a Firewall, it's called a Cisco ASA.

---

### Post by mhaedo on 2012-04-20
> **dcstar said:**
> You already have a Firewall, it's called a Cisco ASA.

The ASA is a capable firewall in some areas.  I have deployed several of them.  However it is incapable of IPS/IDS without an additional module which is very costly.  The Cisco ASA AIP SSC-5 retails for $1,283.99 from CDW.  This is currently out of my budget for my home network.

A well hardened Linux firewall running apf/snort will be a more cost effective solution for me.  That being said, is it preferable to have apf/snort running on my hypervisor or completely separately within a guest OS?

---

### Post by OliverHaslam on 2012-04-20
> **mhaedo said:**
> The ASA is a capable firewall in some areas.  I have deployed several of them.  However it is incapable of IPS/IDS without an additional module which is very costly.  The Cisco ASA AIP SSC-5 retails for $1,283.99 from CDW.  This is currently out of my budget for my home network.

A well hardened Linux firewall running apf/snort will be a more cost effective solution for me.  That being said, is it preferable to have apf/snort running on my hypervisor or completely separately within a guest OS?

I'm afraid this thread may turn into a learning process for the pair of us. I hope you don't mind a semi-hijack do you?

I'm curious why you want extra firewall capability. I just use the NAT/Firewall build into my router. Granted, there's nothing sensitive inside my network, but curious still.

---

### Post by mhaedo on 2012-04-20
> **OliverHaslam said:**
> I'm afraid this thread may turn into a learning process for the pair of us. I hope you don't mind a semi-hijack do you?

I'm curious why you want extra firewall capability. I just use the NAT/Firewall build into my router. Granted, there's nothing sensitive inside my network, but curious still.

Not at all my friend :)  A well configured firewall blocking ports and restricting traffic to others is an important layer of security.  An IDS is a completely separate layer that detects patterns, or signatures, of malicious content.  Depending on your configuration it can alert you to suspicious activity or traffic patterns.

My Cisco ASA 5505 is a great firewall.  However it cannot do something as basic as prevent a brute force attack on one of my servers.  Sure, I am able to do quite a bit to mitigate the risk by securing passwords and restricting source IP addresses.  However I want the additional capabilities and information an IDS/IPS provides.

---

