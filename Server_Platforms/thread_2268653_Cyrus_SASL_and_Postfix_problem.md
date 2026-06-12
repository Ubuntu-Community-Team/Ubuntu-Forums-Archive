---
title: "Cyrus SASL and Postfix problem"
date: 2015-03-10
forum: Server Platforms
---

### Post by mehmet6 on 2015-03-10
Hello guys,
i have some troubles with installing Cyrus sasl and postfix. netcat domain 143 ok but when i try t&#305; login smtp i get error. 
```
netcat mail.domain.com 25
```

AUTH LOGIN
MMIME::Base64 username
MMIME::BASE64 password


[COLOR=#b22222]Mar 10 16:46:20 Ubuntu-1410-utopic-64-minimal postfix/smtpd[8132]: warning: localhost.localdomain[127.0.0.1]: SASL LOGIN authentication failed: authentication failure
Mar 10 16:46:20 Ubuntu-1410-utopic-64-minimal postfix/smtpd[8132]: > localhost.localdomain[127.0.0.1]: 535 5.7.8 Error: authentication failed: authentication failure
Mar 10 16:46:20 Ubuntu-1410-utopic-64-minimal postfix/smtpd[8132]: watchdog_pat: 0x7f6d9a10d910[/COLOR]

Here are my configs. 

main.cf
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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = mail.claksy.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = Ubuntu-1410-utopic-64-minimal, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8, 192.168.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
## sasl settings
smtpd_sasl_authenticated_header = yes


# Use Dovecot's SASL interface.
#smtpd_sasl_auth_enable = yes
#smtpd_sasl_type = dovecot
smtpd_sasl_path = sasl/smtpd
#queue_directory = /etc/postfix
##
#smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
#broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_security_options = noanonymous
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
# Virtual mailbox configuration
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_mailbox_limit = 51200000
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_transport = virtual


smtp_sasl_mechanism_filter = login plain
debug_peer_level = 2

debug_peer_list = 127.0.0.1
```

smtpd.conf
```

pwcheck_method: saslauthdmech_list: plain login
log_level: 15
allow_plaintext: true
#auxprop_plugin: mysql
auxprop_plugin: sql
sql_engine: mysql
sql_hostnames: localhost
sql_user: postfix
sql_passw: "password#"

```


Pls help me. I am trying to work it for 2 days.

---

