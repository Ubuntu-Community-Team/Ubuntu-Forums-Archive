---
title: "Postfix Ubuntu Server 14.04 Some users Local Emails Only"
date: 2016-06-29
forum: Server Platforms
---

### Post by albert41 on 2016-06-29
Hi,
 I was wondering if someone has accomplish what im trying to do? 

 So I have been working with postfix Email server for a while seems to  be running great, I wanted to implement that some users can only send  to thier domain (internal emails only) but cannot send outside or  certain domains but for the sake of it only internal emails
 I have been trying to follow this guide  

 [http://postfix.1071664.n5.nabble.com/How-can-I-restrict-some-specific-users-from-sending-email-to-ex...]("http://postfix.1071664.n5.nabble.com/How-can-I-restrict-some-specific-users-from-sending-email-to-external-domains-td58385.html")
  But i keep getting some undefined warning on postfix which im not sure 
 This is my main.cf

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
smtpd_tls_cert_file = /etc/ssl/certs/server.crt
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = mail.domain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = domain.com, mail.domain.com, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.3.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_restriction_classes =  check_recipient_access hash:/etc/postfix/internal_domains reject 
smtpd_recipient_restrictions = check_sender_access hash:/etc/postfix/internal_senders,permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
sender_bcc_maps = hash:/etc/postfix/sender_bcc
recipient_bcc_maps = hash:/etc/postfix/recipient_bcc
virtual_alias_maps = hash:/etc/postfix/vmaps
milter_default_action = accept
milter_protocol = 2
smtpd_milters = inet:localhost:8891
non_smtpd_milters = inet:localhost:8891



```

i also postmap to create the DB see pictures

Thank you

[http://postimg.org/gallery/2dxb135tk/](http://postimg.org/gallery/2dxb135tk/)

---

### Post by albert41 on 2016-07-01
EDIT: So Now its not showing any erros and it works ONLY on squirrel Mail but if i use outlook it ignores the smtp not sure why?

  New Main.cf

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
smtpd_tls_cert_file = /etc/ssl/certs/server.crt
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = mail.telsatco.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = telsatco.com, mail.telsatco.com, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.3.0/24 192.168.3.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = check_sender_access hash:/etc/postfix/restricted_senders, permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_restriction_classes = local_only
local_only = check_recipient_access hash:/etc/postfix/local_domains, reject
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
sender_bcc_maps = hash:/etc/postfix/sender_bcc
recipient_bcc_maps = hash:/etc/postfix/recipient_bcc
virtual_alias_maps = hash:/etc/postfix/vmaps
milter_default_action = accept
milter_protocol = 2
smtpd_milters = inet:localhost:8891
non_smtpd_milters = inet:localhost:8891


```

[http://postimg.org/gallery/2veisr4bm/](http://postimg.org/gallery/2veisr4bm/)

---

