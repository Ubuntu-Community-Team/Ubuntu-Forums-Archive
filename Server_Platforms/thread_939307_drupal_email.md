---
title: "drupal email"
date: 2008-10-05
forum: Server Platforms
---

### Post by gishaust on 2008-10-05
I have just installed drupal on my webserver. However when it tries to send an email  to create a new account, it will keep giving me an error that I could not be sent. Do I have to open a port or does anyone know how drupal sends email?

---

### Post by Drezard on 2008-10-05
> **gishaust said:**
> I have just installed drupal on my webserver. However when it tries to send an email  to create a new account, it will keep giving me an error that I could not be sent. Do I have to open a port or does anyone know how drupal sends email?

Im guessing you dont have an MTA (Mail server, such as postfix) installed? You need to have an SMTP server configured on the same box (I think, not sure whether you can use an SMTP server on another box). Then it'll send email that way.

Daniel

---

