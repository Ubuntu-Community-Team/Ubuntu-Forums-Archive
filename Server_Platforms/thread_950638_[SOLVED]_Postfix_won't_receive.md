---
title: "[SOLVED] Postfix won't receive"
date: 2008-10-17
forum: Server Platforms
---

### Post by Dr Small on 2008-10-17
I have been noticing over the last several days that I haven't been receiving any mail, and so today I verified by attempting to send mail to my email account from a remote host. So far, none of them have come in the Inbox and no error messages on the other side.

As a foreword, I have not touched Postfix's configuration for sometime, and it just out of the blue stopped working again. So, I will go down the checklist and hopefully someone can help me out.

[LIST]
[*]Router - Port 25 [open]
[*]Server (no firewall), thus port 25 is open
[*]Restarted Postfix (didn't help)
[*]Restarted Server (still didn't help)
[/LIST]

And for the record, here is an exact copy of my /etc/postfix/main.cf:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
# 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes


smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 1h

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

mynetworks = 127.0.0.0/8 192.168.0.0/24
myhostname = mycroftserver.homelinux.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mycroftserver.homelinux.org, selftech.homelinux.org, mycroft, localhost.localdomain, localhost
mailbox_size_limit = 0
recipient_delimiter = +
mydomain = mycroftserver.homelinux.org
home_mailbox = Maildir/
#mailbox_command = 

smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, check_relay_domains

broken_sasl_auth_clients = yes

#relay_domains = lists.mycroftserver.homelinux.org
#transport_maps = hash:/etc/postfix/transport
#mailman_destination_recipient_limit = 1
inet_protocols = ipv4

masquerade_domains = mycroftserver.homelinux.org
relayhost = 
inet_interfaces = all
```

Some further information:
I can send outbound just fine. The remote email account has received every email sent to it.
I tried telnetting to the host on port 25 and sending an email to my local inbox, and I received it. Example:
```
telnet mycroftserver.homelinux.org 25
```

Postfix is starting to annoy me with it's odd unexplained quirks that happen from time to time. If anyone could help me out further, I would be much obliged. I **need** to get my mailserver working again. Thanks!
Dr Small

---

### Post by Dr Small on 2008-10-17
Thanks to vice-versa from #postfix @ freenode, we were able to solve the postfix problem. Apparently, something was messing up with the modem (not Postfix!) and so after I reset the modem, he was able to connect, and then the emails started working again.

Now over the next several hours, I can imagine the emails will be pouring in. I'll mark this as solved for future reference!

Dr Small

---

