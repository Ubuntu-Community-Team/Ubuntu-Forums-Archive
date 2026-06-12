---
title: "postfix multiple instances on same server issue"
date: 2009-08-06
forum: Server Platforms
---

### Post by magickangaroo on 2009-08-06
Hello

Im running into some issues running multiple postfix instances on the same server.

the server has two public ips assigned to it, with one client using one and the other the other.  post fix configs are good when run individually but when run together the second wont run as it sees a lock file and wont run.

sanatised configs are below.

```
root@smtp:/etc/postfix# cat main.cf 
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

myhostname = smtp.xxxxxxx.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = smtp.xxxxxxx.com, localhost.xxxxxxx.com, , localhost
relayhost = 
mynetworks = 79..x.x.x/32, 127.0.0.1/32 
mailbox_size_limit = 0
recipient_delimiter = +
#inet_interfaces = all
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf,mysql:/etc/postfix/mysql-email2email.cf
dovecot_destination_recipient_limit = 1
virtual_transport = dovecot
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination

#multiple instances
alternate_config_directories = /etc/postfix1
inet_interfaces = 79..x.x.x, localhost
default_destination_concurrency_limit = 10
smtp_bind_address = 79..x.x.x
root@smtp:/etc/postfix# 
root@smtp:/etc/postfix# cd ../postfix1
root@smtp:/etc/postfix1# cat main.cf 
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

myhostname = pop.xxxxxxx.com 
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = pop.xxxxxxx.com
mydestination = pop.xxxxxxx.com, localhost.xxxxxxx.com, , localhost
relayhost = 
mynetworks = 95.x.x.x/32 
mailbox_size_limit = 0
recipient_delimiter = +
#inet_interfaces = all
virtual_mailbox_domains = mysql:/etc/postfix1/mysql-virtual-mailbox-domains.cf
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_maps = mysql:/etc/postfix1/mysql-virtual-mailbox-maps.cf
virtual_alias_maps = mysql:/etc/postfix1/mysql-virtual-alias-maps.cf,mysql:/etc/postfix/mysql-email2email.cf
dovecot_destination_recipient_limit = 1
virtual_transport = dovecot
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination

#multiple instances
#alternate_config_directories = /etc/postfix
smtp_bind_address = 95.x.x.x
inet_interfaces = 95.x.x.x
default_destination_concurrency_limit = 10

```

I suspect its something simple and similar to this [http://forums.opensuse.org/network-internet/416944-2-ip-postfix-ip-alias-2.html]("http://forums.opensuse.org/network-internet/416944-2-ip-postfix-ip-alias-2.html")

but i cant see it unfortunately. 

Any help with fresh eyes would of course be greatly appreciated.  The primary reason for multiple postfix instances are in case one customer gets another black listed.  i used this [http://advosys.ca/papers/email/58-postfix-instance.html]("http://advosys.ca/papers/email/58-postfix-instance.html") guide as a basis.

---

