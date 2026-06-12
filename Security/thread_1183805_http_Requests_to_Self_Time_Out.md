---
title: "http Requests to Self Time Out"
date: 2009-06-10
forum: Security
---

### Post by webwriter on 2009-06-10
Long time reader, first time poster. :) 

I have a LAMP server running Intrepid Ibix as a single webserver. 

The server will not accept http requests from itself... I can't reprint my own rss feeds, use a link checker or run scripts via cron although I can remotely run all of these things.

I am guessing that I've set up iptables incorrectly and it's denying access from itself? 

I'm using Webmin's Linux Firewall module to manage iptables and honestly, have not changed it from the default installation profile. 

Any help or pointers would be much appreciated.  Thanks!

---

### Post by webwriter on 2009-06-10
More info:

The default action for packet filtering on incoming packets is set to the following:

Default action: Drop

  [[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=0") If input interface is not **eth0** 
[[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=0") If protocol is **TCP** and TCP flags **ACK** (of **ACK**) are set  
[[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=2") If state of connection is **ESTABLISHED**
 [[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=3") If state of connection is **RELATED** 
[[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=4") If protocol is **UDP** and destination port is **1024:65535** and source port is **53** 
     [[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=5") If protocol is **ICMP** and ICMP type is **echo-reply**
 [[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=6") If protocol is **ICMP** and ICMP type is **destination-unreachable**  
[[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=7") If protocol is **ICMP** and ICMP type is **source-quench**  
[[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=8") If protocol is **ICMP** and ICMP type is **time-exceeded**      
[[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=9") If protocol is **ICMP** and ICMP type is **parameter-problem** 
[[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=10") If protocol is **TCP** and destination port is **ssh** 
 [[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=11") If protocol is **TCP** and destination port is **auth** 
 [[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=12") If protocol is **ICMP** and ICMP type is **echo-request** 
 [[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=13") If protocol is **TCP** and destination port is **80** 
[[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=14") If protocol is **TCP** and destination port is **443** 
 [[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=15") If protocol is **TCP** and destination port is **25** 
 [[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=16") If protocol is **TCP** and destination port is **20:21** 
[[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=17") If protocol is **TCP** and destination port is **110** 
 [[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=18") If protocol is **TCP** and destination port is **143** 
[[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=19") If protocol is **TCP** and destination port is **10000:10010** 
 [[COLOR=#00aa00]Accept[/COLOR]]("https://10.1.0.6:10000/firewall/edit_rule.cgi?table=0&idx=20") If protocol is **TCP** and destination port is **20000**

---

### Post by cdenley on 2009-06-10
At a glance, that firewall configuration looks fine. I you disable the firewall, does it work? What is this output:
```

nc -zv localhost 80
nc -zv mydomain.com 80

```

---

### Post by webwriter on 2009-06-10
Genius!  Thank you, I think that's it.

We have 2 domains, and the DNS nameserver is the old domain, while our public domain is the new one. 

I think I need to rename the server. :p

---

