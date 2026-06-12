---
title: "sasl2 doesn't connect to mysql"
date: 2007-07-31
forum: Server Platforms
---

### Post by gert cuykens on 2007-07-31
```
root@www:/etc/postfix# postconf -n
config_directory = /etc/postfix
disable_dns_lookups = yes
home_mailbox = mailbox
local_recipient_maps = mysql:/etc/postfix/recipients.cf
mailbox_transport = dbmail-lmtp:localhost:24
mydestination = $mydomain
mydomain = lan
myhostname = www.lan
mynetworks = 127.0.0.1/32
myorigin = $mydomain
relay_domains =
smtpd_recipient_restrictions = permit_sasl_authenticated, reject
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_security_level = may
root@www:/etc/postfix#
```

```
root@www:/etc/postfix# cat sasl/smtpd.conf
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5 ntlm
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: dbmail
sql_passwd: dbmail
sql_database: dbmail
sql_select: SELECT passwd FROM dbmail_users WHERE userid = '%u'
log_level: 7
root@www:/etc/postfix#
```

---

