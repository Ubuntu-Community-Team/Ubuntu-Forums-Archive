---
title: "WordPress contact forms not working"
date: 2019-01-05
forum: Server Platforms
---

### Post by vix386 on 2019-01-05
Hi all! I have VPS as a web server. Installed and configured Apache, PHP, MySQL. Also installed WordPress (5 websites) and point domains. Everything works perfect except contact forms on website. Find some articles in google about Postfix. Installed and configured, but it is still not working. Changed port in /etc/postfix/master.cf - same problem. I'm not familiar with servers and I think I'm doing something wrong. Also I do not know which exactly information I have to look for related my problem.  I will be very thankful if someone directs me to the right path, and tells me exactly what I must do to make it work.

---

### Post by volkswagner on 2019-01-05
What do the logs say? Can you post output of logs?

---

### Post by vix386 on 2019-01-05
> **volkswagner said:**
> What do the logs say? Can you post output of logs?

```

Jan  5 14:54:33 localhost postfix/smtp[3606]: connect to alt4.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection timed out
Jan  5 14:54:33 localhost postfix/smtp[3606]: D282420B46: to=<h.humbatov@gmail.com>, relay=none, delay=29555, delays=29405/0.01/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection $
Jan  5 14:57:03 localhost postfix/qmgr[2033]: 3F67920C61: from=<root@localhost.localdomain>, size=405, nrcpt=1 (queue active)
Jan  5 14:57:03 localhost postfix/qmgr[2033]: 6B01620CBB: from=<root@localhost.localdomain>, size=405, nrcpt=1 (queue active)
Jan  5 14:57:33 localhost postfix/smtp[3611]: connect to gmail-smtp-in.l.google.com[74.125.201.27]:25: Connection timed out
Jan  5 14:57:34 localhost postfix/smtp[3610]: connect to gmail-smtp-in.l.google.com[74.125.201.27]:25: Connection timed out
Jan  5 14:58:04 localhost postfix/smtp[3611]: connect to alt1.gmail-smtp-in.l.google.com[173.194.208.27]:25: Connection timed out
Jan  5 14:58:04 localhost postfix/smtp[3610]: connect to alt1.gmail-smtp-in.l.google.com[173.194.208.27]:25: Connection timed out
Jan  5 14:58:34 localhost postfix/smtp[3611]: connect to alt2.gmail-smtp-in.l.google.com[172.217.204.27]:25: Connection timed out
Jan  5 14:58:34 localhost postfix/smtp[3610]: connect to alt2.gmail-smtp-in.l.google.com[172.217.204.27]:25: Connection timed out
Jan  5 14:59:04 localhost postfix/smtp[3611]: connect to alt3.gmail-smtp-in.l.google.com[172.217.192.27]:25: Connection timed out
Jan  5 14:59:04 localhost postfix/smtp[3610]: connect to alt3.gmail-smtp-in.l.google.com[172.217.192.27]:25: Connection timed out
Jan  5 14:59:34 localhost postfix/smtp[3611]: connect to alt4.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection timed out
Jan  5 14:59:34 localhost postfix/smtp[3611]: 6B01620CBB: to=<h.humbatov@gmail.com>, relay=none, delay=34397, delays=34246/0.01/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection $
Jan  5 14:59:34 localhost postfix/smtp[3610]: connect to alt4.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection timed out
Jan  5 14:59:34 localhost postfix/smtp[3610]: 3F67920C61: to=<h.humbatov@gmail.com>, relay=none, delay=34440, delays=34290/0.01/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection $
Jan  5 15:07:03 localhost postfix/qmgr[2033]: 3274720C5D: from=<root@localhost.localdomain>, size=405, nrcpt=1 (queue active)
Jan  5 15:07:33 localhost postfix/smtp[3617]: connect to gmail-smtp-in.l.google.com[74.125.201.27]:25: Connection timed out
Jan  5 15:08:03 localhost postfix/smtp[3617]: connect to alt1.gmail-smtp-in.l.google.com[173.194.208.27]:25: Connection timed out
Jan  5 15:08:33 localhost postfix/smtp[3617]: connect to alt2.gmail-smtp-in.l.google.com[172.217.204.27]:25: Connection timed out
Jan  5 15:09:03 localhost postfix/smtp[3617]: connect to alt3.gmail-smtp-in.l.google.com[172.217.192.27]:25: Connection timed out
Jan  5 15:09:33 localhost postfix/smtp[3617]: connect to alt4.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection timed out
Jan  5 15:09:33 localhost postfix/smtp[3617]: 3274720C5D: to=<h.humbatov@gmail.com>, relay=none, delay=34577, delays=34427/0.01/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection $
Jan  5 15:17:03 localhost postfix/qmgr[2033]: 00F3B20BC2: from=<www-data@mail.caspianappliance.com>, size=13524, nrcpt=1 (queue active)
Jan  5 15:17:34 localhost postfix/smtp[3686]: connect to gmail-smtp-in.l.google.com[74.125.201.27]:25: Connection timed out
Jan  5 15:18:04 localhost postfix/smtp[3686]: connect to alt1.gmail-smtp-in.l.google.com[173.194.208.26]:25: Connection timed out
Jan  5 15:18:34 localhost postfix/smtp[3686]: connect to alt2.gmail-smtp-in.l.google.com[172.217.204.27]:25: Connection timed out
Jan  5 15:19:04 localhost postfix/smtp[3686]: connect to alt3.gmail-smtp-in.l.google.com[172.217.192.27]:25: Connection timed out
Jan  5 15:19:34 localhost postfix/smtp[3686]: connect to alt4.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection timed out
Jan  5 15:19:34 localhost postfix/smtp[3686]: 00F3B20BC2: to=<h.humbatov@gmail.com>, relay=none, delay=35817, delays=35666/0.01/151/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[74.125.193.27]:25: Connection $
Jan  5 15:27:03 localhost postfix/qmgr[2033]: A9EA620F4F: from=<www-data@mail.caspianappliance.com>, size=13509, nrcpt=1 (queue active)
Jan  5 15:27:03 localhost postfix/qmgr[2033]: B695720B41: from=<www-data@mail.caspianappliance.com>, size=997, nrcpt=1 (queue active)
Jan  5 15:27:33 localhost postfix/smtp[3763]: connect to gmail-smtp-in.l.google.com[74.125.124.27]:25: Connection timed out
Jan  5 15:27:33 localhost postfix/smtp[3764]: connect to gmail-smtp-in.l.google.com[74.125.124.27]:25: Connection timed out



```

---

### Post by volkswagner on 2019-01-05
Connection time out is very informative.

Can you telnet on port 25 to smtp.google.com?

Assuming your internet works, we can rule out bad gateway.
Either Google is silently blocking connections from your server, you have firewall rules preventing connection on port 25, or the VPS has an internet provider blocking port 25.

Google and other servers may Bock you because you don't have DNS cofigured on your domain. mail.caspianappliance.com has no A Record setup.

Where is your VPS hosted (is it on a residential or DHCP ISP connection)?
Do you have firewall rules setup?

---

### Post by SeijiSensei on 2019-01-06
How long have you had this VPS?  It's possible that someone was using the same IP for spamming purposes, and it ended up on a blacklist. 

Go here: [https://mxtoolbox.com/blacklists.aspx](https://mxtoolbox.com/blacklists.aspx) 

then enter your IP address.

If this is a legitimate VM provider, like Linode, you shouldn't be blocked from using port 25.  Try the telnet test volkswagner suggested:

```
telnet gmail-smtp-in.l.google.com 25
```

Do you get this banner or does it time out?

```
220 mx.google.com ESMTP k18si1978075qtb.401 - gsmtp
```

---

