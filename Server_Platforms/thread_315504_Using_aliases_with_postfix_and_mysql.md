---
title: "Using aliases with postfix and mysql"
date: 2006-12-09
forum: Server Platforms
---

### Post by lbsalt on 2006-12-09
hey all. i am running postfix 2.2.10 on ubuntu. i have mysql set up to handle auth, mailboxes, etc and everything is working perfectly except for one thing.

i have an alias i need to set up called "noreply" that i want all email to go to /dev/null. i am hosting several domains so i am using virtual maps. i set up the "aliases" table in mysql but i can't specify a destination address of /dev/null as it needs an actual recipient. if i set up a recipient in the users table with the maildir of /dev/null postfix will try to create the dirs under /dev/null before delivering the mail and will be denied as you can't create anything under /dev/null. 

so my question is, is this possible and does anyone else have a similar setup that can help?

here is the output from postconf -n:

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps =
mailbox_size_limit = 0
masquerade_domains = mail.mydomain.com !mail.mydomain.com
masquerade_exceptions = root
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
myhostname = mail.mydomain.com
mynetworks = 192.168.1.0/24
myorigin = /etc/mailname
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_pipelining, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

thanks in advance!!!

---

### Post by deuce868 on 2006-12-09
Maybe we can get the result some other way. What is the purpose of an alias that goes nowhere? Why setup the alias?

---

### Post by lbsalt on 2006-12-09
i was setting up the alias for auto generated messages such as if a user forgets their username, password, etc. i want to send them an email from an account but i dont want to monitor the mailbox

---

