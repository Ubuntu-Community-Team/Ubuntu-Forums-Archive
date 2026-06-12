---
title: "simple iptables rules"
date: 2007-01-05
forum: Server Platforms
---

### Post by sooqing on 2007-01-05
I am a newbie to firewall. I like to ask if it is safe for me to continue using the following rules for ONLY web browsing using my house PC. So far, I have not faced any problem after 6 months of usage and my PC passed the GRC.com's Shield Up test.

Thanks you!

===========

iptables -P INPUT DROP
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT

---

### Post by rth on 2007-01-05
Rules are processed in order. So, your 2nd line is doing nothing at the moment. Other than that, you should be fairly safe as all ports are protected by iptables for inbound connections.

---

### Post by mannheim on 2007-01-08
> **rth said:**
> So, your 2nd line is doing nothing at the moment. 

I don't think that's correct. The "iptables -P INPUT ... " command sets the *policy* for the input chain: this specifies what should happen to a packet *after* it has traversed the chain, if it drops through. So the rules in the chain which are created with "iptables -A INPUT ... " are applied first.

---

### Post by chrisfay on 2007-01-08
> So the rules in the chain which are created with "iptables -A INPUT ... " are applied first.

Wrong....Rules are applied in the order they are given. If you specify a deny all rule first, it doesn't matter what you open afterwards, everything will be blocked.

From [http://www.netfilter.org/](http://www.netfilter.org/):

> Its important to note that the order in which rules are appended is very important. For example, if your first rule is to deny everything... then no matter what you specifically allow, it will be denied.

So in the OP's case, the input rule would make zero difference as stated by rth.

---

### Post by erik.osterholm on 2007-01-11
Except that the first line in the original post is not a rule, it is a **policy**.  It sets the default action for all packets entering the chain.  


[i]iptables -P INPUT DROP
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT[/i]

From man iptables:
       > -P, --policy chain target
              Set  the policy for the chain to the given target.  See the sec&#8208;
              tion TARGETS for the legal targets.   Only  built-in  (non-user-
              defined)  chains  can  have  policies,  and neither built-in nor
              user-defined chains can be policy targets.

And:
> 
If the end of a built-in chain is reached or  a  rule
in a built-in chain with target RETURN is matched, the target specified
by the chain policy determines the fate of the packet.


mannheim was correct.

To the original poster:
I tend to like to explicitly set my policies in the scripts I use to maintain IPTables.  in this way, I don't have to worry that my output policy target might end up being DROP without my knowledge.  So I would add:
iptables -P OUTPUT ACCEPT
to the script.

---

### Post by chrisfay on 2007-01-11
> Except that the first line in the original post is not a rule, it is a policy. It sets the default action for all packets entering the chain.

Touche :mrgreen:

---

