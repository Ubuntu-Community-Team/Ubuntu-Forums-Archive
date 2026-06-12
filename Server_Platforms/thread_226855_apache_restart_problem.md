---
title: "apache restart problem"
date: 2006-07-31
forum: Server Platforms
---

### Post by verbatim210 on 2006-07-31
**when i restart apache this happens...**

[I] * Forcing reload of apache 2.0 web server...                                                                                                                                : No such file or directorybled/*.load
: No such file or directorybled/*.conf
: No such file or directorynf
: No such file or directorynf
: No such file or directory^.#]*
: No such file or directorynf
: No such file or directoryabled/[^.#]*
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 4202) already running[/I]

**i have no idea what this means, suggestions appreciated :)**

---

### Post by veza on 2006-08-04
Hi there!

Did you do some changes to apache's conf ( /etc/apache2/ apache2.conf ? )

---

### Post by verbatim210 on 2006-08-05
hi,

i copied the conf file from my old ubuntu installation to save myself from re-configuring apache2 manually.  

obviously it was corrupted somewhere along the way because when i installed the default conf file and edited the settings again manually it worked.

verbatim

---

