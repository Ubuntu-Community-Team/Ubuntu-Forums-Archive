---
title: "iptables allow via spesific NIC"
date: 2010-12-29
forum: Security
---

### Post by Yizi on 2010-12-29
eth1 has connection to the net via gateway ..
eth0 on the same machine has users on a intranet and needs access to the internet, i need to allow internet connection and prevent packets which logically originate from the internet getting into the intranet

would appreciate if anyone helps.

---

### Post by spynappels on 2010-12-29
You can specify which interface any rule in iptables works on by using the -i ethX flag in the rule.

---

