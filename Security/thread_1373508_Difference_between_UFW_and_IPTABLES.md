---
title: "Difference between UFW and IPTABLES???"
date: 2010-01-05
forum: Security
---

### Post by aniruddha.kadne on 2010-01-05
Can anyone tell me the basic difference between ufw and iptables, if any? Whatever I know, both of them are same and ufw is built on top of iptables. Is it correct? If yes, then why do we need ufw when we already have iptables  serving the same purposes???

---

### Post by FuturePilot on 2010-01-05
UFW is just a simple (hence the U in UFW; **U**ncomplicated **F**ire**W**all) frontend to Iptables. You don't *need* UFW if you know how to and prefer to use Iptables. UFW is there so that someone could set up a firewall without having to know all the complex Iptables commands.

---

### Post by njdove on 2010-01-05
UFW also includes a framework that provides a normalized mechanism for loading iptables-restore(8) rules as well as facilities that allow arbitrary packages to provide their own rule sets that users can easily enable or disable via the "ufw app" commands. See man ufw-framework.

---

