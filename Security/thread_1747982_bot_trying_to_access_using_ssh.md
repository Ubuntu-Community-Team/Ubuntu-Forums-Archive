---
title: "bot trying to access using ssh?"
date: 2011-05-03
forum: Security
---

### Post by ftornell on 2011-05-03
Hi,
Just installed a brand new Ubuntu Server 11.04 with openSSH and Samba.

Edited the open-sshd configurationfile and disabled rootlogins.

Now I'm seeing this in the auth.log and I just want to make sure that this might be normal:
```

May  3 11:09:01 ubuntu CRON[5205]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 11:09:01 ubuntu CRON[5205]: pam_unix(cron:session): session closed for user root
May  3 11:17:01 ubuntu CRON[5213]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 11:17:01 ubuntu CRON[5213]: pam_unix(cron:session): session closed for user root
May  3 11:39:01 ubuntu CRON[5218]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 11:39:01 ubuntu CRON[5218]: pam_unix(cron:session): session closed for user root

```

Is this someone trying to login using root account (bruteforce) and this is simply a log for that?

why is it stating CRON? (root account is disabled in ubuntu right?)

what is pam_unix?

Thx!

---

### Post by spynappels on 2011-05-03
CRON is the internal scheduling engine which executes certain commands at certain times and dates. It has to run some of these commands as root, similar to you running a command as sudo.

This log is fine, you need to look more at unsuccessful authentication attempts to look for brute force attacks by script kiddies and bots.

---

### Post by matt_symes on 2011-05-03
Hi

> **ftornell said:**
> Hi,
Just installed a brand new Ubuntu Server 11.04 with openSSH and Samba.

Edited the open-sshd configurationfile and disabled rootlogins.

Now I'm seeing this in the auth.log and I just want to make sure that this might be normal:
```

May  3 11:09:01 ubuntu CRON[5205]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 11:09:01 ubuntu CRON[5205]: pam_unix(cron:session): session closed for user root
May  3 11:17:01 ubuntu CRON[5213]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 11:17:01 ubuntu CRON[5213]: pam_unix(cron:session): session closed for user root
May  3 11:39:01 ubuntu CRON[5218]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 11:39:01 ubuntu CRON[5218]: pam_unix(cron:session): session closed for user root

```Is this someone trying to login using root account (bruteforce) and this is simply a log for that?

That looks fine to me. Just Cron doing its thing.

> why is it stating CRON? Cron is started to run services, scripts, commands at predefined times. To see what cron is doing..

```
grep -i "cron" /var/log/syslog
```> (root account is disabled in ubuntu right?)Yes

> 
what is pam_unix?
from man pam_unix

> This is the standard Unix authentication module. It uses standard calls
       from the system's libraries to retrieve and set account information as
       well as authentication. Usually this is obtained from the /etc/passwd
       and the /etc/shadow file as well if shadow is enabled.For ssh, use keys. Change the default port is you want. It will reduce the number of hits in the auth.log file. You can also configure iptables to allow a number of connection attempts in a time period.

Kind regards

---

### Post by The Cog on 2011-05-04
cron runs as root because it has to launch different process as different users, and only root has the right to run processes as other users. The cron configuration says what commands to run, when, and who as.

The root account is disabled in the sense that the password is disabled. This means that you cannot log in as root, but the account itself is very much alive with lots of processes running, as the command "ps -ef" will show.

---

### Post by matt_symes on 2011-05-04
Hi

@TheCog. That is excellent clarification :)

Kind regards

---

