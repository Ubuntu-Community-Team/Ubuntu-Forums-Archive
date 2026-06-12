---
title: "BIND9 (help with topology) ubuntu server ed"
date: 2008-07-23
forum: Server Platforms
---

### Post by Kylibar on 2008-07-23
Ok, I have a perfectly good set of dedicated DNS servers, a primary and a secondary. They work just fine, but only on the local network. I understand that 192.168.x.x is for private networks, what I dont understand is the port forwarding and how to actually broadcast. I can point my zone files to my static IP and still no luck. In theory, you should be able to create your own TLD with bind9 right? example; myname.bla


anyway, any tips would be helpful here. I know i need another static IP from my ISP for my secondary?? right? i only have one static ip right now. aside from that, do i need static IP's for my HTTP / FTP / POP3 & SMTP servers? (they are all dedicated as well) a static (public) IP for each unit?

so even if I got all of these IP addresses, and even bought a registered TLD like myname.com, how would the topology be set up? Ive tried several different configs (its easy to get lost in fun stuff :D for example - I have a larger home network totaling in about 10 user nodes and 8 servers 3 network hardware devices (routers / gateways ect) and 1 dedicated shorewall fw. so where do my DNS servers fit in? before my dedicated fw but after the DSL modem? or maybe its some kind of porting and forwarding issue? I know my firewall works fine, along with the rest of my servers. I know it has to be some very small slight setting... just like always. please help.

if anyone needs a current topology diagram :

[INDENT]>internet>>
   [INDENT] >DSL Modem>>[/INDENT] [INDENT]       >Dedicated Firewall (actual computer / unit)>>[/INDENT]            [INDENT]>wired router>>[/INDENT]                 [INDENT][INDENT]>wired router>>
                     [INDENT] >DNS1
                      >DNS2
                      >other servers as well[/INDENT]                 >wireless gateway (actual computer/unit - for all wireless access)
                 >wired router>>
                     [INDENT] >all 10 or so user nodes (lan parties ect...)[/INDENT][/INDENT][/INDENT][/INDENT]hope this helps...hope someone can help me :)

thanks guys

---

