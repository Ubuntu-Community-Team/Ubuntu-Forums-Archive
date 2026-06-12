---
title: "Block countries IP"
date: 2014-01-27
forum: Security
---

### Post by msavard on 2014-01-27
Hi all,

I tried the method in this thread: [http://ubuntuforums.org/showthread.php?t=1931490](http://ubuntuforums.org/showthread.php?t=1931490)

But I get this error message: "specified.4.4: invalid mask" for every entry from my cidr.txt.

Here are a few address from my list:
1.0.1.0/24
1.0.2.0/23
1.0.8.0/21
1.0.32.0/19
1.1.0.0/24
1.1.2.0/23
1.1.4.0/22
1.1.8.0/21
1.1.16.0/20
1.1.32.0/19
1.2.0.0/23
1.2.2.0/24

Any one knows why ?

Thank you

---

### Post by msavard on 2014-01-27
the website who created my list was the problem apparently.

I did another one using this site: [https://www.countryipblocks.net/country_selection.php](https://www.countryipblocks.net/country_selection.php) and I dont have the error message anymore.

My only concern is the number of address in my list, 15000 ! Will this affect the performance of the system ? 

Thanks

---

### Post by sandyd on 2014-01-27
> **msavard said:**
> the website who created my list was the problem apparently.

I did another one using this site: [https://www.countryipblocks.net/country_selection.php](https://www.countryipblocks.net/country_selection.php) and I dont have the error message anymore.

My only concern is the number of address in my list, 15000 ! Will this affect the performance of the system ? 

Thanks

It will, likely - iptables will have to look through all of those addresses each time a connection is incoming into the computer.

---

### Post by SeijiSensei on 2014-01-27
Ah, you solved your problem while I was writing my reply below.  I'll leave it for posterity.

15,000 rules would almost certainly impose some performance hit; the most rules I have on any machine I manage is about 900.  They're on a dual-Xeon box though and have minimal effect.  That said, iptables seems remarkably efficient for what it does with every packet entering or leaving the machine.  Empirical research makes the most sense here.  Impose the rules for a day or two and see if you can detect any difference.

> **sandyd said:**
> It will, likely - iptables will have to look through all of those addresses each time a connection is incoming into the computer.

That's a good point.  I'm usually running publicly-visible servers, so I'm generally concerned about managing inbound traffic.  On a firewall handling requests from LAN users, those 15,000 rules need not be consulted very often if you are careful about how you order your rules.

Rules that block inbound traffic should generally come after rules that exempt obviously permitted traffic like that originating on the LAN or sent in reply to requests from LAN users like web pages.  I usually make sure to place the rule
```
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```
right after the initial rule permitting the localhost interface.  That insures that no time is wasted scanning the reply traffic with other rules.  Right after that should be any rules that permit traffic from known hosts or addresses like the internal network.  Only then should you add the rules that pertain to inbound traffic.


Original response:

I take it you're running the script called "ban" in the thread you referenced?  Let's try a simpler approach first:

```

#!/bin/bash

BAN_LIST=/path/to/list.txt

for addr in $(cat BAN_LIST)
do
    echo "Blocking $addr"
    /sbin/iptables -I INPUT -i eth0 -s $addr -j REJECT
done

```

All this does is read every line in list.txt and inserts (-I) a blocking rule in iptables at the top of the ruleset. This will place these rules ahead of any other rules you may already have that apply to the INPUT chain.  It will also report each address before it inserts the rule. Create a file with these commands, mark it executable ("chmod a+x /path/to/program_file"), then run it. (Use "./program_file" if you are currently in the same directory as the program script.)  What happens?

---

### Post by msavard on 2014-01-27
thank you for your the information Seiji[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=698195") and Sandyd

---

### Post by Habitual on 2014-01-27
wrt: Performance... the .htaccess file is accessed for every 'hit' requested from the server.
If those same 'blocks' were used in a .conf file, then they are only read once, but you'd have to restart apache[2]|http[d] after 
making an entry.

If it's just countries you wish to block, try [www.cloudflare.com]("http://www.cloudflare.com") 
Their control panel has country blocking. You can sign up for free and still use that feature.

I have no association with cloudflare other than being a user of their services.
If you care about visitor stats, you may not wish to use them, as all your hits will be CF IPs.

There are ways around that however, depending on your software. These are noted on their site.

---

### Post by Doug S on 2014-01-27
For what it's worth, for [another post]("http://ubuntuforums.org/showthread.php?t=2107522") one time, I did a test and added 64,009 INPUT chain rules. Yes, the throughput degradation was significant, but as Seiji mentions above the effect can be minimized with careful ordering of the rules. For my test, I purposely did not minimize the effect, but rather maximized it.

---

### Post by canelle2 on 2014-09-19
To block countries using firewall, can refer to IP2Location's country blocker [http://ip2location.com/free/visitor-blocker](http://ip2location.com/free/visitor-blocker).
They supports IPv4 and IPv6.

---

### Post by unspawn on 2014-09-21
I agree a well thought out access policy should be at the basis of this. And if requirements allow it white listing is easier to manage and less reactive and therefore more efficient. Iptables rules are parsed in a "first rule match" way so having a ginormous amount of rules does have an effect. Rule placement, for example ditching traffic destined for the machine early on using the "raw" table PREROUTING chain (with -j NOTRACK?), also keeps your filter table clean. Anyway, performance and management wise using *ipset* would be preferable (fail2ban for example can use ipset) and if not available there's always iptables "recent" module buckets, albeit in a less flexible way compared to what ipset offers.

---

