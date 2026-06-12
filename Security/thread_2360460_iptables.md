---
title: "iptables"
date: 2017-05-05
forum: Security
---

### Post by scratcher on 2017-05-05
i use these rules , but i don't know how to accept this match after 1 minutes,...
these rules if match ,Denying for ever
i need Denying for 2 minutes 
how can i do that?
iptables -A INPUT -i ens33 -p tcp --tcp-flags SYN,ACK SYN -m state --dport 6050 --state NEW -m recent --set

iptable -A INPUT -i ens33 -p --tcp-flags SYN,ACK SYN -m state --dport 6050 --state NEW -m recent --update --seconds 20 --hitcount 3 -j Drop

---

### Post by deadflowr on 2017-05-05
*Moved to **Security***

---

### Post by Doug S on 2017-05-08
> **scratcher said:**
> i use these rules , but i don't know how to accept this match after 1 minutes,...
these rules if match ,Denying for ever
i need Denying for 2 minutes 
how can i do that?
iptables -A INPUT -i ens33 -p tcp --tcp-flags SYN,ACK SYN -m state --dport 6050 --state NEW -m recent --set

iptable -A INPUT -i ens33 -p --tcp-flags SYN,ACK SYN -m state --dport 6050 --state NEW -m recent --update --seconds 20 --hitcount 3 -j DropYour post is a little difficult to understand. I think there are two questions and a statement. The first question "How to ACCEPT after 1 minute?", I'm not sure what you mean.

The statement "If these rules match, then they deny forever", is not true. They deny for 20 seconds, however the timeout resets back to 20 seconds if any packet comes during that time.

The second question "the timeout needs to be 2 minutes. How to do it" Just change the 20 seconds to 120 seconds. Myself, I would reverse the order:
```
iptables -A INPUT -i ens33 -p --tcp-flags SYN,ACK SYN -m state --dport 6050 --state NEW -m recent --update --seconds 120 --hitcount 3 -j Drop
iptables -A INPUT -i ens33 -p tcp --tcp-flags SYN,ACK SYN -m state --dport 6050 --state NEW -m recent --set
```

---

