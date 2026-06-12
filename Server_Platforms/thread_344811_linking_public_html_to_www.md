---
title: "linking public_html to www"
date: 2007-01-23
forum: Server Platforms
---

### Post by docetes on 2007-01-23
hey 

i want to be able to allow users to have there own little webspace
like [www.example.com/~username](www.example.com/~username)

where the public_html would be in each users home folder

Cheers,
Dave

---

### Post by jtc on 2007-01-23
I assume we are talking about Apache2?

Then you need the module userdir loaded. I'm not sure if it is so by default. You can find out what modules you've enabled by looking at the symlinks in /etc/apache2/mods-enabled/

Otherwise this is the easiest way to enable it.

```
a2enmod userdir
```

To configure the it, edit /etc/apache2/mods-available/userdir.conf

You'll have to restart apache for the changes to take effect.

---

