---
title: "Apache2 not accessible from LAN"
date: 2011-04-01
forum: Server Platforms
---

### Post by lam3r on 2011-04-01
Hi there.

I have a problem with apache server. The thing is - I can connect to my server on localhost, but when I try to connect from local network, it doesn't reply.

I can ping my web server from lan. I can ssh my web server from lan.

I haven't modified iptables since install except these commands>

```

iptables -A INPUT -p tcp -s 0/0 --sport 1024:65535 -d $MY_SERVER_IP --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp -s $MY_SERVER_IP --sport 80 -d 0/0 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

iptables -A OUTPUT -p tcp -s $MY_SERVER_IP --sport 1024:65535 -d 0/0 --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -p tcp -s 0/0 --sport 80 -d $MY_SERVER_IP --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT

```

I'm trying to implement dokuwiki and I'm pretty much stuck. I googled thoroughly, but nothing seems to work.

Thanks for every idea.

---

### Post by BkkBonanza on 2011-04-01
The obvious step is to clear iptables and try the web server.

iptables -F

Those rules are nonsense anyway. A source port of 80 makes no sense. And having a rule that matches ESTABLISHED by itself also isn't useful at all. You can make them less confusing by leaving out wide open defaults such as 0/0 as they aren't needed.

Just this will suffice, assuming the default is DROP,
```

iptables -A INPUT -p tcp -d $MY_SERVER_IP --dport 80 -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

```

---

