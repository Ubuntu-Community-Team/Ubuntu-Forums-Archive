---
title: "dns server"
date: 2009-10-13
forum: Server Platforms
---

### Post by chaosc on 2009-10-13
Hey guys I'm running ubuntu server 9.04 in a virtual machine. I want it to be my primary dns lookup. I don't want mypc@mydomain type stuff just instead of going to my isp or thirdparty dns i want to point my computers to a local dns for webpage lookup. Any suggest on how to do this 
thanks

---

### Post by cariboo on 2009-10-13
Why, unless it is some thing you want to learn how to setup. You do realize that once you have a dns server setup, the rest of the world could potentially use you server for dns lookups.

---

### Post by noway2 on 2009-10-13
Chaosc is correct, in that unless there is a reason to do so, which may include just wanting to learn how, needlessly setting up the feature is a potential security risk.

Depending on what else you plan to do with the server, having a local DNS may be helpful or even necessary.  For example, postfix makes use of DNS as part of its function.

Personally, on my home LAN, I have a copy of BIND running as a locally authoritative server and have it tied to the DHCP.  This allows me to access any of the devices on my LAN by name without requiring static IPs.  I made use of this ability this last weekend while experimenting with TCP/IP programming and I had server and client applications running on different machines across the lan.  While this is doable without DNS, it was convenient to use the computer names.  For security, I do keep the server behind a router and only open the necessary ports and the DNS port is closed to the outside world.  I also realized that on the, admittedly infrequent, occasions that my internet service would go down that it was usually a loss of DNS function rather than a total connection loss.  By using my own DNS, I am still able to operate.

---

### Post by chaosc on 2009-10-13
So i can't have a pc on my network that would forward the look up and maintain a list and be for private only

---

### Post by chaosc on 2009-10-13
Would this speed up network access the way you have it.  I have to wait and wait and wait for pcs to show up on network neighborhood so I use ips.  if so is there a tutorial on this setup?

---

### Post by bshosey on 2009-10-13
I run DNS and DHCP server for my home network and foreword everything that is not my internal network. I use dnsmasq to do both.

But it is no virtualized so I don't know if this would work for you or not.

---

### Post by bab1 on 2009-10-13
> **chaosc said:**
> Would this speed up network access the way you have it.  I have to wait and wait and wait for pcs to show up on network neighborhood so I use ips.  if so is there a tutorial on this setup?

This is not DNS problem at all.  If you truly mean "browsing services", you should look at which host is the "Master Browser".  I believe that the browse list is updated every 15 minutes or so.  If the host that is servicing the network changes you will suffer this lag.

Read up on Samba specifically about browsing.

[[COLOR="DarkSlateGray"]_**Here is the Google search.**_[/COLOR]]("http://www.google.com/search?q=samba+browse+master&btnG=Go!")

Edit:  I agree with bshosey on the use of DNSMasq.  It will work in a virtual setting.  You must bridge the virtual guest IP's to the real (host) network.

---

### Post by chaosc on 2009-10-20
is ubuntu better for master browser than xp?

---

### Post by bab1 on 2009-10-20
> **chaosc said:**
> is ubuntu better for master browser than xp?

There is really no difference between Samba and Microsoft.  It is, however, important to use a host that is up (running) all the time.  That way the browse list is available at all times.

---

