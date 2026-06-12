---
title: "Set up mail server?"
date: 2007-10-16
forum: Server Platforms
---

### Post by Xarok on 2007-10-16
So I looked in Ubuntu 6.06 docs 
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/email-services.html)
on how to set up a mail server and it seems to be working...


I used "Zorg"  , my server's localhost name to replace the example.com, but should I be using my domain name? higher9productions.com?

I don't understand this mail server thing at all, or how I'm suppose to use it.

I basicly just want to have my Joomla software be able to send e-mail for registration and newsletter purposes. It doesn't explain anything ...

If you have any advice, let me know.

Peace

---

### Post by HermanAB on 2007-10-16
Yes.  You need a proper domain name if you wish other mail servers to receive your mail and not dump it in a spam bin.  Also, your domain name should resolve forwards (A and MX records) and backwards (PTR records).  

Verify it with nslookup or dig and send mail to/from Yahoo or wherever you have another mail account to test it.

Cheers,

H.

---

### Post by Xarok on 2007-10-18
[IMG]http://higher9productions.com/mx.jpg[/IMG]

```
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = higher9productions.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = higher9productions, zorg, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
```

Is this correct :confused:
I have no idea what I'm doing

---

