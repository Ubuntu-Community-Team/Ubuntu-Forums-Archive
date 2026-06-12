---
title: "Host-only network with multiple VMs"
date: 2012-01-29
forum: Virtualisation
---

### Post by memilanuk on 2012-01-29
So... I'm having some bizarre issues trying to set up a host-only network with multiple VMs accessible from the host.

Just for reference... if I set up say 5 VMs running various 'appliances' and/or distros on the internal network 'intnet', configuring one of them as a gateway/firewall server (providing DHCP), and one of them as a desktop OS with web browser, etc. I get *almost* what I want.  All the server 'appliances' are protected from the Internet by the gateway/firewall, the 'NAT' connection on its outbound connection, plus the firewall/NAT on my physical connection between my LAN and the Internet.  All the appliances can reach the Internet for updates, etc., and I can browse to the webmin control pages on the appliances from the VM with the desktop OS.  Everything works as expected.

The problems start when I try switching things over to a host-only network, so as to be able to do everything mentioned above... but to also be able to browse directly from the host OS (Ubuntu 11.10) to the VMs.  The long and short of it is that the networking starts getting stupid, and I'm at a loss as to why.

If I open Virtualbox and start up the VMs initially, they (usually) will successfully acquire their info from the built-in DHCP server.  Great... then when I try setting up the 'firewall' distro and switch over to its DHCP server... none of the other VMs will use it.  I can turn *OFF* the virtualbox built-in DHCP server, and the VMs still seem to get the same IP addresses from it, and not from the gateway/firewall VM.

Other times I've set up a lone VM on the host-only network, with the built-in DHCP server ON, no problem.  Then I set up a second VM on the host-only network... and it either can't connect to the DHCP server or it gets the same IP address as the first - not good.

I honestly don't know if the problem is with the host OS / VirtualBox (running the stock Oracle version, btw) or with the guest VMs (mostly TurnKey Linux server appliances, Smoothwall firewall/gateway distro, etc.)... but I suspect the host end of things, if not Virtualbox itself.  Either that or this *isn't* something that is possible with Virtualbox, despite what I've been told elsewhere.

TIA,

Monte

---

### Post by japzone on 2012-01-31
Honestly, the only way I can think of to do this without a headache is to switch them all to "Bridged" connections, let them get an IP from the Router and then modify the Guest's settings so they connect through the Firewall Guest's DHCP. For Security Simply get a cheap router to put between your Host and whatever Internet connection you have. That way you more phisically create your "Private" Intranet and not have to Juggle a Complex Software Setup to get the same effect. The only downside to this is that you no longer have access to your Net Connection's Intranet so you won't be able to connect to other Computers that aren't on your "Private" Intranet. A workaround for that would be to have two Network Adapters on your PC and use one for your PC to connect to the Net like usual and the other to be used for Bridging your Guests to their private Router.

---

### Post by memilanuk on 2012-01-31
The idea here was to keep the VMs isolated and off the physical LAN so they (development setups) don't pose a security risk.  Like I said, I can already pretty much do what I want with an internal network; it would be more convenient if I could do it with a host-only network.  At no point would giving each and every VM its own bridged network connection be considered a viable alternative for this situation.

---

### Post by japzone on 2012-01-31
> **memilanuk said:**
> The idea here was to keep the VMs isolated and off the physical LAN so they (development setups) don't pose a security risk.  Like I said, I can already pretty much do what I want with an internal network; it would be more convenient if I could do it with a host-only network.  At no point would giving each and every VM its own bridged network connection be considered a viable alternative for this situation.

Point Taken.

---

