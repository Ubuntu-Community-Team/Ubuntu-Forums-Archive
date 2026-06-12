---
title: "Postfix not accepting messages - NOQUEUE: reject: RCPT"
date: 2007-06-18
forum: Server Platforms
---

### Post by dogterom on 2007-06-18
Hello fellow ubuntu-ers,

I've recently
 upgraded my server from debian unstable to feisty. One big issue is that I cannot receive mail.
The mail.info shows:

NOQUEUE: reject: RCPT from xxx.es[xxxxxxx]: 554 5.7.1 <validuser@mydomain.net>: Relay access denied; from=<xxx@xxxxx> to=<validuser@mydomain.net> proto=SMTP helo=<xxx.es>

My main.cf reads:
myhostname = mail.mydomain.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination=mail.mydomain.net, localhost,localhost.mydomain.net
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all

Does anyone have a clue what could go wrong here? 

Regards,
Vince

---

### Post by Mr. C. on 2007-06-18
Postfix does not see itself as being final destination for mydomain.net, so it rejects the message, thinking it is being asked to relay mail to another server.  Show output of postconf -n, not the contents of your main.cf

MrC

---

### Post by dogterom on 2007-06-18
hi, here's the ouput;

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = scan:127.0.0.1:10026
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command = 
mailbox_size_limit = 0
mydestination =mail.mydomain.net,localhost,localhost.mydomain.net
myhostname = mail.mydomain.net
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = 
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

---

### Post by Mr. C. on 2007-06-18
I don't see mydomain set.  Set it to:

mydomain = mydomain.net

add add mydomain.net (or $mydomain) to mydestination and restart postfix.

I also see that postfix is listening on only the loopback interface.  This allows only clients on the server itself to connect for mail relay.  Is this what you intend?

MrC

---

### Post by dogterom on 2007-06-19
Hi MrC,

Thx!! This resolved my issue :-)
And yes it it intended that only users of that local server are allowed to sent mail.

Thanks!

Vince

---

### Post by Mr. C. on 2007-06-19
Glad things are working for you.

Cheers,
MrC

---

