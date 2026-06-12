---
title: "Can't Start Stunnel"
date: 2008-02-08
forum: Server Platforms
---

### Post by jjb123 on 2008-02-08
I am trying to install and use stunnel with my newsreader. I installed it via apt-get, used openssl to generate the stunnel.pem and mail.pem files, chmoded both to 600, and when I run the "stunnel" command I get the following.

```
2008.02.08 18:13:25 LOG3[7026:3083450032]: Error reading certificate file: /etc/stunnel/stunnel.pem
2008.02.08 18:13:25 LOG3[7026:3083450032]: error stack: 140DC002 : error:140DC002:SSL routines:SSL_CTX_use_certificate_chain_file:system lib
2008.02.08 18:13:25 LOG3[7026:3083450032]: error stack: 20074002 : error:20074002:BIO routines:FILE_CTRL:system lib
2008.02.08 18:13:25 LOG3[7026:3083450032]: SSL_CTX_use_certificate_chain_file: 200100D: error:0200100D:system library:fopen:Permission denied
```

Can anyone help? Thanks.

---

### Post by faulkes on 2008-02-08
Check ownership and permissions of the /etc/stunnel/stunnel.pem file and the /etc/stunnel directory.

Faulkes

---

