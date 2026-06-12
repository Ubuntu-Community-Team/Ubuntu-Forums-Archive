---
title: "DDOS-ing Call of Duty 1 v1.1 Server"
date: 2012-02-19
forum: Security
---

### Post by harut55555 on 2012-02-19
Hello all, i am running an clan for call of duty 1 v1.1, this game has a vulnerability of ddos. attacker sends 'getinfo 'a'1023bytes' and server closes. here is some rules to fix it but i dont know why it isnt working. commands executes normally, no error. here is ddos program [http://aluigi.altervista.org/poc/](http://aluigi.altervista.org/poc/)*codboom*.[I]zip . I would like to know if i am missing somehting or not. thanks in advance.
[/I]

---

### Post by unspawn on 2012-02-19
> **harut55555 said:**
> Call of Duty 1 v1.1
Isn't that a way old version?..


> **harut55555 said:**
> I would like to know if i am missing somehting or not.
If you're certain it is codboom then the fix (COD v1.4) that was released ages ago, see [http://archives.neohapsis.com/archives/fulldisclosure/2004-09/0176.html](http://archives.neohapsis.com/archives/fulldisclosure/2004-09/0176.html)

---

### Post by harut55555 on 2012-02-20
I know, i jus want to keeo the version. here is solution with iptables but i dont know why it doesnt work, it executes normal with no error, but doesnt work, what can i do to make it work :D thx 




#!/bin/sh
iptables -N CODDDOS
iptables -A INPUT -p udp --dport 28960:28980 -j CODDDOS
iptables -A CODDDOS -m length --length 42 -m recent --set --name GETSTATUS
iptables -A CODDDOS -m string --algo bm --string "getstatus" -m recent --update --seconds 1 --hitcount 20 --name GETSTATUS -j DROP
iptables -A CODDDOS -p udp --sport 0:100 -j DROP
iptables -A CODDDOS -p udp --sport 27000:28000 -j DROP

---

