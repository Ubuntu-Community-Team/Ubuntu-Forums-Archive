---
title: "Is netfilter secure?"
date: 2011-03-30
forum: The Cafe
---

### Post by itguy1985 on 2011-03-30
Is it easily bypassed? Is there other programs you can use with it to make more secure?

---

### Post by cariboo on 2011-03-30
Netfilter is actually the firewall that all Linux distributions use, iptables is the frontend for netfilter, and there are several frontends for iptables. Most routers run a linux variant and use netfilter, It wouldn't surprise me if the commercial (window) firewalls are also based on netfilter.

---

### Post by itguy1985 on 2011-03-30
> **cariboo907 said:**
> Netfilter is actually the firewall that all Linux distributions use, iptables is the frontend for netfilter, and there are several frontends for iptables. Most routers run a linux variant and use netfilter, It wouldn't surprise me if the commercial (window) firewalls are also based on netfilter.

So it's pretty much the standard then?

---

### Post by SeijiSensei on 2011-03-30
> **itguy1985 said:**
> So it's pretty much the standard then?

For firewalls built on the Linux kernel, yes.  It's also been in use for about a decade.  If there were serious holes in the code, they would have been found and fixed long before now.  The "[netfilter HOWTO](http://netfilter.org/documentation/HOWTO/packet-filtering-HOWTO.html)" is dated 2002.  There's also a [summary]("http://www.netfilter.org/about.html#history") of the history of the code's development you can read.

---

### Post by itguy1985 on 2011-03-30
> **SeijiSensei said:**
> For firewalls built on the Linux kernel, yes.  It's also been in use for about a decade.  If there were serious holes in the code, they would have been found and fixed long before now.  The "[netfilter HOWTO](http://netfilter.org/documentation/HOWTO/packet-filtering-HOWTO.html)" is dated 2002.  There's also a [summary]("http://www.netfilter.org/about.html#history") of the history of the code's development you can read.

Thanks for the links, and your time kind sir/madam

---

