---
title: "[SOLVED] Ip filtering like a router"
date: 2008-07-01
forum: Server Platforms
---

### Post by jeantasse on 2008-07-01
Hi everybody, i would like to filter ip adress on my ubuntu server like a router would. Exemple: i have block about 10 chinesse isp because about 90% of the people that tries to hack me comes from there. But now my router tells me hes full. Can i compensate with a program install on my server?? Thank you i advance

P.S. Happy Canada Day to all Canadian out there ):P

---

### Post by mrpeenut24 on 2008-07-02
You can usually block ip addresses in your /etc/hosts.deny file.  I'm not entirely sure if ssh looks at this file or not.  It seems that if it's compiled with tcp_wrappers enabled it should.

[Here]("http://forums.devshed.com/bsd-help-31/blocking-a-range-of-ip-s-in-hosts-deny-322368.html")'s a pretty good link.


Another good way to do this is with IPtables, but I'm not very keen on how to use it.  Maybe someone else here can help you with that.  But [here]("http://blacklist.linuxadmin.org/")'s a link that will make iptables use a lot easier.

---

### Post by jeantasse on 2008-07-02
Hey thank you very much for the help and for the links, i will look in to it.

JF:)

P.S. how to i mark this one as solved???

---

### Post by mrpeenut24 on 2008-07-03
At the top, click Thread Tools > Solved

---

