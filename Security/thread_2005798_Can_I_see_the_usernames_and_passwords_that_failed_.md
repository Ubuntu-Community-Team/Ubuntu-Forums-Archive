---
title: "Can I see the usernames and passwords that failed to login on my PC?"
date: 2012-06-18
forum: Security
---

### Post by Rytron on 2012-06-18
Hi.

Example scenario. At my login screen it does not show the possible username(s) to pick from. If someone tried to login as **Zac** with the password **Tulip** -- could I find that out? Or at least the failed login usernames anyway?

---

### Post by zombifier25 on 2012-06-18
I don't know if it shows passwords of failed logins (haven't tried it), but /var/log/lightdm/lightdm.log logs everything related to logins. You need to be root to view it though.

---

### Post by Rytron on 2012-06-18
> **zombifier25 said:**
> I don't know if it shows passwords of failed logins (haven't tried it), but /var/log/lightdm/lightdm.log logs everything related to logins. You need to be root to view it though.

That file is blank.

---

### Post by zombifier25 on 2012-06-18
Are you using LightDM?

---

### Post by Rytron on 2012-06-18
> **zombifier25 said:**
> Are you using LightDM?

I apologise. You were correct. I tried that command from LM MATE on my desktop. It works fine on my laptop (Xubuntu).

```
sudo leafpad /var/log/lightdm/lightdm.log
```

How would I do the same in MATE? Probably somewhere like /var/log/mdm but am not certain.

---

### Post by Cheesemill on 2012-06-18
How about /var/log/auth.log ?

---

### Post by bokopperud on 2012-06-18
You could try the command 'lastb'.  You probably must be root on ubuntu, because of the access-rights of the /var/log/btmp.  (However I see my system is not logging to this as it should.)

Another file you can look at is /var/log/auth.log .  Agian you must be root, and you may have to activate it by uncommenting the lines in /etc/rsyslog or /etc/rsyslog.d/50-default.conf, and touching /var/log/auth.log .  Just look at the auth-log file with less or use grep.

Both will show you which users have tried to log-in with invalid passwords and if unknown users have tried to log-in.  You should also see when and from where.  Neither let you see the actual password used though.

---

### Post by Rytron on 2012-06-18
> **Cheesemill said:**
> How about /var/log/auth.log ?

Works fine in Xubuntu 12.04.

---

### Post by Rytron on 2012-06-18
> **bokopperud said:**
> You could try the command 'lastb'.  You probably must be root on ubuntu, because of the access-rights of the /var/log/btmp.  (However I see my system is not logging to this as it should.)

Another file you can look at is /var/log/auth.log .  Agian you must be root, and you may have to activate it by uncommenting the lines in /etc/rsyslog or /etc/rsyslog.d/50-default.conf, and touching /var/log/auth.log .  Just look at the auth-log file with less or use grep.

Both will show you which users have tried to log-in with invalid passwords and if unknown users have tried to log-in.  You should also see when and from where.  Neither let you see the actual password used though.

What lines do I uncomment?

---

### Post by Cheesemill on 2012-06-18
> **Rytron said:**
> What lines do I uncomment?

If /var/log/auth.log already has entries in it then you don't need to uncomment anything, it's already working.

---

### Post by Rytron on 2012-06-18
> **Cheesemill said:**
> If /var/log/auth.log already has entries in it then you don't need to uncomment anything, it's already working.

Thanks for clarifying that.

Kudos also to bokopperud for suggesting this.
```
sudo lastb
```

---

