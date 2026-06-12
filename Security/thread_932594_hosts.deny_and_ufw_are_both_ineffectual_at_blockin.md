---
title: "hosts.deny and ufw are both ineffectual at blocking access from specific IPs"
date: 2008-09-28
forum: Security
---

### Post by drewww on 2008-09-28
I'm trying to block a few specific IPs from accessing any services on a server running Hardy. Lets call that server Raincloud.

I've tried using both hosts.deny and UFW, but neither seems to do anything. 

Here's the contents of Raincloud's hosts.deny file:

```
ALL: 93.174.93.220, 93.174.93.221
```

I've tried changing those IPs to the IPs of servers I have access to and then trying to SSH into Raincloud from the denied IPs. I can SSH in fine. Same goes for HTTP traffic, too - I can still wget content off of Raincloud from a "banned" IP.

I've tried using UFW, and had pretty much the same experience. 

```
To                         Action  From
--                         ------  ----
22:tcp                     ALLOW   Anywhere
22:udp                     ALLOW   Anywhere
80:tcp                     ALLOW   Anywhere
443:tcp                    ALLOW   Anywhere
5060:tcp                   ALLOW   Anywhere
5060:udp                   ALLOW   Anywhere
6666:tcp                   ALLOW   Anywhere
6666:udp                   ALLOW   Anywhere
53224:tcp                  ALLOW   Anywhere
53224:udp                  ALLOW   Anywhere
Anywhere                   DENY    93.174.93.220
Anywhere                   DENY    93.174.93.221

```

As with hosts.deny, even if I set UFW to block IPs I control, I still have complete access from those IPs to services on Raincloud.

Of course, the spammer seems to still have access too. The servers I'm using to test are hosted in a different facility from Raincloud, so they shouldn't be that different from a spammer.

Anyone have thoughts/suggestions? I'm pretty stumped at this point. I've tried tcpdchk and gotten warnings on the IP's I'm banning not reverse-looking-up, but that's not a surprise and shouldn't be a problem.

Thanks!

---

### Post by kevdog on 2008-09-28
did you restart the firewall after making the changes?  Why dont you just modify iptables directly?  Give me the exact ip addresses you either want to allow or deny (the opposite will be the default behaivor) and Ill write the iptables rule for you!

---

### Post by jerome1232 on 2008-09-28
The reason UFW isn't doing it is the order of the rules matter, those deny rules, need to be before the allow rules. Basically it sees the allow all 22 first, then allows the traffic and never gets to the deny rule.

---

### Post by drewww on 2008-09-28
Ah, the ordering was the bit I was missing. Fixed that up. Thanks for your help!

It was a bit weird that there's no affordance for reordering in ufw itself, and that the config file is hidden in /var/lib/ufw instead of in /etc/ufw/ with the before/after files, but whatever. I found it, reordered, and all is well.

I'm still confused about hosts.deny, though. Any thoughts on why that didn't  have any effect?

---

### Post by jerome1232 on 2008-09-28
I don't know about why hosts.deny isn't working (it does for me) but one thing I wanted to clear up about my answer, when I said your deny rules need to be before your allow rules, I actually meant to say your specific rules need to be before your general rules. ie block/allow specific ips, then specific subnetts, then block/allow all

---

