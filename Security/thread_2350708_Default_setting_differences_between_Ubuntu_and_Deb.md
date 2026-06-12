---
title: "Default setting differences between Ubuntu and Debian"
date: 2017-01-26
forum: Security
---

### Post by olie2 on 2017-01-26
Hey all, 

I usually use xubuntu or lubuntu on my desktop.  But I'm trying to get some software to run for work-related training, and it seems like the only time it is able to run smoothly is with debian. It seemed to run well with openjdk 7, icedtea plugin 7 and the nonfree-flashplayer in Debian. 

Openjdk 7 and icedtea plugin 7 don't seem to be available through apt. 

I have two questions:

1) What are the main differences (security-wise) between ubuntu distros and debian?  Besides one comes installed with ufw and the other doesn't. If I'm running an updated Debian system, with ufw enabled, and in a non-sudo account, are there big security holes I should be aware of?

2) Is there a way to run an updated, stable and secure openjdk 7 with icedtea plugin 7 in xubuntu?

---

### Post by ian-weisser on 2017-01-27
Openjdk 7 is in 12.04 and 14.04, so perhaps a (persistent) LiveUSB or VM with one of those is all you really need.

Little difference in security between Debian and Ubuntu.

UFW is not a firewall. It's merely a frontend to iptables, the real application that handles firewall duties. iptables is already included on all Debian and Ubuntu releases.
For what it's worth, firewalls themselves are a Windows workaround - Microsoft added exploitable listening services and call-home services hat the user couldn't disable. Firewalls in Ubuntu and Debian are essential for internet-facing servers, but any benefit to a Desktop system is fleeting. Better security habits on both Ubuntu and Debian is to regularly audit your open ports, check your network traffic, look at your logs, check that your system is up-to-date, keep regular backups of your data, keep good notes on how to properly restore your system, and have a handy current LiveUSB.

---

