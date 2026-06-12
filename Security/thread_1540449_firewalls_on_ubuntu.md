---
title: "firewalls on ubuntu?"
date: 2010-07-27
forum: Security
---

### Post by Ready2DropWin on 2010-07-27
I have a question about firewalls in ubuntu, are they needed? I was under the impression that ubuntu was a very safe and protected os. If firewalls are needed, or just an extra safely procession, what firewall would you recommend from the software center?
Thanks!

---

### Post by sisco311 on 2010-07-27
I don't know. What "server software(s)" are you using? 

Check out the firewall section from [thread=510812]Ubuntu Security[/thread] before you answer.

---

### Post by bodhi.zazen on 2010-07-27
> **Ready2DropWin said:**
> I have a question about firewalls in ubuntu, are they needed? I was under the impression that ubuntu was a very safe and protected os. If firewalls are needed, or just an extra safely procession, what firewall would you recommend from the software center?
Thanks!

In addition to thre security sticky you can see the security FAQ :

[https://wiki.ubuntu.com/SecurityTeam/FAQ#UFW](https://wiki.ubuntu.com/SecurityTeam/FAQ#UFW)

> Why is the ufw firewall not enabled by default? 

ufw  is available in all new installations of Ubuntu since 8.04 LTS, but is  disabled by default. The standard Ubuntu installation has a [no open service ports]("https://wiki.ubuntu.com/DebuggingSecurity#Local%20Network%20Privacy")  policy, so enabling the firewall by default doesn't gain any extra  security in the default installation, but could provide confusion for  people new to Ubuntu when new software that is installed does not work  because of restrictive firewall rules. As a result, when first [adding ufw to Ubuntu]("https://wiki.ubuntu.com/UbuntuFirewallSpec") it was decided that users must 'opt-in' to using the firewall. In Ubuntu 9.04 and later, you can enable ufw during installation using preseeding. See /usr/share/doc/ufw/README.Debian for details.

---

### Post by Ready2DropWin on 2010-07-29
Thank you, the links help a lot, I have my firewall configured now.

---

