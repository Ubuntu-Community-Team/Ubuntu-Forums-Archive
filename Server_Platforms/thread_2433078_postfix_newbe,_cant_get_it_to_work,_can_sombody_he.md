---
title: "postfix newbe, cant get it to work, can sombody help pls."
date: 2019-12-13
forum: Server Platforms
---

### Post by bertm2 on 2019-12-13
i installed postfix on a rock pi 4 running ubuntu18.4
i try to send mail with telnet:

```
$ telnet localhost 25
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 Bert-server1.fritz.box ESMTP Postfix (Ubuntu)
ehlo bootsmaat.nl
250-Bert-server1.fritz.box
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250-DSN
250 SMTPUTF8
mail from: bert
250 2.1.0 Ok
rcpt to: bertje.knor@gmail.com
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
subject: mailtest 5
bla bla bla
.
250 2.0.0 Ok: queued as D264841B99
421 4.4.2 Bert-server1.fritz.box Error: timeout exceeded
Connection closed by foreign host.
```

i tried this several times, tweaking stuf like main.cf, ufw, portforwarding etc, trying to debug this but i was not successful
if somebody can point me in the right directioni i would be very thankful to you.


**main.cf:**
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# See http://www.postfix.org/COMPATIBILITY_README.html -- default to 2 on
# fresh installs.
compatibility_level = 2

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

#door mij toegevoegt
smtpd_recipient_restrictions =
        permit_sasl_authenticated,
        permit_mynetworks,
        reject_unauth_destination
smtpd_helo_required = yes
smtpd_helo_restrictions =
        permit_mynetworks,
        permit_sasl_authenticated,
        reject_invalid_helo_hostname,
        reject_non_fqdn_helo_hostname,
        reject_unknown_helo_hostname
        check_helo_access hash:/etc/postfix/helo_access

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = Bert-server1.fritz.box
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, bootsmaat.nl, Bert-server1.fritz.box, localhost.fritz.box, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
#virtual_alias_maps = hash:/etc/postfix/virtual

```
**ufw status verbose:**
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp (OpenSSH)           ALLOW IN    Anywhere                  
80,443/tcp (Nginx Full)    ALLOW IN    Anywhere                  
25/tcp (Postfix)           ALLOW IN    Anywhere                  
143/tcp (Dovecot IMAP)     ALLOW IN    Anywhere                  
110/tcp (Dovecot POP3)     ALLOW IN    Anywhere                  
25                         ALLOW IN    Anywhere                  
587                        ALLOW IN    Anywhere                  
22/tcp (OpenSSH (v6))      ALLOW IN    Anywhere (v6)             
80,443/tcp (Nginx Full (v6)) ALLOW IN    Anywhere (v6)             
25/tcp (Postfix (v6))      ALLOW IN    Anywhere (v6)             
143/tcp (Dovecot IMAP (v6)) ALLOW IN    Anywhere (v6)             
110/tcp (Dovecot POP3 (v6)) ALLOW IN    Anywhere (v6)             
25 (v6)                    ALLOW IN    Anywhere (v6)             
587 (v6)                   ALLOW IN    Anywhere (v6)   

```
all these ports are also forwarded to my server


**the last part of my mail.log:**
```
Dec 13 12:01:04 localhost postfix/qmgr[2173]: ADBDA41B95: from=<bert@bootsmaat.nl>, size=365, nrcpt=1 (queue active)
Dec 13 12:01:04 localhost postfix/qmgr[2173]: 762D641B97: from=<bert@bootsmaat.nl>, size=396, nrcpt=1 (queue active)
Dec 13 12:01:34 localhost postfix/smtp[2211]: connect to gmail-smtp-in.l.google.com[74.125.128.26]:25: Connection timed out
Dec 13 12:01:34 localhost postfix/smtp[2216]: connect to gmail-smtp-in.l.google.com[74.125.128.26]:25: Connection timed out
Dec 13 12:02:04 localhost postfix/smtp[2211]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.26]:25: Connection timed out
Dec 13 12:02:04 localhost postfix/smtp[2216]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.26]:25: Connection timed out
Dec 13 12:02:34 localhost postfix/smtp[2216]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.26]:25: Connection timed out
Dec 13 12:02:34 localhost postfix/smtp[2211]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.26]:25: Connection timed out
Dec 13 12:03:04 localhost postfix/smtp[2211]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.27]:25: Connection timed out
Dec 13 12:03:04 localhost postfix/smtp[2216]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.27]:25: Connection timed out
Dec 13 12:03:34 localhost postfix/smtp[2216]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out
Dec 13 12:03:34 localhost postfix/smtp[2211]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out
Dec 13 12:03:34 localhost postfix/smtp[2216]: 762D641B97: to=<matroosenklus@gmail.com>, relay=none, delay=702, delays=552/0.03/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out)
Dec 13 12:03:34 localhost postfix/smtp[2211]: ADBDA41B95: to=<bertje.knor@gmail.com>, relay=none, delay=2228, delays=2078/0/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out)
Dec 13 12:04:12 localhost postfix/postfix-script[2240]: stopping the Postfix mail system
Dec 13 12:04:12 localhost postfix/master[2171]: terminating on signal 15
Dec 13 12:04:13 localhost postfix/postfix-script[2397]: starting the Postfix mail system
Dec 13 12:04:13 localhost postfix/master[2399]: daemon started -- version 3.3.0, configuration /etc/postfix
Dec 13 12:04:27 localhost postfix/smtpd[2421]: connect from localhost[127.0.0.1]
Dec 13 12:05:26 localhost postfix/smtpd[2421]: D264841B99: client=localhost[127.0.0.1]
Dec 13 12:06:32 localhost postfix/cleanup[2425]: D264841B99: message-id=<20191213120526.D264841B99@Bert-server1.fritz.box>
Dec 13 12:06:32 localhost postfix/qmgr[2401]: D264841B99: from=<bert@bootsmaat.nl>, size=381, nrcpt=1 (queue active)
Dec 13 12:06:35 localhost postfix/smtp[2426]: D264841B99: to=<bertje.knor@gmail.com>, relay=smtp.xs4all.nl[194.109.6.51]:25, delay=96, delays=93/0.05/1.2/1.8, dsn=2.0.0, status=sent (250 2.0.0 smtp-cloud8.xs4all.net accepted mail fjiKiyB6NTsDefjiLiiwOe for delivery)
Dec 13 12:06:35 localhost postfix/qmgr[2401]: D264841B99: removed
Dec 13 12:06:35 localhost postfix/smtpd[2427]: connect from lb2-smtp-cloud8.xs4all.net[194.109.24.25]
Dec 13 12:06:35 localhost postfix/smtpd[2427]: B4CCB41B99: client=lb2-smtp-cloud8.xs4all.net[194.109.24.25]
Dec 13 12:06:35 localhost postfix/cleanup[2425]: B4CCB41B99: message-id=<>
Dec 13 12:06:35 localhost postfix/qmgr[2401]: B4CCB41B99: from=<>, size=3895, nrcpt=1 (queue active)
Dec 13 12:06:35 localhost postfix/local[2429]: B4CCB41B99: to=<bert@bootsmaat.nl>, relay=local, delay=0.11, delays=0.07/0.04/0/0, dsn=2.0.0, status=sent (delivered to maildir)
Dec 13 12:06:35 localhost postfix/qmgr[2401]: B4CCB41B99: removed
Dec 13 12:07:05 localhost postfix/smtpd[2427]: disconnect from lb2-smtp-cloud8.xs4all.net[194.109.24.25] ehlo=2 starttls=1 mail=1 rcpt=1 data=1 quit=1 commands=7
Dec 13 12:08:32 localhost postfix/smtpd[2421]: timeout after END-OF-MESSAGE from localhost[127.0.0.1]
Dec 13 12:08:32 localhost postfix/smtpd[2421]: disconnect from localhost[127.0.0.1] ehlo=1 mail=1 rcpt=1 data=1 commands=4
Dec 13 12:09:13 localhost postfix/qmgr[2401]: B360941B98: from=<bert@bootsmaat.nl>, size=403, nrcpt=1 (queue active)
Dec 13 12:09:13 localhost postfix/qmgr[2401]: 2BBC041B96: from=<bert@bootsmaat.nl>, size=365, nrcpt=1 (queue active)
Dec 13 12:09:15 localhost postfix/smtp[2481]: 2BBC041B96: to=<matroosenklus@gmail.com>, relay=smtp.xs4all.nl[194.109.6.51]:25, delay=1883, delays=1882/0.06/1.1/0.09, dsn=2.0.0, status=sent (250 2.0.0 smtp-cloud8.xs4all.net accepted mail fjkwiyC4VTsDefjkxiix3P for delivery)
Dec 13 12:09:15 localhost postfix/qmgr[2401]: 2BBC041B96: removed
Dec 13 12:09:15 localhost postfix/smtp[2480]: B360941B98: to=<bertje.knor@gmail.com>, relay=smtp.xs4all.nl[194.109.6.51]:25, delay=777, delays=775/0.04/1.1/0.1, dsn=2.0.0, status=sent (250 2.0.0 smtp-cloud8.xs4all.net accepted mail fjkwiyC4STsDefjkxiix3O for delivery)
Dec 13 12:09:15 localhost postfix/qmgr[2401]: B360941B98: removed
Dec 13 12:09:15 localhost postfix/smtpd[2421]: connect from lb3-smtp-cloud8.xs4all.net[194.109.24.29]
Dec 13 12:09:15 localhost postfix/smtpd[2482]: connect from lb2-smtp-cloud8.xs4all.net[194.109.24.25]
Dec 13 12:09:15 localhost postfix/smtpd[2421]: A8AA341B96: client=lb3-smtp-cloud8.xs4all.net[194.109.24.29]
Dec 13 12:09:15 localhost postfix/smtpd[2482]: AE40F41B98: client=lb2-smtp-cloud8.xs4all.net[194.109.24.25]
Dec 13 12:09:15 localhost postfix/cleanup[2483]: A8AA341B96: message-id=<>
Dec 13 12:09:15 localhost postfix/qmgr[2401]: A8AA341B96: from=<>, size=3925, nrcpt=1 (queue active)
Dec 13 12:09:15 localhost postfix/cleanup[2484]: AE40F41B98: message-id=<>
Dec 13 12:09:15 localhost postfix/qmgr[2401]: AE40F41B98: from=<>, size=3892, nrcpt=1 (queue active)
Dec 13 12:09:15 localhost postfix/local[2485]: A8AA341B96: to=<bert@bootsmaat.nl>, relay=local, delay=0.13, delays=0.11/0.02/0/0.01, dsn=2.0.0, status=sent (delivered to maildir)
Dec 13 12:09:15 localhost postfix/qmgr[2401]: A8AA341B96: removed
Dec 13 12:09:15 localhost postfix/local[2485]: AE40F41B98: to=<bert@bootsmaat.nl>, relay=local, delay=0.11, delays=0.1/0/0/0, dsn=2.0.0, status=sent (delivered to maildir)
Dec 13 12:09:15 localhost postfix/qmgr[2401]: AE40F41B98: removed
Dec 13 12:09:45 localhost postfix/smtpd[2421]: disconnect from lb3-smtp-cloud8.xs4all.net[194.109.24.29] ehlo=2 starttls=1 mail=1 rcpt=1 data=1 quit=1 commands=7
Dec 13 12:09:45 localhost postfix/smtpd[2482]: disconnect from lb2-smtp-cloud8.xs4all.net[194.109.24.25] ehlo=2 starttls=1 mail=1 rcpt=1 data=1 quit=1 commands=7
Dec 13 12:13:06 localhost postfix/anvil[2428]: statistics: max connection rate 1/60s for (smtp:194.109.24.25) at Dec 13 12:06:35
Dec 13 12:13:06 localhost postfix/anvil[2428]: statistics: max connection count 1 for (smtp:194.109.24.25) at Dec 13 12:06:35
Dec 13 12:13:06 localhost postfix/anvil[2428]: statistics: max cache size 2 at Dec 13 12:09:15
Dec 13 12:14:32 localhost postfix/postfix-script[2509]: stopping the Postfix mail system
Dec 13 12:14:32 localhost postfix/master[2399]: terminating on signal 15
Dec 13 12:14:33 localhost postfix/postfix-script[2666]: starting the Postfix mail system
Dec 13 12:14:33 localhost postfix/master[2668]: daemon started -- version 3.3.0, configuration /etc/postfix
Dec 13 12:14:33 localhost postfix/qmgr[2670]: 762D641B97: from=<bert@bootsmaat.nl>, size=396, nrcpt=1 (queue active)
Dec 13 12:15:03 localhost postfix/smtpd[2692]: connect from a80-101-160-57.adsl.xs4all.nl[80.101.160.57]
Dec 13 12:15:03 localhost postfix/smtp[2677]: connect to gmail-smtp-in.l.google.com[172.217.218.27]:25: Connection timed out
Dec 13 12:15:33 localhost postfix/smtp[2677]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.26]:25: Connection timed out
Dec 13 12:16:03 localhost postfix/smtp[2677]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.27]:25: Connection timed out
Dec 13 12:16:23 localhost postfix/smtpd[2692]: NOQUEUE: reject: RCPT from a80-101-160-57.adsl.xs4all.nl[80.101.160.57]: 554 5.7.1 <bootsmaat.nl>: Helo command rejected: You are not who you say you are. Get lost!; from=<bert@bootsmaat.nl> to=<bertje.knor@gmail.com> proto=ESMTP helo=<bootsmaat.nl>
Dec 13 12:16:33 localhost postfix/smtp[2677]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.27]:25: Connection timed out
Dec 13 12:16:47 localhost postfix/smtpd[2692]: disconnect from a80-101-160-57.adsl.xs4all.nl[80.101.160.57] ehlo=1 mail=1 rcpt=0/1 quit=1 commands=3/4
Dec 13 12:17:03 localhost postfix/smtp[2677]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out
Dec 13 12:17:03 localhost postfix/smtp[2677]: 762D641B97: to=<matroosenklus@gmail.com>, relay=none, delay=1511, delays=1361/0.04/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out)
Dec 13 12:17:05 localhost postfix/smtpd[2692]: connect from a80-101-160-57.adsl.xs4all.nl[80.101.160.57]
Dec 13 12:18:55 localhost postfix/smtpd[2692]: NOQUEUE: reject: RCPT from a80-101-160-57.adsl.xs4all.nl[80.101.160.57]: 554 5.7.1 <bootsmaat.nl>: Helo command rejected: You are not who you say you are. Get lost!; from=<bert> to=<bertje.knor@gmail.com> proto=ESMTP helo=<bootsmaat.nl>
Dec 13 12:19:33 localhost postfix/smtpd[2692]: disconnect from a80-101-160-57.adsl.xs4all.nl[80.101.160.57] ehlo=1 mail=1 rcpt=0/1 quit=1 unknown=0/1 commands=3/5
Dec 13 12:19:53 localhost postfix/smtpd[2692]: connect from a80-101-160-57.adsl.xs4all.nl[80.101.160.57]
Dec 13 12:21:31 localhost postfix/smtpd[2692]: NOQUEUE: reject: RCPT from a80-101-160-57.adsl.xs4all.nl[80.101.160.57]: 554 5.7.1 <bootsmaat.nl>: Helo command rejected: You are not who you say you are. Get lost!; from=<bertje.knor@gmail.com> to=<matroosenklus@gmail.com> proto=ESMTP helo=<bootsmaat.nl>
Dec 13 12:23:32 localhost postfix/smtpd[2692]: timeout after RCPT from a80-101-160-57.adsl.xs4all.nl[80.101.160.57]
Dec 13 12:23:32 localhost postfix/smtpd[2692]: disconnect from a80-101-160-57.adsl.xs4all.nl[80.101.160.57] ehlo=1 mail=1/2 rcpt=0/1 commands=2/4
Dec 13 12:25:03 localhost postfix/anvil[2695]: statistics: max connection rate 1/60s for (smtp:80.101.160.57) at Dec 13 12:15:03
Dec 13 12:25:03 localhost postfix/anvil[2695]: statistics: max connection count 1 for (smtp:80.101.160.57) at Dec 13 12:15:03
Dec 13 12:25:03 localhost postfix/anvil[2695]: statistics: max cache size 1 at Dec 13 12:15:03
Dec 13 12:39:33 localhost postfix/qmgr[2670]: ADBDA41B95: from=<bert@bootsmaat.nl>, size=365, nrcpt=1 (queue active)
Dec 13 12:40:03 localhost postfix/smtp[2775]: connect to gmail-smtp-in.l.google.com[108.177.127.27]:25: Connection timed out
Dec 13 12:40:33 localhost postfix/smtp[2775]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.27]:25: Connection timed out
Dec 13 12:41:03 localhost postfix/smtp[2775]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.27]:25: Connection timed out
Dec 13 12:41:33 localhost postfix/smtp[2775]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.27]:25: Connection timed out
Dec 13 12:42:03 localhost postfix/smtp[2775]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out
Dec 13 12:42:03 localhost postfix/smtp[2775]: ADBDA41B95: to=<bertje.knor@gmail.com>, relay=none, delay=4537, delays=4387/0.05/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out)
Dec 13 12:44:33 localhost postfix/qmgr[2670]: 762D641B97: from=<bert@bootsmaat.nl>, size=396, nrcpt=1 (queue active)
Dec 13 12:45:04 localhost postfix/smtp[2783]: connect to gmail-smtp-in.l.google.com[108.177.126.26]:25: Connection timed out
Dec 13 12:45:34 localhost postfix/smtp[2783]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.26]:25: Connection timed out
Dec 13 12:46:04 localhost postfix/smtp[2783]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.27]:25: Connection timed out
Dec 13 12:46:34 localhost postfix/smtp[2783]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.27]:25: Connection timed out
Dec 13 12:47:04 localhost postfix/smtp[2783]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out
Dec 13 12:47:04 localhost postfix/smtp[2783]: 762D641B97: to=<matroosenklus@gmail.com>, relay=none, delay=3312, delays=3161/0.05/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out)
Dec 13 12:48:18 localhost postfix/smtpd[2845]: connect from localhost[127.0.0.1]
Dec 13 12:49:49 localhost postfix/smtpd[2845]: 59A4641B96: client=localhost[127.0.0.1]
Dec 13 12:50:24 localhost postfix/cleanup[2849]: 59A4641B96: message-id=<20191213124949.59A4641B96@Bert-server1.fritz.box>
Dec 13 12:50:24 localhost postfix/qmgr[2670]: 59A4641B96: from=<bert@bootsmaat.nl>, size=352, nrcpt=1 (queue active)
Dec 13 12:50:55 localhost postfix/smtp[2850]: connect to gmail-smtp-in.l.google.com[173.194.79.26]:25: Connection timed out
Dec 13 12:51:25 localhost postfix/smtp[2850]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.26]:25: Connection timed out
Dec 13 12:51:55 localhost postfix/smtp[2850]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.27]:25: Connection timed out
Dec 13 12:52:25 localhost postfix/smtpd[2845]: timeout after END-OF-MESSAGE from localhost[127.0.0.1]
Dec 13 12:52:25 localhost postfix/smtpd[2845]: disconnect from localhost[127.0.0.1] ehlo=1 mail=1 rcpt=1 data=1 commands=4
Dec 13 12:52:25 localhost postfix/smtp[2850]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.26]:25: Connection timed out
Dec 13 12:52:55 localhost postfix/smtp[2850]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out
Dec 13 12:52:55 localhost postfix/smtp[2850]: 59A4641B96: to=<bertje.knor@gmail.com>, relay=none, delay=245, delays=95/0.04/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out)
Dec 13 12:59:33 localhost postfix/qmgr[2670]: 59A4641B96: from=<bert@bootsmaat.nl>, size=352, nrcpt=1 (queue active)
Dec 13 13:00:03 localhost postfix/smtp[2861]: connect to gmail-smtp-in.l.google.com[108.177.126.27]:25: Connection timed out
Dec 13 13:00:33 localhost postfix/smtp[2861]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.27]:25: Connection timed out
Dec 13 13:01:03 localhost postfix/smtp[2861]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.26]:25: Connection timed out
Dec 13 13:01:33 localhost postfix/smtp[2861]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.26]:25: Connection timed out
Dec 13 13:02:03 localhost postfix/smtp[2861]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out
Dec 13 13:02:03 localhost postfix/smtp[2861]: 59A4641B96: to=<bertje.knor@gmail.com>, relay=none, delay=793, delays=643/0.06/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out)
Dec 13 13:06:52 localhost postfix/smtpd[2899]: connect from localhost[127.0.0.1]
Dec 13 13:08:04 localhost postfix/smtpd[2899]: E7D2B41B98: client=localhost[127.0.0.1]
Dec 13 13:08:42 localhost postfix/cleanup[2902]: E7D2B41B98: message-id=<20191213130804.E7D2B41B98@Bert-server1.fritz.box>
Dec 13 13:08:42 localhost postfix/qmgr[2670]: E7D2B41B98: from=<bert@bootsmaat.nl>, size=354, nrcpt=1 (queue active)
Dec 13 13:09:13 localhost postfix/smtp[2905]: connect to gmail-smtp-in.l.google.com[108.177.119.26]:25: Connection timed out
Dec 13 13:09:25 localhost postfix/smtpd[2899]: disconnect from localhost[127.0.0.1] ehlo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
Dec 13 13:09:43 localhost postfix/smtp[2905]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.26]:25: Connection timed out
Dec 13 13:10:13 localhost postfix/smtp[2905]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.26]:25: Connection timed out
Dec 13 13:10:43 localhost postfix/smtp[2905]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.26]:25: Connection timed out
Dec 13 13:11:13 localhost postfix/smtp[2905]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out
Dec 13 13:11:13 localhost postfix/smtp[2905]: E7D2B41B98: to=<bertje.knor@gmail.com>, relay=none, delay=233, delays=83/0.04/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out)
Dec 13 13:14:33 localhost postfix/qmgr[2670]: 59A4641B96: from=<bert@bootsmaat.nl>, size=352, nrcpt=1 (queue active)
Dec 13 13:15:03 localhost postfix/smtp[2963]: connect to gmail-smtp-in.l.google.com[108.177.127.27]:25: Connection timed out
Dec 13 13:15:33 localhost postfix/smtp[2963]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.26]:25: Connection timed out
Dec 13 13:16:03 localhost postfix/smtp[2963]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.26]:25: Connection timed out
Dec 13 13:16:33 localhost postfix/smtp[2963]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.26]:25: Connection timed out
Dec 13 13:17:03 localhost postfix/smtp[2963]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out
Dec 13 13:17:03 localhost postfix/smtp[2963]: 59A4641B96: to=<bertje.knor@gmail.com>, relay=none, delay=1694, delays=1543/0.06/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out)
Dec 13 13:19:33 localhost postfix/qmgr[2670]: E7D2B41B98: from=<bert@bootsmaat.nl>, size=354, nrcpt=1 (queue active)
Dec 13 13:20:03 localhost postfix/smtp[2971]: connect to gmail-smtp-in.l.google.com[108.177.127.26]:25: Connection timed out
Dec 13 13:20:33 localhost postfix/smtp[2971]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.27]:25: Connection timed out
Dec 13 13:21:03 localhost postfix/smtp[2971]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.27]:25: Connection timed out
Dec 13 13:21:33 localhost postfix/smtp[2971]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.26]:25: Connection timed out
Dec 13 13:22:04 localhost postfix/smtp[2971]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out
Dec 13 13:22:04 localhost postfix/smtp[2971]: E7D2B41B98: to=<bertje.knor@gmail.com>, relay=none, delay=884, delays=734/0.06/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out)
```

**the last part of my syslog :**
```
Dec 13 13:00:33 localhost postfix/smtp[2861]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.27]:25: Connection timed out
Dec 13 13:01:03 localhost postfix/smtp[2861]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.26]:25: Connection timed out
Dec 13 13:01:33 localhost postfix/smtp[2861]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.26]:25: Connection timed out
Dec 13 13:02:03 localhost postfix/smtp[2861]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out
Dec 13 13:02:03 localhost postfix/smtp[2861]: 59A4641B96: to=<bertje.knor@gmail.com>, relay=none, delay=793, delays=643/0.06/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out)
Dec 13 13:02:28 localhost kernel: [ 9844.536479] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=6675 DF PROTO=2 
Dec 13 13:04:33 localhost kernel: [ 9969.535483] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=34286 DF PROTO=2 
Dec 13 13:06:38 localhost kernel: [10094.534761] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=47510 DF PROTO=2 
Dec 13 13:06:52 localhost postfix/smtpd[2899]: connect from localhost[127.0.0.1]
Dec 13 13:08:04 localhost postfix/smtpd[2899]: E7D2B41B98: client=localhost[127.0.0.1]
Dec 13 13:08:42 localhost postfix/cleanup[2902]: E7D2B41B98: message-id=<20191213130804.E7D2B41B98@Bert-server1.fritz.box>
Dec 13 13:08:42 localhost postfix/qmgr[2670]: E7D2B41B98: from=<bert@bootsmaat.nl>, size=354, nrcpt=1 (queue active)
Dec 13 13:08:43 localhost kernel: [10219.533896] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=52671 DF PROTO=2 
Dec 13 13:09:01 localhost CRON[2907]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Dec 13 13:09:02 localhost systemd[1]: Starting Clean php session files...
Dec 13 13:09:02 localhost systemd[1]: Started Clean php session files.
Dec 13 13:09:13 localhost postfix/smtp[2905]: connect to gmail-smtp-in.l.google.com[108.177.119.26]:25: Connection timed out
Dec 13 13:09:25 localhost postfix/smtpd[2899]: disconnect from localhost[127.0.0.1] ehlo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
Dec 13 13:09:43 localhost postfix/smtp[2905]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.26]:25: Connection timed out
Dec 13 13:10:13 localhost postfix/smtp[2905]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.26]:25: Connection timed out
Dec 13 13:10:43 localhost postfix/smtp[2905]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.26]:25: Connection timed out
Dec 13 13:10:48 localhost kernel: [10344.533051] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=57512 DF PROTO=2 
Dec 13 13:11:13 localhost postfix/smtp[2905]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out
Dec 13 13:11:13 localhost postfix/smtp[2905]: E7D2B41B98: to=<bertje.knor@gmail.com>, relay=none, delay=233, delays=83/0.04/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.26]:25: Connection timed out)
Dec 13 13:12:53 localhost kernel: [10469.532326] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=21933 DF PROTO=2 
Dec 13 13:14:33 localhost postfix/qmgr[2670]: 59A4641B96: from=<bert@bootsmaat.nl>, size=352, nrcpt=1 (queue active)
Dec 13 13:14:58 localhost kernel: [10594.531109] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=22476 DF PROTO=2 
Dec 13 13:15:03 localhost postfix/smtp[2963]: connect to gmail-smtp-in.l.google.com[108.177.127.27]:25: Connection timed out
Dec 13 13:15:33 localhost postfix/smtp[2963]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.26]:25: Connection timed out
Dec 13 13:16:03 localhost postfix/smtp[2963]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.26]:25: Connection timed out
Dec 13 13:16:33 localhost postfix/smtp[2963]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.26]:25: Connection timed out
Dec 13 13:17:01 localhost CRON[2966]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 13 13:17:03 localhost kernel: [10719.530059] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=40434 DF PROTO=2 
Dec 13 13:17:03 localhost postfix/smtp[2963]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out
Dec 13 13:17:03 localhost postfix/smtp[2963]: 59A4641B96: to=<bertje.knor@gmail.com>, relay=none, delay=1694, delays=1543/0.06/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out)
Dec 13 13:19:08 localhost kernel: [10844.529059] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=49731 DF PROTO=2 
Dec 13 13:19:33 localhost postfix/qmgr[2670]: E7D2B41B98: from=<bert@bootsmaat.nl>, size=354, nrcpt=1 (queue active)
Dec 13 13:20:03 localhost postfix/smtp[2971]: connect to gmail-smtp-in.l.google.com[108.177.127.26]:25: Connection timed out
Dec 13 13:20:33 localhost postfix/smtp[2971]: connect to alt1.gmail-smtp-in.l.google.com[172.253.118.27]:25: Connection timed out
Dec 13 13:21:03 localhost postfix/smtp[2971]: connect to alt2.gmail-smtp-in.l.google.com[64.233.189.27]:25: Connection timed out
Dec 13 13:21:13 localhost kernel: [10969.528251] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=54212 DF PROTO=2 
Dec 13 13:21:33 localhost postfix/smtp[2971]: connect to alt3.gmail-smtp-in.l.google.com[173.194.202.26]:25: Connection timed out
Dec 13 13:22:04 localhost postfix/smtp[2971]: connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out
Dec 13 13:22:04 localhost postfix/smtp[2971]: E7D2B41B98: to=<bertje.knor@gmail.com>, relay=none, delay=884, delays=734/0.06/150/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[108.177.9.27]:25: Connection timed out)
Dec 13 13:23:18 localhost kernel: [11094.527332] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=6178 DF PROTO=2 
Dec 13 13:25:23 localhost kernel: [11219.525833] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=14052 DF PROTO=2 
Dec 13 13:27:28 localhost kernel: [11344.524209] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=38447 DF PROTO=2 
Dec 13 13:29:33 localhost kernel: [11469.523557] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=51630 DF PROTO=2 
Dec 13 13:31:38 localhost kernel: [11594.522846] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=1150 DF PROTO=2 
Dec 13 13:33:43 localhost kernel: [11719.521392] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=22394 DF PROTO=2 
Dec 13 13:35:48 localhost kernel: [11844.520655] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=30379 DF PROTO=2 
Dec 13 13:36:51 localhost kernel: [11907.830973] [UFW BLOCK] IN=eth0 OUT= MAC=42:b7:32:51:e1:bd:dc:39:6f:15:9f:a6:08:00 SRC=71.6.233.36 DST=192.168.178.20 LEN=44 TOS=0x00 PREC=0x00 TTL=239 ID=54321 PROTO=TCP SPT=993 DPT=993 WINDOW=65535 RES=0x00 SYN URGP=0 
Dec 13 13:37:53 localhost kernel: [11969.519503] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:dc:39:6f:15:9f:a6:08:00 SRC=192.168.178.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=42052 DF PROTO=2 






```

---

### Post by SeijiSensei on 2019-12-13
Let's start with the basics. See if you can telnet to port 25 on gmail-smtp-in.l.google.com.

GMail is pretty fussy about which servers it will accept mail from. If you're on a residential connection, your mail may be rejected. Also you need to have correct DNS resolution for the server in the domain which you are using.  Other services like Yahoo are even more restrictive than GMail.

Sending mail is not a simple task these days because providers have to protect themselves against spam. (Spam constitutes over 90% of all mail and has for years now.) Things like whether you have both forward and reverse DNS resolution correctly configured, whether you have an SPF record in your domain's zone files, whether you use DKIM or DMARC, all of these affect whether your mail will go through. At least your IP address doesn't appear to be on any blacklists: [https://mxtoolbox.com/SuperTool.aspx?action=blacklist%3a80.101.160.57&run=toolpage](https://mxtoolbox.com/SuperTool.aspx?action=blacklist%3a80.101.160.57&run=toolpage).

---

### Post by bertm2 on 2019-12-14
seijisensei  thank you for responding.
for me this is a big learning exercise. I was really frustrated Yesterday and went to bed early.This  Morning I tried to telnet gmail-smtp-in.l.Google.com and failed. I disabled ufw firewall and  Try Again and faled Again. 
> $ sudo ufw disable                                                                                                                                                     
Firewall stopped and disabled on system startup                                                                                                                        
$ telnet gmail-smtp-in.l.google.com 25                                                                                                                                 
Trying 2a00:1450:4013:c01::1a...                                                                                                                                       
Trying 173.194.79.26...                                                                                                                                                
telnet: Unable to connect to remote host: Connection timed out                                                                                                         
$ sudo ufw enable


Next i checkout my router settings,I see no problems   there. 

 as of yet I don't know where it goes wrong.


I check The forward and reverse DNS resolution and I don't think that I've got a problem there. these are the results:
> IP address or host name:                                        **FCrDNS test result:**

80.101.160.57 resolved to a80-101-160-57.adsl.xs4all.nl;
a80-101-160-57.adsl.xs4all.nl resolved to 80.101.160.57; 
[COLOR=green]rDNS if forward confirmed.[/COLOR]
 **Generic PTR record test result:**
[COLOR=red]a80-101-160-57.adsl.xs4all.nl looks like generic.[/COLOR]
 
then I checked the spf Record in my DNS:
> bootsmaat.nl      txt       v=spf1 include:_spf.hostnet.nl -all

As far as I know I don't use DKIM OR DMARK. I don't now where to check this.


Next  thing I gonna do is calling my internet provider, and ask if they got any suggestions.
if you got any suggestions  i would be very thankful to you.

---

### Post by bertm2 on 2019-12-14
ok i made a little progress, changed some settings from mi internet provider. and i can telnet to google:

> $ telnet gmail-smtp-in.l.google.com 25
Trying 2a00:1450:4013:c05::1b...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP op12si2938765ejb.46 - gsmtp

but i still cant sent a email with telnet:
> $ telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 Bert-server1.fritz.box ESMTP Postfix (Ubuntu)
ehlo bootsmaat.nl
250-Bert-server1.fritz.box
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250-DSN
250 SMTPUTF8
mail from: bert
250 2.1.0 Ok
rcpt to: [EMAIL="bertje.knor@gmail.com"]bertje@gmail.com[/EMAIL]
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
subject: test8
wgedpjhqgedpjhqgwd
.
250 2.0.0 Ok: queued as 68A5241B95
421 4.4.2 Bert-server1.fritz.box Error: timeout exceeded
Connection closed by foreign host.

than i changed my spf in my dns to:
> v=spf1 a mx ip4:80.101.160.57 -all
and i have to wait a couple of hours to see if this changes something

and i found a DMARC rekort in mi dns:
> _dmarc.bootsmaat.nl   TXT   v=DMARC1; p=reject

i dont know if this spf is better then the old one, and the DMARC record is the standard record you get when you buy a domain name with hostnet.nl 
if you can advise me how to proceed would be great. have a nice day, greetings bert

---

### Post by SeijiSensei on 2019-12-14
Mail from "bert" will not be accepted. It needs to be a complete address.

More significantly, I find this when I look up your hostname and address:

```

# host bert-server1.fritz.box
Host bert-server1.fritz.box not found: 3(NXDOMAIN)
# host 80.101.160.57
57.160.101.80.in-addr.arpa domain name pointer a80-101-160-57.adsl.xs4all.nl.

```

The server needs to have a fully-qualified domain name in a real domain. For best results the reverse lookup for 80.101.160.57 needs to return the same hostname.

---

### Post by bertm2 on 2019-12-14
sorry i diddent read your last reply.

Okay again I made some progress.I Changed:
> $myhostname =80-101-160-57.adsl.xs4all.nl, in [main.cf]("http://main.cf") so mxtools banner check gave an green light 

And my _DMARC to v=DMARC1; p = none; rua=mailto:[EMAIL="bertje.knor@gmail.com"]bertje.knor@gmail.com[/EMAIL], and  tried again . with mail from: [EMAIL="bert@bootsmaat.nl"]bert@bootsmaat.nl[/EMAIL]
 this time it worked and my mail arrived In  my mailbox.
But mxtoolbox  said that the last part was incorrect(rua=malto......), so i deleted it from my DMARC.

And tried to mail Myself Again,  and this time it didn't work.
I tried several combinations and Sometimes it arrived in my spambox, or It didn't arrive, or it arrived in my inbox.

The Last Time It arrived In My inbox I didn't Change Anything And Try Again, to no avail.

And Now I'm seriously Lost
if you can advise me how to proceed would be great. have a nice day, greetings bert

---

### Post by bertm2 on 2019-12-14
the last couple of times i dit it like this:
> $ telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 80-101-160-57.adsl.xs4all.nl ESMTP Postfix (Ubuntu)
ehlo bootsmaat.nl
250-80-101-160-57.adsl.xs4all.nl
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250-DSN
250 SMTPUTF8
mail from: [email]bert@bootsmaat.nl[/email]
250 2.1.0 Ok
rcpt to: [email]bertje.knor@gmail.com[/email]
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
subject:test28
ik hoop dat het werkt
.
250 2.0.0 Ok: queued as 654AC41B95
some times it workt,but most of the times it didn&#8217;t work

---

### Post by SeijiSensei on 2019-12-14
Looks like that worked; did you get the message at GMail? 

Any chance you can get xs4all to create a reverse DNS record for your IP that points to bootsmaat.nl rather than 80-101-160-57.adsl.xs4all.nl?

What if you send from [email]bert@80-101-160-57.adsl.xs4all.nl[/email] and use "ehlo 80-101-160-57.adsl.xs4all.nl"?

---

### Post by bertm2 on 2019-12-14
this one arrived in my spam folder

> $ telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 80-101-160-57.adsl.xs4all.nl ESMTP Postfix (Ubuntu)
ehlo bootsmaat.nl
250-80-101-160-57.adsl.xs4all.nl
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250-DSN
250 SMTPUTF8
mail from: [EMAIL="bert@bootsmaat.nl"]bert@bootsmaat.nl[/EMAIL]
250 2.1.0 Ok
rcpt to: [EMAIL="bertje.knor@gmail.com"]bertje.knor@gmail.com[/EMAIL]
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
subject: test31
ik hoop weer dat het lukt
.
250 2.0.0 Ok: queued as ABE8941B95

---

### Post by bertm2 on 2019-12-14
this one arived in my inbox
> 250 2.0.0 Ok: queued as ABE8941B95
421 4.4.2 80-101-160-57.adsl.xs4all.nl Error: timeout exceeded
Connection closed by foreign host.
$ telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 80-101-160-57.adsl.xs4all.nl ESMTP Postfix (Ubuntu)
ehlo 80-101-160-57.adsl.xs4all.nl
250-80-101-160-57.adsl.xs4all.nl
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250-DSN
250 SMTPUTF8
mail from: [email]bert@80-101-160-57.adsl.xs4all.nl[/email]
250 2.1.0 Ok
rcpt to: [email]bertje.knor@gmail.com[/email]
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
subject: test31
bla bla bla
.
250 2.0.0 Ok: queued as 8FAEC41B95
wait a munite im gona try again

---

### Post by bertm2 on 2019-12-14
Yay it worked, first time it workt 2 times after each other
 can't I put 80-101-160-57.adsl.xs4all.nl in my A record off My DNS, 
would that work?
i dont know if i can get xs4all to create a reverse DNS record for my IP that points to bootsmaat.nl.
i wil ask them tomorrow, because they're closed now
thank you seijisensei you are the hero of my day

---

### Post by SeijiSensei on 2019-12-16
How about:

```

@     IN     A     80.101.160.57

      IN     TXT   "v=spf1 a:bootsmaat.net a:80.101.160.57 ~all"

```

Not having the forward and reverse lookups match will count against you when it comes to determining spam. Here are the DNS entries for one of my domains:

```

$ host -t mx cyways.com
cyways.com mail is handled by 0 mail.cyways.com.

$ host mail.cyways.com
mail.cyways.com has address 50.116.11.117

$ host -t ptr 50.116.11.117
117.11.116.50.in-addr.arpa domain name pointer mail.cyways.com.

$ host -t txt cyways.com
cyways.com descriptive text "v=spf1 a:smtp.cyways.com a:mail.cyways.com a:cyways.cyways.com ~all"

```

I also have a DKIM "domainkey" in another TXT record.

---

### Post by bertm2 on 2019-12-19
For not replying a couple of Days I Had to go work , I am a Sailor on an old Sail barge so no internet.First I Made The Change You suggested
>  "v=spf1 a:bootsmaat.net a:80.101.160.57 ~all"


Then I Change It into what I  thought you suggested, not [bootsmaat.net]("http://bootsmaat.net") but [bootsmaat.nl]("http://bootsmaat.nl") , and no ""
> v=spf1 a:bootsmaat.nl a:80.101.160.57 ~al
thank you seijisensei

 The First Time I tried to mail ass [EMAIL="bert@bootsmaat.nl"]bert@bootsmaat.nl[/EMAIL], it worked. The second Time I didn't work so It's Still intermittent.
 When I tried on spf record made by MX tools namely:

>  v=spf1 a:bootsmaat.nl a:mx ip4:80.101.160.57 ~all
and i changed my main.conf ,> myhostname=80.101.160.57.xs4all.adsl.nl to > myhostname=bootsman.nl
and now it seem to work consistently
thank you seijisensei i will let you no how it works out in the log term.
greetings bert

---

### Post by bertm2 on 2019-12-30
i gave it  up for the moment things still doesn't work some times.
i have learned a lot and it is like van gaal would say "a totally different cookie "(dutch proverb ). and call it a successful failure.
thank you seijisensei for all your help.
when I'm gonna try again i hope i can call on you again.
greetings bert

---

