---
title: "connect to an ftp site through proxy error"
date: 2006-12-19
forum: Server Platforms
---

### Post by wshamroukh on 2006-12-19
Hi all

i have an Ubuntu box acting in my  network as proxy(squid) and firewall(iptables) server. my problem summarizes as following:

my windows xp clients obtain their ip's from a DHCP server,
ip address 192.116.3.34
subnetmask 255.255.255.0
gateway 192.116.3.13
primary dns 192.116.3.14

the gateway ip here is the ip of the Ubuntu proxy server. No when this client try to connect to an FTP server using ftp browsers such as WS_FTP, it would not connect at all to the FTP server.

I have another internet line, and my users connect to this line through a FC4 Linux proxy server and firewall. which has ip: 192.116.3.11

when i change the windows xp gateway ip to 192.116.3.11(e.i to the FC4 proxy server) the FTP browser WS_FTP can connect to the FTP server without any error.. The amazing thing, is that, both of those proxy servers, i mean the Ubuntu and the FC4 server, has the same settings in the squid and in the iptables... this really astonishing me.. I cannot figure it out why the first one will not allow my windws clients to open FTP while the second allow my windows client to go through and open FTP through the FTP browser.

and the most astonishing thing, when i open the ftp server on either IE or Firefox browser, it will open normally without anything wrong. I mean when my gateway is set to 192.116.3.13 or to 192.116.3.11

can anybody tell me what is going on here


thank u in advance guys

---

