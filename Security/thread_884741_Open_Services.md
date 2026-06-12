---
title: "Open Services"
date: 2008-08-09
forum: Security
---

### Post by Drezard on 2008-08-09
Hello,

Did a quick nmap scan on my server, it has:

port 21, 22 and 80 open (all were opened by me)

but! it has port 23, 53 and 1723 (pptp) filtered... (none of which opened by me. 

any ideas?

Drez

---

### Post by brian_p on 2008-08-09
> **Drezard said:**
> 

any ideas?



Where was nmap run from? What was the command? What was the output?

---

### Post by cariboo on 2008-08-10
It looks like you got a telnet and dns servers running, plus vpn.

Jim

---

