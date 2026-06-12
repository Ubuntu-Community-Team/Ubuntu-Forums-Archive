---
title: "iptables question"
date: 2011-06-16
forum: Security
---

### Post by desire.linux on 2011-06-16
When looking at the iptables manual for the -s and -d parameters, it says:

> 
[!] -s, --source address[/mask]
              Source  specification.  Address  can be either a network name, a
              hostname [COLOR=Red](please note that specifying any name  to  be  resolved
              with a remote query such as DNS is a really bad idea)[/COLOR], a network
              IP address (with /mask), or a plain IP address.
Why is it a bad idea to use DNS lookups when adding rules?

---

### Post by capscrew on 2011-06-16
> **desire.linux said:**
> When looking at the iptables manual for the -s and -d parameters, it says:

Why is it a bad idea to use DNS lookups when adding rules?

Two reasons come to mind right away.
[LIST=1]
[*]One more layer of complexity that can fail
[*]DNS can be hacked
[/LIST]

---

### Post by BkkBonanza on 2011-06-16
It also adds quite a bit of load to have such a low level piece of code doing DNS lookups so often. For minimal activity it won't matter but consider if you have a busy network and iptables is bogged down doing hundreds/thousands of DNS lookups for all packets it needs to check passing thru. Every rule that has a name dependency will cause extra packets to be sent just to eval the rule, and the packet in question will be delayed until the DNS query returns and the rule can be resolved. I'm sure it must have some caching but still... only if there is no other way should this be done.

If you need to use names you might consider doing the DNS lookup at the time the rules are loaded if that is workable. And maybe use a cron to reload rules periodically perhaps - just an idea that came to mind.

---

### Post by desire.linux on 2011-06-16
> **capscrew said:**
> Two reasons come to mind right away.
[LIST=1]
[*]One more layer of complexity that can fail
[*][COLOR=Red]DNS can be hacked[/COLOR]
[/LIST]


Can you explain 2. some further? Thanks.

---

### Post by BkkBonanza on 2011-06-16
Anyone who can gain admin access to a DNS server is able to forge entries that could be used to direct traffic to the wrong server. DNS servers with vulnerabilities (as some older releases have shown) are able to be poisoned by hackers. Properly updated DNS servers should be safe, but it's always an area of concern and any user who can direct intercept traffic between you and the DNS server can potentially fake name resolution. An example is using ARP spoof attacks to re-route gateway traffic on a LAN. In an unsecured LAN (such as wifi) this is potentially dangerous.

So the reasoning is why make your iptables security rules dependent on potentially unsafe outside resolution.

---

### Post by Dave_L on 2011-06-16
> **BkkBonanza said:**
> Anyone who can gain admin access to a DNS server is able to forge entries that could be used to direct traffic to the wrong server.

That's an interesting point.

Suppose I'm accessing by web browser, for example, a banking site. Does the web site's security certificate provide a reasonable degree of protection against DNS hacking?

---

### Post by BkkBonanza on 2011-06-16
At this time DNS and certificates are completely separate. The certificate tells you are connected to the correct site as long as the certificate hasn't been forged (but it has no IP info embedded). It's not easy to forge a certificate for your average guy but it is within the realm of what some agencies, governments or deep pocketed hackers could achieve.

By this I mean that I could forge a certificate but if it's not accepted by your browser then you get a security warning. However, it doesn't warn you if the certificate authority is accepted - so a forgery can be made by any authority that is accepted by your browser, and that list is quite long nowadays (see the list of Authorities in the certificate manager in your browser!). And some newbie users may not recognize that their browser is shouting at them when an unverified certificate is received and ignore it anyway.

Ideally you would use a plugin like "Certificate Patrol" which will check each certificate accepted and compare it to the last time you visited and if it's changed then it lets you know something is up. It may be a normal renewal but it potentially could be a forgery created by another authority.

There are plans in motion to combine certificates with DNS to provide better security using DNSSEC but I don't think we're going to see that soon even though it is supported by some DNS providers.

---

### Post by Dave_L on 2011-06-16
Thanks for the explanation.

---

### Post by SeijiSensei on 2011-06-16
I always thought the reason not to use hostnames is a simple one: name resolution usually isn't available when the rules are loaded.  Iptables runs before the network is started, even on machines with static IP setups using /etc/network/interfaces.*  So if you use hostnames in the rules, they won't be resolvable unless they're all listed in /etc/hosts.  Using IP addresses throughout the rules avoids this problem entirely.

> **BkkBonanza said:**
> It also adds quite a bit of load to have such a low level piece of code doing DNS lookups so often. For minimal activity it won't matter but consider if you have a busy network and iptables is bogged down doing hundreds/thousands of DNS lookups for all packets it needs to check passing thru.

This shouldn't happen in practice.  All the iptables rules are IP-based; any names used in the rules would be resolved only once, to determine the IP address to be used when creating the rule.  After that, symbolic hostnames in the ruleset shouldn't matter at all.


_____________________

*In fact, the iptables rules should be loaded before the network is started for maximum security.  Otherwise there will be a small window of opportunity for exploitation between when the network starts and when the rules are imposed.

---

### Post by BkkBonanza on 2011-06-16
Ya, that probably makes more sense.

---

### Post by 016284 on 2011-06-16
> **BkkBonanza said:**
> At this time DNS and certificates are completely separate. The certificate tells you are connected to the correct site as long as the certificate hasn't been forged (but it has no IP info embedded). It's not easy to forge a certificate for your average guy but it is within the realm of what some agencies, governments or deep pocketed hackers could achieve.

By this I mean that I could forge a certificate but if it's not accepted by your browser then you get a security warning. However, it doesn't warn you if the certificate authority is accepted - so a forgery can be made by any authority that is accepted by your browser, and that list is quite long nowadays (see the list of Authorities in the certificate manager in your browser!). And some newbie users may not recognize that their browser is shouting at them when an unverified certificate is received and ignore it anyway.

Ideally you would use a plugin like "Certificate Patrol" which will check each certificate accepted and compare it to the last time you visited and if it's changed then it lets you know something is up. It may be a normal renewal but it potentially could be a forgery created by another authority.

There are plans in motion to combine certificates with DNS to provide better security using DNSSEC but I don't think we're going to see that soon even though it is supported by some DNS providers.

Indeed, also having a Firewal in your router may be helpful.

---

### Post by capscrew on 2011-06-16
> **016284 said:**
> Indeed, also having a Firewal in your router may be helpful.

IPtables ***is ***the firewall.

---

