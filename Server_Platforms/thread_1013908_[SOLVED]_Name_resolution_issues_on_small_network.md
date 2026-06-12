---
title: "[SOLVED] Name resolution issues on small network"
date: 2008-12-17
forum: Server Platforms
---

### Post by Lord_Dicranius on 2008-12-17
[IMG]http://i44.tinypic.com/a3owo1.jpg[/IMG]

Ubuntu Router
[indent]_eth0_
IP: 12.1.1.2
Netmask: 255.0.0.0
Gateway: 12.1.1.1[/indent]
[indent]_eth1_
IP: 192.168.1.254
Netmask: 255.255.255.0[/indent]

Ubuntu Desktop
[indent]_eth0_
IP: 192.168.1.1
Netmask: 255.255.255.0
Gateway: 192.168.1.254[/indent]

-I have a bare firewall setup on the Ubuntu Router to do IP Masquerading
-/etc/resolv.conf on the Ubuntu Router is configured with two AT&T DNS servers

-From the Ubuntu Router, I'm able to ping Google.com by its name and IP
-From the Ubuntu Desktop, I'm able to ping Google.com by its IP, but not by its name

What would I need to do to get the Ubuntu Desktop able to surf the Internet?  Working on this all day yesterday, I installed bind9 on the Ubuntu  Router and configured the named.conf.options file with forwarders to the external DNS servers configured in the resolv.conf; then configured the DNS server on the Ubuntu Desktop to use Ubuntu Router, thinking that any request sent by Ubuntu Desktop would be forwarded by the Ubuntu Router to the AT&T DNS servers for name resolution, but that didn't work.  I tried configuring the Ubuntu Desktop with the AT&T DNS servers also, but that didn't work either.

**Any** help would be **GREATLY** appreciated! :)

---

### Post by Lord_Dicranius on 2008-12-17
It's fixed and I feel like an idiot.  But it's ok, because it works now haha  I was using a live Ubuntu desktop for the Ubuntu Desktop machine.  I installed it to the hard drive, and it worked as soon as I configured eth0.

---

