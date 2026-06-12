---
title: "Synergy &amp; iptables"
date: 2009-09-21
forum: Security
---

### Post by utannheim on 2009-09-21
I use Ubuntu in work and am running iptables (corp. standards and all that good stuff). I want to copy & paste text (well the clipboard really) between my Windows box and Ubuntu. 
Someone said to use Synergy. To get it working I need to disable iptables. Does anyone know how to configure iptables so that Synergy will work? Or is there a preferred alternative to allow clip sharing? 

Thanks!

---

### Post by bodhi.zazen on 2009-09-21
On the synergy server you need to allow (inbound) traffic to port 24800

What are you using to configure your firewall ?

---

### Post by utannheim on 2009-09-22
> **bodhi.zazen said:**
> What are you using to configure your firewall ?

No special tools - I will just execute the appropriate iptables commands to add the rule. Is there something you can recommend?

---

### Post by bodhi.zazen on 2009-09-22
No, I use iptables myself. Just write a rule to accept new connections on port 24800. I personally would limit connections to my subnet or a few specific ip addresses.

---

