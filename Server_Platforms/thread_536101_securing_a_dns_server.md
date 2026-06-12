---
title: "securing a dns server"
date: 2007-08-27
forum: Server Platforms
---

### Post by mtime2457 on 2007-08-27
Hello,

We have recently built a DNS server running on Ubuntu 6.0.6 and wanted to know what if anything should we do to lock down the system.

We are currently running ssh and bind9

---

### Post by Mr. C. on 2007-08-27
You're going to have to give a more complete description before you'll get more specific advice.

[LIST]
[*]Is this an internal-only DNS server ?
[*]Or does it serve the WAN as well ?
[*]How have you configured it ?
[*]Is there a firewall or NATing device between it and the WAN ?
[*]etc, etc.
[/LIST]

MrC

---

### Post by koenn on 2007-08-27
I don't know much about DNS / bind, but here's 2 cents :

1- make sure the server as such is secure. The usual : strong passwords; limit the # of users that can login /use ssh, ... 

2- DNS-specific :
other than exploits of bind, which I know nothing about, you don't want your DNS abused to reveil information about internal networks / hosts that shouldn't be known ouside your private LAN(s). 
Say your DNS is meant to resolve public domain names you host, than it shouldn't also resolve names of your file or database server or PC's on your LAN. You actually should use separate dns servers for public and private networks/domains/zones, and preferably those servers should be on seperate networks (i.e. the public DNS in a DMZ)

You also want to be able to trust your DNS and make sure that e.g. it's cache isn't polluted with spoofed addresses that take you to places you don't want to go. Step 1 to accomplish this is tell the dns server which other dns servers it should talk to / get info from. Usually, this means you set "forwarders" to dns servers you trust, and disable root hints. 

3- zone transfers. 
If you have multiple dns servers in a master-slave relation or replicating whith each other, you need to look up "zone transfers" . You may need to allow zone transfers between your servers, but don't want the mechanism abused for 2-

This should keep you usefully busy while you wait for other replies of more knowledgeble people  :)

edit: oh, someone more knowledgeble already beat me to it.

---

### Post by mtime2457 on 2007-08-27
We are building two internal dns systems and one external system.  The two internal systems will be behind a firewall and the third will be outside the firewall.

---

### Post by GigaVolt on 2007-08-27
HINT:
1) ACL
2) Views
URL: [http://www.isc.org/index.pl?/sw/bind/arm95/](http://www.isc.org/index.pl?/sw/bind/arm95/)

---

