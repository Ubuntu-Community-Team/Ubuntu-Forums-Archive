---
title: "saslauthd not starting"
date: 2007-07-06
forum: Server Platforms
---

### Post by nibbo on 2007-07-06
I have a postfix mailsystem running on my ubuntu edgy server. But I have some problems with smtp authentication with tls... My mail.log says the following:
```
Jul  6 13:39:31 hades postfix/smtpd[6579]: connect from unknown[192.168.1.1]
Jul  6 13:39:31 hades postfix/smtpd[6579]: setting up TLS connection from unknown[192.168.1.1]
Jul  6 13:39:31 hades postfix/smtpd[6579]: TLS connection established from unknown[192.168.1.1]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Jul  6 13:39:33 hades postfix/smtpd[6579]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Jul  6 13:39:33 hades postfix/smtpd[6579]: warning: SASL authentication failure: Password verification failed
Jul  6 13:39:33 hades postfix/smtpd[6579]: warning: unknown[192.168.1.1]: SASL PLAIN authentication failed: generic failure
Jul  6 13:39:33 hades postfix/smtpd[6579]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Jul  6 13:39:33 hades postfix/smtpd[6579]: warning: unknown[192.168.1.1]: SASL LOGIN authentication failed: generic failure
Jul  6 13:39:37 hades postfix/smtpd[6579]: lost connection after AUTH from unknown[192.168.1.1]
Jul  6 13:39:37 hades postfix/smtpd[6579]: disconnect from unknown[192.168.1.1]
Jul  6 13:42:57 hades postfix/anvil[6581]: statistics: max connection rate 1/60s for (smtp:192.168.1.1) at Jul  6 13:39:30
Jul  6 13:42:57 hades postfix/anvil[6581]: statistics: max connection count 1 for (smtp:192.168.1.1) at Jul  6 13:39:30
Jul  6 13:42:57 hades postfix/anvil[6581]: statistics: max cache size 1 at Jul  6 13:39:30

```

While messing around I noticed that saslauthd isn't started. When starting it with 
```
sudo /etc/init.d/saslauthd start
```
just says "Starting SASL Authentication Daemon:"
But when trying to stop it i get: ```
nibbo@hades:~$ sudo /etc/init.d/saslauthd stop
Stopping SASL Authentication Daemon: (not running).

```

So it looks like the saslauthd isnt running :(
Any suggestions on how to solve this?

---

### Post by turinglabs on 2007-07-06
Take a look in /var/log/daemon.log, or run the command as 'sudo sh -x /etc/init.d/saslauthd start' to get a shell trace. Also look in /etc/default/ to see if there is a config file for saslauthd that might have a missing option.

---

### Post by Psylocybe on 2008-05-18
I had this error after upgrading from Edgy to Feisty.

Turned out that in /etc/default/saslauthd the line
```
PARAMS="-m ${PWDIR}"
```

Needed to be changed to: 
```
OPTIONS="-m ${PWDIR}"
```

Then restart saslauthd and it worked like a charm again.

---

