---
title: "Firewall issue - swapping between router and direct connect"
date: 2014-07-12
forum: Security
---

### Post by oygle on 2014-07-12
I have been using a Sierra USB/dongle modem attached to a router. I'm the only user on the network and the only user of this computer. If I need a port opened on the outgoing, I simply add it to the routers table. All incoming ports are closed.

I need to be able to also use that same modem/dongle on either a laptop or on a desktop, attached directly, not behind a router. 

I see I have **iptables** and **ufw** installed by default. **Ufw** is disabled though , as would be expected.

When I go to use the modem directly attached/connected to the computer, what is the easiest method to add rules to **iptables**.

I have **ufw**, so is the GUI **Gufw** stable and robust, and no bugs ?

Thanks,

Oygle

---

### Post by bashiergui on 2014-07-12
No software is free of bugs. You can see the current and past bugs for gufw here, along with the updates released [https://launchpad.net/gui-ufw](https://launchpad.net/gui-ufw)
I'm sure if you fuzz it long enough you'll uncover some more bugs. 

Gufw is fine, it is in the official repositories and it is actively maintained.

If you're asking whether iptables, ufw, or gufw is easiest it depends entirely on you. Read the documentation for each and then decide which you prefer.

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

there are also several stickies in the security section with more helpful information.

---

### Post by oygle on 2014-07-13
Thanks [bashiergui]("http://ubuntuforums.org/member.php?u=1879546"), I will enable ufw and install gufw to add some rules.

I assume it is easy to disable ufw/iptables when I use the wireless broadband modem attached to the router, and then enable them again when the modem is directly attached to the computer.

Or can ufw/iptables work alongside a NAT firewall in the router ? Or, is that extra (unecessary) overhead ?

Oygle

---

### Post by SeijiSensei on 2014-07-13
If you trust the router, add a rule near the top of the ruleset to accept all traffic from its IP address.  You might want to consider using a non-typical subnet internally like 192.168.43.0/24.  Then if you take the machine out into the world, it is very unlikely to encounter another router with the same internal address and will ignore the rule entirely.

---

