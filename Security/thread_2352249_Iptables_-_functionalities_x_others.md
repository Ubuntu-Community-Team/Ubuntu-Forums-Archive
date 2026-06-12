---
title: "Iptables - functionalities x others"
date: 2017-02-10
forum: Security
---

### Post by mieciow on 2017-02-10
Hello people


I'm starting iptables studies and full of doubts:
- Does he only make the rules and block by ip or does it by mac adress?
- can it, for example, limit speed to some terminal?
- Can I make rules for those who connect through the wifi router?
- Can I make rules by time?


Should I continue my studies in him or do you suggest me any other?


Thank you

---

### Post by SeijiSensei on 2017-02-11
> **mieciow said:**
> - Does he only make the rules and block by ip or does it by mac adress?
Don't know about MAC addresses, but you can write rules that apply to interfaces like eth0.
```
/sbin/iptables -A INPUT -i eth0 -j REJECT
```
would block all the incoming traffic on the eth0 interface.

> can it, for example, limit speed to some terminal?
I think so, but I've never had any need to do so.

> Can I make rules for those who connect through the wifi router?
Of course.  You can write rules that apply to interfaces, individual IPs, or entire subnets like this:
```
/sbin/iptables -A INPUT -p tcp -s 192.168.1.0/24 --dport 80 -j ACCEPT
```
That allows traffic to the machine's HTTP port from any address starting with 192.168.1.

> Can I make rules by time?
You mean different rules at different times of day?  Again I think so but again, I've never had any need for that.  You could also use cron for this, writing scripts with different rulesets that would run at different times of day.

> Should I continue my studies in him or do you suggest me any other?
You mean some other firewalling tool other than iptables?  No, that is the method that is built into the Linux kernel.  There are command shells like ufw that might be easier for novice users, but I've always written iptables rules from scratch.

---

