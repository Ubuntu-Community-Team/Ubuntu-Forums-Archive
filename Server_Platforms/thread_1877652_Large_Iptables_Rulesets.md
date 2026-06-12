---
title: "Large Iptables Rulesets"
date: 2011-11-08
forum: Server Platforms
---

### Post by BajaMnstr on 2011-11-08
I have a conundrum I'm hoping someone can help with.

I'm running a bandwidth shaping server on ubuntu 8.04.1 (kernel 2.6.24-24-server)

I have a large number 4000+ Iptables rules that are flushed and rebuilt quite often throughout the day as changes are made. These rules are matching traffic based on source mac address. ( $IPTABLES -t mangle -A PREROUTING -m mac --mac-source $MAC -j MARK --set-mark 0x42 ) 

This pulls the requisite information from a database and builds out the rules. The problem comes in because the rules take 59 seconds to load, I'm running into problems with concurrent sessions trying to rebuild the rules. 

What I'm looking for is a way to rebuild the rules, or put them into a set a la ipset. Where iptables doesn't have to pull the rules from ram and reload them with every rule change. Which takes longer and longer as the rule table grows. 

Any ideas?

-Wayne

---

### Post by koenn on 2011-11-08
If you're using 4000+ seperate iptables statements, you might want to try iptables-restore

this reads in a set of rules in 1 uptables call (in stead of 4000)

```
iptables-restore < /path/to/ruleset-file
```

So instead of generating iptables statements, you should generate iptables-restore compatible rules in a file that you can feed into yptables-restore

the format is described by "iptables-save" : 
[http://www.faqs.org/docs/iptables/iptables-save.html](http://www.faqs.org/docs/iptables/iptables-save.html)


that said, there are maybe  better ways to do traffic shaping, 
eg [http://linux.die.net/man/8/tc](http://linux.die.net/man/8/tc)

---

### Post by BajaMnstr on 2011-11-09
Koenn,

Thanks for the reply. However, I have tried the iptables save and restore trick before. However I ran into issues concerning reliability of the ruleset once loaded into memory.

I am using TC for bandwidth shaping, however these are the firewall rules that block/allow/redirect/bypass traffic through the firewall and before they are passed off to the queuing mechanism. However the blocking rules must be in place to prevent traffic to unknown or unauthorized addresses. 

-Wayne

---

### Post by koenn on 2011-11-09
> However I ran into issues concerning reliability of the ruleset once loaded into memory.
and you think that's a limitation of iptables-restore ? why ?

what sort of reliability issues ?

---

### Post by BajaMnstr on 2011-11-09
Sorry that I wasn't more detailed in my previous reply. 

The resulting instability of the rule set basically boils down to the actual functioning rules in memory, not actually being what was loaded from file. IE.. 4000 Rules loaded and only 3500 mangling packets correctly. This only occurs when I load with iptables-restore.

When I load the rules one at a time through the command line script, the mangling performance is consistent and correct. It just appears that some of the rules do not function after performing an iptables-restore.

---

