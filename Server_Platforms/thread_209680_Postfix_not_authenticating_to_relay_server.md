---
title: "Postfix not authenticating to relay server"
date: 2006-07-05
forum: Server Platforms
---

### Post by mexlinux on 2006-07-05
Hi:
I'm setting up an ubuntu mail server, using a dynamic IP, with no-ip.com and relaying certain mail throught their server with their smtp alternate port.

I can see from the log that transport is working but not the authentication, can some one plase take a look an tell me what can I have wrong??

This is what I see in /var/loga/mail.log
```

Jul  5 12:16:15 localhost postfix/smtpd[6255]: connect from unknown[172.16.1.169]
Jul  5 12:16:18 localhost postfix/smtpd[6255]: C3CBF108FA: client=unknown[172.16.1.169], sasl_method=PLAIN, sasl_username=mcanedo
Jul  5 12:16:18 localhost postfix/cleanup[6260]: C3CBF108FA: message-id=<200607051216.13367.user@server.com>
Jul  5 12:16:18 localhost postfix/qmgr[6247]: C3CBF108FA: from=<mcanedo@server.com>, size=692, nrcpt=1 (queue active)
Jul  5 12:16:18 localhost postfix/smtpd[6255]: disconnect from unknown[172.16.1.169]
Jul  5 12:16:23 localhost postfix/smtp[6261]: certificate verification failed for smtp-auth.no-ip.com: num=20:unable to get local issuer certificate
Jul  5 12:16:23 localhost postfix/smtp[6261]: certificate verification failed for smtp-auth.no-ip.com: num=27:certificate not trusted
Jul  5 12:16:24 localhost postfix/smtp[6261]: Server certificate could not be verified
Jul  5 12:16:25 localhost postfix/smtp[6261]: C3CBF108FA: to=<user@server.com>, relay=smtp-auth.no-ip.com[204.16.252.95], delay=7, status=bounced (host smtp-auth.no-ip.com[204.16.252.95] said: 554 <user@server.com>: Relay access denied (in reply to RCPT TO command))
Jul  5 12:16:25 localhost postfix/cleanup[6260]: 90045108FC: message-id=<20060705171625.90045108FC@server.com>
Jul  5 12:16:25 localhost postfix/qmgr[6247]: 90045108FC: from=<>, size=2501, nrcpt=1 (queue active)
Jul  5 12:16:25 localhost postfix/qmgr[6247]: C3CBF108FA: removed
Jul  5 12:16:33 localhost postfix/smtp[6261]: Server certificate could not be verified
Jul  5 12:16:34 localhost postfix/smtp[6261]: 90045108FC: to=<user@server.com>, relay=smtp-auth.no-ip.com[204.16.252.95], delay=9, status=bounced (host smtp-auth.no-ip.com[204.16.252.95] said: 554 <user@server.com>: Relay access denied (in reply to RCPT TO command))
Jul  5 12:16:35 localhost postfix/qmgr[6247]: 90045108FC: removed


```

This is my /et/postfix/main.cf
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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = grupogcm.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = grupogcm.com,  localhost.grupogcm.com, localhost
relayhost =
mynetworks = 127.0.0.0/8
# mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
#quite el noanonymouse a como esta en postfix.statoe-of-mind.de
#smtpd_sasl_security_options = noanonymous
smtpd_sasl_security_options =
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

#Mis cambios*****************************
#usar Maildir
home_mailbox = Maildir/

#Archivo con Contraseña para servidores relay (ej. no-ip)
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

#Indicar que vaya a buscarar el transporte elegido (como smtproutes en qmail)
transport_maps = hash:/etc/postfix/transport


```

This is my /etc/postfix/transport
```

domain-with-rbl.com    smtp:smtp-auth.no-ip.com:3325

```

This is my /etc/postfix/sasl_passwd
```

smtp-auth.no-ip.com:3325 mydomain.com@noip-smtp:mypass

```

---

