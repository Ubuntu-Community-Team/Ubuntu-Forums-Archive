---
title: "TP-LINK router with Firewall."
date: 2012-07-13
forum: Security
---

### Post by kleenex on 2012-07-13
Hi, I have a trivial question, but I do not understand something. Let say, that I am using TP-LINK router for WiFi on laptop and one compiter with classical cable connection[COLOR=Red]*[/COLOR]. The router firewall is enabled with also some additional protections, such as SYN Flood protection, limit ICMP etc. My question: whether the firewall enabled in the router protects both computers? I mean laptop and just a simple desktop computer. On each computer is Linux installed. Do I need a firewall on these two Linux systems, or just the firewall of the router is sufficient? Or perhaps it is best to have the firewall on both computers and router the same time? 

[COLOR=Red]*[/COLOR] Topology - it looks more or less this way: ```
[COLOR=DarkGreen]ISP modem[/COLOR] [COLOR=Blue]**--**[/COLOR] [COLOR=DarkRed]ROUTER[/COLOR] **[COLOR=Blue]--[/COLOR]** [COLOR=Olive]Desktop (cable connection)[/COLOR]
                [COLOR=Blue]**|**[/COLOR]
                [COLOR=Blue]|[/COLOR]
         [COLOR=Purple]laptop with WiFi[/COLOR]
```Router firewall protects all internet connections: WiFi and cable?  Am I right?

---

### Post by Cheesehead on 2012-07-13
> **kleenex said:**
> Router firewall protects all internet connections: WiFi and cable?  Am I right?

Yes. Most routers treat the wireless and ethernet LAN as a single local network, and the firewall protects it from the untamed internet (unless you turn the protection off).

---

### Post by kleenex on 2012-07-14
Okay, now everything is clear. Thank You Cheesehead!

---

