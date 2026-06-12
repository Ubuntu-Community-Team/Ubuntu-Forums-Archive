---
title: "Postfix SMTP SmartPhone"
date: 2009-06-07
forum: Server Platforms
---

### Post by ericwait on 2009-06-07
I have never gotten smtp working 100%.  I can send while on the local network just fine.  When I am not on the network, I can send mail depending on my location (eg. school network --Works, public library --Doesn't Work).  This might just be because of those public networks blocking ports, I don't know.

However, the biggest issue is that I just got a smart phone (Palm Pre) and cannot send mail.  Gmail works and imap works to receive mail from my postfix server but I cannot send anything using my server.

Here is what happens when the phone tries to send: (from /var/log/mail.info)
```
Jun  7 09:40:27 xxxx postfix/smtpd[32599]: lost connection after STARTTLS from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:27 xxxx postfix/smtpd[32599]: disconnect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:27 xxxx postfix/smtpd[32599]: connect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:27 xxxx postfix/smtpd[32599]: setting up TLS connection from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:28 xxxx postfix/smtpd[32599]: Anonymous TLS connection established from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]: TLSv1 with cipher DHE-
RSA-AES256-SHA (256/256 bits)
Jun  7 09:40:28 xxxx postfix/smtpd[32599]: lost connection after STARTTLS from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:28 xxxx postfix/smtpd[32599]: disconnect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:28 xxxx postfix/smtpd[32599]: connect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:28 xxxx postfix/smtpd[32599]: setting up TLS connection from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:29 xxxx postfix/smtpd[32599]: Anonymous TLS connection established from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]: TLSv1 with cipher DHE-
RSA-AES256-SHA (256/256 bits)
Jun  7 09:40:29 xxxx postfix/smtpd[32599]: lost connection after STARTTLS from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:29 xxxx postfix/smtpd[32599]: disconnect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:36 xxxx postfix/smtpd[32599]: connect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:36 xxxx postfix/smtpd[32599]: setting up TLS connection from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:37 xxxx postfix/smtpd[32599]: Anonymous TLS connection established from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]: TLSv1 with cipher DHE-
RSA-AES256-SHA (256/256 bits)
Jun  7 09:40:37 xxxx postfix/smtpd[32599]: lost connection after STARTTLS from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:37 xxxx postfix/smtpd[32599]: disconnect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:37 xxxx postfix/smtpd[32599]: connect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:37 xxxx postfix/smtpd[32599]: setting up TLS connection from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:38 xxxx postfix/smtpd[32599]: Anonymous TLS connection established from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]: TLSv1 with cipher DHE-
RSA-AES256-SHA (256/256 bits)
Jun  7 09:40:38 xxxx postfix/smtpd[32599]: lost connection after STARTTLS from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:38 xxxx postfix/smtpd[32599]: disconnect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:38 xxxx postfix/smtpd[32599]: connect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:38 xxxx postfix/smtpd[32599]: setting up TLS connection from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:39 xxxx postfix/smtpd[32599]: Anonymous TLS connection established from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]: TLSv1 with cipher DHE-
RSA-AES256-SHA (256/256 bits)
Jun  7 09:40:39 xxxx postfix/smtpd[32599]: lost connection after STARTTLS from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:39 xxxx postfix/smtpd[32599]: disconnect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:39 xxxx postfix/smtpd[32583]: disconnect from mail-ew0-f214.google.com[209.85.219.214]
Jun  7 09:40:49 xxxx postfix/smtpd[32599]: connect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:50 xxxx postfix/smtpd[32599]: setting up TLS connection from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:50 xxxx postfix/smtpd[32599]: Anonymous TLS connection established from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]: TLSv1 with cipher DHE-
RSA-AES256-SHA (256/256 bits)
Jun  7 09:40:50 xxxx postfix/smtpd[32599]: lost connection after STARTTLS from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:50 xxxx postfix/smtpd[32599]: disconnect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:50 xxxx postfix/smtpd[32583]: connect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:51 xxxx postfix/smtpd[32583]: setting up TLS connection from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:51 xxxx postfix/smtpd[32583]: Anonymous TLS connection established from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]: TLSv1 with cipher DHE-
RSA-AES256-SHA (256/256 bits)
Jun  7 09:40:51 xxxx postfix/smtpd[32583]: lost connection after STARTTLS from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:51 xxxx postfix/smtpd[32583]: disconnect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:51 xxxx postfix/smtpd[32599]: connect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:52 xxxx postfix/smtpd[32599]: setting up TLS connection from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:52 xxxx postfix/smtpd[32599]: Anonymous TLS connection established from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]: TLSv1 with cipher DHE-
RSA-AES256-SHA (256/256 bits)
Jun  7 09:40:53 xxxx postfix/smtpd[32599]: lost connection after STARTTLS from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]
Jun  7 09:40:53 xxxx postfix/smtpd[32599]: disconnect from xxx-xxx-xxx-xxx.pools.spcsdns.net[xxx.xxx.xxx.xxx]

```

I will attach relevant config files.

Any insight would be appreciated :D

---

### Post by LepeKaname on 2009-06-07
Try to set your debug level higher (in main.cf):

debug_peer_level = 5

This way you may know what is happening.

Also check your "smtpd_recipient_restrictions" settings. 
Read postfix documentation.

---

### Post by ericwait on 2009-06-09
Well the debug level did not produce anything new :(

But I did go to [http://www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html](http://www.debianadmin.com/debian-mail-server-setup-with-postfix-dovecot-sasl-squirrel-mail.html)

Where it brought me to look at /etc/dovecot/dovecot.conf

I had ```
auth default {
mechanisms = plain
```
where they were saying, use```
auth default {
mechanisms = plain login
```

After restarting saslauthd, postfix, and dovecot it seems to be working now.

I don't know if I have left myself more open now to attacks.  If you see anything that would be, please let me know.  I tested for open relay using abuse.net relay checker and nothing.

I guess I shall see.
Thanks

---

