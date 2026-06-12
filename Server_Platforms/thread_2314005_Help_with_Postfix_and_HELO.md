---
title: "Help with Postfix and HELO"
date: 2016-02-17
forum: Server Platforms
---

### Post by Ed_Meadows on 2016-02-17
I'm struggling with trying to get an antiquated PBX doing VM to email with Office 365. What I've done so far is to install a new Ubuntu 14.04 LTS Server and configure Postfix on it as a relay to their Office 365 tenant. Problem that I'm having is that I'm getting a connection dropped from Postfix b/c the PBX is not sending a FQDN with the initial helo.

If I telnet into the server with 'helo anything', I can get connected and all is good. After much reading, I though that the lines highlighted below would bypass the helo requirement for any device on the same subnet as the server. That is not happening. Furthermore, I've done some more testing and it would seem that the smtpd_helo_restrictions is not doing anything at all. Taking out the permit_mynetworks in that line still lets me connect with 'helo anything', and I would think it would only accept something like 'helo server1.domain.com'.

Any help would be greatly appreciated.
Ed
```

postconf -n

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = Relay, localhost.localdomain, localhost
myhostname = Relay
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 10.2.0.0/24
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = [relay-com.mail.protection.outlook.com]
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
[COLOR=#ff0000]smtpd_delay_reject = yes[/COLOR]
[COLOR=#ff0000]smtpd_helo_required = yes[/COLOR]
[COLOR=#ff0000]smtpd_helo_restrictions = permit_mynetworks, reject_non_fqdn_helo_hostname, permit[/COLOR]
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = no
```

---

### Post by sandyd on 2016-02-17
Moved to *Server Platforms*

---

