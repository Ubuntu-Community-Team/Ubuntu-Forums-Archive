---
title: "opening access to specific websites with iptables"
date: 2007-06-21
forum: Server Platforms
---

### Post by jhloaded on 2007-06-21
Good afternoon everyone,

I had the good fortune of picking up Linux on the fly after a recent departure by our Linux sys admin.  Being completely new to the Linux environment, I have already picked up quite a bit.  However, I stumbled on a problem with iptables.  Currently we have our laptops with locked access to everything except our internal network.  What I want to do is open up a specifc set of IP ranges for certain websites while continuing to restrict all other websites.  Below is a snapshot of what we are currently using:

> Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
REJECT     all  --  anywhere            !customer-reverse-entry.69.59.144.116 reject-with icmp-port-unreachable

My first question is how would I add an opening for the computer to access yahoo.com and continue to restrict access to all other non-internal websites?

My second question is more for my own knowledge.  Would it be possible for someone to provide a simple explanation of what the INPUT & OUTPUT chains are actually doing here?  

I appreciate any help with this.  

Thank you,

---

### Post by turinglabs on 2007-06-21
> **jhloaded said:**
> 
My first question is how would I add an opening for the computer to access yahoo.com and continue to restrict access to all other non-internal websites?


You would add a rule above the reject rule to ACCEPT tcp traffic on ports 80 and 443  to yahoo.com.  What to use in the rule for 'yahoo.com' is a problem, since the DNS entries are likely to be load balancers, the real connections will be sent elsewhere, and for big domains like yahoo it's even worse, as the load is distributed geographically. 

Decisions of this sort are probably best dealt with at the application layer, perhaps with a squid proxy and squidguard as a filter. If you do use the domain name in the iptables rule (as in 'iptables -A OUTPUT -d yahoo.com -j ACCEPT'), you will get one rule for each IP address that yahoo.com resolves to *at the time the ruleset is loaded*. I get something like this:

```

Chain OUTPUT (policy ACCEPT)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     0    --  *      *       0.0.0.0/0            216.109.112.135     
       0        0 ACCEPT     0    --  *      *       0.0.0.0/0            66.94.234.13

```

> **jhloaded said:**
> 
My second question is more for my own knowledge.  Would it be possible for someone to provide a simple explanation of what the INPUT & OUTPUT chains are actually doing here?  


INPUT is only traversed by packets with a destination address of the firewalled host itself.
OUTPUT is only traversed by packets originated from the host itself.

One thing - I notice your INPUT chain has a default drop policy (good), but you are accepting all traffic. Is this what you intend? If this is the case, the second rule accepting established and related packets will never be hit. For INPUT chains on host-based firewalls, you typically just want to drop everything. I have some scripts you can look at for an example if you are interested, let me know.

---

### Post by jhloaded on 2007-06-22
Thanks much Doug.  This was very helpful.  I am going to test this change over the weekend.  As to your question about the INPUT chain, I think you may be right.  Basically we have these set so they only accept internal connections but cannot be seen from the outside world.  With that being said, should I remove that first line?

---

### Post by turinglabs on 2007-06-22
Yes, remove the accept/all/all on the input chain and replace it with something like accept/lan/all for state NEW, so you are just specifying your internal network as a source. The default drop policy will drop everything else, and the established/related accept will handle existing connections (once they get past the NEW state).

FYI, I have some commented scripts you can look at for examples of this here: [http://geekpit.blogspot.com/2006/03/linux-iptables-firewall-scripts.html](http://geekpit.blogspot.com/2006/03/linux-iptables-firewall-scripts.html)

For your scenario, you would use the bastion host  script.

---

