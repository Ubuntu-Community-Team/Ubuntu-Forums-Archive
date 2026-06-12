---
title: "Ubuntu not resolving url's"
date: 2006-09-18
forum: Server Platforms
---

### Post by cybrid on 2006-09-18
Hi there ubunters:

I have a problem, till 2 days ago my ubuntu was doing fine,but now it seems it can only resolve ip addressess and not url's, although DNS servers are configured (their addressess are set in /etc/resolv.conf). I have it running a LAMP and iptables has no rules set.

has anybody an idea of what can be going on?.

Thanks in advance.

---

### Post by cybrid on 2006-09-18
Ok, solved, it seems that gnome-network-manager wasn't really writeing the ip addressess of the DNS's and they dissapeared with each reboot :( and therefore ubuntu didn't resolve url's. Though this is strange; can it be a gnome-network-manager bug?

---

