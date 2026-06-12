---
title: "Firewall assistance"
date: 2007-10-25
forum: Server Platforms
---

### Post by TorchlightJay on 2007-10-25
Hello,

So I want to setup a firewall on my network. I have an old machine, it's like a PIII but I plan to install a NIC and turn it into a firewall and DHCP server (should I separate those, oh that's another issue). Anyway, currently my ISP gave me five static IPs and a nice little router/modem combo. 

Now, naturally I don't want all my computers to have a static IP. I have computers that come in and leave and just need DHCP. So I got myself a nice little Linksys Wireless Router and set it up with one of the five static IPs and then the router gives DHCP from that. Two other static IPs are in use by servers so three are in use, two are open.

Now I want to use just one firewall but I am not sure where in the network to put it. Since I have two routers, it's like I have two networks (albeit that one of the routers has it's IP from the first). Where should I put my firewall or will I need to make two? Once I made a Windows Server and it was connected to the same router the whole network was. I just turned DHCP off of the router and the server took over and also got a firewall setup. Can I do something similar with my network?

INTERNET ----- ISP_Modem/Router(static) ----- Linksys Wifi-DHCP ---- Laptops
                                 |               |
                                 |               |
                              Server1   Server2

Basic Idea of my network there. Thanks all for your help

---

### Post by whit on 2007-10-25
You can take your firewall box, and using iproute2 assign all 5 IPs to one NIC. Set up SNAT or masquerading on the firewall. Put a second NIC in the firewall box. Assign that to an IP on a private network (like 192.168.1.* - but probably not .1 as that's often the wireless router's default LAN address). So from the ISPs box all IPs got straight to your firewall. It's easiest usually to run DHCP on that and turn it off on your wireless router, by the way. Then your wireless router and any other internal LAN machines connect to a switch (or hub) that connects to the second NIC in your firewall box.

This is a very standard setup. You'll find lots of examples of firewall rulesets around the net that support it.

---

### Post by TorchlightJay on 2007-10-25
Cool, so let me make sure I understand you correctly. I connect my modem/router from my ISP directly to the firewall. Now as far as you know (I know you've never seen my ISPs modem/router), I don't need to set anything up on my ISPs box, everything is set on the firewall. From there all my computers connect. Now can I do both static and DHCP or will I have to have three NICs (one to accept internet connection from ISP, one for DHCP, and one for Static). That's my concern there. I want my whole network to be protected. Maybe there's another way. I've heard of DMZ zones but I do not know much about it. Any ideas are welcome cause I want to run both ways for my servers and the computers. Any help is appreciated. 

Also, what's good software? I don't want to knock ubuntu but I have heard of firewall distros and stuff. Any ideas or is ubuntu good enough. What software will I need to make it work? 

Thanks all, very appreciated.

---

### Post by TorchlightJay on 2007-10-25
Cool, so let me make sure I understand you correctly. I connect my modem/router from my ISP directly to the firewall. Now as far as you know (I know you've never seen my ISPs modem/router), I don't need to set anything up on my ISPs box, everything is set on the firewall. From there all my computers connect. Now can I do both static and DHCP or will I have to have three NICs (one to accept internet connection from ISP, one for DHCP, and one for Static). That's my concern there. I want my whole network to be protected. Maybe there's another way. I've heard of DMZ zones but I do not know much about it. Any ideas are welcome cause I want to run both ways for my servers and the computers. Any help is appreciated. 

Also, what's good software? I don't want to knock ubuntu but I have heard of firewall distros and stuff. Any ideas or is ubuntu good enough. What software will I need to make it work? 

Thanks all, very appreciated.

---

### Post by TorchlightJay on 2007-10-30
any ideas?

---

