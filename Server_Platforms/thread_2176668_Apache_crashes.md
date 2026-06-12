---
title: "Apache crashes"
date: 2013-09-25
forum: Server Platforms
---

### Post by jovan2 on 2013-09-25
My apache worked perfectly, and suddenly crashed. I am not sure what happend, but when i try to start it again, i get this error:

```
* Starting web server apache2                                                  Syntax error on line 1 of /etc/apache2/conf.d/fqdn.save:
Invalid command 'G', perhaps misspelled or defined by a module not included in the server configuration
Action 'start' failed.
The Apache error log may have more information.


```

Does anyone knows what is the problem?
I tried to edit or delete fqdn.save file, but I can't.

---

### Post by tgalati4 on 2013-09-25
Look in /var/log/apache for clues.

---

### Post by jovan2 on 2013-09-25
Last error is:

[Tue Sep 24 16:09:36 2013] [notice] caught SIGTERM, shutting down

What that can be?

---

### Post by SeijiSensei on 2013-09-25
> Syntax error on line 1 of /etc/apache2/conf.d/fqdn.save:
Invalid command 'G', perhaps misspelled or defined by a module not included in the server configuration

Look at the file /etc/apache2/conf.d/fqdn.save.  Do you see a "G" on the first line?  It's probably just a stray character that got added during editing.

---

### Post by jovan2 on 2013-09-26
But how I can open that file? I always get some error unkown format.

---

### Post by koenn on 2013-09-29
> **jovan2 said:**
> But how I can open that file? I always get some error unkown format.

with nano or vim, of course

what are you trying to open it with ?

---

