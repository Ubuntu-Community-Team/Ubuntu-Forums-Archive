---
title: "[SOLVED] PHP5 Sendmail permission error"
date: 2008-10-17
forum: Server Platforms
---

### Post by batfastad on 2008-10-17
Hi everyone

Currently converting a newsletter mailing script to the SwiftMailer class from the old PHPMailer.
Seems to work well on our main hosting provider, but I want to get it working on our intranet Apache2/PHP5 server
PHP is 5.2.4-2ubuntu5.3, the server is Ubuntu 8.04, Apache/2.2.8 (Ubuntu) mod_ssl/2.2.8 OpenSSL/0.9.8g

However when I try and send through sendmail, I get the following error:
```
Fatal error: Uncaught exception 'Swift_ConnectionException' with message 'Sendmail cannot be seen with lstat().
```

After a bit of digging around it seems that could be caused by PHP/Apache not having permission to access to the sendmail binary.
Since this server is a dedicated intranet server and under my control, I can actually do something about the permissions.

I'd rather change some permissions or a php.ini setting than hack Swift. I like to keep my PHP classes so I can just drop in the newer versions when necessary.

Any ideas / suggestions on what I need to change?

I'm fairly new to Linux, and very new to Ubuntu though I've been learning gradually over the past few months.
Apparently Exim is actually the preferred way of handling mail on Ubuntu/Debian, but this SwiftMailer PHP class has sendmail as one of it's supported libraries

Thanks, B

EDIT: Ok slightly solved. Seems the command Swift was sending to sendmail was invalid. I've changed this to /usr/sbin/sendmail -bs
Hope this helps someone out

---

