---
title: "Suggestions for future Ubuntu versions"
date: 2008-04-05
forum: The Cafe
---

### Post by gwm on 2008-04-05
Hi,
I looked around the forums and didn't see where to put this post. Maybe I'm just blind. If so, please ignore suggestion number one. This is a wish list of some things that I have seen on Windows that I think are really cool and that I would like to see here too. Who knows, maybe there are security issues that I am unaware of.

1. A separate heading for posting wish list things. One man's wish is another man's revulsion. This could be a place to discuss possibilities and a source for improving the product.

2. I switch off my ADSL router and unplug it during our frequent electric storms. If I start up in Ubuntu and then realize the router is unplugged, too bad! I must reboot! Windows on the other hand, detects the router and connects flawlessly.

3. Something similar to 2. above but with respect to detecting shared printers on another PC when it boots up and joins the network

---

### Post by smartboyathome on 2008-04-05
There is already an idea pool under "Development and Programming". Also, there is brainstorm.ubuntu.com.

---

### Post by FuturePilot on 2008-04-05
1. [http://ubuntuforums.org/forumdisplay.php?f=306]("http://ubuntuforums.org/forumdisplay.php?f=306")

2. I've never had to reboot because of something like that. Network Manager should automatically take care of that. If it doesn't try left clicking on Network Manager and reselect your wired connection.

---

### Post by gwm on 2008-04-05
Thanx smartboyathome. I'll remember that for next time.
Also futurepilot.
I have Gutsy installed. if I look at the wireless connection properties, I have automatic detection (DHCP) selected. I tried turning it off and on again etc. without success. now that you have prompted me, I looked again and noticed something useful. In the past, I had a fixed IP address. That appears grayed out. When I tried finding the router with *PING 10.0.0.2* I received an error message about it being unreachable and I seem to remember that old fixed IP address being in the error message somewhere, instead of 127.0.0.1 as I expected. Perhaps if I go and wipe out the old fixed address, it will come right.
It pays to complain! Even when you're really dumb, someone will sort you out. Thanks a million.
:popcorn:

---

### Post by billgoldberg on 2008-04-05
> **gwm said:**
> 

2. I switch off my ADSL router and unplug it during our frequent electric storms. If I start up in Ubuntu and then realize the router is unplugged, too bad! I must reboot! Windows on the other hand, detects the router and connects flawlessly.



I never had that problem.

If I reset my router, or it's turned off and I turn it on, network manager finds my connection in a few seconds.

---

### Post by gwm on 2008-04-06
Thanx,
I hear y'all. I don't have a wired connection to the router, only a wireless one. From your responses, it would seem that this thing should work. I'll go over to a more appropriate forum and report it as a bug with ifconfig outputs etc.

---

### Post by corney91 on 2008-04-06
Yeah, mine detects the wireless connection within a minute of rebooting the router. I'm positive it should find it straight away...

---

### Post by gwm on 2008-04-18
Hi,
I've been trying things out and reading all the posts in this thread again. I think everyone has misunderstood the problem. I'm not talking about resetting the router, I'm talking about powering it up after the initial boot.

Everyone who responded talks of resetting the router after everything is working. When you switch off the router, Ubuntu doesn't lose it's IP address that has already been established. *ifconfig* in terminal mode confirms this. Therefore, when the router is powered up again, the connection is easy.

The behavior that Microsoft have got right but that Ubuntu hasn't, is that the networking system discovers it's router even if it never found one initially. If DHCP fails initially, Ubuntu gives the PC  the IP address assigned to the network card by the manufacturer. Thereafter, it is unable to find the router.

The way I see it, is that the subnet defined by the mask of 255.255.255.0 prevents it from doing so. In fact, even opening the mask to 255.0.0.0 would still fail.

---

