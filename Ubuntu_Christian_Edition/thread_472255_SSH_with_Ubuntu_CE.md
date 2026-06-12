---
title: "SSH with Ubuntu CE"
date: 2007-06-12
forum: Ubuntu Christian Edition
---

### Post by Hamm on 2007-06-12
Is Ubuntu CE running a firewall that would block SSH? I sudo and install ssh using apt-get and it is running, but when I try to shell in it is timed out. I also tried to ping it also. If a firewall is up? How do I punch a hole in it for SSH tunnel?

---

### Post by Hamm on 2007-07-24
Bump::::

---

### Post by mysticrider92 on 2007-07-25
Ubuntu CE uses the FireHOL firewall by default.

You need to edit the file /etc/firehol/firehol.conf (sudo gedit /etc/firehol/firehol.conf in a terminal) and add the line "server ssh accept" (without the quotes) under server cups accept. Now restart firehol with "sudo firehol stop" then "sudo firehol start".

---

### Post by Hamm on 2007-09-03
That worked perfectly. Thanks you for the information.

---

### Post by robertmf on 2009-04-15
> **mysticrider92 said:**
> Ubuntu CE uses the FireHOL firewall by default.

You need to edit the file /etc/firehol/firehol.conf (sudo gedit /etc/firehol/firehol.conf in a terminal) and add the line "server ssh accept" (without the quotes) under server cups accept. Now restart firehol with "sudo firehol stop" then "sudo firehol start".
[COLOR="DarkRed"]Also, Thanks![/COLOR]

---

