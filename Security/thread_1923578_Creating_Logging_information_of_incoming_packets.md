---
title: "Creating Logging information of incoming packets"
date: 2012-02-10
forum: Security
---

### Post by Thesis on 2012-02-10
Hi all,

how can i log the information about the incoming packets to the netfilter.

i am using the mangle table like this

[B][FONT=Times New Roman]sudo iptables –t mangle –A PREROUTING -p tcp -j NFQUEUE --queue-num 0  

[/FONT][/B][COLOR=#222222][FONT=monospace][FONT=Times New Roman]and i would[/FONT][/FONT][/COLOR][COLOR=#222222][FONT=monospace][FONT=Times New Roman]like to know how can i look whether all the packets are entering to it or not...

any ideas???
[/FONT][/FONT][/COLOR]

---

### Post by unspawn on 2012-02-11
Two ways. You don't need a rule for it if you just watch the chains packet counters: list rules with 'iptables -t raw -nvxL PREROUTING' then sort by packet count or packet number. If you want a rule then add a "-j LOG" one before the one you listed with the options you need (see 'iptables -j LOG --help' or'man iptables').

---

