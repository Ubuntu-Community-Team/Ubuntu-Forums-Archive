---
title: "Need help in bind9 configuration"
date: 2013-06-06
forum: Server Platforms
---

### Post by kr0no on 2013-06-06
Hi,


I have to mount a DNS server and create a forward zone (srd.lan) and reverse zone (172.20.64.0/20) on a Ubuntu server.


The fact is that when using 20 bits for the network mask, do not know how I have to create the reverse zone correctly.


In full activity I have to do:



[LIST]
[*]Set the zone "srd.lan" and its corresponding reverse zone (172.20.64.0/20).
[*] The primary DNS server is identified by the IP 172.20.64.1, your name will servidor.srd.lan.
[*] This server will also mail server (with alternative names mail.srd.lan and [url] www.srd.lan [/ url]).
[*] The server will also servidor.srd.lan these aliases: alum1.srd.lan, a1.srd.lan, alum2.srd.lan and a2.srd.lan
[*]A secondary DNS server IP 172.20.72.1 called servidor2.srd.lan with
[/LIST]
This server has to be well specified both the main server and secondary.
It will also be a mail server with the same priority as the mail server and with two names servidor.srd.lan (correo.srd.lan., And web.srd.lan).
[LIST]
[*]Two customers with names and client100.srd.lan client1.srd.lan with IPs (172.20.71.254 and 172.20.79.254).
[*]The parameters of the direct and inverse area are: Mail Administrator (administrador@srd.lan), serial number 5, update time 2 hours, 10 minutes retry time, Expiry at 12 hours and lifetime in cache 12 hours.
[*]The generic lifetime for all records will be 10 hours.
[/LIST]


The fact is that currently I have this:
**named.conf.local**
[IMG]http://gyazo.com/9e1bb84c2dbdb1de754c5d74381dcc50.png[/IMG]


[B]db.srd.lan
[/B][IMG]http://gyazo.com/5e17bdb2e7eeb7be44ecdd30a5d27d4e.png[/IMG]


[B]db.172.20
[/B][IMG]http://gyazo.com/3e69d8d8f91a96f2fce3b462f1ab6714.png[/IMG]

But yet, when I do a dig to see the DNS servers not responding nothing ANSWER and the status it's SERVFAIL:
[IMG]http://gyazo.com/7f796f4c165738ef78ce1dd054c20f0e.png[/IMG]


Anyone can help me out and tell me what happens? 

Sorry for my english, translated with Google traductor

---

