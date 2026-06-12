---
title: "Four Port NIC or Something Funky?"
date: 2011-12-24
forum: Server Platforms
---

### Post by dmattox10 on 2011-12-24
I have been wanting to take my server farther. I can't afford to keep buying a new server for every feature I want at home, so everything gets built into one box. After my question I'll list what it does now and specs, for anyone interested.

[]("http://www.ebay.com/itm/Intel-PRO-1000-MT-Quad-Port-PCI-X-Server-Adapter-Nic-card-C32199-001-/220916876733?pt=LH_DefaultDomain_0&hash=item336fac05bd")[LINK]("http://www.ebay.com/itm/Intel-PRO-1000-MT-Quad-Port-PCI-X-Server-Adapter-Nic-card-C32199-001-/220916876733?pt=LH_DefaultDomain_0&hash=item336fac05bd")
Is this thing what it looks like? I would like to add router/switch functionality to the server. 
Can I connect separate network devices to each port and use some sort or software on the server to go above and beyond a simple firewall, and turn my server into a router/switch?
My server has two pci-x ports, so I could install two of these and ditch my four port switch, or go buy a second four port switch and stop unplugging cables based on need.

My server already provides:

External: 
Apache Web Server, multiple sites through virtual hosts.
Internal:
FTP
NFS
SMB
UPnP Media
Relaxx front end to MPD
TorrentFlux-b4rt
Firewall

---

### Post by elico on 2011-12-25
using BRIDGE interfaces and ebtables or iptables you can use it as a router\switch but in most cases a linux machine that will function as switch will be more money on electricity then you will spend on a basic 1GB switch.
if you do want advance switching with vlans it can be affordable but not really nice to configure a linux machine for that.

---

### Post by CharlesA on 2011-12-25
Just get a 8-port gigabit switch and be done with it.

---

### Post by dmattox10 on 2011-12-26
Thank you, a gigabit 8 port switch it is. So then can I use the server as a router? I have dual gigabit nics in the server, and would like to use dansguardian to protect my little one.

---

### Post by CharlesA on 2011-12-26
> **dmattox10 said:**
> Thank you, a gigabit 8 port switch it is. So then can I use the server as a router? I have dual gigabit nics in the server, and would like to use dansguardian to protect my little one.
You could do that, yes.

---

### Post by collisionystm on 2011-12-28
You could do the 2 NIC cards and turn your server into a network switch. However at 40 bucks per card you may as well just buy a switch, as mentioned.
Turning your server into a firewall/router is rather simple.
You just need a NIC port to interface with the internet and a NIC to interface with the local network.
Enable routing and adjust the iptables. You will be rocking in minutes.

---

### Post by dmattox10 on 2011-12-30
Well I followed [this]("https://help.ubuntu.com/community/Router") guide and [this]("http://www.server-servers.com/ubuntu-router-network-gateway/") guide, and the server is unreachable from my laptop, connected to the switch, connected to the server... ssh fails, and the internet did't even work... Will the fastest thing be to just format the server?

---

### Post by CharlesA on 2011-12-31
If the machine can access the internet, then just flush the firewall rules and redo them.

```
sudo iptables -F
```

---

