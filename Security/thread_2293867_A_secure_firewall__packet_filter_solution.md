---
title: "A secure firewall / packet filter solution"
date: 2015-09-08
forum: Security
---

### Post by Drenriza on 2015-09-08
Hi all

I have been through the great internet in search of peoples experiences with different firewall solutions, and have in that regard
discovered several sites saying that Ubuntu / iptables as a firewall and packet filter solution is unsecure.

The reasons for this is that 
[LIST]
[*]Ubuntu in the past and present has / is being shipped with unsecure software / ports in the default installation. Which widen the attack surface.
[*]That iptable
[LIST]
[*]Isint truly a stateful firewall (SPI)
[*]Has had several security bugs in the firewall itself, which (for example) lead attackers to pass the different chains unchecked.
[/LIST]
[/LIST]

I am really hoping for some feedback from the community on this, and what firewall / packet filter solutions you're using yourselves.

Thanks on advance
Kind regards

---

### Post by The Cog on 2015-09-08
That's not my understanding of iptables.
Do you have any references to support these claims?

---

### Post by Drenriza on 2015-09-08
> **The Cog said:**
> That's not my understanding of iptables.
Do you have any references to support these claims?

Well i wouldn't really call it a claim, more of a open question question i seek a more definitive answer to.

The resources that i find are for example
[http://www.unixmen.com/pf-vs-iptables-untangle-pfsense-why-not-both/](http://www.unixmen.com/pf-vs-iptables-untangle-pfsense-why-not-both/)

Edit
iptables is on its way out?

Wikipedia
> The successor of iptables is [nftables]("https://en.wikipedia.org/wiki/Nftables"), which was merged into the [Linux kernel mainline]("https://en.wikipedia.org/wiki/Linux_kernel_mainline") in kernel version 3.13, which was released on 19 January 2014

---

### Post by The Cog on 2015-09-08
I would entirely disregard that article as FUD.
> .. it doesn’t do true stateful inspection and has had quite a number of bugs.
I don't know about bug history. Most software has had bugs in the past. That's true of the software he is trying to push as well. 
No stateful inspection is simply not true. The iptables --state keyword relies on stateful inspection states. 
He is trying to compare to smoothwall and untangle - I think both of these are simply front-ends that end up configuring iptables - I am not going to talk about 3rd-party configuration generation utilities.

> With iptables things are different, packets are processed by various “chains” in different order, depending on the source and destination in the actual packet. For example, normal outgoing packets are processed by the output chain on the table. Rules within this chain can create processing to jump over to a different set of rules on a user-defined chain for example, or might even take such an action on a packet. When a packet matches a rule, processing on that chain stops without hesitation and the action is taken into effect. 
He is trying to imply that having multiple chains is a bad thing. I think that having a different set of rules for (say) incoming packets and outgoing packets is probably a good thing. It does of course make understanding the rules more complex than with a single linear list - maybe that's what is confusing him.

He is trying to imply that dropping out of a ruleset halfway through is a bad thing. I cannot see any reason to continue processing a packet once you know whether to reject or accept it - what else is there to think about? Other rules that might reverse the decision? Then don't put in a command that terminates packet processing - perhaps instead the packet should be passed to another more specific set of rules dealing with this special case, e.g. a chain of rules specifically tailored for packets from your server farm. I administer a server with (currently) 110 user-defined rules chains dealing with traffic to/from different groups of machines. I'd hate to try to do that in a single linear list.

My impression of that article is that he's trying to push his chosen software solution.

---

### Post by Lars Noodén on 2015-09-08
> **The Cog said:**
> He is trying to imply that dropping out of a ruleset halfway through is a bad thing. I cannot see any reason to continue processing a packet once you know whether to reject or accept it - what else is there to think about?

Even PF now has the [quick](http://www.openbsd.org/cgi-bin/man.cgi/OpenBSD-current/man5/pf.conf.5?query=pf.conf) option now for its rules.   A rule with *quick* on it is considered the last matching rule, and evaluation of subsequent rules is skipped.  As The Cog points out, once the decision is made about the packet, there is no need to waste more cycles on it.  

Either way, with iptables or PF, you can build either complex or fairly simple decision trees.

---

### Post by Drenriza on 2015-09-11
Awesome thanks for the information guys.

---

### Post by The Cog on 2015-09-11
> Edit
iptables is on its way out?


Edit: Previous post content deleted as it was totally wrong.

 I just tried this
```
iptables -A INPUT -s 8.8.4.4 -j DROP
nft add table ip test
nft add chain ip test input { type filter hook input priority 0 \; }
nft add rule test input ip saddr 8.8.8.8 counter drop
```
Both work - I can no longer ping 8.8.8.8 or 8.8.4.4. I can see the filters and the counters with these two commands:
```
iptables -nvL
nft listruleset
```
They show their own rules and counters, but not each other's . But both are active together.

So I guess nftables is there and ready to be used. I don't know what would happen if you configured conflicting rules. I imagine it would be best to use one or other only.

---

### Post by Drenriza on 2015-09-14
> **The Cog said:**
> Edit: Previous post content deleted as it was totally wrong.

 I just tried this
```
iptables -A INPUT -s 8.8.4.4 -j DROP
nft add table ip test
nft add chain ip test input { type filter hook input priority 0 \; }
nft add rule test input ip saddr 8.8.8.8 counter drop
```
Both work - I can no longer ping 8.8.8.8 or 8.8.4.4. I can see the filters and the counters with these two commands:
```
iptables -nvL
nft listruleset
```
They show their own rules and counters, but not each other's . But both are active together.

So I guess nftables is there and ready to be used. I don't know what would happen if you configured conflicting rules. I imagine it would be best to use one or other only.

Thank you very much for the reply and testing out nftables / iptables together :)
All in all i got some really good info on iptables with more.

Kind regards

---

