---
title: "Web Server + IPTables ?"
date: 2008-11-01
forum: Security
---

### Post by EMCGFX on 2008-11-01
Hi, can you guys help me out with this rules...
Ones I execute this rules in CentOS 5, it locks down.
I can't access SSH or WEB. Can any one tell me what is wrong with this rules ?

```
#!/bin/bash

iptables -F
iptables -X

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -I INPUT 1 -i lo -p all -j ACCEPT

iptables -A FORWARD -i venet0 -j ACCEPT
iptables -A FORWARD -o venet0 -j ACCEPT

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A OUTPUT -p udp --sport 22 -j ACCEPT

iptables -A INPUT -p tcp -m tcp --sport 80 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT

```

---

### Post by EMCGFX on 2008-11-01
I get this error > iptables: Unknown error 4294967295

---

### Post by lovinglinux on 2008-11-01
I'm not an expert, but your iptables commands looks fine to me.

Do you have any iptables manager like Firestarter or ufw installed and running?

It would help if could post the iptables using the following command, to see if there is any additional rules blocking your connection.

```
sudo iptables -L
```

---

### Post by EMCGFX on 2008-11-01
That what I thought, the rules is fine =) I knew it, but I was sleepy yesterday and wanted to make sure. But no one anwswered yesterday =) No I don't have anything else running, and rules in firewall was empty when I've applied this. I think its something to due with "modules" not been loading in the kernel properly. Cuz I get the following error...

iptables v1.3.5: unknown protocol `output' specified

Why CentOS 5.2 uses iptables v1.3.5, beats me.

---

### Post by cariboo on 2008-11-02
Not that it should make any difference, but are you running CentOS in a VM?

Jim

---

### Post by EMCGFX on 2008-12-31
Yes, I run CentOS in HyperVM, and yes it would make a diference if proper iptable modules is not loaded in HyperVM. Also, uses some other than eth0...

---

