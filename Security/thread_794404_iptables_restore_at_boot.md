---
title: "iptables restore at boot?"
date: 2008-05-14
forum: Security
---

### Post by DigitalDuality on 2008-05-14
d

---

### Post by bobblehat on 2008-05-15
Hi, there's a tutorial on IPTables here which includes instructions on making your config persistent [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

It seems to suggest 
pre-up iptables-restore < /etc/iptables.rules
as you mention.

I hope that helps.

---

