---
title: "How to change sendmail www-data?"
date: 2010-07-21
forum: Server Platforms
---

### Post by mlinux on 2010-07-21
The sendmail was setup in default condition. While testing some php application using @mail function, it uses the sender name as "www-data@xxx.com". How to replace the "www-data"?

---

### Post by Ryan Dwyer on 2010-07-22
Configure it in /etc/php5/apache2/php.ini (search for sendmail_from).

---

### Post by Bachstelze on 2010-07-22
Or (better) just add a "From: " header to the message.

---

