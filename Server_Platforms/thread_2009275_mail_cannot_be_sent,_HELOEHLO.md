---
title: "mail cannot be sent, HELO/EHLO"
date: 2012-06-24
forum: Server Platforms
---

### Post by A2llex on 2012-06-24
hi,

i have a problem with sending an email, it's returning me only this error message:

host host.tld[IP adress] said: 550 Access     denied - Invalid HELO name (See RFC2821 4.1.1.1) (in reply to MAIL FROM     command)


host [] said: 554 5.7.1     Mail (id-34054-07247) appears to be unsolicited - Forged Helo - resend with     the code uvamupu4 appended to subject and ask to have your email     whitelisted (the code uvamupu4 changes each 24 hours). (in reply to end of     DATA command) 

bellow is my main.cf 
there's no HELO/EHLO restriction in 
smtpd_recipient_restrictions.

Why is this happening?

```
smtpd_banner = $myhostname ESMTP $mail_name (mr. Bean)
biff = no

myhostname = localhost
mydestination = $mydomain
myorigin = /etc/mailname
mynetworks = 127.0.0.0/8, 10.0.0.0/24
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
home_mailbox = Maildir/
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /var/mail/virtual
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_alias_maps = hash:/etc/postfix/valiases
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
relayhost =
debug_peer_list = heytherewego.com

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks,reject_unauth_destination


smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes

content_filter = smtp-amavis:[127.0.0.1]:10024


message_size_limit = 40960000
```

---

### Post by yashar on 2012-06-24
send a log file with error.

add this option

[B]smtp_always_send_ehlo (default: yes)

or are you trying to send a mail from an account with other spf record?

[/B]

---

### Post by A2llex on 2012-06-24
> **yashar said:**
> send a log file with error.

add this option

[B]smtp_always_send_ehlo (default: yes)

or are you trying to send a mail from an account with other spf record?

[/B]

there's nothing in error log.

i had this installed:
postfix-policyd-spf-python

but the problem persists.

---

### Post by yashar on 2012-06-24
what is the reply if you send a mail to your yahoo or gmail account?

change your debug mode and send the mail log.

---

### Post by A2llex on 2012-06-25
this has been solved, i didn't have set FQDN.

---

