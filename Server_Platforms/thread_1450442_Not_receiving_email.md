---
title: "Not receiving email"
date: 2010-04-09
forum: Server Platforms
---

### Post by fortune2008 on 2010-04-09
So far i've got everything working good up to this point i can't receive email nor send and everything is said to be working i even tested it online i'm using post fix here is my main.cf

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
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.chatalker.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.chatalker.com, localhost, localhost.localdomain, chatalker.com, triniwiz.com, trinivybz.com, tubeinn.com, lovebugg.net, wizgames.net, monsterads.net, wizdigg.info, seriousporn.info, referraltraffic.info, 
relayhost = 
mynetworks = 127.0.0.0/8, 192.168.10.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
## TLS Settings
#
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
#
## SASL Settings
# This is going in to THIS server
smtpd_sasl_auth_enable = yes
# We need this
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtpd_sasl_local_domain = $myhostname
smtp_sasl_security_options = noanonymous
#smtp_sasl_security_options =
smtp_sasl_tls_security_options = noanonymous
smtpd_sasl_application_name = smtpdhtml_directory = /usr/share/doc/postfix/html
inet_protocols = ipv4
virtual_alias_domains = 
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings

```

---

### Post by lisati on 2010-04-09
I just sent a couple of test messages from my email server to yours. If you look at your mail.log file there should be a couple entries relating to my test messages being bounced back.

---

### Post by fortune2008 on 2010-04-09
here is my mail queue 

```
[SIZE=1]12:26[/SIZE] [SIZE=1]root@mail.chatalker.com[/SIZE] [SIZE=1]support@seriousporn.info [/SIZE] [SIZE=1]945 bytes[/SIZE] [SIZE=1]mail transport unavailable[/SIZE]

[SIZE=1]01:35[/SIZE] [SIZE=1]MAILER-DAEMON[/SIZE] [SIZE=1]root@server-1 [/SIZE] [SIZE=1]2.61 kB[/SIZE] [SIZE=1]delivery temporarily suspended: Host or domain name not found. Name service error for name=server-1 type=A: Host not found, try again[/SIZE]
```

---

