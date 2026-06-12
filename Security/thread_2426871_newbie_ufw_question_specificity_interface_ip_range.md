---
title: "newbie ufw question: specificity interface ip ranges and port/proto"
date: 2019-09-14
forum: Security
---

### Post by dave219 on 2019-09-14
hello guys:

i have a system with multiple interfaces and tried to set up a rule that specifies interface, ip range, port/proto.

user@home:~$ sudo ufw allow in on eth1 to 192.168.0.10 from 192.168.0.0/24 to any port 22 proto tcp
ERROR: Improper rule syntax

checked manual for ufw but still not able to figure out

_dave

---

### Post by dave219 on 2019-09-14
never mind. i used this command and it worked:

sudo ufw allow in on eth1 from 192.168.0.0/24 to any port 22 proto tcp

---

### Post by uRock on 2019-09-14
Cool that you figured it out. If your install has a desktop, the GUFW offers a GUI interface for setting up rules.

---

