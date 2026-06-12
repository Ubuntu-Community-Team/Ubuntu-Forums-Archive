---
title: "Ubuntu Mail Server (10.10) can't receive e-mail"
date: 2011-02-08
forum: Server Platforms
---

### Post by blasto333 on 2011-02-08
For some reason I cannpt receive e-mail on my account [email]chrismuench@poweranew.com[/email]. There is a mail folder (/home/chrismuench/mail), but the message never gets delivered..(I don't get a response back from the server that the account doesn't exist)

Here is my /var/log/email.log (The part that matters)

```

Feb  8 22:06:25 ip-10-112-42-106 postfix/smtpd[8033]: connect from asmtpout029.mac.com[17.148.16.104]
Feb  8 22:06:25 ip-10-112-42-106 postfix/smtpd[8033]: D11D441657: client=asmtpout029.mac.com[17.148.16.104]
Feb  8 22:06:25 ip-10-112-42-106 postfix/cleanup[8037]: D11D441657: message-id=<6863F7A8-AA9F-4701-8314-3B9CFC510F30@me.com>
Feb  8 22:06:25 ip-10-112-42-106 postfix/qmgr[7863]: D11D441657: from=<cmuench@me.com>, size=1197, nrcpt=1 (queue active)
Feb  8 22:06:25 ip-10-112-42-106 postfix/local[8038]: D11D441657: to=<chrismuench@poweranew.com>, relay=local, delay=0.1, delays=0.09/0.01/0/0.01, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Feb  8 22:06:25 ip-10-112-42-106 postfix/qmgr[7863]: D11D441657: removed
Feb  8 22:06:26 ip-10-112-42-106 postfix/smtpd[8033]: disconnect from asmtpout029.mac.com[17.148.16.104]


```
Here is my postfix configuration file: (/etc/postfix/main/cf)

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

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/postfix.pem
smtpd_tls_key_file = /etc/ssl/postfix.key
smtpd_sasl_application_name=smtpd
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.poweranew.com
virtual_alias_maps = hash:/etc/postfix/virtual
home_mailbox = mail/
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = poweranew.com, ip-10-112-42-106.ec2.internal, localhost.ec2.internal, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
inet_protocols = ipv4
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

Any ideas/things to check?

---

### Post by weblizist on 2011-02-11
You deliver your e-mail to procmail. You should check your procmail log - or if logging not enabled you should enable it.
I assume it has been delivered to a place, where you wouldn't expect it to be ;-)

---

