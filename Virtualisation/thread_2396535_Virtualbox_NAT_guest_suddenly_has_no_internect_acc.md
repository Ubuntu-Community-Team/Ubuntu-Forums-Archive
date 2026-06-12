---
title: "Virtualbox NAT guest suddenly has no internect access"
date: 2018-07-17
forum: Virtualisation
---

### Post by goodstuff9 on 2018-07-17
Ubuntu 17.10 host, Virtualbox 5.1.34_Ubuntu r121010.  

In Virtualbox I have a couple guest systems – Windows 10, Linux Mint, Fedora – that had been working just fine, they had internet access.  They all were set up with the NAT attachment.  

Yesterday, for some reason I cannot figure out, they all lost internet access.  

When I experimented and change the attachment setting from NAT to Bridged, they all again had internet access.  

How can I figure out what the problem is with the NAT attachment setting?

---

### Post by SeijiSensei on 2018-07-17
Any firewall on the host blocking the 10 network over which NAT runs?

---

### Post by goodstuff9 on 2018-07-19
I don't know what you mean by the term "10 network", but I can tell you that using GUFW Firewall I confirmed that no firewall settings are active at all.

---

### Post by TheFu on 2018-07-28
Not that is should matter for the problem you are asking about, but support for 17.10 ended last week.   [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)  There's a nice chart.

Please move to 18.04 or back to 16.04. Both of those releases are LTS, unlike 17.10 and upcoming 18.10 both which will have less than a yr of support.

A "10 network" is commonly used for internal, non-public-routeable IP subnets.  172.16.x.x and 192.168.x.x subnets are similarly non-public-routeable IP subnets.  So, a 10.x.x.x subnet would be similarly non-public-routeable. Internet routers will not route traffic on their internet interfaces with any of those subnets.

GUFW is just a GUI.  It isn't the only possible way to have an active firewall. The linux kernel has the only real firewall, netfilter.  To see all the rules, you'll need to use **sudo iptables -L**.  iptables is just another interface program into netfilter controls, but it sees the full netfilter config.  I don't think either ufw or gufw can.

---

### Post by dexterisawesome on 2018-07-29
> **goodstuff9 said:**
> I don't know what you mean by the term "10 network", but I can tell you that using GUFW Firewall I confirmed that no firewall settings are active at all."1

"10 Network"? That'd be the network that Windows 10 is running off of, but do you even have a Windows 10 on another harddrive? or do you have a split harddrive?

---

