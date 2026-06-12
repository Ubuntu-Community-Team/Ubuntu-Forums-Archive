---
title: "Thunderbird - SSL is on but encrypted password is not."
date: 2010-09-18
forum: Security
---

### Post by zozza on 2010-09-18
Hello,

In my Thunderbird options I have SPOP, SSMTP, and SIMAP.  If I go to Server Settings / Security Settings the connection is SSL / TLS as I would expect.  

However, the authentication method is "normal password" rather than "encrypted password".  Does this mean all my passwords go out in plain text or, since they go via secure POP, secure IMAP, and secure SMTP, they are encrypted?

When I try "encrypted password" I get an error message because the server does not support this function. 

Thanks.

---

### Post by krishnandu.sarkar on 2010-09-18
Does the mail server you are using support encryption..?? If not then that's not the fault of Thunderbird.

---

### Post by Bachstelze on 2010-09-18
If it's SSL/TLS, everything is encrypted, including the password.  Some other authentication mechanisms encrypt only the password, so they are obviously redundant if you use TLS already. They're for when you use an insecure channel.

---

