---
title: "Ubuntu 16.04 Webmin &#304;ptables Problem"
date: 2018-08-09
forum: Server Platforms
---

### Post by secooonder on 2018-08-09
Hello
i manage iptables firewall with Webmin.i managed 30 iptables firewall until  today.
but ,first time i took an error from webmin.Moreover i added the same rule !
When i add establish,related state,i can not iptables-restore.i took an error.
i sent an attachment.
i think,When i added new or establish or related sentences,webmin is not detecting.
i tried it on different browsers and i turned off Antivirus programs but it wasnt solved.

Webmin version is 1.890
Ubuntu version is 16.04.4 Xenial.

Can you help me please?
Thank you

---

### Post by volkswagner on 2018-08-09
Did you look at /etc/iptables/rules.v4 line 180?

Don't use Webmin. It mangles your system then you wonder why
you get unexpected/undesired results.

If you still need help, please post /etc/iptables/rules.v4 contents (you can sanitize any public ip addresses to keep privacy).

---

### Post by secooonder on 2018-08-09
Volkswagner Thank you for your answer
i posted line 180 /etc/iptables/rules.v4

> -A FORWARD -p tcp -m tcp -m conntrack -s 192.168.5.51 -d 192.168.70.101 -j ACCEPT
COMMIT
&#305; click New,Relate Button ? Conntrack is irrelevant?

---

### Post by Doug S on 2018-08-09
> **secooonder said:**
> &#305; click New,Relate Button ? Conntrack is irrelevant?Yes, you specify the conntrack module, but then do not use it, hence the error message.

---

### Post by secooonder on 2018-08-09
what do you recommend.i did not write it like that in webmin

---

### Post by Doug S on 2018-08-09
> **secooonder said:**
> what do you recommend.i did not write it like that in webminWell, like volkswagner mentioned, don't use webmin. I assume you want this command:
```
iptables -A FORWARD -p tcp -s 192.168.5.51 -d 192.168.70.101 -j ACCEPT
```also as volkswagner mentioned, we would need your entire iptables rule set to be able to help further.

---

