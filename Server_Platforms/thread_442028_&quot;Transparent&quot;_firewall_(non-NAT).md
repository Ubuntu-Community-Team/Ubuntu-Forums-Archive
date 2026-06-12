---
title: "&quot;Transparent&quot; firewall (non-NAT)"
date: 2007-05-13
forum: Server Platforms
---

### Post by Selmer79 on 2007-05-13
I posted this topic in the networking-forum yesterday ([http://ubuntuforums.org/showthread.php?t=441090](http://ubuntuforums.org/showthread.php?t=441090)), but it's just drowning in "can't get my wireless to work" posts, and I guess it's really more appropriate in this forum..

I've been asked by my old computer-club if I could help them by being the net-admin on their next major LAN-party. I have told them I'll look into setting up the server for them, but I can't really be arsed to go to the LAN-party (I'm too old for that kinda thing now).

I was thinking about setting up a Feisty server for them that lets every internal PC have a valid external IP for IRC and such.

Last year they used ClarkConnect, but it has some exotic firewall-scripting that means you can have everyone with their own external IP, but then there is no firewall, or you can have a firewall, but then everyone share the gateway's external IP.

I'll draw up a schematic of what I want:
```
[CENTER]
Internet
|
IP: 4.3.2.1
Gateway
IP: 4.3.2.2
|
LAN
DHCP 4.3.2.10-126[/CENTER]

```IPs 3-9 would be reserved for managed switches.

The result I'd like to get is that the firewall should prevent party-goers from bringing the internet-connection to it's knees with P2P, but people would still have their own external IP so that they can IRC without getting kicked off servers from too many concurrent connections.

Please be gentle, as it's the first time I set up a router like this.

---

### Post by PilotJLR on 2007-05-13
The addressing scheme you're proposing would require only a switch past the cable modem (or DSL or whatever), because all of these addresses are in one big subnet. This would also prevent you from having any gateway control, since traffic destined outside your subnet would presumably go direct to the ISP gateway.

If you want everyone to have a public address, the service provider would need to sell you a block of public addresses. A few hundred of these would be expensive.

But basically, you would need an ISP-assigned address for your gateway's WAN, then an ISP-assigned subnet with which to assign to your LAN. This could be done without NAT, but then would still require internet destined traffic to pass from your internal public subnet through your feisty gateway and then off on its journey.

---

### Post by Selmer79 on 2007-05-13
> **PilotJLR said:**
> The addressing scheme you're proposing would require only a switch past the cable modem (or DSL or whatever), because all of these addresses are in one big subnet. This would also prevent you from having any gateway control, since traffic destined outside your subnet would presumably go direct to the ISP gateway.
A switch behind the modem wouldn't give me a firewall to choke P2P or protect the internal LAN from attacks..

So what you're saying is that it has to look like this?
```
[CENTER]
Internet
|
IP: *.*.*.*
Gateway
IP: 4.3.2.1
|
LAN
DHCP 4.3.2.10-126[/CENTER]

```> **PilotJLR said:**
> If you want everyone to have a public address, the service provider would need to sell you a block of public addresses. A few hundred of these would be expensive.
Getting the IPs is no problem. The ISP gave us a full subnet to play with last year.

> **PilotJLR said:**
> But basically, you would need an ISP-assigned address for your gateway's WAN, then an ISP-assigned subnet with which to assign to your LAN. This could be done without NAT, but then would still require internet destined traffic to pass from your internal public subnet through your feisty gateway and then off on its journey.
And as far as I can tell, what you say here is exactly what I want. No NAT, but traffic still passes through a gateway (Feisty server) for shaping.

---

### Post by PilotJLR on 2007-05-13
> **Selmer79 said:**
> A switch behind the modem wouldn't give me a firewall to choke P2P or protect the internal LAN from attacks..

Exactly my point  :-)



Your diagram is correct... just need to keep the WAN and LAN on different subnets... if your ISP will give you the addresses for that, then you are all set.
This way, you are not using NAT; clients are still connected because your public subnet is in your ISP's routing table.
And your clients must use your gateway, since it is the only means to leave their local subnet.

---

### Post by Selmer79 on 2007-05-13
OK, I just got off the phone with one of my linux-friends, and he walked me through the entire gig..

Here it is:

For starters, open **/etc/sysctl.conf** and look for:
```
#net.ipv4.conf.default.forwarding=1
```and uncomment it.

Connect a client to one of the NICs and try to ping the other NIC.

If Ping is successful, your server is forwarding packets.

Then type **iptables -t nat -L**. If you get any output then your box is NAT'ing, if not then it's doing plain forwarding (what I wanted).

- Set up the Gateway's external IP with whatever you need to get it up and running on the internet.
- Make sure the ISP is forwarding all packets destined for your C-net to the external IP of the gateway.
- Set up the Gateway's internal IP to an address in the C-net you have aquired. (*.*.*.1 is a good choice.)
- Assign fixed addresses to routers and servers that need it.
- Set up the DHCP pool to assign the remaining addresses.
- Start scripting blocking-rules in **iptables**.

That should be it.. Do you see anything missing?

(PS: My friend walked me through how it is on Red Hat Server, so paths and configs might be different.)

---

### Post by Frosty Cold Drink on 2007-05-13
I think subconciously you want a bridging firewall. It won't be a router but will sit in the routers position. It will simply bridge 2 segments of the pysical network (internal LAN to WAN coming from your uplink). If you do this your clients can get IP addresses directly from the ISP.

---

### Post by PilotJLR on 2007-05-13
Yep, sounds very good!
Turning on IP routing is slightly different in debian based systems, as opposed to Red Hat. What you'll need to do is:
```

sudo -s
echo "1" > /proc/sys/net/ipv4/ip_forward

```

---

### Post by Frosty Cold Drink on 2007-05-13
It should be both methods. ecoing to /proc enableds it immediately. Editing the value is sysctl.conf tells the startup scripts to set the value on following boots.

---

### Post by Selmer79 on 2007-05-13
Now I just need to find a way to test it.. Theory is no good unless it actually works! ;)

---

