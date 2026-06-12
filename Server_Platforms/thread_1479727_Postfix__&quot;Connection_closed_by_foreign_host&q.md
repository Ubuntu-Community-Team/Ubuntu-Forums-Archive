---
title: "Postfix  &quot;Connection closed by foreign host&quot;"
date: 2010-05-11
forum: Server Platforms
---

### Post by conryf on 2010-05-11
I recently installed postfix and squirrelmail. And it doesn't work.

> > telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
Connection closed by foreign host.

squirrellmail give the error, after entering login info:

> Error connecting to IMAP server: localhost.
111 : Connection refused

I belive this may have something to do with my main.cf file, so I am also including that:

> # Network/Connections
myhostname = iwriteit.com
myorigin = /etc/mailname
mydestination = loft4657.serverloft.com, localhost.localdomain, loft4657, localhost, iwriteit.com, iwriteit.it
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
inet_interfaces = all
default_destination_concurrency_limit = 2

# Databases
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#canonical_maps = hash:/etc/postfix/canonical
#virtual_alias_maps = hash:/etc/postfix/virtual

# SASL / SMTP authentication
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
broken_sasl_auth_clients = yes

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
#smtpd_tls_CAfile = /etc/ssl/certs/CA_CERT_FILE
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# Security/Relay
smtpd_delay_reject = yes 
smtpd_helo_restrictions = reject_invalid_hostname
smtpd_sender_restrictions = reject_unknown_address
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

#### Greylisting
#smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, check_policy_service unix:private/postgrey
#### Mailfilter
#smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_access hash:/etc/postfix/confixx_unfilteredDomains, reject_unauth_destination
#smtpd_recipient_restrictions_mailfilter=check_recipient_access hash:/etc/postfix/confixx_filteredDomains, reject_unauth_destination

# Mailbox/Message
home_mailbox = Maildir/
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
message_size_limit = 104857600
unknown_local_recipient_reject_code = 550
recipient_delimiter = +

# misc
biff = no
allow_percent_hack = no
append_at_myorigin = no
append_dot_mydomain = no
swap_bangpath = no
readme_directory = no
inet_protocols = all
smtpd_sasl_security_options = noanonymous
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom


Please help!

---

### Post by jjcv on 2010-05-12
I see you are using TLS.   Can you telnet to port 587?

The email server does not do IMAP.  This is handled by the your POP/IMAP server, whatever you are using.   Squirralmail talks to this server to read mailboxes and can be configured for a variety of IMAP servers.

When installing a mailserver it is important to take one step at a time and make sure it works before going to the next.   I would suggest you go back to the basic configuration and then as you add features test them.

---

