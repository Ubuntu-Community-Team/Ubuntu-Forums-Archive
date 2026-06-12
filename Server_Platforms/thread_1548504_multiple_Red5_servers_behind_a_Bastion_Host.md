---
title: "multiple Red5 servers behind a Bastion Host"
date: 2010-08-08
forum: Server Platforms
---

### Post by tapas_mishra on 2010-08-08
[FONT=arial]I have multiple [Red5]("http://code.google.com/p/red5/") servers running on some machines internally on LAN.
For different subdomains.Ubuntu 10.04

The front end to the world is apache2 on a Bastion Host.

To be able to reach the streaming server I 
embed a javascript in HTML pages 
as follows
```

<embed .....
var="rtmp://site1.[m]("http://ocw.openitup.in/")[y_domain.com]("http://y_domain.com/")"
>
```[/FONT]
the problem is the website are many 

[site1.mydomain.com]("http://site1.mydomain.com/")
[site2.mydomain.com]("http://site2.mydomain.com/")
[site3.mydomain.com]("http://site3.mydomain.com/")
[site4.mydomain.com]("http://site4.mydomain.com/")

each on a separate physical server.
Each of these four have their  own [Red5]("http://code.google.com/p/red5/") installations the front end to each of these four is a common Bastion Host.

If I run rtmp on each of the subdomains at a different port 

how will I make sure 
a request such as 
rtmp://[site1.mydomain.com]("http://site1.mydomain.com/")
rtmp://[site2.mydomain.com]("http://site2.mydomain.com/")

goes to their respective servers.
from the front end server.
What do I need to handle in this case ?

IPTABLES came to mind instantly but from the client browser on internet when some one requests
rtmp://site1.mydomain.com

how will I make sure this rtmp request is mapped to a port different than 1935 as there are three other streaming servers which are also to respond to their respective requests
?

---

### Post by tapas_mishra on 2010-08-09
Ok I got some thing if some one is reading this thread.

To do with a single Public IP address. It requires
either port redirection or layer7 firewalls/reverse proxies such as SOCKS or
perhaps Squid.

One way is to run these streaming servers at different ports as
rtmp://site1.mydomain:8888 ---> your public IP address port 8888 which then
hits the firewall and is redirected:
publicIP port 8888 -----> privateip 192.168.0.1 port1935

rtmp://site2.mydomain:9999 ---> your public IP address port 9999 which then
hits the firewall and is redirected:

publicIP port 9999 -----> privateip 192.168.0.2 port1935


Simple to do and works well.


But in this case when I would like to try 

Layer 7 proxies / firewall have to look at the url requested and then

So if some one has got close to this one some idea let me know now how to proceed.

---

### Post by stlsaint on 2010-08-09
It seems you are referring to port forwarding and vhosting. Port forwarding is done with your router in your network. Forwarding IE: Port 80 to private ip.
Vhost is the process of hosting multiple domains with one ipaddress. This is done with apache2.

---

### Post by tapas_mishra on 2010-08-09
Please see this [link.]("http://comments.gmane.org/gmane.comp.emulators.xen.user/60848")
May be you can suggest me some thing.

---

