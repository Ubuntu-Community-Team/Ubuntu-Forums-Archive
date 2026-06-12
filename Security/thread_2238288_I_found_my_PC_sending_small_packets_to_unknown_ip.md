---
title: "I found my PC sending small packets to unknown ip"
date: 2014-08-07
forum: Security
---

### Post by c8898f8f on 2014-08-07
Hi, newbie here, so this might be a stupid question...  I've started using etherape and wireshark recently, and when i was using VPN to surf, I found there are some strange link between my original IP and other strange IP. Sometimes it's my original internet service provider:(   From what i see in etherape, i seemed to have been sending small packets (56byes ), sometimes MYSQL and sometimes TCP-Unknown, but when I turn to wiresharks, the logs showed otherwise, i am really confused. Can anyone help me?

---

### Post by TheFu on 2014-08-07
Keepalive?

If you are using wireshark, you have the packets. What is the data being sent?  The labels may not be correct.

You could always just block all outbound data to that IP using iptables and see what happens.

---

### Post by c8898f8f on 2014-08-08
> **TheFu said:**
> Keepalive?  If you are using wireshark, you have the packets. What is the data being sent?  The labels may not be correct.  You could always just block all outbound data to that IP using iptables and see what happens.        Hi, thanks for the reply.  I checked with wireshark, and found there're some kind of ppp lcp packets going around, but it has no destination.  So either the etherape is wrong, or there is something I miss...        Is it possible to change wireshark logs if the system has already been compromised?   another thing I notice is that when i capture the packets using etherape, it says no IPv4 address is assigned, so the packets may be incorrect, maybe this is why the labels and the link indication are wrong? How can i assign my IPv4 address?        Sorry for all these questions.

---

