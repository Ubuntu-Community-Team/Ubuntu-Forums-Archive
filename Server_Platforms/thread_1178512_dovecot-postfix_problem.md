---
title: "dovecot-postfix problem"
date: 2009-06-04
forum: Server Platforms
---

### Post by msinternet on 2009-06-04
Hi all,

I have been trying to setup a new server and have got so far but the emails have me totally stumped. I have followed loads of tutorials and I think I have done everything right but it just doesn't work. So the problems are:

1) If I send an email to my domain it shows up in the logs but I don't get any emails???

2) If I send mail via php the emails seem to be from www-data but don't actually get out of my server

The end of my main.log is

```

Jun  4 19:16:34 t300 postfix/smtpd[13474]: connect from mailforwards.extendcp.co.uk[79.170.40.74]
Jun  4 19:16:34 t300 postfix/smtpd[13474]: setting up TLS connection from mailforwards.extendcp.co.uk[79.170.40.74]
Jun  4 19:16:35 t300 postfix/smtpd[13474]: Anonymous TLS connection established from mailforwards.extendcp.co.uk[79.170.40.74]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Jun  4 19:16:35 t300 postfix/smtpd[13474]: 3E5998D22C8: client=mailforwards.extendcp.co.uk[79.170.40.74]
Jun  4 19:16:35 t300 postfix/cleanup[13479]: 3E5998D22C8: message-id=<4A280F81.8090002@msinternet.com>
Jun  4 19:16:35 t300 postfix/qmgr[13438]: 3E5998D22C8: from=<info(at)msinternet.com>, size=852, nrcpt=1 (queue active)
Jun  4 19:16:35 t300 deliver(martin): msgid=<4A280F81.8090002@msinternet.com>: saved mail to INBOX
Jun  4 19:16:35 t300 postfix/local[13480]: 3E5998D22C8: to=<martin(at)mailpro.org.uk>, relay=local, delay=0.15, delays=0.12/0/0/0.03, dsn=2.0.0, status=sent (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}")
Jun  4 19:16:35 t300 postfix/qmgr[13438]: 3E5998D22C8: removed

...

Jun  4 20:07:08 t300 postfix/smtp[15254]: A299D8D23EB: to=<info(at)zoejewellery.com>, relay=mail.zoejewellery.com[79.170.40.26]:25, delay=0.4, delays=0.04/0/0.29/0.07, dsn=5.0.0, status=bounced (host mail.zoejewellery.com[79.170.40.26] said: 550 Please turn authentication on (in reply to RCPT TO command))
Jun  4 20:07:08 t300 postfix/qmgr[15243]: 952C48D23E7: removed
Jun  4 20:07:08 t300 deliver(www-data): msgid=<20090604190708.05AAE8D23EC@t300.mailpro.org.uk>: saved mail to INBOX
Jun  4 20:07:08 t300 postfix/local[15266]: 05AAE8D23EC: to=<www-data@mailpro.org.uk>, relay=local, delay=0.05, delays=0.03/0/0/0.03, dsn=2.0.0, status=sent (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}")
Jun  4 20:07:08 t300 postfix/qmgr[15243]: 05AAE8D23EC: removed
Jun  4 20:07:08 t300 postfix/cleanup[15247]: 16C128D22C6: message-id=<20090604190708.16C128D22C6@t300.mailpro.org.uk>
Jun  4 20:07:08 t300 postfix/bounce[15261]: A299D8D23EB: sender non-delivery notification: 16C128D22C6
Jun  4 20:07:08 t300 postfix/qmgr[15243]: A299D8D23EB: removed
Jun  4 20:07:08 t300 postfix/qmgr[15243]: 16C128D22C6: from=<>, size=5389, nrcpt=1 (queue active)
Jun  4 20:07:08 t300 deliver(www-data): msgid=<20090604190708.16C128D22C6@t300.mailpro.org.uk>: saved mail to INBOX
Jun  4 20:07:08 t300 postfix/local[15258]: 16C128D22C6: to=<www-data@mailpro.org.uk>, relay=local, delay=0.03, delays=0.02/0/0/0.02, dsn=2.0.0, status=sent (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}")
Jun  4 20:07:08 t300 postfix/qmgr[15243]: 16C128D22C6: removed
Jun  4 20:10:49 t300 postfix/qmgr[15243]: 207228D23E5: from=<>, size=5389, nrcpt=1 (queue active)
Jun  4 20:10:49 t300 postfix/qmgr[15243]: D75118D23E2: from=<>, size=5397, nrcpt=1 (queue active)
Jun  4 20:10:49 t300 postfix/qmgr[15243]: F03028D23E8: from=<>, size=5397, nrcpt=1 (queue active)
Jun  4 20:10:49 t300 postfix/qmgr[15243]: 81BF18D23E9: from=<>, size=5389, nrcpt=1 (queue active)
Jun  4 20:10:49 t300 postfix/qmgr[15243]: 829078D23EA: from=<>, size=5397, nrcpt=1 (queue active)
Jun  4 20:10:49 t300 postfix/qmgr[15243]: E8EEB8D23DE: from=<>, size=5389, nrcpt=1 (queue active)
Jun  4 20:10:49 t300 deliver(www-data): msgid=<20090604183428.D75118D23E2@t300.mailpro.org.uk>: saved mail to INBOX
Jun  4 20:10:49 t300 deliver(www-data): msgid=<20090604190443.207228D23E5@t300.mailpro.org.uk>: saved mail to INBOX
Jun  4 20:10:49 t300 postfix/local[15531]: 207228D23E5: to=<www-data@mailpro.org.uk>, relay=local, delay=366, delays=366/0.01/0/0.06, dsn=2.0.0, status=sent (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}")
Jun  4 20:10:49 t300 postfix/qmgr[15243]: 207228D23E5: removed
Jun  4 20:10:49 t300 postfix/local[15534]: D75118D23E2: to=<www-data@mailpro.org.uk>, relay=local, delay=2180, delays=2180/0.01/0/0.05, dsn=2.0.0, status=sent (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}")
Jun  4 20:10:49 t300 postfix/qmgr[15243]: D75118D23E2: removed
Jun  4 20:10:49 t300 deliver(www-data): msgid=<20090604185154.81BF18D23E9@t300.mailpro.org.uk>: saved mail to INBOX
Jun  4 20:10:49 t300 deliver(www-data): msgid=<20090604190442.F03028D23E8@t300.mailpro.org.uk>: saved mail to INBOX
Jun  4 20:10:49 t300 postfix/local[15531]: F03028D23E8: to=<www-data@mailpro.org.uk>, relay=local, delay=366, delays=366/0.06/0/0.05, dsn=2.0.0, status=sent (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}")
Jun  4 20:10:49 t300 postfix/qmgr[15243]: F03028D23E8: removed
Jun  4 20:10:49 t300 postfix/local[15534]: 81BF18D23E9: to=<www-data@mailpro.org.uk>, relay=local, delay=1135, delays=1135/0.06/0/0.05, dsn=2.0.0, status=sent (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}")
Jun  4 20:10:49 t300 postfix/qmgr[15243]: 81BF18D23E9: removed
Jun  4 20:10:49 t300 deliver(www-data): msgid=<20090604185154.829078D23EA@t300.mailpro.org.uk>: saved mail to INBOX
Jun  4 20:10:49 t300 postfix/local[15541]: 829078D23EA: to=<www-data@mailpro.org.uk>, relay=local, delay=1135, delays=1135/0.11/0/0.05, dsn=2.0.0, status=sent (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}")
Jun  4 20:10:49 t300 postfix/qmgr[15243]: 829078D23EA: removed
Jun  4 20:10:49 t300 deliver(www-data): msgid=<20090604183428.E8EEB8D23DE@t300.mailpro.org.uk>: saved mail to INBOX
Jun  4 20:10:49 t300 postfix/local[15531]: E8EEB8D23DE: to=<www-data@mailpro.org.uk>, relay=local, delay=2180, delays=2180/0.11/0/0.08, dsn=2.0.0, status=sent (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}")
Jun  4 20:10:49 t300 postfix/qmgr[15243]: E8EEB8D23DE: removed

```

and my mail.err

```
Jun  4 19:40:54 t300 deliver(www-data): mkdir(/var/www/Maildir/new) failed: Permission denied (euid=33(www-data) egid=33(www-data) missing +w perm: /var/www/Maildir)
Jun  4 19:40:54 t300 last message repeated 6 times
Jun  4 19:42:43 t300 last message repeated 2 times
Jun  4 19:44:43 t300 deliver(www-data): mkdir(/var/www/Maildir/new) failed: Permission denied (euid=33(www-data) egid=33(www-data) missing +w perm: /var/www/Maildir)
Jun  4 19:44:43 t300 deliver(www-data): mkdir(/var/www/Maildir/new) failed: Permission denied (euid=33(www-data) egid=33(www-data) missing +w perm: /var/www/Maildir)
Jun  4 19:50:37 t300 deliver(www-data): mkdir(/var/www/Maildir/new) failed: Permission denied (euid=33(www-data) egid=33(www-data) missing +w perm: /var/www/Maildir)
Jun  4 19:50:37 t300 last message repeated 5 times
Jun  4 19:51:54 t300 last message repeated 2 times
Jun  4 20:00:37 t300 deliver(www-data): mkdir(/var/www/Maildir/new) failed: Permission denied (euid=33(www-data) egid=33(www-data) missing +w perm: /var/www/Maildir)
Jun  4 20:00:37 t300 last message repeated 10 times
Jun  4 20:04:43 t300 deliver(www-data): mkdir(/var/www/Maildir/new) failed: Permission denied (euid=33(www-data) egid=33(www-data) missing +w perm: /var/www/Maildir)
Jun  4 20:05:57 t300 last message repeated 2 times
Jun  4 20:05:57 t300 deliver(www-data): mkdir(/var/www/Maildir/new) failed: Permission denied (euid=33(www-data) egid=33(www-data) missing +w perm: /var/www/Maildir)

```

At least the emails are in the system somewhere but it is driving me nuts. I figure the biggest clues are the  "550 Please turn authentication" for sent mail and the permissions thing.

If anyone can figure this out I would be hugely grateful.

Thanks,

Martin

---

### Post by LepeKaname on 2009-06-05
> Jun  4 20:05:57 t300 deliver(www-data): mkdir(/var/www/Maildir/new) failed: Permission denied (euid=33(www-data) egid=33(www-data) missing +w perm: /var/www/Maildir)

Your user www-data has its home directory in /var/www/ , so it is trying to create the inbox at that "home directory". That what this error is about.

At you postfix/main.cf add this 2 lines (if you don't have them)

debug_peer_list = 127.0.0.1
debug_peer_level = 5

In that sense, you will be able to have a more detailed information in your mail.log. Maybe then, you can have a clue...

---

### Post by msinternet on 2009-06-19
Ok, an update. I installed webmin and got the mailboxes t owork so I can recieve emails ok but when I try to send emails out I get a message from the recipients server that says "550 Please turn authentication" so I figure I have probably messed up TLS or SASL or something else related. 

Has anybody got a clue how to figure out what I am not authenticating properly???

Thanks,

Martin

---

### Post by msinternet on 2009-06-22
ANOTHER UPDATE

I think I have TLS and SASL working ok now but I ma a bit confused by two points:

1) How does the self signed certificate thing work? I followed the instructions but I dont get the difference to if I use a CA

2) do I need to to the domain-key thing? How does this work? The bit I really don;t follow is about setting DNS, how do I do this - I have no clue!??

Thanks,

Martin

---

### Post by LepeKaname on 2009-06-22
I'm not sure about your first question, but for the second one, this thread may be useful:

[http://ubuntuforums.org/showthread.php?t=1189531](http://ubuntuforums.org/showthread.php?t=1189531)

---

