---
title: "Hobbit Appache Problem"
date: 2008-09-11
forum: Server Platforms
---

### Post by tcanthonyii on 2008-09-11
I'm having a problem getting some of my CGI webpages working on a machine other than the server.  I get the error :

Forbidden

You don't have permission to access /hobbit-cgi/bb-hostsvc.sh on this server.

Apache/2.2.8 (Ubuntu) Server at 192.168.7.99 Port 80


I know it's a permissions issue somewhere but this is my first go around with apache and I haven't used linux in over 5 years so i'm extremely rusty.

Any help is appreciated.

Thanks

T.C.

---

### Post by luccom on 2008-10-20
Did you change the security in /etc/apache2/conf.d/hobbit ?
 Allow from localhost ::1/128 

will only alloy access from the local server.

---

