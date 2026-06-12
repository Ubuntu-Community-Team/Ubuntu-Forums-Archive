---
title: "[SOLVED] Denyhosts and Iptables for a simple network"
date: 2008-02-29
forum: Security Discussions
---

### Post by Oldsoldier2003 on 2008-02-29
Hello, I need some guidance from the security gurus out there on how to protect a simple home network.

I have three PCs behind an ADSL gateway configured as 192.168.0.1

the gateway is set up to forward traffic on port 9998 and port 22 to my Ubuntu 7.10 server which resides at 192.168.0.5

I've read several tutorials on Iptables and also on shorewall, but they've really confused me because they mostly refer to using the ubuntu server as the firewall server/router.

Early on i set up denyhosts to stop the SSH brute force attacks and am happy with that level of protection. What I am trying to do now is understand the best way to protect my server from unwanted accesses on port 9998.

What i need to help with is how allow all of my available services to be reached by computers on my private subnet 192.168.0.*  , and block certain IP ranges from the internet. Specifically I need SFTP on port 22 available and tcp 9998 available to the outside world. Is this possible with only one network interface and a dynamic IP address redirected to my hostname by dyndns?

---

### Post by Oldsoldier2003 on 2008-02-29
Never mind, after taking a deep breath I installed Bastille and found a script that makes blocking by ip range rather simple.

---

