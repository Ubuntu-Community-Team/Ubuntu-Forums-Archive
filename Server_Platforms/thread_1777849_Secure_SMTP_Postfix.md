---
title: "Secure SMTP Postfix"
date: 2011-06-08
forum: Server Platforms
---

### Post by Jay89 on 2011-06-08
Hello, I have an ssl configured Postfix email server with dovecot. I can connect to my inbox from thunderbird fine using port 993 and SSL/TLS connections. What's strange is that my IPAD can send and receive messages fine using port 25 for SMTP and 993 for the inbox. (I know port 25 is not secure but I'm not sure how to fix that yet). However, If I try to send mail using thunderbird it times out and I see this in /var/log.

Jun  8 07:06:59 newmail dovecot: imap-login: Login: user=<fakeuser>, method=PLAIN, rip=10.1.1.142, lip=10.1.0.28, TLS
Jun  8 07:08:25 newmail dovecot: imap-login: Login: user=<fakeuser>, method=PLAIN, rip=10.1.1.142, lip=10.1.0.28, TLS
Jun  8 07:08:26 newmail dovecot: imap-login: Login: user=<fakeuser>, method=PLAIN, rip=10.1.1.142, lip=10.1.0.28, TLS
Jun  8 07:08:26 newmail dovecot: imap-login: Login: user=<fakeuser>, method=PLAIN, rip=10.1.1.142, lip=10.1.0.28, TLS
Jun  8 07:19:30 newmail dovecot: imap-login: Login: user=<fakeuser>, method=PLAIN, rip=10.1.1.142, lip=10.1.0.28, TLS
[B]Jun  8 07:21:43 newmail postfix/smtpd[3581]: connect from testcomputer.test.net[10.1.1.142]
Jun  8 07:22:13 newmail postfix/smtpd[3581]: lost connection after UNKNOWN from testcomputer.test.net[10.1.1.142]
Jun  8 07:22:13 newmail postfix/smtpd[3581]: disconnect from testcomputer.test.net[10.1.1.142][/B]
[B]Jun  8 07:25:33 newmail postfix/anvil[3584]: statistics: max connection rate 1/60s for (smtp:10.1.1.142) at Jun  8 07:21:43
Jun  8 07:25:33 newmail postfix/anvil[3584]: statistics: max connection count 1 for (smtp:10.1.1.142) at Jun  8 07:21:43
Jun  8 07:25:33 newmail postfix/anvil[3584]: statistics: max cache size 1 at Jun  8 07:21:43
[/B]
I don't recall setting any max connections. Below is my main.cf for postfix.


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

myhostname = newmail.test.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = test.net, newmail.test.net, localhost.test.net, localhost
relayhost = 
relay_domains = test.net
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-dovecot-postfix.conf -n -m "${EXTENSION}"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = .maildir/
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_tls_auth_only = yes
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_sasl_authenticated_header = yes
smtpd_sender_restrictions = reject_unknown_sender_domain
smtp_use_tls = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_host_lookup = native

---

