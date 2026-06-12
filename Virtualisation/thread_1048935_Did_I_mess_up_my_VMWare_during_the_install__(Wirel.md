---
title: "Did I mess up my VMWare during the install?  (Wireless and other issues)"
date: 2009-01-24
forum: Virtualisation
---

### Post by steve04 on 2009-01-24
When I was setting up VMWare 1.0.7 using the tutorial (BTW: great tutorial thanks!) I changed the default device for my network settings.  I think in the install it had ETH1 but I changed it to WLAN1 (since I only have access to wireless).  Now when I boot into my Virtual XP I don't even see a wireless choice.  Under network connections it only shows my wired connection (which I don't have hooked up).  How do I get this to show my wireless card so I can access the internet and download stuff for my virtual machine?  Also, how can I get it to recognize my external hard drive?  Thanks in advance!

---

### Post by bluntknife on 2009-01-24
Hi,

I think you'll find that is normal.  It sounds like you have configured VMware on your host machine to use WLAN1 for networking.  If this is your route out to the world then this is fine.  
Your virtual machine will not show a connection to a wireless network, it will show a connection to a physical 'virtual' network (this is by design).  You can configure your virtual NIC on your virtual machine to either have a 'bridged' or 'NAT' connection to your host machine's network. Your virtual network will route external traffic out through your physical wireless NIC.
(You could also choose to configure your virtual NIC as 'host only' but this means your virtual machines traffic will not be routed out to the web and can only see other VM's and your host machine.)

I hope this makes sense...

---

