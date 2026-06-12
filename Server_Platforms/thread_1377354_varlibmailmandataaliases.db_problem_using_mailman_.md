---
title: "/var/lib/mailman/data/aliases.db problem using mailman and postfix"
date: 2010-01-10
forum: Server Platforms
---

### Post by bloodqc on 2010-01-10
I carefully followed the instruction at [https://help.ubuntu.com/community/Mailman](https://help.ubuntu.com/community/Mailman) to setup mailman with postfix but I got this in my mail.log and postfix don't output anything on the port 25 after the connection is established :

```
Jan 10 07:30:05 obiwan postfix/smtpd[24700]: fatal: open database /var/lib/mailman/data/aliases.db: No such file or directory
```

I tried playing with check_perms, genaliases from /usr/lib/mailman/bin but without luck.

Anyone know if I'm missing something?

thanks

---

