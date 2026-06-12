---
title: "constant postfix warnings"
date: 2006-08-26
forum: Server Platforms
---

### Post by AndersAA on 2006-08-26
```
Aug 27 02:35:09 hollowtube postfix/qmgr[29608]: warning: connect to transport smtp-amavis: No such file or directory
```

The thing is, I dont use amavis, I use spamassassin through procmail, infact I dont have any direct link between amavis and postfix whatsoever.

grep -i 'amavis' /etc/* -R shows nothing.  So why on earth is postfix complaining about this?

---

### Post by chrisfay on 2006-08-26
Do you see something like this in your main.cf:

```
content_filter=smtp-amavis:[127.0.0.1]:10024
```


Or something like this in master.cf:

```
smtp-amavis unix -	-	n	-	4  smtp
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
    -o disable_dns_lookups=yes
    -o max_use=20
```

Your error means that somewhere in your config file you have added a directive that looks for amavis. I use amavis and get this exact error when trying to send mail if my amavis daemon hasn't been started.

---

### Post by AndersAA on 2006-08-27
that's the thing, I dont.  And when searching through every file in /etc, I dont have a trace of amavis there.

---

