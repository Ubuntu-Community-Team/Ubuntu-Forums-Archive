---
title: "SASL Crypt support"
date: 2007-03-21
forum: Server Platforms
---

### Post by stickboy2642 on 2007-03-21
I set up postfix, sasl and mysql support on an Edgy installation, and I am having problems with SASL authentication.  When I try to authenticate with my encrypted password that is stored in the database, authentication fails.  If I add in another field to my mailbox table that contains the password in clear text, SASL will authenticate.  Courier-imap authenticates against the encrypted password just fine, and I can receive mail.  But if I do not have the non-encrypted field for SASL to authenticate against, I am not able to send mail.  From googling around, I have seen a few poeple mention a lack of crypt support in SASL without installing a patch.  Is this still an issue?

I have attached my smtpd.conf file for inspection.  


```
# /etc/postfix/sasl/smtpd.conf:

pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: PLAIN LOGIN CRYPT CRAM-MD5 DIGEST-MD5
password_format: crypt
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_database: postfix
sql_user: mail
sql_passwd: password
sql_select: SELECT password FROM mailbox WHERE username='%u@%r' AND active = '1'

```

```
# /etc/postfix/main.cf (SASL and TLS relevant parts)

smtpd_sender_restrictions =
        permit_sasl_authenticated,
        permit_mynetworks,
        reject_unauth_pipelining,
        permit

smtpd_recipient_restrictions =
   permit_sasl_authenticated,
   permit_mynetworks,
   reject_non_fqdn_recipient,
   reject_unknown_recipient_domain,
   reject_unauth_pipelining,
   reject_unauth_destination

mynetworks = 127.0.0.0/8, 172.20.0.0/22, 172.21.0.0/16, 204.13.255.0/24
local_recipient_maps =

smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_local_domain =

smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_data_restrictions = reject_unauth_pipelining

```


Any suggestions would be greatly appreciated.

---

