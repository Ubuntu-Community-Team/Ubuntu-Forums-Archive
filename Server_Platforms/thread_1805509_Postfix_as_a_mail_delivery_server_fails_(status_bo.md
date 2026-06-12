---
title: "Postfix as a mail delivery server fails (status bounced loops back to myself)"
date: 2011-07-16
forum: Server Platforms
---

### Post by apollothethird on 2011-07-16
I'm trying to configure my Postfix server as a delivery agent for the server.  From studying the Postfix documentation it appears that the feature for this is virtual_alias_domains and virtual_alias_maps.

I created a virtual hash file.  No matter what I do with the virtual access the system will interpret the address as local and send the email to the local system, not the specified domain.  I know that the Postfix server can find the domain because a mail test with the virtual setup removed will send the mail to the proper machine.

/etc/postfix/main.cf:
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
# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
myhostname = ubunserver.apollo3.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ubunserver.apollo3.com, localhost.apollo3.com, , localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

# ----------- Virtual Block ----------------------------
virtual_alias_domains = apollo3.com
virtual_alias_maps = hash:/etc/postfix/virtual
# ------------------------------------------------

```I tried these /etc/postfix/virtual.db files:

```

apollo3.com        ignore_this_line
ljames@apollo3.com    ljames@apollo3.com

```mailtest:
```

echo "test" | mail -s "test subject" ljames@apollo3.com

```/var/log/mail.log:
```

Jul 15 17:15:10 ubuntuserver postfix/pickup[10001]: 23D2FDFC6D: uid=1002 from=<ljames>
Jul 15 17:15:10 ubuntuserver postfix/cleanup[10007]: 23D2FDFC6D: message-id=<20110715211510.23D2FDFC6D@ubunserver.apollo3.com>
Jul 15 17:15:10 ubuntuserver postfix/qmgr[10002]: 23D2FDFC6D: from=<ljames@ubuntuserver.apollo3.com>, size=337, nrcpt=1 (queue active)
Jul 15 17:15:10 ubuntuserver postfix/error[10009]: 23D2FDFC6D: to=<ljames@apollo3.com>, relay=none, delay=0.18, delays=0.1/0/0/0.07, dsn=5.0.0, status=bounced (User unknown in virtual alias table)
Jul 15 17:15:10 ubuntuserver postfix/cleanup[10007]: 471DEDFC81: message-id=<20110715211510.471DEDFC81@ubunserver.apollo3.com>
Jul 15 17:15:10 ubuntuserver postfix/qmgr[10002]: 471DEDFC81: from=<>, size=2183, nrcpt=1 (queue active)
Jul 15 17:15:10 ubuntuserver postfix/bounce[10011]: 23D2FDFC6D: sender non-delivery notification: 471DEDFC81
Jul 15 17:15:10 ubuntuserver postfix/qmgr[10002]: 23D2FDFC6D: removed
Jul 15 17:15:10 ubuntuserver postfix/smtp[10012]: 471DEDFC81: to=<ljames@ubuntuserver.apollo3.com>, relay=none, delay=0.08, delays=0.07/0/0/0, dsn=5.4.6, status=bounced (mail for ubuntuserver.apollo3.com loops back to myself)
Jul 15 17:15:10 ubuntuserver postfix/qmgr[10002]: 471DEDFC81: removed

```For some reason the system will turn the [EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL] to [EMAIL="ljames@ubuntuserver.apollo3.com"]ljames@ubuntuserver.apollo3.com[/EMAIL] and deliver the mail to itself rather than to the apollo3.com machine.

I also tried:
/etc/postfix/virtual.db:
```

apollo3.com        ignore_this_line
ljames@apollo3.com    ljames

```It still delivered the email to itself rather than the apollo3.com machine.

```

Jul 15 17:20:05 ubuntuserver postfix/pickup[10164]: 84324DFC6D: uid=1002 from=<ljames>
Jul 15 17:20:05 ubuntuserver postfix/cleanup[10173]: 84324DFC6D: message-id=<20110715212005.84324DFC6D@ubunserver.apollo3.com>
Jul 15 17:20:05 ubuntuserver postfix/qmgr[10165]: 84324DFC6D: from=<ljames@ubuntuserver.apollo3.com>, size=337, nrcpt=1 (queue active)
Jul 15 17:20:05 ubuntuserver postfix/smtp[10175]: 84324DFC6D: to=<ljames@ubuntuserver.apollo3.com>, orig_to=<ljames@apollo3.com>, relay=none, delay=0.15, delays=0.13/0.02/0/0, dsn=5.4.6, status=bounced (mail for ubuntuserver.apollo3.com loops back to myself)
Jul 15 17:20:05 ubuntuserver postfix/cleanup[10173]: B52D8DFC81: message-id=<20110715212005.B52D8DFC81@ubunserver.apollo3.com>
Jul 15 17:20:05 ubuntuserver postfix/qmgr[10165]: B52D8DFC81: from=<>, size=2342, nrcpt=1 (queue active)
Jul 15 17:20:05 ubuntuserver postfix/bounce[10177]: 84324DFC6D: sender non-delivery notification: B52D8DFC81
Jul 15 17:20:05 ubuntuserver postfix/qmgr[10165]: 84324DFC6D: removed
Jul 15 17:20:05 ubuntuserver postfix/smtp[10175]: B52D8DFC81: to=<ljames@ubuntuserver.apollo3.com>, relay=none, delay=0.1, delays=0.09/0/0/0, dsn=5.4.6, status=bounced (mail for ubuntuserver.apollo3.com loops back to myself)
Jul 15 17:20:05 ubuntuserver postfix/qmgr[10165]: B52D8DFC81: removed

```If I uncomment the virtual block from the main.cf file the system will deliver the mail to the proper place.  Of course it isn't using the virtual.db configuration.

/etc/postfix/main.cf
```

# ----------- Virtual Block ----------------------------
# virtual_alias_domains = apollo3.com
# virtual_alias_maps = hash:/etc/postfix/virtual
# ------------------------------------------------

```/var/log/mail.log
```

Jul 15 17:24:58 ubuntuserver postfix/master[10309]: daemon started -- version 2.8.2, configuration /etc/postfix
Jul 15 17:25:03 ubuntuserver postfix/pickup[10312]: A821BDFC6D: uid=1002 from=<ljames>
Jul 15 17:25:03 ubuntuserver postfix/cleanup[10321]: A821BDFC6D: message-id=<20110715212503.A821BDFC6D@ubunserver.apollo3.com>
Jul 15 17:25:03 ubuntuserver postfix/qmgr[10313]: A821BDFC6D: from=<ljames@ubuntuserver.apollo3.com>, size=337, nrcpt=1 (queue active)
Jul 15 17:25:06 ubuntuserver postfix/smtp[10323]: A821BDFC6D: to=<ljames@apollo3.com>, relay=mail.apollo3.com[216.153.132.70]:25, delay=2.4, delays=0.11/0.01/2.3/0.02, dsn=2.0.0, status=sent (250 2.0.0 p6FLP3u6006021 Message accepted for delivery)
Jul 15 17:25:06 ubuntuserver postfix/qmgr[10313]: A821BDFC6D: removed

```The postfix service was restarted between each configuration change.

I'm running the Ubuntu 11.04 server.  The postfix installation is from the distro repository.

Thanks in advance for anyone who has any insight one this.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

