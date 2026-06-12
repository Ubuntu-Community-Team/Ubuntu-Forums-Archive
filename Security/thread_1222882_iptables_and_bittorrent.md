---
title: "iptables and bittorrent"
date: 2009-07-25
forum: Security
---

### Post by devil81 on 2009-07-25
Hi: 

I was along time user of the iptables gui' but decided to try my hand at configuring iptables manually with some success I configured http, imaps, https and dns lookup.

I configured all of my rules manually but I am aware you can use ESTABLISHED and RELATED, for the replies to connections on the INPUT chain but I prefer to do it this way.

Anyway back to my question, I am using ktorrent and have configured the incoming, tracker and dht port access rights correctly, I think, in iptables and port forwarded from my router but Im getting no bittorrent traffic or connections whatsoever, so there must be something wrong. Heres my iptables rules:

-A INPUT -i lo -j ACCEPT 
-A INPUT -i eth0 -p udp -m udp --sport 53 --dport 1024:65535 -j ACCEPT
-A INPUT -i eth0 -p udp -m udp --sport 45682 --dport 1024:65535 -j ACCEPT

[CENTER]**45682 udp tracker port**[/CENTER]

-A INPUT -i eth0 -p udp -m udp --sport 51252 --dport 1024:65535 -j ACCEPT

[CENTER]**51252 udp dht port**[/CENTER]
 
-A INPUT -i eth0 -p tcp -m multiport --sports 80,443,993,11371 -j ACCEPT 
-A INPUT -i eth0 -p tcp -m tcp --sport 55821 --dport 1024:65535 -j ACCEPT   

[CENTER]**55821 main port**[/CENTER]

-A OUTPUT -o lo -j ACCEPT 
-A OUTPUT -o eth0 -p udp -m udp --sport 1024:65535 --dport 53 -j ACCEPT
-A OUTPUT -o eth0 -p udp -m udp --sport 1024:65535 --dport 45682 -j ACCEPT

[CENTER]**45682 udp tracker port**[/CENTER]

-A OUTPUT -o eth0 -p udp -m udp --sport 1024:65535 --dport 51252 -j ACCEPT


[CENTER]**51252 udp dht port**[/CENTER]
 
-A OUTPUT -o eth0 -p tcp -m multiport --dports 80,443,993,11371 -j ACCEPT 
-A OUTPUT -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 55821 -j ACCEPT  

[CENTER]**55821 main port**[/CENTER]

Forgive any amateurish mistakes as I only started configuring iptables via the CLI yesterday.

Thanks for any help,

devil81

---

### Post by The Cog on 2009-07-27
There are some strange incoming source port numbers there. I guess you think that torrent trackers are always on the same port number, but I think that is unlikely to be the case. You can control the port your own torrent tracker/server use, but you can't control everyone elses. That is why allowing related/establised is so useful. Anything that you choose to connect to can then reply. I think you might be spending a long time debuggig failures to connect to various services.

Otherwise it looks workable.

---

