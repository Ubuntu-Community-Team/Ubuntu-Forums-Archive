---
title: "Network passthrough?"
date: 2013-10-03
forum: Server Platforms
---

### Post by Falklian on 2013-10-03
I'm not sure if thread title is what I'm actually looking for...

Anyway, I have a [small computer]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856205007") that is getting re-purposed as a web server/development box.  As it has two LAN ports, I thought about connecting it directly to my cable modem and then connecting it to my wireless router (modem > server > router).  Would it be possible to just "pass through" the internet connection to the router or would I have to use the server I'm building as the router and turn the wireless router into a wireless access point (it has a built in "bridge mode" that I have used in the past)?

Thanks in advance!

---

### Post by CharlesA on 2013-10-03
You'd need to set up the server to do the routing and just use the router as a switch/access point.

---

### Post by SeijiSensei on 2013-10-04
You don't want to use bridging, though.  Either you can put the wifi router behind the Linux box, or put the Linux box behind the router.  In the first method, you'd give both the router and the router-facing interface on the Linux box a pair of static IPs, say 10.10.10.1 and 10.10.10.2, and let the router handle managing client machines with DHCP as it probably does now.  The other method is more complicated since you would need to run isc-dhcp-server on the Linux box to manage the local network.

In both cases you will probably need to configure the Linux box with an iptables rule that "[masquerades]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29")" packets from the network behind it.  For instance, if the wifi router is configured with 10.10.10.1, and the local network behind the Linux box uses 192.168.1.0/24 for the client workstations, the router will mishandle packets reaching it with a 192.168.1.x address.  If you masquerade all the outbound traffic, then it will all appear to come from the externally-facing interface of the Linux box which in this example has 10.10.10.2.

---

