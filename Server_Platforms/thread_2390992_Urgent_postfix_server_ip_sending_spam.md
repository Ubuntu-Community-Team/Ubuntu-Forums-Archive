---
title: "Urgent: postfix server ip sending spam"
date: 2018-05-04
forum: Server Platforms
---

### Post by kingdev on 2018-05-04
Hi guys,
my postfix mail server is sending spam.
you can find bellow mail.log last lines

```
root@mail:/var/log# tail -f /var/log/mail.logMay  4 21:17:42 mail postfix/smtpd[22653]: warning: unknown[181.214.206.133]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  4 21:17:42 mail postfix/smtpd[22653]: disconnect from unknown[181.214.206.133]
May  4 21:18:07 mail postfix/smtpd[22653]: connect from unknown[181.214.206.133]
May  4 21:18:09 mail postfix/smtpd[22653]: warning: unknown[181.214.206.133]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  4 21:18:09 mail postfix/smtpd[22653]: disconnect from unknown[181.214.206.133]
May  4 21:18:45 mail dovecot: pop3-login: Login: user=<mail@host.com>, method=PLAIN, rip=41.142.104.219, lip=45.254.93.23, mpid=22665, session=<qJCB3WdrcAApjmjb>
May  4 21:18:48 mail dovecot: pop3(mail@host.com): Disconnected: Logged out top=0/0, retr=0/0, del=0/206, size=56306961
May  4 21:19:57 mail dovecot: imap-login: Disconnected (no auth attempts in 8 secs): user=<>, rip=139.162.109.245, lip=45.254.93.23, TLS: Disconnected, session=<0PXE4Wdr7gCLom31>
May  4 21:20:15 mail postfix/smtpd[22669]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
May  4 21:20:15 mail postfix/smtpd[22669]: connect from unknown[181.214.206.133]
May  4 21:20:18 mail postfix/smtpd[22669]: warning: unknown[181.214.206.133]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  4 21:20:18 mail postfix/smtpd[22669]: disconnect from unknown[181.214.206.133]
May  4 21:20:20 mail dovecot: pop3-login: Login: user=mail@host.com <q72.223, lip=545.254.93.23, mpid=22675, session=<QEgl42drXABpvUjf>
May  4 21:20:21 mail dovecot: pop3(mail@host.com): Disconnected: Logged out top=2/51777, retr=0/0, del=0/89, size=78439634

May  4 21:20:42 mail postfix/smtpd[22669]: connect from unknown[181.214.206.133]
```

Here is main.cf file

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

# The first text sent to a connecting process.
smtpd_banner = $myhostname ESMTP $mail_name
biff = no
# appending .domain is the MUA's job.
append_dot_mydomain = no
readme_directory = no


# SASL parameters
# ---------------------------------
# Use Dovecot to authenticate.
smtpd_sasl_type = dovecot
# Referring to /var/spool/postfix/private/auth
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
smtpd_sasl_authenticated_header = yes


# TLS parameters
# ---------------------------------


# Replace this with your SSL certificate path if you are using one.
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
# The snakeoil self-signed certificate has no need for a CA file. But
# if you are using your own SSL certificate, then you probably have
# a CA certificate bundle from your provider. The path to that goes
# here.
#smtpd_tls_CAfile=/path/to/ca/file


smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache

#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
```

the server ip is blacklisted in CBL SpamHaus

---

### Post by darkod on 2018-05-04
Where do you see any mail sent in that log? It only shows auth failed which is rather normal because of intents to use it to send mail. But that doesn't mean they managed to do that. When an email message is actually sent it has different log entry, most often a 250 OK message.

The IP could be blacklisted as part of whole subnet of the provider for example, or just partially blacklisted on some of the lists, not all.

---

### Post by kingdev on 2018-05-04
> **darkod said:**
> Where do you see any mail sent in that log? It only shows auth failed which is rather normal because of intents to use it to send mail. But that doesn't mean they managed to do that. When an email message is actually sent it has different log entry, most often a 250 OK message.

The IP could be blacklisted as part of whole subnet of the provider for example, or just partially blacklisted on some of the lists, not all.

i've check the mailq

this is an exemple

```
[COLOR=#000000][FONT=Menlo](host mx01.1and1.es[217.72.192.67] refused to talk to me: 554-kundenserver.de (mxeue111) Nemesis ESMTP Service not available 554-No SMTP service 554-IP address is black listed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]host mx1.dsv.c3s2.host.com[216.71.158.68] refused to talk to me: 554-esa10.dsv.c3s2.iphmx.com 554 Your access to this mail system has been rejected due to the sending MTA's poor reputation.

[/FONT][/COLOR]
```


a copy of [COLOR=#000000][FONT=Menlo]mail.log
[/FONT][/COLOR]

```
May  5 00:04:32 mail postfix/smtp[24333]: 7E1F6336035: to=<client@host.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=5.7, delays=1.1/0.01/0/4.6, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as E0D25336042)
May  5 00:04:32 mail postfix/qmgr[23972]: 7E1F6336035: removed
May  5 00:04:33 mail dovecot: lda(client@host.com): msgid=<598021895.294141525478657016.JavaMail.backend@ma-back-02>: saved mail to INBOX
May  5 00:04:33 mail postfix/pipe[24341]: E0D25336042: to=<client@host.com>, relay=dovecot, delay=0.11, delays=0.05/0/0/0.06, dsn=2.0.0, status=sent (delivered via dovecot service)
May  5 00:04:33 mail postfix/qmgr[23972]: E0D25336042: removed
May  5 00:04:33 mail postfix/smtpd[24318]: disconnect from mta477a.sparkpostmail.com[52.26.78.194]
May  5 00:04:33 mail postfix/smtpd[24324]: disconnect from mta477a.sparkpostmail.com[52.26.78.194]
May  5 00:05:33 mail postfix/smtpd[24318]: connect from unknown[181.214.206.133]
May  5 00:05:35 mail postfix/smtpd[24318]: warning: unknown[181.214.206.133]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 00:05:35 mail postfix/smtpd[24318]: disconnect from unknown[181.214.206.133]
May  5 00:05:36 mail dovecot: pop3-login: Login: user=<qualite@host.com>, method=PLAIN, rip=105.189.72.223, lip=51.254.93.88, mpid=24389, session=<8aYsMmprpABpvUjf>
May  5 00:05:37 mail dovecot: pop3(qualite@host.com): Disconnected: Logged out top=2/51777, retr=0/0, del=0/89, size=78439634
May  5 00:05:46 mail dovecot: pop3-login: Login: user=<facturation@host.com>, method=PLAIN, rip=197.253.201.163, lip=51.254.93.88, mpid=24391, session=<JdrMMmprwQDF/cmj>
May  5 00:05:47 mail dovecot: pop3(facturation@host.com): Disconnected: Logged out top=0/0, retr=0/0, del=0/1962, size=964262009
May  5 00:05:53 mail postfix/smtpd[24324]: connect from mta477a.sparkpostmail.com[52.26.78.194]
May  5 00:05:53 mail postfix/smtpd[24318]: connect from mta477a.sparkpostmail.com[52.26.78.194]
May  5 00:05:53 mail postfix/smtpd[24392]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
May  5 00:05:53 mail postfix/smtpd[24392]: connect from mta477a.sparkpostmail.com[52.26.78.194]
May  5 00:05:53 mail postfix/smtpd[24324]: Anonymous TLS connection established from mta477a.sparkpostmail.com[52.26.78.194]: TLSv1.2 with cipher ECDHE-RSA-AES256-GCM-SHA384 (256/256 bits)
May  5 00:05:53 mail postfix/smtpd[24318]: Anonymous TLS connection established from mta477a.sparkpostmail.com[52.26.78.194]: TLSv1.2 with cipher ECDHE-RSA-AES256-GCM-SHA384 (256/256 bits)
May  5 00:05:54 mail postfix/smtpd[24392]: Anonymous TLS connection established from mta477a.sparkpostmail.com[52.26.78.194]: TLSv1.2 with cipher ECDHE-RSA-AES256-GCM-SHA384 (256/256 bits)
May  5 00:05:54 mail postgrey[1056]: action=pass, reason=client AWL, client_name=mta477a.sparkpostmail.com, client_address=52.26.78.194, sender=msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com, recipient=client@host.com
May  5 00:05:54 mail postgrey[1056]: action=pass, reason=client AWL, client_name=mta477a.sparkpostmail.com, client_address=52.26.78.194, sender=msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com, recipient=client@host.com
May  5 00:05:54 mail postfix/smtpd[24324]: 5793E336035: client=mta477a.sparkpostmail.com[52.26.78.194]
May  5 00:05:54 mail postgrey[1056]: action=pass, reason=client AWL, client_name=mta477a.sparkpostmail.com, client_address=52.26.78.194, sender=msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com, recipient=exploitation@host.com
May  5 00:05:54 mail postgrey[1056]: action=pass, reason=client AWL, client_name=mta477a.sparkpostmail.com, client_address=52.26.78.194, sender=msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com, recipient=exploitation@host.com
May  5 00:05:54 mail postfix/smtpd[24318]: 66D08336042: client=mta477a.sparkpostmail.com[52.26.78.194]
May  5 00:05:54 mail postgrey[1056]: action=pass, reason=client AWL, client_name=mta477a.sparkpostmail.com, client_address=52.26.78.194, sender=msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com, recipient=info@host.com
May  5 00:05:54 mail postgrey[1056]: action=pass, reason=client AWL, client_name=mta477a.sparkpostmail.com, client_address=52.26.78.194, sender=msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com, recipient=info@host.com
May  5 00:05:54 mail postfix/smtpd[24392]: 8C2F6336043: client=mta477a.sparkpostmail.com[52.26.78.194]
May  5 00:05:54 mail postfix/cleanup[24328]: 5793E336035: message-id=<754545035.294201525478744128.JavaMail.backend@ma-back-02>
May  5 00:05:54 mail postfix/cleanup[24331]: 66D08336042: message-id=<1379590926.294191525478744121.JavaMail.backend@ma-back-02>
May  5 00:05:55 mail postfix/cleanup[24394]: 8C2F6336043: message-id=<1488424671.294211525478744138.JavaMail.backend@ma-back-02>
May  5 00:05:55 mail postfix/qmgr[23972]: 66D08336042: from=<msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com>, size=151587, nrcpt=1 (queue active)
May  5 00:05:55 mail postfix/qmgr[23972]: 5793E336035: from=<msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com>, size=151555, nrcpt=1 (queue active)
May  5 00:05:55 mail postfix/qmgr[23972]: 8C2F6336043: from=<msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com>, size=151541, nrcpt=1 (queue active)
May  5 00:05:57 mail postfix/smtpd[24340]: connect from localhost.localdomain[127.0.0.1]
May  5 00:05:57 mail postfix/smtpd[24340]: 07F16336044: client=localhost.localdomain[127.0.0.1]
May  5 00:05:57 mail postfix/cleanup[24331]: 07F16336044: message-id=<1379590926.294191525478744121.JavaMail.backend@ma-back-02>
May  5 00:05:57 mail postfix/qmgr[23972]: 07F16336044: from=<msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com>, size=152587, nrcpt=1 (queue active)
May  5 00:05:57 mail postfix/smtpd[24340]: disconnect from localhost.localdomain[127.0.0.1]
May  5 00:05:57 mail amavis[22205]: (22205-12) Passed CLEAN {RelayedInbound}, [52.26.78.194]:13499 <msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com> -> <exploitation@host.com>, Queue-ID: 66D08336042, Message-ID: <1379590926.294191525478744121.JavaMail.backend@ma-back-02>, mail_id: SjL1GIgYRz8E, Hits: 4.098, size: 151586, queued_as: 07F16336044, dkim_sd=scph0416:stgfleet.com, 1816 ms
May  5 00:05:57 mail postfix/smtp[24336]: 66D08336042: to=<exploitation@host.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=2.9, delays=1.1/0/0/1.8, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 07F16336044)
May  5 00:05:57 mail postfix/qmgr[23972]: 66D08336042: removed
May  5 00:05:57 mail postfix/smtpd[24340]: connect from localhost.localdomain[127.0.0.1]
May  5 00:05:57 mail postfix/smtpd[24340]: 23E8E336042: client=localhost.localdomain[127.0.0.1]
May  5 00:05:57 mail postfix/cleanup[24328]: 23E8E336042: message-id=<754545035.294201525478744128.JavaMail.backend@ma-back-02>
May  5 00:05:57 mail dovecot: lda(exploitation@host.com): msgid=<1379590926.294191525478744121.JavaMail.backend@ma-back-02>: saved mail to INBOX
May  5 00:05:57 mail postfix/pipe[24341]: 07F16336044: to=<exploitation@host.com>, relay=dovecot, delay=0.13, delays=0.08/0/0/0.06, dsn=2.0.0, status=sent (delivered via dovecot service)
May  5 00:05:57 mail postfix/qmgr[23972]: 07F16336044: removed
May  5 00:05:57 mail postfix/qmgr[23972]: 23E8E336042: from=<msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com>, size=152543, nrcpt=1 (queue active)
May  5 00:05:57 mail postfix/smtpd[24340]: disconnect from localhost.localdomain[127.0.0.1]
May  5 00:05:57 mail amavis[22794]: (22794-09) Passed CLEAN {RelayedInbound}, [52.26.78.194]:65477 <msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com> -> <client@host.com>, Queue-ID: 5793E336035, Message-ID: <754545035.294201525478744128.JavaMail.backend@ma-back-02>, mail_id: uWaai-tUSeJn, Hits: 4.098, size: 151554, queued_as: 23E8E336042, dkim_sd=scph0416:stgfleet.com, 1844 ms
May  5 00:05:57 mail postfix/smtp[24333]: 5793E336035: to=<client@host.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=3.1, delays=1.2/0/0/1.8, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 23E8E336042)
May  5 00:05:57 mail postfix/qmgr[23972]: 5793E336035: removed
May  5 00:05:57 mail dovecot: lda(client@host.com): msgid=<754545035.294201525478744128.JavaMail.backend@ma-back-02>: saved mail to INBOX
May  5 00:05:57 mail postfix/pipe[24341]: 23E8E336042: to=<client@host.com>, relay=dovecot, delay=0.16, delays=0.09/0/0/0.07, dsn=2.0.0, status=sent (delivered via dovecot service)
May  5 00:05:57 mail postfix/qmgr[23972]: 23E8E336042: removed
May  5 00:05:58 mail postfix/smtpd[24340]: connect from localhost.localdomain[127.0.0.1]
May  5 00:05:58 mail postfix/smtpd[24340]: 515B0336035: client=localhost.localdomain[127.0.0.1]
May  5 00:05:58 mail postfix/cleanup[24394]: 515B0336035: message-id=<1488424671.294211525478744138.JavaMail.backend@ma-back-02>
May  5 00:05:58 mail postfix/qmgr[23972]: 515B0336035: from=<msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com>, size=152525, nrcpt=1 (queue active)
May  5 00:05:58 mail amavis[24347]: (24347-01) Passed CLEAN {RelayedInbound}, [52.26.78.194]:32863 <msprvs1=17663n-qlmi2D=bounces-27637@spmailtechnol.com> -> <info@host.com>, Queue-ID: 8C2F6336043, Message-ID: <1488424671.294211525478744138.JavaMail.backend@ma-back-02>, mail_id: u5soUnxboY21, Hits: 4.098, size: 151540, queued_as: 515B0336035, dkim_sd=scph0416:stgfleet.com, 2943 ms
May  5 00:05:58 mail postfix/smtp[24398]: 8C2F6336043: to=<info@host.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=4.1, delays=1/0.01/0.34/2.7, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 515B0336035)
May  5 00:05:58 mail postfix/qmgr[23972]: 8C2F6336043: removed
May  5 00:05:58 mail dovecot: lda(info@host.com): msgid=<1488424671.294211525478744138.JavaMail.backend@ma-back-02>: saved mail to INBOX
May  5 00:05:58 mail postfix/pipe[24341]: 515B0336035: to=<info@host.com>, relay=dovecot, delay=0.16, delays=0.09/0/0/0.07, dsn=2.0.0, status=sent (delivered via dovecot service)
May  5 00:05:58 mail postfix/qmgr[23972]: 515B0336035: removed
May  5 00:06:00 mail postfix/smtpd[24409]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
May  5 00:06:00 mail postfix/smtpd[24409]: connect from unknown[181.214.206.133]
May  5 00:06:00 mail postfix/smtpd[24318]: disconnect from mta477a.sparkpostmail.com[52.26.78.194]
May  5 00:06:00 mail postfix/smtpd[24324]: disconnect from mta477a.sparkpostmail.com[52.26.78.194]
May  5 00:06:00 mail postfix/smtpd[24392]: disconnect from mta477a.sparkpostmail.com[52.26.78.194]
May  5 00:06:02 mail postfix/smtpd[24409]: warning: unknown[181.214.206.133]: SASL LOGIN authentication failed: UGFzc3dvcmQ6
May  5 00:06:02 mail postfix/smtpd[24409]: disconnect from unknown[181.214.206.133]
^C




```

---

### Post by SeijiSensei on 2018-05-04
Run the tests at mxtoolbox.com. Are you an open relay?

---

### Post by darkod on 2018-05-05
Run the smtp server tests on mxtoolbox like Sensei says. But I'm still not convinced you are spamming.

In your log extracts I see only one domain mainly mentioned (@host.com), is that something you are using/set up yourself?

Also, in the mail.log you can filter out sent messages quickly with something like:
```
cat /var/log/mail.log | grep 'status=sent'
```

It will filter out just the lines saying sent.

And if you are an open relay that someone found about, you would see literary hundreds of messages within only few minutes. Are there so many?

The poor reputation message can be because of number of things. SPF record (or lack of), reverse DNS not existing, postfix settings, etc... It doesn't necessarily mean spamming.

PS. Plus, why are you using 1and1 mail relay when you have your own mail server? Let it send directly to destination servers. It's not necessary to use your provider mail servers. Maybe they have higher threshold of reputation than the rest...

---

### Post by kingdev on 2018-05-05
> **SeijiSensei said:**
> Run the tests at mxtoolbox.com. Are you an open relay?

I have done the test
This is the result

[img]https://preview.ibb.co/g26t4S/5649_C8_AC_200_E_4_FB7_BDBF_00_B8_F8_D75714.png[/img]

It’s not an open relay

---

### Post by darkod on 2018-05-05
Did you see my previous post too?

You have reverse DNS mismatch. And it also seems you left your server fqdn as mail.example.com. The public IP rDNS record is mail.fta.ma.

That mismatch will not bring you good reputation...

---

### Post by kingdev on 2018-05-05
> **darkod said:**
> Did you see my previous post too?

You have reverse DNS mismatch. And it also seems you left your server fqdn as mail.example.com. The public IP rDNS record is mail.fta.ma.

That mismatch will not bring you good reputation...

Hello,

Yes, now seems good in the test ( screenshot attached )

So we need to wait CBL check

regarding [COLOR=#000000]filter out sent messages txt file attached[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by kingdev on 2018-05-06
problem resolved please close the t[COLOR=#000000]hread[/COLOR]

---

### Post by QIII on 2018-05-06
Hello!

You may mark the thread as solved by clicking on "Thread tools" above your initial post.

---

