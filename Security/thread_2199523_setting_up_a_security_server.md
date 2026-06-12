---
title: "setting up a security server"
date: 2014-01-14
forum: Security
---

### Post by Coogan on 2014-01-14
This is not so much Ubuntu-specific questions, but general Linux networking and security questions.  I came to this forum because it seems my questions have a better chance of getting answered, and it's for security purposes.

I'm in the process of setting up a security server on my home network to do some packet analysis, security scanning, bandwidth monitoring, etc.  There are some limitations to the layout of my network that I've worked through, and after some Googling, I think I've come up with a solution.  However, there are some things about Linux that I'm not familiar enough with and wanted to get some questions answered and general feedback.

I'm running off a DSL connection with a static IP.  Currently I have a Netgear Wireless N router working as my border router, handling the DSL connection, DHCP server, and stateful firewall.  From here a cable runs to an upstair switch in my office closet, which has 2 Windows 7 desktops, a Raspberry Pi, and an Ubuntu server.  A Roku from my son's bedroom also connects to the switch.  Pretty much all other devices are connected via wireless (two more Rokus, a smart TV, a few iDevices).

I'd like to capture all inbound and outbound traffic on my border router, and send it to the Ubuntu server upstairs.  I have a spare Buffalo Wireless G router running TomatoUSB, and I discovered (via Google) that it can handle port mirroring using iptables to redirect in- and outbound traffic to another system:

```

iptables -t mangle -A PREROUTING -j TEE --gateway x.x.x.x
iptables -t mangle -A POSTROUTING -j TEE --gateway x.x.x.x

```

I'm not really familiar with iptables, but after reading some documentation I got the gist about what's going on with the above commands.  However, one question I have is, would the above command create a "feedback loop" if the mirrored traffic was sent out the same interface that was being mirrored?  In other words, the interface sees traffic on eth0, mirrors it out eth0, which is seen on eth0, which is mirrored again out eth0, etc, etc, etc until something catastrophically fails.

Secondly, the Ubuntu server has 3 interfaces on it, 2 of which are unused.  Preferably I'd like to send the mirrored traffic to one of the unused interfaces.  How do I set it up so that this interface would essentially be a "dumb" interface - nothing goes out of it, it's just used for receiving the mirrored data?  And does it need to be in promiscuous mode?

I've attached a rough drawing of my proposed design for feedback.  So far I have nmap and OpenVAS (+ Greenbone Security Assistant) running on it.  I've used Snort in the past, so will probably use that for security monitoring.  I'm still looking at bandwidth monitoring applications.

Any feedback or suggestions are welcome.

Thanks

Coogan

---

### Post by sandyd on 2014-01-14
Why dont you just setup the Linux server as a DHCP Server and gateway?

Things will be much easier then

---

### Post by Coogan on 2014-01-14
> **sandyd said:**
> Why dont you just setup the Linux server as a DHCP Server and gateway?

Things will be much easier then

It would also require me moving the Linux server from my upstairs office closet to my downstairs living room.  Sorry, I should've mentioned in the first post that there's not a lot of flexibility for moving equipment around or running new cable.

Coogan

---

### Post by sandyd on 2014-01-14
You wont - basically if you 

a) Disable DHCP on Netgear wireless router, setup static IP (192.168.0.2)
b) Set static IP on Ubuntu Server (192.168.0.1)
c) Setup Gateway on Ubuntu Server, set it to route to 192.168.0.2
d) Setup DHCP on Ubuntu Server, set gateway to 192.168.0.1

---

### Post by Coogan on 2014-01-14
> **sandyd said:**
> You wont - basically if you 

a) Disable DHCP on Netgear wireless router, setup static IP (192.168.0.2)
b) Set static IP on Ubuntu Server (192.168.0.1)
c) Setup Gateway on Ubuntu Server, set it to route to 192.168.0.2
d) Setup DHCP on Ubuntu Server, set gateway to 192.168.0.1

Are there any decent GUI's for the DHCP server?  I used to run it on the Ubuntu server but stopped because I got tired of having to vim the dhcpd.conf file every time I wanted to add or remove a device to the network.  The Netgear (or Tomato) GUI makes it easy to do this, as well as see if there's any unauthorized systems on my network.

I've Googled some DHCP GUIs and none that I found look very impressive.

Coogan

---

### Post by sandyd on 2014-01-14
> **Coogan said:**
> Are there any decent GUI's for the DHCP server?  I used to run it on the Ubuntu server but stopped because I got tired of having to vim the dhcpd.conf file every time I wanted to add or remove a device to the network.  The Netgear (or Tomato) GUI makes it easy to do this, as well as see if there's any unauthorized systems on my network.

I've Googled some DHCP GUIs and none that I found look very impressive.

Coogan

webmin comes to mind

---

### Post by Coogan on 2014-01-14
> **sandyd said:**
> webmin comes to mind

Yeah, Webmin occurred to me a few minutes after I posted.

Something else that popped into my mind after posting: would using your method also capture inbound traffic?  While devices on my network would be required to go thru the Ubuntu server to go out, I'm not sure if the inbound traffic would be.  Particularly the wireless traffic - I would think the Netgear would receive the inbound traffic and send it right out the access point.

Thanks for your suggestions.  It's a lot simpler than what I had planned.

Coogan

---

### Post by CharlesA on 2014-01-16
Depends on how you have it set up, if you have the Ubuntu box using the modem as the router as the gateway and tell each client to use the Ubuntu box's IP for the gateway, traffic in and out would have to pass through the Ubuntu box.

I'd probably just replace the router with the dedicated box and leave it at that, but if you can't move the machine over there, you'll have to make do with a somewhat more complicated configuration.

---

### Post by Coogan on 2014-01-17
> **CharlesA said:**
> Depends on how you have it set up, if you have the Ubuntu box using the modem as the router as the gateway and tell each client to use the Ubuntu box's IP for the gateway, traffic in and out would have to pass through the Ubuntu box.

I'd probably just replace the router with the dedicated box and leave it at that, but if you can't move the machine over there, you'll have to make do with a somewhat more complicated configuration.

Actually I've got the network changes working just as I mapped in my first post.  I haven't enabled port-mirroring on the router yet, because I need one last thing: how to configure an interface (using either route or iptables) to not allow any traffic at all to go out a particular interface, eth1 in this case.

Eth0 - "normal" traffic.  SSH, Samba, Plex Media Server, etc
Eth1 - only used to receive traffic forwarded from the router

I've actually enabled two interfaces on the system at the same time (using Eth1 as a VPN tunnel for BitTorrent) and found that I had a case of asymmetrical routing - traffic going out Eth0 and coming back in Eth1.  I can't have that happening for this application at all.  I did fix the problem with some route commands, but I don't think those would be applicable in this case.

Any suggestions on how to set eth0 as the primary interface and eth1 in receive-only mode?

Coog

---

### Post by Coogan on 2014-01-21
Ok, so after a few days of fiddling around, my original plan doesn't seem to be working.  For whatever reason, the port mirroring using iptables doesn't seem to be working.  Despite me verifying the rules are correctly set, the receiving interface is not seeing the mirrored traffic.  I don't know why it's not working, but it's not.  Additionally, anytime I try to connect to the Tomato router via web GUI or SSH, it times out.

So I had to go back to the drawing board.  I decided the best way is to set the Ubuntu system inline between the border router and the rest of the network, so modem->Tomato->Ubuntu eth1->Ubuntu eth2->Switch->rest of LAN.  This will mean moving the wireless AP (Netgear) up to my office closet, but that's manageable.  I'm assuming that means bridging eth1 and eth2, but wouldn't that also put my Tomato router on a different network and rendering it unreachable from the rest of the LAN?

Coogan

---

### Post by CharlesA on 2014-01-21
Yes, it would end up being a mess to configure because you will need to set up the *buntu box to NAT (masquerading) and the Netgear is already set to do NAT...

The Ubuntu box would work better if you just set it up as your gateway/dhcp server and used the normal router as just an access point. That way all traffic would go thru the Ubuntu box.

---

### Post by Coogan on 2014-01-21
The Netgear is not doing NATting currently; the Tomato router is handling that.  All the Netgear is doing at this point is acting as a wireless AP.

I don't have a problem setting the Ubuntu box to act as the border router, but I do **not** want to have to jerk around with iptables to handle the firewall duties.  I've played with iptables enough in the past enough to know that I hate messing with it, which is why I'd prefer to use the Tomato router and it's built-in firewall configs so all I have to do is specify any port-forwarding.

---

