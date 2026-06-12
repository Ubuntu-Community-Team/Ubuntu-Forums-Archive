---
title: "Need Postfix configuration for Nokia's Ovi Mail"
date: 2010-08-05
forum: Server Platforms
---

### Post by cirobr on 2010-08-05
Hello,

When Postfix on a clean Ubuntu 10.04 Server installation tries to relay email to Nokia Ovi, the following error message shows up:

> Aug  5 18:14:37 note1-server postfix/smtp[2608]: 76324C151D: to=<abc@terra.com.br>, relay=smtp.mail.ovi.com[8.12.152.72]:465, delay=1062, delays=998/0.2/64/0, dsn=4.4.2, status=deferred (lost connection with smtp.mail.ovi.com[8.12.152.72] while receiving the initial server greeting)


For reference, please find below relevant portion of Postfix main.cf file:

```
# Postfix configuration to relay e-mail through ISP
relayhost = [smtp.mail.ovi.com]:465
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous

# TLS
smtp_sasl_tls_security_options = noanonymous
smtp_use_tls  = yes
smtp_tls_CAfile = /etc/ssl/certs/server.crt
smtp_sasl_tls_security_options = noanonymous
```

Postfix sasl_passwd file:

```
[smtp.mail.ovi.com] userid@ovi.com:password
```

Besides that, self-signed certificates are generated per the below document:

[https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html]("https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html")



Any help is greatly appreciated.

Thanks.

---

### Post by cirobr on 2010-09-26
No ideas?

---

### Post by lisati on 2010-09-26
A stab in the dark here: change the relayhost line to:
```
relayhost = smtp:smtp.mail.ovi.com:465
```

---

### Post by cirobr on 2010-09-26
> **lisati said:**
> A stab in the dark here: change the relayhost line to:
```
relayhost = smtp:smtp.mail.ovi.com:465
```

Thanks for the tip. I've got "Unknown mail transport error in reply", so it doesn't work.

---

### Post by cirobr on 2010-09-26
I wonder if the problem isn't related to self signed certificates ... When relaying emails directly to Nokia Ovi SMTP server with Evolution mail client, operation is done smoothly (SSL connection is configured).

Does anyone know how Evolution treats SSL connection and which certificate it uses?

Thanks.

---

