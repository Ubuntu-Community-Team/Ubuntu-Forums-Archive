---
title: "blocking msn &amp; yahoo using iptables"
date: 2008-05-08
forum: Security
---

### Post by usernameomar on 2008-05-08
I'm not familiar with iptables but i wanna block users in my network from using MSN Messenger & Yahoo Messenger, i have a netserver my entire network using it to connect to the internet i found this:-"http://lists.netfilter.org/pipermail/netfilter/2003-December/048925.html"

But i need to block the entire network and allow some hosts, any ideas?
i read in iptables but i understand little things the chains " FORWARD INPUT OUTPUT " but i just need to do it now.

---

### Post by mattress on 2008-05-08
There are a number of ways to do this. Probably the easiest is to setup your allow rules first, then simply block all traffic from your LAN to the common MSN ports. 

If you do a quick Google, you can grab this list.

Personally, if you're new to IPtables I'd go for something like Shorewall which makes life alot easier.

Writing a firewall script from scratch is not easy so perhaps start with Shorewall until you're a bit more familiar.

HTH

-m

---

### Post by damatta on 2008-05-08
I guess snort Intrusion Detection System meet your needs, however it's a daunting task to set up, unless you need it only for MSN filtering. It can detect this traffic regardless to what port or address are being used.
Once you get acquainted to it, just find some predefined rules such as chat.rules. However, people may still make use of, lets say, SSH tunneling to obscure their chat, but nothing so hard to tackle.
Heres is their official site: [http://www.snort.org/](http://www.snort.org/)
Here you can find some free rules: [http://www.bleedingthreats.net/](http://www.bleedingthreats.net/)

---

