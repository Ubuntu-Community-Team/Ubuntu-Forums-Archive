---
title: "Network configuration not working"
date: 2016-09-08
forum: Server Platforms
---

### Post by simonhk2 on 2016-09-08
Hi.

I've been using Debian till now but want to try out Ubuntu instead. However I'm getting stuck on the network configuration and I can't seem to figure out what the problem is.

I'm running Ubuntu Server 12.04.1 LTS as a virtual machine and I have changed /etc/network/interfaces to contain:

auto lo eth0
iface lo inet loopback
iface eth0 inet static
address 91.133.111.123
netmask 255.255.255.255
broadcast 91.133.111.123
post-up route add 149.200.100.254 dev eth0
post-up route add default gw 149.200.100.254
post-down route del 149.200.100.254 dev eth0
post-down route del default gw 149.200.100.254
dns-nameservers 208.67.222.222 208.67.220.220

I've used the exact same configuration on Debian and it works, but here on Ubuntu the network won't work at all - trying to ping an IP address just tells me the network is unreachable.
All numbers have been tripple checked and the configuration is correct, I've also checked that the MAC address I supplied to the NIC is correct and matches the IP I specify in the config.

Any clue what the problem can be, or do I need to configure the network somewhere else in Ubuntu? According to all info I've been able to find I'm doing it right but it won't work.

Thanks.

// Simon

---

### Post by volkswagner on 2016-09-08
Can you verify the VM can get networking functioning via DHCP first? With a VM there are added
complexities which require verifying the host bridge/network is working.

I've never seen a single ip like your setup (I'm no expert). I'm not sure how the broadcast can be the same as host ip.
Even if your ISP gives you just a single IP, normally this would be part of a subnet with unique gateway, broadcast, and network config.

You are missing "auto eth0" as first line if you expect interface to come up on boot (unless you are running your in if-up script).
Normally a default gateway is included in config, while additional routes are added like your post-up rules.
You should also have a network stanza as well.

Is this vm really going to have a public ip directly without a firewall/NAT?

example:
```
[COLOR="#FF0000"]auto eth0[/COLOR]
iface eth0 inet static
        address 192.168.0.10
        [COLOR="#FF0000"]network 192.168.0.0[/COLOR]
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

---

### Post by simonhk2 on 2016-09-08
Thank you for your reply.

The configuration is provided by my host where I have my dedicated box. 
It is setup with VMWare ESXi 6 and I run Ubuntu as a guest, just like I've been running Debian as a guest.
When I use the posted configuration for Debian the network works fine, but with Ubuntu it doesn't - the configuration is supposed to be the same for Ubuntu and Debian which makes sense.

This is the configuration provided by my host: [http://help.ovh.com/BridgeClient](http://help.ovh.com/BridgeClient)

Yes the VM is supposed to have a public IP with nothing in-between.

---

### Post by darkod on 2016-09-08
Well, that tutorial says the GW is your server IP ending in .254. But in your config you set address to 91.xxx and GW to 149.xxx. How does that match their instructions???

I also haven't seen the broadcast to be identical to the IP address, they must have some really weird routing/subnetting there.

PS. Plus those instructions are in English but very confusing. Like automatic translation that went really bad. On one hand it says "you must in no case use route add" and then their example below uses precisely route add. Besides no one in English would say "must in no case".... :)

What happens if you simply try:
```
gateway 91.133.111.254
```

Without any of the route add and route del commands.
And you shouldn't need to specify the broadcast either, it is calculated automatically from the IP address and netmask. So try commenting the broadcast line too.

---

### Post by simonhk2 on 2016-09-08
It is a French hosting provider, their English isn't exactly prime. 

What puzzles me is that the configuration works on Debian but not on Ubuntu - if I copy and paste the configuration to Debian it works right away and I have access. So the configuration I posted here is correct and works as intended on Debian - but not for Ubuntu for some reason.

I have 1 IP (eg. 149.200.99.105) for the dedicated box and 4 additional IPs (91.130.110.224, .225, etc.) that I can use and assign to VMs. 
The Gateway is the IP of the dedicated box (the ESXi host) with .254 at the end (eg. 149.200.99.254), so it is completely different from the IP I'm trying to assign to the VM.

It is indeed a pretty weird setup, but nevertheless it is supposed to work and works for Debian and Windows without any problems.

---

### Post by darkod on 2016-09-08
OK, now it is little clearer... So they give you 4 IPs all of them with netmask 255.255.255.255? I would try without the broadcast, as I mentioned. Actually I have never used broadcast in ubuntu, and it always worked.

You better contact them I guess and explain what happens and get some advice. We can't advise you not knowing what type of bridging they are doing.

---

