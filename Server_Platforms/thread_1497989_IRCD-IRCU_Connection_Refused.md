---
title: "IRCD-IRCU Connection Refused"
date: 2010-05-31
forum: Server Platforms
---

### Post by cusinndzl on 2010-05-31
I have an Ubuntu server and I recently upgraded to 10.04. Before I upgraded I used IRCD-IRC2 and that worked fine as long as I did not have it startup automatically with the machine. Once I upgraded to 10.04 IRCD-IRC2 stopped working so I switched to IRCD-IRCU. I installed IRCD-IRCU and got it all working, then I rebooted and it stopped working. I'm trying to connect with X-Chat and I get Connection Failed. Error: Connection Refused. I've tried to connect with other things like Mibbit and even IRSSI on the server. 

I really need some help on this, I'm installing the programs from apt-get as root. Can anyone help me? I can provide additional information if needed.

---

### Post by cusinndzl on 2010-06-01
I switched to InspIRCD and I like that better, but I would still like more information on what happened.

---

### Post by tors on 2010-09-21
```

root@host# mkdir /var/run/ircd
root@host# chown irc:irc /var/run/ircd
root@host# /etc/init.d/ircd-ircu restart

```

---

### Post by DiSTORT3D on 2011-02-03
Nice :D

---

