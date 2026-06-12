---
title: "SASL problems when Postfix starts before Dovecot during boot"
date: 2011-10-16
forum: Server Platforms
---

### Post by XMLove on 2011-10-16
I get the following error on every boot: “fatal: no SASL authentication mechanisms”

Calling “/etc/init.d/postfix restart” resolves the problem.

It seems to be caused by the fact that Dovecot is the local mail delivery (LDA) and SASL authentication provider for Postfix. And the **Dovecot process is started after Postfix** in Ubuntu Server 11.10. This was not a problem with 11.04.

Dovecot is a upstart script, and Postfix uses an init script. I have no idea how to delay Postfix until Dovecot is ready in this scenario. Any suggestions?

---

### Post by XMLove on 2011-10-24
*bump*

---

### Post by neuralnet on 2011-11-06
Exactly the same problem here..

---

### Post by XMLove on 2011-11-06
Currently, I just restart the postfix service manually after reboot.

Would appreciate a suggestion for how to fix it. I don’t know enough about how upstart and the old system works to find a fix.

---

