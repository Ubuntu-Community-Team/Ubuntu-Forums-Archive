---
title: "Hi have made a mistake in Maverick synaptic"
date: 2011-06-06
forum: Security
---

### Post by Mat11 on 2011-06-06
Hi think i tampered with my network security without knowing the default's first !
What is the default defacto for Maverick with preinstalled packages in synaptic regarding Telnet-ssl or Telnetd-ssl .?  I know i shouldn't have touched !

Does anyone know? 

Matt11

---

### Post by doas777 on 2011-06-07
telnet of any flavor is not installed by default. I'd just remove it if present, unless you have need for telnet (and then I have to ask why). 
telnet is pretty much a dead protocol. almost anything that uses it, either supports ssh, or is so old that hyperterm/minicom is actually better.

---

### Post by Mat11 on 2011-06-07
> **doas777 said:**
> telnet of any flavor is not installed by default. I'd just remove it if present, unless you have need for telnet (and then I have to ask why). 
telnet is pretty much a dead protocol. almost anything that uses it, either supports ssh, or is so old that hyperterm/minicom is actually better.

Thanks Doas you are right.Have deleted the telnet-ssl package installed in error, also noticed an internet speed issue for the few minutes the package was used.

Many thanks for your advice.

Matt

---

