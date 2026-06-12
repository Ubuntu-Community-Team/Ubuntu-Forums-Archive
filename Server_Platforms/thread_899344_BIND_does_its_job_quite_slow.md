---
title: "BIND does its job quite slow"
date: 2008-08-24
forum: Server Platforms
---

### Post by Moepi on 2008-08-24
Hello,
I've set up an Ubuntu server which I use as DNS and DHCP server for my LAN. Everything seems to work fine, but while browsing using a client in the LAN I experience strange delays during DNS resolution. On my Mac using Firefox 3 it takes up to 2 seconds to resolve the address of the domain name. If I use my local router as DNS server there are nor such delays.
It is very interesting that these delays do not appear while using nslookup oder dig on the command line. The problem seems not to be related directly to Firefox since Safari shows a similar behaviour.

I've configured a public DNS Server of T-Online as forwarder. The problem affects also FQDNS located in the LAN and handled by the DNS server - also only if accessed via a browser. So the forwarder can not be the problem.

Does anyone know about similar issues? Thanks in advance!

---

### Post by RealPSL on 2008-08-24
Moepi,

I had a similar problem once not on Ubuntu but on SuSE Linux and disabling the IPv6 setup on the clients cleared it up. While lookup for specific instructions on how to disable IPv6 I came across this.

[Disabling IPv6]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4")

---

### Post by Moepi on 2008-08-24
Thanks for your recommendation, but this did not fix the problem. But it made me think about IPv6 in Firefox in MacOS again. Although it does not seem to be the fault of Firefox (remember that Safari shows the same beaviour) setting network.dns.disableIPv6 to false (by typing about:config into the address bar and modifying the key) resolved the problem.

Thanks again!

---

### Post by inphektion on 2008-08-24
have you disabled ipv6 in the bind dns server?  then I don't think you'd have to in all the clients...  I killed the ipv6 modules on my bind server and I think I even blacklisted them and I never see any slowness...

---

