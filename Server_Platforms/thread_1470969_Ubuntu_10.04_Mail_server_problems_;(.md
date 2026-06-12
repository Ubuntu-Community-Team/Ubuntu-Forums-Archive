---
title: "Ubuntu 10.04 Mail server problems ;("
date: 2010-05-03
forum: Server Platforms
---

### Post by halvors on 2010-05-03
Hi!

I have some problems with my email server, i use postfix and dovecot, but it does not work right now.

Anyone understand the log?

```

May  3 14:17:38 ss1 postfix/postalias[11709]: warning: /etc/aliases, line 58: need name:value pair
May  3 14:22:53 ss1 postfix/smtpd[11990]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
May  3 14:23:53 ss1 postfix/postmap[12329]: warning: /etc/aliases, line 2: record is in "key: value" format; is this an alias file?
May  3 14:37:36 ss1 postfix/postqueue[13588]: warning: Mail system is down -- accessing queue directly
May  3 14:47:55 ss1 dovecot: dovecot: Killed with signal 15 (by pid=14633 uid=0 code=kill)
May  3 14:49:04 ss1 postfix/smtpd[14695]: warning: cannot get RSA private key from file /etc/ssl/private/smtpd.key: disabling TLS support
May  3 14:49:04 ss1 postfix/smtpd[14695]: warning: TLS library problem: 14695:error:0906D06C:PEM routines:PEM_read_bio:no start line:pem_lib.c:650:Expecting: ANY PRIVATE KEY:
May  3 14:49:04 ss1 postfix/smtpd[14695]: warning: TLS library problem: 14695:error:140B0009:SSL routines:SSL_CTX_use_PrivateKey_file:PEM lib:ssl_rsa.c:669:

```

---

