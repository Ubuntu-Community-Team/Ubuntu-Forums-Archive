---
title: "Server Diagnostic tools?"
date: 2007-02-11
forum: Server Platforms
---

### Post by cap10kirk on 2007-02-11
Hi all. I had to restart my webserver twice this past week. The webserver went offline for some reason. The ftp, smtp, pop3, and mysql servers stayed online. Are there any type of diagnostic software that would checkout the problem if it happens again?

Thanks,
Kirk

---

### Post by jtc on 2007-02-11
> **cap10kirk said:**
> Are there any type of diagnostic software that would checkout the problem if it happens again?
Have your checked your log-files. Suprisingly often you find all the answers, or at least clues, you nead in them.

---

### Post by smdeep on 2007-02-12
You can install monit to restart services if they fail. monit can email you too so you can login immediately and check why the service failed. I have personally tested out monit and it is really a cool script.

HTH

---

### Post by cap10kirk on 2007-02-12
I just had to restart again, so I checked the error log. The server is constantly logging the following error:
[error] an unknown filter was not added: PHP
I have hundreds of those errors logged

Now I believe this next error is causing me to restart:
[error] server reached MaxClients setting, consider raising the MaxClients setting

The only other oddity is this:
[error] [client 208.254.45.254] Invalid method in request \x80@\x01\x03

And finally, I believe this is logged when I restart:
[notice] caught SIGTERM, shutting down
[Mon Feb 12 14:25:56 2007] [notice] suEXEC mechanism enabled (wrapper: /usr/lib/apache2/suexec2)
[Mon Feb 12 14:25:56 2007] [notice] FastCGI: process manager initialized (pid 27232)
[Mon Feb 12 14:25:58 2007] [notice] Apache/2.0.55 (Ubuntu) mod_fastcgi/2.4.2 PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a mod_perl/2.0.2 Perl/v5.8.7 configured -- resuming normal operations

any help would be greatly appreciated,
Kirk

---

