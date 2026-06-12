---
title: "just installed apache server locally, do I need to secure it?"
date: 2008-12-04
forum: Server Platforms
---

### Post by Orange Luna on 2008-12-04
hello all, i just installed apaches to run tinyrss on this server at localhost.  it runs great and all but I thinking I may need to add security to it.  do i?  will adding apache make a port open?  will others have access to it?  if i do, i'd appreciate any tips or references to guides that can help secure it.

---

### Post by Thirtysixway on 2008-12-04
Apache opens, by default, port 80.  If your computer is behind a router or good firewall, then it should not be open to the world so you're safe.  You can do a simple check at [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/) simply scan your IP and port 80.

---

### Post by cdenley on 2008-12-04
Any server opens a port. If it didn't, then it wouldn't be a server. Do you want it to be accessible only from the computer it's running on ([http://localhost/)?](http://localhost/)?) If so, edit /etc/apache2/ports.conf changing "Listen 80" to "Listen 127.0.0.1:80". Then restart apache:
```

sudo /etc/init.d/apache2 restart

```

---

### Post by Orange Luna on 2009-01-13
Thanks for the tip cdenley.  I'd thank you but the thanks button is off. :(  Also the secure port is a good idea to set to localhost.

---

### Post by Iowan on 2009-01-13
Hmmm... I was gonna reference [this]("https://help.ubuntu.com/community/ApacheMySQLPHP#Securing%20Apache") help page, but **cdenley** already covered it - almost exactly.

---

### Post by Orange Luna on 2009-01-14
Appreciate the reference - good help.  I don't have access to my ubuntu box right at this time but on my Gentoo box I had to redirect the ssl port too:

```
Listen 127.0.0.1:443
```

Just FYI.

---

