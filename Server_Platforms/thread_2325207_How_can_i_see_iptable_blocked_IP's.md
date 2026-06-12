---
title: "How can i see iptable blocked IP's"
date: 2016-05-20
forum: Server Platforms
---

### Post by CrewDK on 2016-05-20
Hey. I got some rules in my iptables: 

```
$IPT -A INPUT -p tcp --dport 2525 -m state --state NEW -m recent --name BLOCK --set
$IPT -A INPUT -p tcp --dport 2525 -m state --state NEW -m recent --name BLOCK --update --seconds 60 --rttl --hitcount 3 -j DROP
$IPT -A INPUT -p tcp --syn --dport 2525 -j ACCEPT

```

All works fine. But is there any way i can see this blocked IP's?

---

### Post by The Cog on 2016-05-20
You need to create a new chain (often called LOG_DROP) that logs then drops the packets. 
See here: [http://stackoverflow.com/questions/21771684/iptables-log-and-drop-in-one-rule](http://stackoverflow.com/questions/21771684/iptables-log-and-drop-in-one-rule)
```

$IPT -N LOG_DROP
$IPT -A LOG_DROP -j LOG --log-prefix "INPUT:DROP:" --log-level 6
$IPT -A LOG_DROP -j DROP
$IPT -A INPUT -p tcp --dport 2525 -m state --state NEW -m recent --name BLOCK --set
$IPT -A INPUT -p tcp --dport 2525 -m state --state NEW -m recent --name BLOCK --update --seconds 60 --rttl --hitcount 3 -j LOG_DROP
$IPT -A INPUT -p tcp --syn --dport 2525 -j ACCEPT
```

It's not unusual to also rate limit the log messages. Google for  "iptables log drop".

---

### Post by CrewDK on 2016-05-20
Thank you for your answer.

---

### Post by Doug S on 2016-05-20
I used to use a generic "log-n-drop" type chain, as The Cog suggests. However, I wanted a unique log message per type of DROP, so I moved away from "log-n-drop" and just do it in-line. Example:
```
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT
```

---

