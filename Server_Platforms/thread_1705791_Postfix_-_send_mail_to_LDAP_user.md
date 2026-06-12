---
title: "Postfix - send mail to LDAP user"
date: 2011-03-12
forum: Server Platforms
---

### Post by thesti on 2011-03-12
Hello,

I've configured Postfix and Dovecot with basic configuration. I've been able to send email to local user and login through Dovecot by using LDAP user account. 

However, when I try to send email to LDAP user, it fails. This is the error message I get from Thunderbird. 

```
The mail server responded: 5.1.1 Recipient address rejected. User unknown in local recipient table.
```Where did I do wrong?

Thank you.

---

### Post by druhboruch on 2011-03-13
Have you installed postfix-ldap on the server?
You may also check this wiki:
[http://wiki.dhits.nl/index.php/Dovecot_postfix_ldap](http://wiki.dhits.nl/index.php/Dovecot_postfix_ldap)

---

### Post by thesti on 2011-03-14
> **druhboruch said:**
> Have you installed postfix-ldap on the server?
You may also check this wiki:
[http://wiki.dhits.nl/index.php/Dovecot_postfix_ldap](http://wiki.dhits.nl/index.php/Dovecot_postfix_ldap)


Hello druhboruch!

I have checked that wiki, just screening it and I see this 'vmail' part. Does it mean Virtual Mail? Should I really create a Virtual Mail to enable Postfix recognize LDAP user mail account?

Thanks!

---

