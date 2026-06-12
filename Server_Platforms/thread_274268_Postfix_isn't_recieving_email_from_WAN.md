---
title: "Postfix isn't recieving email from WAN"
date: 2006-10-09
forum: Server Platforms
---

### Post by kerinin on 2006-10-09
I'm in the process of moving my work's web page to a new VPS server, and i'm trying to set up the email server.

The biggest problem i have is that i can't have an interruption in the email service, so i'm trying to set up and test the server using a Dynamic DNS, and then when the domain transfers i'll change the postfix settings and hope it all works.

I've set up postfix and courier, and almost everything works.  I can send and recieve mail locally, and i can send mail from a local account to my gmail account.  The problem is that i can't recieve any emails from the world at large.  

Here's /etc/postfix/main.cf:

```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

myhostname = ###.dnsalias.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ###.dnsalias.net,localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
mailbox_command = 
inet_protocols = all

```

Any ideas?

---

### Post by kerinin on 2006-10-09
Well, it seems to be working now - strange.

Maybe they were just taking a long time...

---

