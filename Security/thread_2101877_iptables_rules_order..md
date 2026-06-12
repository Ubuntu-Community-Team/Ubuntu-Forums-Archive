---
title: "iptables: rules order."
date: 2013-01-05
forum: Security
---

### Post by kleenex on 2013-01-05
Hello, there's something bothering me for a long time. It is about the order of the rules in the packet filter. Honestly, it's about one rule, responsible for [COLOR=Green]RELATED[/COLOR] and [COLOR=Green]ESTABLISHED[/COLOR] states. Let say, that default policy for [COLOR=Blue]INPUT[/COLOR] chain is set to DROP. There is also several others rules, for incoming packets like e.g. blocking icmp, invalid packets etc. My question: where I should put this rule: 
```
iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```I mean a rules order. This (above) rule should be placed on the beginning or at the end of [COLOR=Blue]INPUT[/COLOR] chain? I read a lot of iptables HOWTO's, FAQ's and many others. From what I understand, it is better to put this rule at the end of chain, because iptables check for matched rule from the top to bottom, right? I'm so confused.

Generally: From security point of view, it is better to put above rule, at the end or at the beginning of [COLOR=Blue]INPUT[/COLOR] chain?

---

### Post by Doug S on 2013-01-06
The short answer is the rule should go where it makes sense in the context of all your other rules in the INPUT chain.
 
To me, it does not make sense that it would be the last rule in the INPUT chain. Why? Two reasons: First, because it is typically used as a bypass around other rules that DROP or REJECT packets; Second is efficiency of traversing the iptables rule set, where you want to ACCEPT known good packets quickly and waste extra rule steps time on less frequent events.
 
It might be the first rule in the INPUT chain, if you have no specific things you want to DROP REJECT or ACCEPT. For example, you might want to DROP packets from some specific IP addresses or IP address ranges.
 
For my own iptables rule sets: For the server that is not also a router, the ESTABLISHED,RELATED ACCEPT rule is the first rule in the INPUT chain; For the server that is also a router the rule is about 2/3 of the way into the INPUT chain rules, after specific IP address DROPs, and some invalid state checks.

---

### Post by kleenex on 2013-01-06
Hi. Ok, it seems to be logic. Thank You, mr **Doug**.

---

