---
title: "postfix virtual problem"
date: 2011-10-03
forum: Server Platforms
---

### Post by inabor on 2011-10-03
I'm following this [thread ]("http://flurdy.com/docs/postfix"), trying to config a Mail Server. But I doesn't make it. I can login a user var outlook or mutt,but cannot send/receive any messages. Here is the log:

> root@mail:~# postqueue -p
-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
CF97943002*     558 Sun Oct  2 07:50:13  [email]root@nabor.dns66.net[/email]
                                         [email]root@mail.nabor.dns66.net[/email]

B65D743026*     702 Sat Oct  1 15:57:50  ***@hotmail.com
                                         [email]root@nabor.dns66.net[/email]

root@mail:~# tail -f /var/log/syslog
Oct  2 10:02:23 mail postfix/master[22273]: warning: /usr/lib/postfix/virtual: bad command startup -- throttling
Oct  2 10:03:23 mail postfix/virtual[25220]: fatal: dict_open: unsupported dictionary type: virtual:  Is the postfix-virtual package installed?
Oct  2 10:03:24 mail postfix/master[22273]: warning: process /usr/lib/postfix/virtual pid 25220 exit status 1
Oct  2 10:03:24 mail postfix/master[22273]: warning: /usr/lib/postfix/virtual: bad command startup -- throttling

postfix configuration:
> root@mail:~# postconf -n
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_at_myorigin = no
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = no
config_directory = /etc/postfix
delay_warning_time = 4h
inet_interfaces = all
inet_protocols = all
local_recipient_maps =
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
masquerade_classes = header_sender,envelope_sender
masquerade_domains = nabor.dns66.net
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination =
mydomain = nabor.dns66.net
myhostname = mail.nabor.dns66.net
mynetworks = all
myorigin = $mydomain
readme_directory = no
recipient_delimiter = ;
relayhost =
smtp_helo_timeout = 60s
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_tls_note_starttls_offer = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_hard_error_limit = 22
smtpd_recipient_limit = 50
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = virtual:5000
virtual_mailbox_base = /mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_transport = virtual
virtual_uid_maps = virtual:5000


Any one can give me some tips? Thanks!

---

