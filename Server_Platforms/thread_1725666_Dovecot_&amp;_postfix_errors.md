---
title: "Dovecot &amp; postfix errors"
date: 2011-04-10
forum: Server Platforms
---

### Post by robbrandt on 2011-04-10
Hi.  I have a server on which I originally installed Ubuntu 9 and had it running perfectly as a web/mail server, then I upgraded to Ubuntu 10.  After the upgrade it stopped filtering spam effectively but by that time I no longer used it as a important mail server.  That was a year ago.  I need to use it as a mail server again and so need to fix this problem.

The mail.err log shows these errors:

dovecot: deliver(list): mkdir(/var/list/Maildir/cur) failed: Permission denied (euid=38(list) egid=38(list) missing +w perm: /var)
postfix/smtpd[17879]: fatal: no SASL authentication mechanisms

I am not a mail guru by any means.  But I can say that /var/list/Maildir/ is not where mail is supposed to be stored, it is stored in /home/{username}/Maildir.  So I suspect a configuration error, but I don't know where to look.  Suggestions?

Thanks

Rob

---

### Post by venol on 2011-04-10
what the value parameter "home_mailbox" in main.cf ?

---

### Post by robbrandt on 2011-04-11
Thanks for replying.

home_mailbox = Maildir/

---

### Post by falko on 2011-04-11
Can you post your main.cf?

---

### Post by robbrandt on 2011-04-11
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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.dom.ain
alias_maps = hash:/etc/aliases,hash:/usr/local/mailman/data/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = amd64.dom.ain, localhost.dom.ain,localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
virtual_alias_maps = hash:/etc/postfix/virtual,hash:/usr/local/mailman/data/virtual-mailman
home_mailbox = Maildir/
content_filter = smtp-amavis:[127.0.0.1]:10024
debug_peer_list = amd64.dom.ain

unknown_local_recipient_reject_code = 550
transport_maps = hash:/etc/postfix/transport
smtpd_sasl_type = dovecot
# smtpd_sasl_path = private/auth-client
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
inet_interfaces = all
smtpd_tls_auth_only = yes
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
header_checks = regexp:/etc/postfix/header_checks
default_process_limit = 400
smtpd_sasl_authenticated_header = yes
smtpd_sender_restrictions = reject_unknown_sender_domain
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-dovecot-postfix.conf -n -m "${EXTENSION}"
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium

---

### Post by robbrandt on 2011-04-13
Anyone?

---

### Post by markhorrocks on 2011-08-16
You have myhostname = mail.dom.ain

it should be the fqdn of your server.

---

### Post by hawk2010 on 2011-08-16
Most probably this is a permission issue. Run the following command

ls -la /var/list/

Check the permissions of Maildir

---

