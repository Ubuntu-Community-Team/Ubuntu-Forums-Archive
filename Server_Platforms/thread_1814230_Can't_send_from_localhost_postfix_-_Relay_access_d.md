---
title: "Can't send from localhost postfix - Relay access denied"
date: 2011-07-29
forum: Server Platforms
---

### Post by SiggSauer on 2011-07-29
I've configured a postfix server with zarafa webmail. I can send and receive mail from Thunderbird, I can only receive mail on the webaccess and send mail to addresses in my domain. When I send mail from the webaccess to my external mail it returns an undelivered mail.

Just to note we run our own mail host 

In the mail.log this pops up.
```

Jul 29 11:31:17 RTS-GW postfix/smtpd[8824]: connect from localhost.rtsoffice.lan[127.0.0.1]
Jul 29 11:31:17 RTS-GW postfix/smtpd[8824]: NOQUEUE: reject: RCPT from localhost.rtsoffice.lan[127.0.0.1]: 554 5.7.1 <mymail@hotmail.com>: Relay access denied; from=<mymail@realtimesolutions.nl> to=<mymail@hotmail.com> proto=SMTP helo=<RTS-GW.rtsoffice.lan>

```Postfix main.conf
```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
delay_warning_time = 1h

myhostname = RTS-GW.rtsoffice.lan
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_alias_maps = mysql:/etc/postfix/mysql-aliases.cf

# Domain properties
mydomain = realtimesolutions.nl
myorigin = /etc/mailname
mydestination = $mydomain, rts-gw.rtsoffice.lan, mail.$mydomain, localhost.rtsoffice.lan, localhost
relayhost =
mynetworks = 192.168.41.0/24 127.0.0.0/8 80.113.202.88
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html

# Zarafa commands
mailbox_command = /usr/bin/zarafa-dagent "$USER"
mailbox_transport = zarafa: zarafa_destination_recipient_limit = 15

# SASL/TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes

smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

smtpd_use_tls = yes
smtpd_tls_auth_only = yes
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s

smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_recipient_restrictions = permit_sasl_authenticated,reject_unauth_destination,reject_unknown_sender_domain,permit_mynetworks,reject_rbl_client list.dsbl.org,reject_rbl_client sbl.spamhaus.org,reject_rbl_client cbl.abuseat.org,reject_rbl_client dul.dnsbl.sorbs.net,reject_rbl_client zen.spamhaus.org,permit
smtpd_client_restrictions = permit_mynetworks,reject_unknown_recipient_domain,permit
broken_sasl_auth_clients = yes
tls_random_source = dev:/dev/urandom

smtpd_error_sleep_time = 3s
smtpd_soft_error_limit = 10
smtpd_hard_error_limit = 20
```Does anybody have a clue on why it doesn't work?

---

### Post by Entilza on 2011-07-29
Did you telnet to your mail server port 25 and go through the manual testing.

Is your error on 

RCPT To: <email@address.com>

I was missing the wrong authenticated network setup in "mynetworks = ... " then it was solved.  It seems you have your 192 network there though is that the right one?

Mine is:  

mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 10.1.16.0/24

---

### Post by SiggSauer on 2011-07-30
The networks in **mynetworks **are correct, the fact that i can send mail from my thunderbird client proves that it should work. It could be an authentication problem, that for some reason it can't authenticate the localhost.
 
RCPT To: [EMAIL="email@address.com"]email@address.com[/EMAIL] I think I saw something like that come by in the log, but i'll have to look at that on monday when I can acces the machine again.

---

