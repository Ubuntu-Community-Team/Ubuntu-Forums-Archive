---
title: "Iptables log every connection"
date: 2009-05-13
forum: Security
---

### Post by pjani on 2009-05-13
Is there any posible way to log connections i mean time, src address, src port, destination address, destination port with ip tables?

Thankyou.

---

### Post by lovinglinux on 2009-05-13
Here is an example to log inbound tcp connections:

```
iptables -A INPUT -p tcp -j LOG --log-prefix ' INPUT TCP ' --log-level 4
```

You should put it in the top of the chain to log all incoming tcp traffic.

---

### Post by lovinglinux on 2009-05-13
BTW, I think the easiest way to log all the stuff is to create a new chain:

```
iptables -N INBOUND
```

Then instead of using ACCEPT, redirect all traffic that should be accepted to the INBOUND chain. For example:

```
iptables -A INPUT -i eth0 -p tcp -m state --state ESTABLISHED,RELATED -j INBOUND
```

Then log and accept every connection on the INBOUND chain:

```
iptables -A INBOUND -p tcp -j LOG --log-prefix ' INBOUND TCP ' --log-level 4
iptables -A INBOUND -p tcp -j ACCEPT
```

---

### Post by The Cog on 2009-05-13
I guess you only want to log the initial connection rather than every packet. So I would suggest accepting packets on established connections without logging. Something like this:
```
# Create a chain that logs new connections:
iptables -N LOGNEW
iptables -A LOGNEW -j LOG --log-prefix ' INBOUND TCP ' --log-level 4
iptables -A LOGNEW -j ACCEPT
# Accept packets on existing connections without any fuss:
iptables -A INPUT -p tcp -m state --state ESTABLISHED,RELATED -j ACCEPT
# Log incoming packets on new conections:
iptables -A INPUT -p tcp -j LOGNEW

```

---

### Post by uljanow on 2009-05-13
```
iptables -I INPUT -m state --state NEW -j LOG --log-prefix "New Connection: "
iptables -I OUTPUT -m state --state NEW -j LOG --log-prefix "New Connection: "
```;)

---

### Post by lensman3 on 2009-05-14
I don't think NEW works for UDP packets.  I think all packets will be logged in the UDP case.  UDP are stateless.  I checked my iptables script and it has UDP packets with a NEW flag.  I'm not sure if the ESTABLISHED path even works for UDP.  All UDP packets may go through the NEW path.

ICMP packets are generally stateless too.

---

### Post by uljanow on 2009-05-14
> **lensman3 said:**
> I don't think NEW works for UDP packets.

Wrong. The state module uses a logical connection layer/abstraction.


```
[ 2134.566659] New Connection: IN= OUT=wlan0 SRC=192.168.178.229 DST=192.168.178.21 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=65094 DF PROTO=UDP SPT=55717 DPT=53 LEN=40 
```

---

### Post by sokol99 on 2010-01-26
uljanow: you da man! :)

---

### Post by spezticle on 2010-06-16
> **uljanow said:**
> ```
iptables -I INPUT -m state --state NEW -j LOG --log-prefix "New Connection: "
iptables -I OUTPUT -m state --state NEW -j LOG --log-prefix "New Connection: "
```;)

where do these logs go? i tried the command but can't find the log

---

### Post by spezticle on 2010-06-16
> **spezticle said:**
> where do these logs go? i tried the command but can't find the log

nevermind i figured out where the log is... uh.. now how do i turn it off my log is going to eat my hdd up in a matter of hours.

edit:
i'll figure it out later, i just shutdown the pc for now. i'm going to bed deal with it in the morning.

---

