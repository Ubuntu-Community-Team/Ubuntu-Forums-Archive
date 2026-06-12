---
title: "iptables rule selection + new,related connections"
date: 2016-06-14
forum: Security
---

### Post by Drenriza on 2016-06-14
Hi all

I have two questions i hope someone can help me with

#1 Does iptables use the first rule that fulfills a criteria, or does iptables read all the rules and select the most specific?

#2 If you have a 3G / 4G router that you wont allow to be contacted from the outside world >but< connections / sessions established from the local network through the router
are allowed to cross in both directions?

I know you can use the new, established and related keywords for this, but i have never quite figured out how and the information ( that i can find ) aren't defining these keywords that well.

Thanks in advance
Kind regards.

---

### Post by Drenriza on 2016-06-16
anyone? :)

---

### Post by Doug S on 2016-06-16
> **Drenriza said:**
> #1 Does iptables use the first rule that fulfills a criteria, or does iptables read all the rules and select the most specific?packets will traverse the iptables rule set in order. If the rule "fulfills a criteria" it follows that rule, and if that rule branches out somehow, then subsequent rules will not be tested against.

> **Drenriza said:**
> #2 If you have a 3G / 4G router that you wont allow to be contacted from the outside world >but< connections / sessions established from the local network through the router
are allowed to cross in both directions?Yes, that is how most iptables based routers / firewalls are setup. (I do not know what you mean by a 3G / 4G router. I am only answering about iptables).

> **Drenriza said:**
> I know you can use the new, established and related keywords for this, but i have never quite figured out how and the information ( that i can find ) aren't defining these keywords that well.I don't know how to help with this. These are some of the most fundamental keywords in any iptables rule set. I don't know how to describe them any better than is already done in [man iptables-extensions]("http://manpages.ubuntu.com/manpages/xenial/man8/iptables-extensions.8.html"). Excerpt:
```
       NEW    The packet has started a new connection or otherwise associated with a connection which has not seen packets in both directions.

       ESTABLISHED
              The packet is associated with a connection which has seen packets in both directions.

       RELATED
              The packet is starting a new connection, but is associated with an existing connection, such as an FTP data transfer or an ICMP error.
```However, using tcp as an example, it might help to study how a new tcp connection is made, moving from the initial SYN packet to the ESTABLISHED state, via two way handshaking (i.e. a SYN ACK packet for the initial SYN).

---

### Post by SeijiSensei on 2016-06-16
1)  The first matching rule takes precedence.

2)  I'm not sure what you're asking.  If you're using a router, it will already masquerade your outbound traffic.  You don't need any "established,related" rule of your own.  In general, the router will be using the same type of rule, only accepting inbound traffic in reply to an outbound request.

---

