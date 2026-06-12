---
title: "iptables settings"
date: 2010-02-19
forum: Security
---

### Post by hobert on 2010-02-19
Hi! A friend of mine typed following in my root-bash: 
```
iptables -P INPUT DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT --source srcaddr  -j DROP
iptables -A INPUT -s 192.168.0.0/24 -p tcp -m tcp --dport ssh -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport ssh -m state --state NEW -m recent --hitcount 3 --seconds 180 --update -j DROP
iptables -A INPUT -p tcp -m tcp --dport ssh -m state --state NEW -m recent --set -j ACCEPT
```Ment to ensure the security of the system. Is this right? Don't really know much about these instructions... Would appreciate if someone could tell me what the heck he was doing there! :)

Greets hobert

---

### Post by bodhi.zazen on 2010-02-19
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

