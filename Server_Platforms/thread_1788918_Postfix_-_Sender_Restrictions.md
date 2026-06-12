---
title: "Postfix - Sender Restrictions"
date: 2011-06-23
forum: Server Platforms
---

### Post by jmacgowan on 2011-06-23
I have an email server with a FQDN of example1.com, and another email server with a FQDN of example2.com.  I have full control of example1.com, but limited access to example2.com Example1.com has a Postfix v2.8.1 + Dovecot v1.2.12 + Spamassassin v3.3.1 setup that works wonderfully.

I want to limit the receipt of emails by example1.com to only example1.com and example2.com.  I have searched and tried a few solutions, but nothing that fits what I need.

Just to clarify, on example1.com, I want to reject all emails not from example1.com or example2.com.  Any help or pointing me in the right direction is greatly appreciated.

---

### Post by Bachstelze on 2011-06-24
Define "from". :)

---

### Post by falko on 2011-06-24
Take a look at Postfix header checks: [http://www.postfix.org/header_checks.5.html](http://www.postfix.org/header_checks.5.html)

---

### Post by jmacgowan on 2011-06-24
Thanks falko, looks like just what I need.  Much appreciated.

---

