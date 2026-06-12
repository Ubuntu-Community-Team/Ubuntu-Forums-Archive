---
title: "postfix guides - mail problem"
date: 2011-02-18
forum: Server Platforms
---

### Post by Rowanmf on 2011-02-18
i hope somebody can help me , 

i am setting up my first mailserver using Ubuntu 10.10 server .

i first followed the setup for ispconfig3 .. which seemed to have some problems so i went to postfix guides - [http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid](http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid)
i have now completed every thing according to the guide but cant recieve mail , when i watch the log files i can see there is a problem here -
Feb 18 13:30:10 rondebult postfix/local[5033]: 9F8CAB41163: to=<www-data@rondebult.co.zw>, relay=local, delay=0.11, delays=0.05/0.01/0/0.05, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")

it should say deliverd to INBOX 
I cant seem to find where this error is hiding . if anybody can help i would be very grateful.

Thanks

Rowan

---

### Post by rudelgurke on 2011-02-18
Did you check that a file "www-data" maybe exists in /var/mail (or /var/spool/mail) ?
If so, setup an appropriate alias for the www-data user.

---

### Post by Rowanmf on 2011-02-18
the file is there , under var/mail .. 
here is the user that i am using to test with -


Feb 18 13:28:15 rondebult postfix/smtpd[4950]: 1EF17B41168: client=localhost[127.0.0.1]
Feb 18 13:28:15 rondebult postfix/cleanup[4946]: 1EF17B41168: message-id=<4D5E57CB.3050104@rondebult.co.zw>
Feb 18 13:28:15 rondebult postfix/qmgr[1640]: 1EF17B41168: from=<Info@rondebult.co.zw>, size=1105, nrcpt=1 (queue active)
Feb 18 13:28:15 rondebult postfix/trivial-rewrite[4945]: warning: do not list domain rondebult.co.zw in BOTH mydestination and virtual_mailbox_domains
Feb 18 13:28:15 rondebult amavis[1156]: (01156-09) Passed CLEAN, LOCAL [192.168.1.36] [192.168.1.36] <Info@rondebult.co.zw> -> <info@rondebult.co.zw>, Message-ID: <4D5E57CB.3050104@rondebult.co.zw>, mail_id: Np37lMjHNiL7, Hits: -1, size: 660, queued_as: 1EF17B41168, 282 ms
Feb 18 13:28:15 rondebult postfix/smtp[4947]: C826BB41163: to=<info@rondebult.co.zw>, relay=127.0.0.1[127.0.0.1]:10024, delay=0.42, delays=0.13/0.01/0/0.28, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=01156-09, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as 1EF17B41168)
Feb 18 13:28:15 rondebult postfix/qmgr[1640]: C826BB41163: removed
Feb 18 13:28:15 rondebult postfix/smtpd[4950]: disconnect from localhost[127.0.0.1]
Feb 18 13:28:15 rondebult postfix/local[4951]: 1EF17B41168: to=<info@rondebult.co.zw>, relay=local, delay=0.16, delays=0.07/0.01/0/0.09, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb 18 13:28:15 rondebult postfix/qmgr[1640]: 1EF17B41168: removed

---

### Post by elico on 2011-02-18
i dont know what setup you did and ispconfig is one of the most complicated setups just for mail
you should look at 
[http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)
very good but have one missing line
and also this tutorial.
[http://www.kernel-panic.it/openbsd/mail/](http://www.kernel-panic.it/openbsd/mail/)
pdf link
[http://www.kernel-panic.it/openbsd/mail/OpenBSD_mail_server.pdf](http://www.kernel-panic.it/openbsd/mail/OpenBSD_mail_server.pdf)

i dont like to give tutorials and reading info but in this case  i recommend to read first
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

---

