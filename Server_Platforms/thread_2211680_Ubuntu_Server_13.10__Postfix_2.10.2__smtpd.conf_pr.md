---
title: "Ubuntu Server 13.10 | Postfix 2.10.2 | smtpd.conf problem"
date: 2014-03-17
forum: Server Platforms
---

### Post by Roswebnet on 2014-03-17
Hi everyone

I would like that my Postfix accepts only LOGIN and PLAIN authentication methods (or methods as first).

I did following changes in configurations files.

/etc/postfix/main.conf

```
# SASL parameters
#
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = cyrus
smtpd_sasl_path = smtpd
smtpd_sasl_local_domain = $mydomain 
smtpd_sasl_security_options = noanonymous
#Supporting non-standard mail clients
broken_sasl_auth_clients = yes
```

I created /*etc/postfix/sasl/smptd.conf a*nd */usr/lib/sasl2/smtpd.conf*. I did the same for chrooted postfix and created 
*/var/spool/postfix/etc/postfix/sasl/smptd.conf* and */var/spool/postfix/usr/lib/sasl2/smtpd.conf*
With following configuration:

```
pwcheck_method: auxprop
auxprop_plugin: sasldb
mech_list: plain login

```

However, I get following output:

```
[EMAIL="root@srv01"]root@srv01[/EMAIL]:~# telnet mail.domain.tld 25
Trying 83.83.94.49...
Connected to mail.roshost.tk.
Escape character is '^]'.
220 mail.roshost.tk server ready.
ehlo mail.domain.tld
250-mail.domain.tld
250-PIPELINING
250-SIZE 10485760
250-ETRN
250-STARTTLS
[B]250-AUTH DIGEST-MD5 NTLM CRAM-MD5 PLAIN LOGIN
250-AUTH=DIGEST-MD5 NTLM CRAM-MD5 PLAIN LOGIN[/B]
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN


```

What is wrong?

Thank you.

---

### Post by Roswebnet on 2014-03-23
no one?

---

