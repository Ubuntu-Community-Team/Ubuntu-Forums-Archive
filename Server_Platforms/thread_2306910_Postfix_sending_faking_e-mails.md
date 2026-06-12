---
title: "Postfix sending faking e-mails"
date: 2015-12-20
forum: Server Platforms
---

### Post by Lucas_Matheus_Test on 2015-12-20
Hello guys, could you help me please ?

My postfix server is sending spam from my server with fake e-mails using my domain, for example:

[email]BarackObama@mydomain.com[/email]

my main.cf:

# See /usr/share/postfix/main.cf.dist for a commented, more complete version




# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname


smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no


# appending .domain is the MUA's job.
append_dot_mydomain = no


# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h


readme_directory = no


smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_helo_restrictions = reject_unknown_sender_domain


# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/postfix.pem
smtpd_tls_key_file = /etc/ssl/private/postfix.pem
smtpd_use_tls = yes
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtpd_tls_received_header = yes
smtpd_tls_loglevel = 1
smtpd_tls_session_cache_timeout = 3600s
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.


myhostname = iserver.ccdm.ufscar.br
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#myorigin = /etc/mailname
myorigin = $myhostname
mydestination = iserver.ccdm.ufscar.br, localhost.ccdm.ufscar.br, , localhost
relayhost = 
#mynetworks = 200.136.214.128/25
#mynetworks = 200.136.214.134, 200.136.214.130, 200.136.214.132, 200.136.214.185, 200.136.214.133, 200.136.214.190, 200.136.214.169, 200.136.214.162, 200.136.214.172, 200.136.214.161,  200.136.214.232, 177.84.241.75
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf,mysql:/etc/postfix/mysql-email2email.cf
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
smtpd_tls_auth_only = yes
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_delay_reject = yes
smtpd_helo_required = yes


content_filter = smtp-amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings


smtpd_client_restrictions = permit_mynetworks,reject_unknown_client_hostname, reject


message_size_limit = 30240000
bounce_template_file = /etc/postfix/bounce.cf






Please...Thank you.

---

### Post by SeijiSensei on 2015-12-20
Are you sure you're sending these messages?  It's quite possible a spammer is sending them from elsewhere on the Internet and spoofing your domain.

What do you see in /var/log/mail.log corresponding to the message above?  You should be able to determine its origin.

---

### Post by Lucas_Matheus_Test on 2015-12-21
I think I found it, one of my users has been hacked recently and the found his password wich is the same of the e-mail, so the emails were entering my server with the password of this user.

---

