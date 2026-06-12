---
title: "network monitoring"
date: 2007-07-08
forum: Server Platforms
---

### Post by saintj0n on 2007-07-08
I have been researching different  tools for monitoring networks and nothing seems to be an obvious solution for what I need to monitor (as far as OS.) Does anyone have a suggestion as to a utility on my Ubuntu server that will  monitor several windows 2000 servers and a vpn? I want fairly granular details on the report (bandwidth usage by connection, who is going to which sites, who is using way too much bandwidth for normal use, perhaps other things I could trap for thaat I haven't mentioned).  

I also would like notifications when my windows servers go down, a virus enters the network, possible malware activity and massive downloading.

Thanks...

---

### Post by murraymca on 2007-07-08
Hi,

You can use iptables to track bandwidth, not sure if per user like you want.

In my shameful past job, I used HP system insight manager ([http://h18004.www1.hp.com/products/servers/management/hpsim/dl_linux.html](http://h18004.www1.hp.com/products/servers/management/hpsim/dl_linux.html)) to monitor windows servers, it emailed me when one went down, hardware problems (I guess only useful if you have a HP server) etc.

I've never used SQUID but I guess that might be your best bet for monitoring user surfing?

Good luck.

---

### Post by textguru on 2007-07-13
how to install/configure iptables?

---

### Post by murraymca on 2007-07-13
Hiya,

Not sure if this will meet your needs though.  I assume you are on ubuntu...to install iptables:

sudo apt-get install iptables

I can't really explain how to configure but the Linux Network Administrators Guide has a good section on iptables and also IP accounting which will help you monitor bandwidth.  The guide can be brought or you can:
-  read it online:  [http://tldp.org/LDP/nag2/index.html](http://tldp.org/LDP/nag2/index.html)
-  download it:  [http://tldp.org/LDP/nag-2.0.html.tar.gz](http://tldp.org/LDP/nag-2.0.html.tar.gz)
- download PDF:  [http://tldp.org/LDP/nag2/nag2.pdf](http://tldp.org/LDP/nag2/nag2.pdf)

Look for the the section "9.8 Netfilter and IP Tables (2.4 Kernels)" under Chapter 9, TCP/IP Firewall.  Chapter 10, IP Accounting, will help with bandwidth monitoring, but again, might not be what you are after.  There are also GUI tools to configure iptables such as firestarter [http://www.fs-security.com](http://www.fs-security.com)...well it was a GUI for iptables the last time I looked but that was many years ago.

All the best.

---

### Post by gaten on 2007-07-13
You could try Ossec HIDS ([http://www.ossec.net](http://www.ossec.net)). Its an IDS that runs in Linux and Windows, and will email you alerts. I've never run it in Windows, so I can't vouch for its usefulness there, but it ran great on my Dapper system. Can't get it working with feisty though...

---

### Post by murraymca on 2007-07-14
I just found this tool from a link on [http://librenix.com/](http://librenix.com/)

It is a monitoring tool, apparently makes nice graphs, has agents for unix, linux and windows...

[http://www.zabbix.org/](http://www.zabbix.org/)

Some tutorials that might help if you are interested:

[http://www.howtoforge.com/zabbix_network_monitoring_debian_etch](http://www.howtoforge.com/zabbix_network_monitoring_debian_etch)

[http://www.howtoforge.com/zabbix_network_monitoring](http://www.howtoforge.com/zabbix_network_monitoring)

It sounds like it does most of what you want...

Take care!

---

