---
title: "How do I get &quot;secure authentication&quot; supported by my mail server"
date: 2010-09-22
forum: Server Platforms
---

### Post by minhnghivn on 2010-09-22
Using Thunderbird as mail client, I notice an option in the mail  account's Server Settings which reads "Use secure authentication" which  allow secured transition of your username and password.

I also have my own mail server. Hence, how do I enable this  functionality for my mail server (I'm using Postfix & Dovecot) ?

Any help will be highly appreciate

---

### Post by Bachstelze on 2010-09-22
Define "mail server". For sending or receiving mail?

---

### Post by minhnghivn on 2010-09-22
> **Bachstelze said:**
> Define "mail server". For sending or receiving mail?

I think think I will need both. No matter if users are sending or receiving mail, their authentication information should be transferred as encrypted rather than plain data.

Currently, my Postfix smtpd_sasl_type is set to dovecot

```
smtpd_sasl_type = dovecot
```

So I think I only need to configure somewhere in the dovecot.conf to get "secure authentication" work for both sending and receiving

---

### Post by Bachstelze on 2010-09-23
Just set up SSL/TLS. Then you won't need a secure authentication mechanism, as the traffic will be encrypted anyway.

---

### Post by minhnghivn on 2010-09-24
> **Bachstelze said:**
> Just set up SSL/TLS. Then you won't need a secure authentication mechanism, as the traffic will be encrypted anyway.
Thank you Bachstelze, but how to get my Postfix/Dovecot accept SSL/TLS ?

---

### Post by Bachstelze on 2010-09-24
> **minhnghivn said:**
> Thank you Bachstelze, but how to get my Postfix/Dovecot accept SSL/TLS ?

[https://help.ubuntu.com/10.04/serverguide/C/email-services.html](https://help.ubuntu.com/10.04/serverguide/C/email-services.html)

---

