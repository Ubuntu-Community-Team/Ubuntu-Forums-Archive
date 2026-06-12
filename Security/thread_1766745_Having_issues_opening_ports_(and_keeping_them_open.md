---
title: "Having issues opening ports (and keeping them open) with Firestarter"
date: 2011-05-24
forum: Security
---

### Post by grant907 on 2011-05-24
Hello, I have been using Firestarter as a GUI for iptables. I have never had a problem with common ports like 22, 21, 80, 443 as Firestarter notices them as a service such as (22=SSH, 80=HTTP) so it opens the ports correctly. When I try to open port 10000 for Webmin or port 6666 for my IRC server, it works for about 3 minutes then reverts back to some weird firewall setting and opens a whole new set of ports including submission, pop3, snmp which I don't use and closes the ones I put into Firestarter. Anybody have a solution to this? I have tried flushing iptables and the only solution that works currently is restarting Firestarter. Thanks!

---

### Post by grant907 on 2011-05-24
Solved

---

