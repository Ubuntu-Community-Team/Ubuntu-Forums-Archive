---
title: "Postfix status=deferred error"
date: 2010-06-19
forum: Server Platforms
---

### Post by snmp01 on 2010-06-19
Hi 
After upgrading from a working 9.10 system to 10.04 Postfix has stopped delivery email to users but the mail is sitting in the Postfix mail queue

Sending email is fine and IMAP(s) and POP are working fine but when receiving messages I now get the following message:

postfix/pipe[14331]: 65B941B61F0: to=<me@fred.com>, relay=dovecot, delay=1081, delays=1081/0.02/0/0.1, dsn=4.3.0,** status=deferred (temporary failure)**

Using Postfix with Dovecot, MySQL & Amavis plus spamassasin

Does anyone have any idea what the upgrade process from 9.10 to 10.04 may of changed. The conf file were not replaced during the upgrade and only one parameter caused a issue for Dovecot after the upgrade "ssl_disable = no" after disabling this dovecot started but I changed this to SSL=yes


Thanks for any help
Ian

The mail conversation the mail is passed buy amavis to postfix of, not further errors are on the system so I am stuck:-

amavis[11903]: (11903-07) Passed CLEAN, [203.109.136.66] [203.109.136.66] <jo@sendme.com> -> <me@fred.com>, Message-ID: <0F7C3FE1-0427-45A6-86D5-5C3E7BA9AFA3@sendme.com>, mail_id: g2dA3mnd8fca, Hits: -1.901, size: 905, queued_as: DE7891B6273, 3768 ms
postfix/smtp[18091]: 16C2A1B6106: to=<me@fred.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=4, delays=0.22/0/0/3.8, dsn=2.0.0, status=sent (250 2.0.0 Ok, id=11903-07, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as DE7891B6273)
postfix/pipe[18100]: DE7891B6273: to=<me@fred.com>, relay=dovecot, delay=0.23, delays=0.11/0/0/0.12, dsn=4.3.0, status=deferred (temporary failure)

---

