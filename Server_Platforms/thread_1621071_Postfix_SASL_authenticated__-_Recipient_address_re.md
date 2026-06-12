---
title: "Postfix SASL authenticated  - Recipient address rejected: Access denied"
date: 2010-11-13
forum: Server Platforms
---

### Post by Excizted on 2010-11-13
Hello,

I am running Ubuntu Server 10.04 in an OpenVZ based virtual machine.

By following this guide: [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3) I have set up a mail server based on Postfix with SASL through PEM through MySQL authentication.

I use SASL authentication to allow end users (from external IP's) to connect and send mail through this SMTP server.

When I try to send a mail from an external PC, through the server, I get 
[B]RCPT TO <excizted@gmail.com> failed: <excizted@gmail.com>: Recipient address rejected: Access denied

[/B]Googling tells me to allow the IP or use SASL - *BUT I AM USING SASL!!!!*
Contiued Googling tells me to add **smtpd_recipient_restrictions = permit_sasl_authenticated, reject** to my config - *BUT IT IS ADDED!!!!*

I am going crazy about this!
Would love if anyone could help me out!

This is my config (/etc/postfix/main.cf):
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

mydomain = mydomain.com

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
smtpd_tls_auth_only = no
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = server.mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = server.mydomain.com, localhost, localhost.localdomain, proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
relayhost =
mynetworks = 127.0.0.0/8, [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated, reject
smtpd_tls_security_level = may
transport_maps = proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
virtual_mailbox_limit_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = "The user you are trying to reach is over quota."
virtual_overquota_bounce = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_can$
smtpd_sender_restrictions = check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = maildrop
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous

```Thank you very much and have a nice weekend. :KS

Note: mydomain.com is replaced with the actual domain the server is hosting.

---

