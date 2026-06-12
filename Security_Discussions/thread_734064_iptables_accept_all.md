---
title: "iptables accept all"
date: 2008-03-24
forum: Security Discussions
---

### Post by prezbedard on 2008-03-24
I am currently running ipconfig and dansguardian.

I've been running this combo since last summer.

I have had some luck with the current setup.I have been adding rules here and there when different network issues arise caused by iptables not letting something through. I was thinking that I can improve things if I change the config on iptables to something like this.

I place the one rule I need which is to forward all port 80 traffic to port 8080 where dansguardian is listening. I then accept all other traffic.
However I am not sure how to set it to accept all other traffic. 

Could someone please point me in the correct direction?

Thanks,

---

### Post by Sam Lars on 2008-03-24
I think that it should accept all traffic by default...
You could always add a chain that says ACCEPT instead of DROP.

---

### Post by Holy Cheater on 2008-03-24
```

iptables -P INPUT ACCEPT

```
This should make netfilter accept all incoming connections (except for what are denied by rules).

---

### Post by prezbedard on 2008-03-24
I'm not sure it does accept by default cause I would think I wouldn't have so many issues. For example when I've set this box's ip as the default gateway I can't use outlook, it causes gmail to not work and other annoying issues with outgoing traffic. I mean dansguardian works but non web traffic and some web traffic is adversely affected. So all I want to do is accept all and redirect port 80 to 8080 which is one thing I got working.

Thanks Sam I'll give that a try.

---

### Post by update_manager on 2008-03-24
[deleted double post]

---

### Post by update_manager on 2008-03-24
> **prezbedard said:**
> I'm not sure it does accept by default cause I would think I wouldn't have so many issues. For example when I've set this box's ip as the default gateway I can't use outlook, it causes gmail to not work and other annoying issues with outgoing traffic. I mean dansguardian works but non web traffic and some web traffic is adversely affected. So all I want to do is accept all and redirect port 80 to 8080 which is one thing I got working.


I'd say this is close what you want. Replace $LAN and $WAN to eth-whatever

iptables -F
iptables -F INPUT
iptables -F OUTPUT

iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

echo 1 > /proc/sys/net/ipv4/ip_forward

iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -i $LAN -j ACCEPT

iptables -t nat -A PREROUTING -i $LAN -p tcp --dport 80 -j REDIRECT --to-port 8080

iptables -N Firewall
iptables -A Firewall -m limit --limit 10/second -j LOG --log-prefix "Firewall: "
iptables -A Firewall -j DROP

iptables -A FORWARD -i $WAN -m state --state NEW,INVALID -j Firewall
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -j Firewall


This rule is the easiest to mess up - note the "-i $WAN"
iptables -A FORWARD -i $WAN -m state --state NEW,INVALID -j Firewall

---

### Post by The Cog on 2008-03-25
I thonk that REDIRECT argument should be pleural **--to-ports** rather than **--to-port** (reading the man page - learning all the time).

---

### Post by prezbedard on 2008-06-16
ok I finally had the opportunity to try and implement this. However when I ran the command sudo iptables-restore < "text file containing new rules"

I got an error. It said ```
iptables-restore: line 1 fail
```

---

### Post by prezbedard on 2008-06-16
I attempted to perform the changes line by line instead of with one file.

I got to about line 4 or 5 and it killed my ssh connection and I can't ssh back in.

I am now trying to get back on the box locally for unrelated reason my keyboard delay is extremely slow.

I had to reboot the system. I restored the previous rules until I can get a better grasp on this. Is there a rule I can put in while entering these new ones so I can do i via ssh without getting ssh killed permanently like what just happened?


Thanks!

---

