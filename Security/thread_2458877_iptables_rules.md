---
title: "iptables rules"
date: 2021-03-05
forum: Security
---

### Post by dave219 on 2021-03-05
hello team:

i need help to check my rules for iptables (converted from ipfw). what i intend to do is to specify specific rules first (drop or accept) then drop (and log) anything else:

sudo iptables -A INPUT -i lo -j ACCEPT


sudo iptables -A INPUT -d 127.0.0.0/8 -j DROP


sudo iptables -A INPUT -s 127.0.0.0/8 -j DROP


sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT


sudo iptables -A INPUT -i em0 -p tcp -m state --state NEW --source 192.168.1.0/24 --dport 22 -j ACCEPT


sudo iptables -A INPUT -i em0 -p tcp -m state --state NEW --source 100.100.100.0/24 --dport 22 -j ACCEPT


sudo iptables -A INPUT -i em0 -p icmp -m state --state NEW --source 192.168.1.0/24 -j ACCEPT

sudo iptables -P INPUT DROP


sudo iptables -P FORWARD DROP

thanks

_dave

---

### Post by SeijiSensei on 2021-03-05
I don't understand the first three rules. You permit traffic to the lo interface, then block addresses in 127/8.  I doubt the second and third rules are ever reached.

You don't have a logging rule. Usually I have

```
iptables -A INPUT -j LOG
```

at the bottom of my ruleset to log unmatched packets.

---

### Post by dave219 on 2021-03-05
> **SeijiSensei said:**
> I don't understand the first three rules. You permit traffic to the lo interface, then block addresses in 127/8.  I doubt the second and third rules are ever reached.

You don't have a logging rule. Usually I have

```
iptables -A INPUT -j LOG
```

at the bottom of my ruleset to log unmatched packets.

thanks.

those rule sets are to drop packets from and to 128.0.0.0/8. i borrowed them from ipfw rules. 

btw, what is the default action for "iptables -A INPUT -j LOG"? just log packets? so shall i put "iptables -P INPUT DROP" after the line "iptables -A INPUT -j LOG"?

---

### Post by SeijiSensei on 2021-03-06
Put the logging rule ahead of a reject one like this:
```

iptables -A INPUT -j LOG
iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited

```
and put them both at the bottom of the INPUT chain.

Or you can use DROP rather than REJECT to drop the packets on the floor. REJECT informs the source of the packets that they are being ignored.

Do you already have these rules implemented somewhere? If so, run 
```
sudo iptables -L -nv
```
and see how many packets have hit the rules for 127.0.0.0/8.  I bet the number is zero.  There's literally no reason to block any traffic to the localhost interface, and doing so can interfere with the operation of some programs. For instance, Ubuntu since 18.04 with systemd-resolved accepts DNS queries at the address 127.0.0.53.  You don't want to block that.

---

