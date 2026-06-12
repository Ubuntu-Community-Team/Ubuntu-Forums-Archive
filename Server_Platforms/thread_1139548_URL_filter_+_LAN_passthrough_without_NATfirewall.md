---
title: "URL filter + LAN passthrough without NAT/firewall"
date: 2009-04-27
forum: Server Platforms
---

### Post by c0d3sl1ng3r on 2009-04-27
OK, I want to look at setting up and configuring a URL filter to log all network HTTP requests (who and when, mainly) and filter based on undesirable content parameters.

So far I am looking at SquidGuard on top of Dansguardian, which looks about as good as it gets.

The tricky part is that this box will go into an already established and predominantly Windows network that sits behind a comprehensive and thoroughly set up firewall. The firewall controls all sorts of things including serving L2TP/IPSEC and SSL VPN, remote Outlook Web Access, SSH etc.

For obvious reasons that last thing I want to do is put a second NAT firewall behind the first.

Ideally I want to put a box in that passes all network traffic through 2 NICs (internally and externally facing respectively) and only listen for and react to URL requests on the network.

Anyone have any clues to resources on establishing something like this ?

My last efforts along this line was some years ago using SUSE Linux 8 or 9 (I forget which) and I know that things have moved on apace.

Most of the resources I can find involve using the Linux box as a fully blown firewall/router whereas I only want traffic passthrough routing and scanning.

---

### Post by windependence on 2009-04-27
Take a look at untangle. Pfsense is good also. Both of these can do routing but don't have to. You can set them up just for filtering or traffic shaping.

-Tim

---

### Post by iponeverything on 2009-04-27
squid/squidGuard work well. If your firewall supports wccp2, it will make it very easy to for you to drop a transparent proxy into the mix without the need for the dual NIC setup.

---

