---
title: "LDAP + Postfix + Dovecot"
date: 2011-05-14
forum: Server Platforms
---

### Post by kohdesmond on 2011-05-14
Hi guys,

anybody can show me how to set up a LDAP Postfix Dovecot server config ?

i have a running postfix dovecot server with smtp relaying server.

i have ldap installed in another server how does both of them communicate ?

any suggestion is appreciated

thanks 

desmond

---

### Post by kohdesmond on 2011-05-18
the postfix and dovecot is working for local users, but i still could not communicate to my ldap users. i'm not sure i is wrong please help.

desmond


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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = MailServer.bingo.inn650
alias_maps = hash:/etc/aliases,ldap:/etc/postfix/ldap_aliases.cf
smtpd_sender_login_maps = ldap:/etc/postfix/ldap_senders.cf


local_recipient_maps = ldap:/etc/postfix/ldap_users.cf
local_transport = virtual
virtual_mailbox_domains = $mydomain
virtual_mailbox_base = /home/vmail/
virtual_mailbox_maps = ldap:/etc/postfix/ldap_users.cf
virtual_uid_maps = static:1013
virtual_gid_maps = static:1013

myorigin = /etc/mailname
mydestination = MailServer.bingo.inn650,bingo.inn650,localhost.bingo.inn650,localhost
relayhost =
relay_domains =
mynetworks = 127.0.0.0/8 10.5.0.0/16 [2402:ec00:ffe5::]/48 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
html_directory = /usr/share/doc/postfix/html


ldap_bind_dn = cn=admin,dc=bingo,dc=inn650
ldap_bind_pw =secret
ldap_search_base = ou=people,dc=bingo,dc=inn650
ldap_domain = dc=bingo,dc=inn650
ldap_server_host = 10.5.3.7
ldap_server_port = 389
ldap_version = 3

---

