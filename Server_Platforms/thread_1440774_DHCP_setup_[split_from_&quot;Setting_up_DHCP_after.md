---
title: "DHCP setup [split from &quot;Setting up DHCP after the install&quot;]"
date: 2010-03-26
forum: Server Platforms
---

### Post by bskumar7080 on 2010-03-26
I am newbie to linux please can anyone give howto to install DHCP server in ubuntu 9.10

---

### Post by Iowan on 2010-03-27
I like DNSMasq, but DHCP3-server is another option. Both should be in repo's. The "fun" comes after the install.

---

### Post by koenn on 2010-03-28
I like dnsmasq too.

---

### Post by noway2 on 2010-03-28
I like this one: [http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/](http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/)

I used DHCP3 in combination with Bind.  One nice thing about the link above is that it shows you how to set things up so that you have dynamic LAN addresses that are identifiable by name.  As far as difficulty, I managed to get it working in less than hour when I was still a newbie to server administration.

---

### Post by koenn on 2010-03-28
> **noway2 said:**
> 
I used DHCP3 in combination with Bind.  One nice thing about the link above is that it shows you how to set things up so that you have dynamic LAN addresses that are identifiable by name.  As far as difficulty, I managed to get it working in less than hour when I was still a newbie to server administration.
setting up a dhcp is pretty straightforward - if you understand your network, it's just like filling out a form. 
Setting up bind (correctly) and have it opdated by dhcp3 is a bit more complicated, IIRC

One of the nice things about dnsmasq is that it can do both dhcp and dns (so 1 small program instead of 2 larger ones), and the dns part automatically knows about the hostname and ip adress pairs the dhcp handled : built-in "dynamic update' dns !

---

### Post by Iowan on 2010-03-28
A couple of pages from the 9.10 Server guide:
[https://help.ubuntu.com/9.10/serverguide/C/dhcp.html]("https://help.ubuntu.com/9.10/serverguide/C/dhcp.html")
[https://help.ubuntu.com/9.10/serverguide/C/dns.html]("https://help.ubuntu.com/9.10/serverguide/C/dns.html")
These set up **DHCP3** and **bind**.

---

