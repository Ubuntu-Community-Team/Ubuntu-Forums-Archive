---
title: "Iptables destination"
date: 2010-08-24
forum: Security
---

### Post by FuturePilot on 2010-08-24
Can someone explain what the "destination" field in iptables means? For example, what is the difference between these two rules?

These would be in INPUT
```
ACCEPT     tcp  --  192.168.1.0/24       192.168.1.4
```
```
ACCEPT     tcp  --  192.168.1.0/24       0.0.0.0/0
```

Is one better to use than the other? Since 0.0.0.0/0 means anywhere does that mean that someone could forward packets through to another computer?

---

### Post by stlsaint on 2010-08-24
Not sure what you are asking since you dont have any ACTIONS, (DROP REJECT) on any ports (TCP,UDP) or the accept ALL

something like:
```
iptables -option [Chain] [Rule] -j [Target]
```

See here for details: [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by FuturePilot on 2010-08-24
> **stlsaint said:**
> Not sure what you are asking since you dont have any ACTIONS, (DROP REJECT) on any ports (TCP,UDP) or the accept ALL

something like:
```
iptables -option [Chain] [Rule] -j [Target]
```

See here for details: [http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Huh? That's what I did to create those rules. I posted the output of iptables -L

---

### Post by TwoEars on 2010-08-24
Destination means which IP address the packet in question is going to, for example, a packet might go through your computer in order to access another, and in the example given, this is only allowed to 192.168.1.4

---

### Post by FuturePilot on 2010-08-24
> **TwoEars said:**
> Destination means which IP address the packet in question is going to, for example, a packet might go through your computer in order to access another, and in the example given, this is only allowed to 192.168.1.4

So if the destination is 0.0.0.0/0 can packets go through that computer to another without configuring anything else like adding something special in PREROUTING? 

I don't want anyone being able to rout traffic through another computer so I'd probable be better off using a specific destination IP?

---

### Post by TwoEars on 2010-08-24
Sorry, let me clarify. Destination can also mean locally. It allows you to define which port on which device the source connects to, for example, 192.168.1.4/80(if 192.168.1.4 was localhost) would be one to allow, though 192.168.1.3/22 would be one to block. To stop all forwarding to other devices, ```
iptables -P FORWARD DROP
``` will work.

If you want to restrict it to localhost only, on certain ports, then using -d 192.168.1.4 -dport portnumber would be a good idea.

---

