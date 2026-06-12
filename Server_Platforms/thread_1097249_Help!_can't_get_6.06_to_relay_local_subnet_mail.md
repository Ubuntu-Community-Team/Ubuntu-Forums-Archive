---
title: "Help! can't get 6.06 to relay local subnet mail"
date: 2009-03-15
forum: Server Platforms
---

### Post by wkulecz on 2009-03-15
Help!, I'm stumped.

I'm trying to setup my 6.06 file server to relay mail from my local subnet via gmail.  The fact that everything outgoing would appear to originate from my gmail account doesn't matter for this application (Legacy Windoze video security system that can't do the password authorization recently implimented by my ISP).

I can telnet into my box from a local command prompt (telnet myhost 25) and manually give the SMTP commands to send a test message and it works perfectly, even though I give a from address for the Windows machine.  But when I try to do the same from the Windoze box the seesion immediately closes after the telnet connects :(

Here is my postfix main.cf file:
```

#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Wahine Ubuntu 6.06)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_use_tls = yes


# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = wahine
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = video-edit, wahine, localhost, localhost.localdomain, localhost
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_password_maps = hash:/etc/postfix/saslpasswd
smtp_always_send_ehlo = yes
relayhost = [smtp.gmail.com]:587
mynetworks_style = subnet
mynetworks = 127.0.0.0/8 192.168.1.0/8 [::ffff:127.0.0.0]/104 [::1]/128
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination
smtpd_reject_unlisted_recipient = no
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html

```

I'm desperate!
--wally.

---

### Post by wkulecz on 2009-03-16
Anybody?

bump.

I need to unsecure POSTFIX and have smtpd accept mail from anyone on my local subnet.  Once I get it in the queue it gets relayed correctly.  I just can't get smtpd to accept from anything but the 6.06 Ubuntu machine.

--wally.

---

### Post by wkulecz on 2009-03-16
mynetworks = 192.168.1.0/24 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128

instead of: 192.168.1.0/8.

The key tidbid was found in:
[http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/opensource/0672329093/ch24lev1sec2.html](http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/opensource/0672329093/ch24lev1sec2.html)

--wally.

---

