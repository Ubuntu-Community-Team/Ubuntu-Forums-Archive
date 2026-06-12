---
title: "iptables countbytes"
date: 2010-09-16
forum: Security
---

### Post by yashar on 2010-09-16
why this rule not working:

-A FORWARD -i eth1 - countbytes --countbytes 100000: --countbytes-dir both --countbyte-mode bytes -j DROP

this is not working!! 100000 means 100 kB am i correct ? so i'm expecting all connections get closed after of 100k data transfer, but nothing happen!

---

### Post by BkkBonanza on 2010-09-16
Your syntax is incorrect. 

It's --connbytes not countbytes. 
You need both -- not -, no space between -- and connbytes. 
No colon after the 100000. Use the colon only if a limit value is needed.

Try,

-A FORWARD -i eth1 -m connbytes --connbytes 100000 --connbytes-dir both --connbytes-mode bytes -j DROP

Also, you likely need to set the net.netfilter.nf_conntrack_acct flag,

echo 1 > /proc/sys/net/netfilter/nf_conntrack_acct

so that connection accounting is turned on.

---

### Post by yashar on 2010-09-17
thanks, i'll use that  tomorrow.

---

### Post by yashar on 2010-09-18
it is not working, maybe because i used to accept forwarded connections before that?
the code is like below, but not working

-A FORWARD -i eth1 -o eth0 -j accept
-A FORWARD -i eth1 -m connbytes --connbytes 100000: --connbytes-dir both --connbytes-mode bytes -j DROP

 /proc/sys/net/netfilter/nf_conntrack_acct has a 1 value.

---

