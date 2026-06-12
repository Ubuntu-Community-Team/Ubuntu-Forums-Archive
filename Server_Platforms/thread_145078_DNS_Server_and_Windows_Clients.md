---
title: "DNS Server and Windows Clients"
date: 2006-03-15
forum: Server Platforms
---

### Post by Yogibear on 2006-03-15
I have an Ubuntu box setup to connect to the internet via ADSL and act as a gateway for my domain clients (running windows) to connect to the internet.

The problem is that if I open a command line on a Windows box, and try ping [www.google.com](www.google.com) it fails (Pinging the ip address works though). 

I can ping google from the Ubuntu server.

I can access the internet from my clients because I am using a SQUID proxy.

Does anyone have an idea what could solve this problem?

---

### Post by Horndog on 2006-03-15
[QUOTE=Yogibear]I have an Ubuntu box setup to connect to the internet via ADSL and act as a gateway for my domain clients (running windows) to connect to the internet.

[color=red]The problem is that if I open a command line on a Windows box, and try ping [www.google.com](www.google.com) it fails[/color] (Pinging the ip address works though). 

I can ping google from the Ubuntu server.

I can access the internet from my clients because I am using a SQUID proxy.

Does anyone have an idea what could solve this problem?[/QUOTE]
This would be consistent with a client behind a proxy server.

---

### Post by Glut on 2006-03-15
**Horndog: **Not so, that is consistent with being unable to lookup a host name. He can ping the ip address from the windows box, so the inference is that ICMP packets are being routed.

**Yogibear: **What DNS server do you have setup on the windows boxes? You can obviously route ICMP, why not UDP? just use iptables to route your DNS requests to your ISP. The alternative is to use bind to cache DNS.

---

### Post by Horndog on 2006-03-16
[http://www.squid-cache.org/Doc/FAQ/FAQ-12.html#ss12.28]("http://www.squid-cache.org/Doc/FAQ/FAQ-12.html#ss12.28")

> The**[color=red] source_ping**[/color] feature has been disabled in Squid-2. If you're seeing packets to port 7 that are coming from a Squid cache (remote port 3130), then its probably a very old version of Squid.
**Glut:** Apparently It is so.

---

### Post by Yogibear on 2006-03-16
I tried to use BIND, but it didn't seem to work and I don't really know how to properly set it up.

I set my Windows clients to use my gateway as their primary DNS server and my ISP's IP as their secondary DNS. This seems to work, but this is sub-optimal.

---

### Post by faulkner132 on 2006-03-16
Is DHCP also installed on your DNS server?  It would be best to have your Ubuntu box act as the DNS and DHCP server and then have your Windows server act as a domain controller only.

---

### Post by Glut on 2006-03-16
[QUOTE=Horndog][http://www.squid-cache.org/Doc/FAQ/FAQ-12.html#ss12.28]("http://www.squid-cache.org/Doc/FAQ/FAQ-12.html#ss12.28")


**Glut:** Apparently It is so.[/QUOTE]

The Source-ping feature is where the squid proxy pings the destination server - squid doesn't proxy pings in its default state (I'm sure you could force it to if you tried :-). This is not the case here, where the user's machine behind the proxy can ping an ip address, but cannot ping a host name. I'm assuming that he's running a very default squid2.

---

### Post by Horndog on 2006-03-16
[QUOTE=Glut]The Source-ping feature is where the squid proxy pings the destination server - squid doesn't proxy pings in its default state (I'm sure you could force it to if you tried :-). This is not the case here, where the user's machine behind the proxy can ping an ip address, but cannot ping a host name. I'm assuming that he's running a very default squid2.[/QUOTE]

That is probably the way squid2 implements the "No Source-ping feature. They just disabled the access to the DNS server when a ping  command is enabled. Lazy by semi effective for free software. Bottom line is squid2 does not want clients behind their proxy to ping, reducing the threat of a DoS attack using some ones poorly setup open proxy server making their identity untraceable.

---

