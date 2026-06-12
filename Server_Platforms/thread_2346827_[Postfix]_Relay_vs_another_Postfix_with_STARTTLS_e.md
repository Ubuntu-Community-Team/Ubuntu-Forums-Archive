---
title: "[Postfix] Relay vs another Postfix with STARTTLS enable"
date: 2016-12-19
forum: Server Platforms
---

### Post by pres961 on 2016-12-19
Hi,
I need your help to finish my idea about this problem.
I have a mail server with Postfix (mx1). My Postfix is configurated to accept only STARTTLS mail transaction. When I try to send mails it works correctly.
When I send a mail from another server (www1) with Postfix configurated to relay to mx1, I receive:
```
Dec 19 10:36:07 ubntu16 postfix/smtp[13319]: 738A66310A: to=<cberti@officinedigitali.it>, relay=mailone.ovh-private.od.loc[192.168.20.5]:587, delay=0.04, delays=0.02/0/0.02/0,
dsn=5.7.0, status=bounced (host mailone.ovh-private.od.loc[192.168.20.5] said: 530 5.7.0 Must issue a STARTTLS command first (in reply to MAIL FROM command))

```
This is my main.cf at mx1
```
# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
#smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_tls_security_level = may
smtpd_tls_cert_file = /etc/postfix/ssl/postfix.crt
smtpd_tls_key_file = /etc/postfix/ssl/postfix.key
smtpd_tls_auth_only = yes
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
# enable opportunistic TLS support in the SMTP server and client
smtp_tls_security_level = may
smtpd_tls_auth_only = yes

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = mx1.odcloud.it
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = odcloud.it, mailone.ovh-private.od.loc, localhost.ovh-private.od.loc, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces =  192.168.20.5, localhost
smtpd_milters           = inet:127.0.0.1:8891
non_smtpd_milters       = $smtpd_milters
milter_default_action   = accept
milter_protocol         = 2

```
and this is my master.cf
```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master" or
# on-line: http://www.postfix.org/master.5.html).
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
submission inet n       -       -       -       -       smtpd
  -o syslog_name=postfix/submission
  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    unix  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
#qmgr     unix  n       -       n       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5

```
Can you help me?

---

### Post by pres961 on 2016-12-21
No one has any idea how to fix this?

---

### Post by pres961 on 2016-12-29
Has anybody had the same problem?

---

### Post by SeijiSensei on 2016-12-29
Is there some policy reason you are only accepting TLS?  Most mail servers will use TLS if it's an option on both ends and default to plain text if not.  

You could run another instance of Postfix on a different port and permit only your relay to connect to it.  Or you could set up an OpenVPN tunnel between the two machines and have the relay use that.  

Running a server that only accepts TLS contravenes the standards for mail exchange. From [RFC 3207]("https://tools.ietf.org/html/rfc3207"):

> A publicly-referenced SMTP server MUST NOT require use of the STARTTLS extension in order to deliver mail locally.  This rule prevents the STARTTLS extension from damaging the interoperability of the Internet's SMTP infrastructure.  A publicly-referenced SMTP server is an SMTP server which runs on port 25 of an Internet host listed in the MX record (or A record if an MX record is not present) for the domain name on the right hand side of an Internet mail address.

---

### Post by pres961 on 2017-01-02
Thank you SeijiSensei to reply.
MX1 is my public MX server. This server isn't a relay.
This server accept only TLS because if I send mail without STARTTLS, mail mark as SPAM.
It's a best practice or not?
Thanks

---

### Post by SeijiSensei on 2017-01-02
No, it violates standards. Did you read the RFC I linked to? Or the paragraph I quoted?

There are a great many ways to deal with spam. I use MailScanner which uses SpamAssassin at the SMTP level. It's also possible to handle this at the delivery level by passing the message to spamd, the daemonized version of SpamAssassin, through a procmail recipe. I also refuse mail from servers in some of the new top-level domains like .link and .download which are almost always spam.

There are many anti-spam solutions available that don't require TLS-only. Most of them involve SpamAssassin so I'd start there: [http://spamassassin.apache.org/](http://spamassassin.apache.org/).

Wait, are you talking about an **outbound** server? If you're outbound mail is marked as spam, your server likely has a bad "reputation." Go to mxtoolbox.com and check to see if you're in any of the blacklists. Also run the test to make sure you're not an "open relay."

---

### Post by pres961 on 2017-01-05
Hi SeijiSensei,
Yes, I'm talking about an outbound server. For example, when I try to send an email to my personal gmail account, mail mark as spam. If I check, for example in mxtoolbox.com, my outbound server, didn't have bad reputation and didn't mark as open relay.
In my case there isn't install spamassasin.
You know if there are some manual about mail server configuration?
Thanks

---

### Post by SeijiSensei on 2017-01-05
Send some tests to other places besides gmail. They have some fairly stringent rules that generate false positives.

SpamAssassin won't help with this. It's designed to filter incoming mail.

Do you have an [SPF](http://www.openspf.org) record for this server? If not, you should add one to the DNS records for those domains for which this is a valid sending server.

---

