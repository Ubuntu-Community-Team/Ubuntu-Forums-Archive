---
title: "Postfix and SASL auth"
date: 2010-02-26
forum: Security
---

### Post by Ghiepo on 2010-02-26
Hi everybody, I followed this How To ([https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)) in order to add smtp authentication to my Postfix installation used as spam filter for my exhange server, and it'seem all ok; the only thing that I don't understand is where I list all the users (with passwords) that I authorize to send mail through my server...
Can you help me? thank you...

---

### Post by Bachstelze on 2010-02-26
The HOWTO you are using uses PAM for authentication. This means that by default, users will authenticate with Postfix using the same password they use to login on the system.

---

### Post by Ghiepo on 2010-02-26
oh this wasn't clear to me! and what I have to use in order to be able to authorize user that don't login to the systems? shadow? this server don't have users, it must only process the incoming mails for spam and virus but I need that some external users use it to send mails out of our domain... thank you.

---

### Post by Bachstelze on 2010-02-26
> **Ghiepo said:**
> oh this wasn't clear to me! and what I have to use in order to be able to authorize user that don't login to the systems? shadow? this server don't have users, it must only process the incoming mails for spam and virus but I need that some external users use it to send mails out of our domain... thank you.

PAM supports a wide range of authentication mechanisms besides system passwords (those are just the default because they will obviously work everywhere). You can for example store usernames/passwors in a MySQL database, in a text file, or use fancy stuff like LDAP. Google should give you plenty of information about using PAM with Postfix.

---

