---
title: "Windows DHCP Server - Multiple Linux Boot Servers. Ehh?"
date: 2011-04-01
forum: Server Platforms
---

### Post by Roasted on 2011-04-01
I'm curious if anybody can shed some light for me in this department. We're in a large environment with a Windows DHCP Server. We have been tinkering with LTSP on Edubuntu as thin and fat clients. It works great, but right now we just have 1 server handling the lab, which works fine unless we want to expand, which may be very possible.

These are the instructions I received:

[LIST]
[*]Login to your windows server and load the DHCP configuration screen
[*]Create a DHCP reservation for the MAC address you obtained
[*]Add the configuration options below to enable the machine to boot from the LTSP server
[*]017 Root Path: /opt/ltsp/i386
[*]066 Boot Server Host Name: <ip address>
[*]067 Bootfile Name: ltsp/arch/pxelinux.0 # Specify CPU architecture in place of 'arch', for instance 'i386'
[/LIST]

From: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP)

I'm curious, what if I want to have multiple Ubuntu servers on the network that I want to have bootable? For example, let's say I have 3 labs, and 3 servers. Server A to Lab A, Server B to Lab B, and Server C to Lab C. I want all C's computers to boot to C, and B to B, A to A, etc.

1 - How would I add multiple entries on the Windows DHCP Server to allow all 3 (A B C) servers to boot?

2 - How would I be able to isolate the clients so ONLY Lab A clients boot to Server A, etc?

---

### Post by Fire_Chief on 2011-04-01
Without going into the detailed bits...you would use three different subnets for A, B, and C (and therefore three different DHCP Scopes on your Windows server configured respectively). The second half would be to use VLANs to isolate your traffic and configure DHCP helper addresses (also called DHCP proxy) to forward the requests to the Windows DHCP server.

Cheers!

---

### Post by Roasted on 2011-04-03
Not sure I follow. If we can't do subnetting with our environment already being set up, is a proxy the only alternative? Secondly, how difficult is that to set up?

---

### Post by boldford on 2011-04-03
Another simple way, avoiding VLANs etc, might be to ditch DHCP and settle for fixed Ip addresses. Unusual but doable.

---

### Post by Roasted on 2011-04-04
> **boldford said:**
> Another simple way, avoiding VLANs etc, might be to ditch DHCP and settle for fixed Ip addresses. Unusual but doable.

2,000 systems here at work.

This certainly falls under undoable.

Any other suggestions to make this work?

---

### Post by Fire_Chief on 2011-04-04
> **Roasted said:**
> Not sure I follow. If we can't do subnetting with our environment already being set up, is a proxy the only alternative? Secondly, how difficult is that to set up?

It was not meant to be two separate approaches but two steps in conjunction to accomplish the network isolation setup.

The other option is to configure the labs as isolated networks where each lab subnet has its own DHCP server configured.

If you prefer to keep DHCP on the single server, let me know how your networking is configured and we can workout the config changes needed to implement the vlans and DHCP proxy bits. DHCP proxy is typically configured on the network switch or the subnet default gateway. All it does it receive the DHCP requests from the clients and pass it along to a specified DHCP server on another subnet to assign the address to the client.

Cheers!

---

### Post by koenn on 2011-04-04
> **Fire_Chief said:**
> 
The other option is to configure the labs as isolated networks where each lab subnet has its own DHCP server configured.

how about 1 dhcp with multiple NICs, 1 in each subnet ?


although long term, with 2000 hosts and with future expansion "quite possible", VLANs and a bit of network redesign maybe isn't a bad idea

---

### Post by Roasted on 2011-04-07
After discussing it more, I think that's what we're doing, is giving each server it's own DHCP service with its own scope, and VLAN'ing it from the rest of the network. I suppose it makes sense, to have 1 VLAN per lab. I hear of some schools doing this anyway. Now that we're doing this it does make more sense. I guess I just need to read up more on VLANing. :P

---

