---
title: "virtual_alias_maps problem in Postfix"
date: 2007-05-31
forum: Server Platforms
---

### Post by makiten on 2007-05-31
Hello.

I've been having this consistent problem with a "virtual_alias_maps" problem. In my log file, I get this every second (and my site is not actually mydomain.tld):

```
May 31 13:41:51 mydomain postfix/pickup[17838]: BFD158D00E7: uid=107 from=<smmsp>
May 31 13:41:51 mydomain postfix/cleanup[17890]: warning: connect to mysql server localhost: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
May 31 13:41:51 mydomain postfix/cleanup[17890]: warning: BFD158D00E7: virtual_alias_maps map lookup problem for root@mail.mydomain.tld
May 31 13:41:51 mydomain postfix/pickup[17838]: warning: maildrop/CE16F8D045C: Error writing message file

```

Right now I'm running Postfix (and Postfixadmin), Dovecot, and MySQL, and I can telnet, but when using the SMTP port and then using "ehlo localhost," the server stalls and never returns a result.

My main.cf file looks like this:

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version



# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

#content_filter = scan:127.0.0.1:10026
#receive_override_options = no_address_mappings

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtp_tls_CAfile = /etc/ssl/mydomain.pem
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_CAfile = /etc/ssl/cacert.pem
#smtpd_tls_CApath = /etc/ssl/
smtpd_tls_ask_ccert = yes
smtpd_tls_req_ccert = no

#smtpd_tls_cert_file=/etc/ssl/certs/mail-cert.pem
#smtpd_tls_key_file=/etc/ssl/private/mail-key.pem
smtpd_use_tls=yes
smtpd_tls_session_cache_database=btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database=btree:${queue_directory}/smtp_scache

# SASL parameters
broken_sasl_auth_clients = yes smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_hostname, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unauth_destination, reject_unauth_pipelining, reject_invalid_hostname

smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_security_options = noanonymous
smtpd_sasl_exceptions_networks = $mynetworks
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.mydomain.tld
mynetworks_style = host
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydomain = mail.mydomain.tld
myorigin = /etc/mailname
mydestination = localhost, localhost.localdomain, mail.mydomain.tld

smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, permit_tls_all_clientcerts, reject_unauth_destination, permit

relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

# Virtual mailbox settings

virtual_alias_maps = mysql:/etc/postfix/mysql/mysql_virtual_alias_maps.cf
virtual_gid_maps = static:114
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = mysql:/etc/postfix/mysql/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql/mysql_virtual_mailbox_maps.cf
virtual_minimum_uid = 110
#virtual_transport = virtual
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1
virtual_uid_maps = static:110

inet_protocols = all
masquerade_domains = $mydomain
smtpd_helo_required = yes

```

Mail servers are always causing headaches for me whenever MySQL is in the mix... But, setting up an email server with virtual servers is a new thing to me.

Can anyone help me on where to start with this problem?

---

