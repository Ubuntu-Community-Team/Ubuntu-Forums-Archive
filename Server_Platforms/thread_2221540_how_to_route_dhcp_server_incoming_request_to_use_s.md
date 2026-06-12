---
title: "how to route dhcp server incoming request to use squid instead just dhcp internet"
date: 2014-05-02
forum: Server Platforms
---

### Post by salmankorrani on 2014-05-02
dear sir im using isc-dhcp-server and i want that all request it receives for internet should go through squid installed in the same server

for example my dhcp server is also a proxy server and physical connections or ip configurations handle by bond0 instead of using just eth
plz say some thing about!

---

### Post by papibe on 2014-05-02
Thread moved to **Server Platforms**.

---

### Post by SeijiSensei on 2014-05-05
No, DHCP is not the solution for this; "transparent" proxying is.  You need a couple of iptables rules to intercept outbound traffic on port 80 and push it through Squid.  You also need to make a couple of minor adjustments to squid.conf.  See [this post](http://ubuntuforums.org/showthread.php?t=2017239&p=12077921&viewfull=1#post12077921) for details.

As I wrote there, you should start off with port 80 traffic.  HTTPS poses a variety of challenges.  If you want to proxy that as well, you need to install version 3.3 or later with [SSLBump]("http://wiki.squid-cache.org/Features/SslBump").  As a beginner, I suggest you stick to proxying HTTP for now.

---

