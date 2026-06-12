---
title: "Firewall Help"
date: 2010-07-25
forum: Security
---

### Post by astrosmokewf on 2010-07-25
Is there a firewall I can install that will only let certain MAC addresses through on a certain port?

---

### Post by cariboo on 2010-07-25
Iptables is installed by default, as there are no services running in a default installion, there are no firewall rules set. Ufw a frontend for iptables is also installed by defaultm if you need a gui, gufw is in the repositories. I would suggest you have a look a bodi.zazens's [Iptables Primer]("http://bodhizazen.net/Tutorials/iptables/").

---

### Post by bodhi.zazen on 2010-07-25
> **astrosmokewf said:**
> Is there a firewall I can install that will only let certain MAC addresses through on a certain port?

iptables will do this for you.

[http://www.cyberciti.biz/tips/iptables-mac-address-filtering.html](http://www.cyberciti.biz/tips/iptables-mac-address-filtering.html)

---

