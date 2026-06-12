---
title: "Ubuntu Mail Server"
date: 2011-07-21
forum: Server Platforms
---

### Post by gypsumwolf on 2011-07-21
Just tried to setup lubuntu as a mail server following this guide: [https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer")

I installed Postfix, PostfixAmavisNew, Dovecot, and OpenWebMail. Set up for IMAP and IMAPS.
[list]
[*] I can send mail!
[*] I **can't** receive mail!
[/list]
Any ideas?

My routers forwarded ports are 25, 993, 143, ...

---

### Post by gypsumwolf on 2011-07-22
*bumb*, do you need to see my postfix config?

```

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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.realdomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.realdomain.com, realdomain.com, neptune, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command = 
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
content_filter = smtp-amavis:[127.0.0.1]:10024


```

---

### Post by SeijiSensei on 2011-07-22
```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
```

Only mail sent from localhost will be admitted by this directive.  Try adding the network address of your server's Ethernet interface, something like 192.168.x.y/24.

---

### Post by gypsumwolf on 2011-07-22
I added my internal IP. I also have my rDNS (PTR record) for external ip to mydomain.com.

I have a mx record set for mail.mydomain.com.

I am still not receiving e-mails on my server.

---

### Post by e79 on 2011-07-22
> **gypsumwolf said:**
> I added my internal IP. I also have my rDNS (PTR record) for external ip to mydomain.com.

I have a mx record set for mail.mydomain.com.

I am still not receiving e-mails on my server.
Just checking; did you set a 'hostname record' (A record) with 'mail.domain.com' and then set your MX to point to it (at the ISP level)? The MX needs a hostname to work properly.

just my $0.02

---

### Post by SeijiSensei on 2011-07-23
Perhaps your ISP blocks inbound port 25 to enforce a "no-servers" policy?

What does /var/log/mail.log tell you about incoming messages?

---

