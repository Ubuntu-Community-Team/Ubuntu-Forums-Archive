---
title: "Krb5 + ssh"
date: 2010-03-07
forum: Server Platforms
---

### Post by mnelsonwhite on 2010-03-07
Hi.

I am banging my head against the wall trying to get ssh to authenticate with kerberos.

samba works with winbind just fine.
When I try;

[INDENT][COLOR="DarkGreen"]ssh mnelsonwhite@localhost
mnelsonwhite@localhost's password:
Last login: Mon Mar  8 11:32:19 2010 from localhost
Connection to localhost closed.[/COLOR][/INDENT]

/etc/pam.d/sshd is empty. Is this required for sshd auth? If so, what should it look like?

---

### Post by mnelsonwhite on 2010-03-07
Syslogs are showing no errors T___T

---

