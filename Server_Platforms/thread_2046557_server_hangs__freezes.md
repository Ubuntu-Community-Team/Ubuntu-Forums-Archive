---
title: "server hangs / freezes"
date: 2012-08-23
forum: Server Platforms
---

### Post by Invincibles on 2012-08-23
Hi,

We're using -
openldap-2.3.43-12.el5_6.5
nss_ldap-253-25.el5

on RHEL-5.5
HP G7 server with 24GB RAM.

Intermittently the entire system hangs, no message is present in any of the log files, login to the system fails, ssh fails, ping fails, the only way to recover is to hard-boot the system.

We consulted Red-hat for this and through kdump's vmcore analysis, they have identified that the problem lies somewhere in the authentication i.e. ldap.

Please help us to find out how we can troubleshoot this issue and move towards resolution.

This may not be the right forum to post, but if someone faced/knows this problem, please provide some suggestions to move forward.

Appreciate a quick response !!


Thanks and Regards,

---

### Post by nerdux on 2012-08-23
Feels like a hardware problem...

---

