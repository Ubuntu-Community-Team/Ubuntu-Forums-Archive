---
title: "iptables rule and rc.local"
date: 2005-11-23
forum: Server Platforms
---

### Post by mirza.k on 2005-11-23
/sbin/iptables --flush
/sbin/iptables --table nat --flush
/sbin/iptables --delete-chain
/sbin/iptables --table nat --delete-chain

/sbin/iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
/sbin/iptables --append FORWARD --in-interface  eth0 -j ACCEPT
echo 1 > /proc/sys/net/ipv4/ip_forward

is that correct ?
info :
eth0 = public IP
eth1 = LAN GAteway

i want to set it up for default gateway only
----------
and where is the rc.local ?
so i can put it there
i cant find the rc.local :((

---

### Post by LordHunter317 on 2005-11-23
Those rules look fine to me, though I don't think you need either iptables --delete-chain rule.

And there is no rc.local, you need to create your own init script.

---

### Post by mirza.k on 2005-11-24
[QUOTE=LordHunter317]Those rules look fine to me, though I don't think you need either iptables --delete-chain rule.

And there is no rc.local, you need to create your own init script.[/QUOTE]

allrite i find thread @ this forum that talk about rc.local

but i currious why i no need iptables --delete-chain ?
can u give me the complete and simple iptables rule ?

---

### Post by LordHunter317 on 2005-11-24
Your rules are fine otherwise.  ASsuming this is only running at startup, even iptables -F isn't necessary, the ruleset will be empty.  Anyway, --delete-chain is only necessary if you ever add chains, and you don't.

---

### Post by mirza.k on 2005-11-24
thx for your help guys

this topic solved
or maybe anyone have idea to make iptables look great ?
i mean simple with all needed command
only for gateway server

---

