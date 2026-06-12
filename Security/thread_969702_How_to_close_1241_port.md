---
title: "How to close 1241 port?"
date: 2008-11-03
forum: Security
---

### Post by markomk on 2008-11-03
i scan my pc and i found a few open ports i close almost all, but 1241 port i can't :S
How can i close this port? 
tnx

---

### Post by cariboo on 2008-11-03
Are you running Nessus? If so then shut down nessus to close port 1241.

Jim

---

### Post by markomk on 2008-11-03
> **cariboo907 said:**
> Are you running Nessus? If so then shut down nessus to close port 1241.

Jim

i close nessus but 1241 port its open :S

---

### Post by randy78 on 2008-11-03
in a terminal, type:
sudo ufw deny 1241/tcp

To re-open it, type:
sudo ufw allow 1241/tcp

hope this helps

---

