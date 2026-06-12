---
title: "Postfix email receiving woes: 553 sorry, relaying denied from your location"
date: 2007-05-22
forum: Server Platforms
---

### Post by mrmzytplk on 2007-05-22
I haven't seen a response to this which relates to my problem yet -

I'm running Ubuntu 6.10. I just installed Postfix. I can send emails out to my gmail account, but I cannot reply to those emails - the message I get back is


```
PERM_FAILURE: SMTP Error (state 13): 553 sorry, relaying denied from your location
```

I run a tail -f on /var/log/mail.log and no updates are posted during the entire duration between when I reply to the email and when I get the error message back.

My MX records and A records all point to the same IP address.

Here is my postconf -n:
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
ignore_mx_lookup_error = yes
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
mydestination = /etc/mailname, localhost
mydomain = domain.com
myhostname = domain.com
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes

```

Where domain.com is my domain. What should my next troubleshooting steps be?

Thanks in advance for any help.

---

### Post by Mr. C. on 2007-05-22
[http://ubuntuforums.org/showthread.php?t=341034&page=2](http://ubuntuforums.org/showthread.php?t=341034&page=2)

---

### Post by gombadi on 2007-05-22
> I run a tail -f on /var/log/mail.log and no updates are posted during the entire duration between when I reply to the email and when I get the error message back.

To me that indicates that the reply is not going to your machine. Which server is reporting the relay denied error?

> My MX records and A records all point to the same IP address.

That indicates that you know what MX records are for and therefore should be correct ;)

If you have access to another linux machine you could run swaks and/or dig to try and find out what is going on. Or you could tell us the domain name and we do some remote testing for you.

What does /etc/mailname contain? The same domain name as your reply will have in the to field?  Make sure it is not something like subdomain.domain.com.

---

