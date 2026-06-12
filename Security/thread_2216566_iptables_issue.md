---
title: "iptables issue"
date: 2014-04-12
forum: Security
---

### Post by matias6 on 2014-04-12
Hi everyone, i got a ubuntu server distro and  iptables. 
i have eth0 and eth1 
eth0:172.16.221.122
eth1: 192.168.222.254

laptop1= 172.16.221.120
laptop2= 192.168.222.249

I have configured the iptables in this way = 

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

and a rule like this: 

iptables -A FORWARD -s 192.168.222.249 -p tcp --dport 3389 -j ACCEPT 

the 3389 is for RDP cnn, but does not work. 

whem I go to connect from laptop2(222.249) to laptop1(221.120)my question is why iptables drop me if I already created a rule/exception for the 249 ip ?

thanks

---

### Post by SeijiSensei on 2014-04-12
You need to enable packet forwarding in /etc/sysctl.conf.  Uncomment the net.ipv4.ip_forward=1 line.

---

### Post by matias6 on 2014-04-12
Hi SeijiSensei that line was uncomment before I asked the question and doesn't work...

---

### Post by SeijiSensei on 2014-04-12
Let's see the results of running "route -n" on both machines.  Wrap the output in [noparse]```

```[/noparse] tags to make it legible. 

Also flush all the iptables rules and make sure you can connect without them.
```

/sbin/iptables -F INPUT
/sbin/iptables -F FORWARD
/sbin/iptables -F OUTPUT

```

---

### Post by matias6 on 2014-04-12
[COLOR=#000000]Ago[/COLOR]
[COLOR=#000000]SeijiSensei: 

with or without FLUSH the rules: 

```
iptables -P FORWARD DROP
``` 

not work.

```
iptables -P FORWARD ACCEPT[/COLOR]
```

then it works. 

but that I knew that. My problem is: open (ip/port) with a FORWARD rule when the FORWARD POLICY is set to DROP... 

(PS: the laptops have Windows 7 with windows firewall off).

---

### Post by HermanAB on 2014-04-13
Well, there is nothing left to FORWARD after you dropped everything at the INPUT.

First get the thing to work with all the rules flushed, then read the iptables man page about ten times (I'm serious!), then try to set a few rules.

---

### Post by The Cog on 2014-04-13
You probably also need a rule to allow the replies from laptop2 to go back to laptop1. TCP requires two-way traffic.
The easiest way to do this is probably:
```
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
```
The above rule will automatically allow traffic on connections that have previously been allowed by other rules (e.g. the laptop1-laptop2 connection request).

---

### Post by matias6 on 2014-04-13
my friend already set INPUT DROP and OUTPUT-FORWARD ACCEPT and the RCP cnn is working OKEY, so... you too read the man page!

---

### Post by matias6 on 2014-04-13
THE COG! yes, it work! with the default policy in DROP.. thanks

---

