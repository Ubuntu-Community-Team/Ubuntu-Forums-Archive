---
title: "[SOLVED] Ubuntu firewall questions!"
date: 2008-06-14
forum: Security
---

### Post by Rytron on 2008-06-14
Hi,
I have a few questions on Ubuntu and firewalls. I think that Firestarter is a frontend to  IP tables(please correct me on this if I am wrong). Is there a need to install a firewall in Ubuntu or are the IP tables a firewall? Also are the IP tables configured by default to provide the best security for Ubuntu users? Please help as I'd like clarification on this. 
Thanks.

---

### Post by Rytron on 2008-06-14
Found this:
[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")

---

### Post by ibutho on 2008-06-14
Most of the so called "Linux firewalls" are actually frontends to Netfilter and Iptables (When most people refer to iptables, they usually mean iptables+netfilter). I find it easier to use a fontend like [Shorewall]("http://www.shorewall.net") instead of memorising the iptables commands. Ubuntu has its own frontend called ufw (uncomplicated firewall).

---

### Post by spike_strip on 2008-06-14
Also see thread hear: [http://ubuntuforums.org/showthread.php?t=795141]("http://ubuntuforums.org/showthread.php?t=795141")

---

### Post by Pjotr123 on 2008-06-14
Security in Ubuntu explained:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

