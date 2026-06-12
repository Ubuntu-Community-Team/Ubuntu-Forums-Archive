---
title: "[SOLVED] Iptables rules for loopback"
date: 2017-04-22
forum: Security
---

### Post by ty89 on 2017-04-22
Hi guys.

I am wondering what I have to think about in regards to making iptables rules for my server`s loopback for it to function properly without much risks.

Also I have a question about what the following rule means: 

iptables -A INPUT ! -i lo -s 127.0.0.0/8 -j REJECT

Thanks in advance.

---

### Post by SeijiSensei on 2017-04-23
That rule prevents spoofing of the localhost IP subnet (127/8) from any interface other than lo ("! -i lo").  I've never used such a rule and never had issues.

You should allow all traffic on localhost up at or near the top of your ruleset with
```
iptables -A INPUT -i lo -j ACCEPT
```
If you have a default deny policy for output packets, then you'll also need
```
iptables -A OUTPUT -o lo -j ACCEPT
```

---

### Post by ty89 on 2017-04-23
That's what I thought, but in the article I read it said "[FONT=Monaco][I]reject traffic
[/I][/FONT][FONT=Monaco]*to localhost that does not originate from lo0*[/FONT]". Is that the same? I was thinking that since it has -s it should be from 127/8.

And thanks for the reply :)

---

### Post by The Cog on 2017-04-23
As SeijiSensei says, the rule prevents spoofing: prevents other computers sending you packets that would appear to have come from yourself. 
I'm not sure what mischief could be achieved by sending such packets and have never used such a rule myself, but I see no harm in using it.

---

### Post by ty89 on 2017-04-23
Ok. But is it the same as [COLOR=#000000]"[/COLOR][COLOR=#000000][FONT=Monaco]*reject traffic *[/FONT][/COLOR][COLOR=#000000][FONT=Monaco]*to localhost that does not originate from lo0*[/FONT][/COLOR][COLOR=#000000]"? I am asking because I want to learn the logic of iptables, and the article I read said that. I think it should have -d 127/8 for it to be the same.[/COLOR]

---

### Post by SeijiSensei on 2017-04-23
It uses -s because it is intended to block packets with source addresses in 127/8 that are not originating from the actual localhost interface.  Suppose you had an interface eth0 with address 192.168.1.28.  That rule would block packets sent from another host on the 192.168.1.0/24 network that have a spoofed source address in 127/8.

This is pretty unlikely to arise in any real setting.  You'd need to have someone on the 192 network with a sophisticated piece of software that can spoof addresses.

---

### Post by ty89 on 2017-04-24
Ok, now I get it. Thanks

---

