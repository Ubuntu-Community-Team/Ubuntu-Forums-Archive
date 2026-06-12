---
title: "Module placeholder.so"
date: 2008-09-10
forum: Server Platforms
---

### Post by makekee on 2008-09-10
Been tyring to install evergreen library system on ubuntu.After installing apache and trying to start it, it gives me the following message Syntax error on line 3 of /etc/apache2/httpd.conf:
Invalid command '/usr/lib/apache2/modules/mod_placeholder.so', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]

I have looked for the module mod_placeholder.so everywhere in the apache folders and its not there. what must i do.

Ephraim

---

### Post by inphektion on 2008-09-10
look on line 3 of your httpd.conf.  if you see a "-e" there delete it.

---

### Post by makekee on 2008-09-11
> **inphektion said:**
> look on line 3 of your httpd.conf.  if you see a "-e" there delete it.
there is no "-e" on line 3. is there a way of downloading individual apache modules?

---

### Post by windependence on 2008-09-11
It looks like this line somehow got uncommented. It is part of the documentation in the apache2.conf file. Find this line in your conf file and comment it out like this:

```
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
```

Then, try restarting Apache.

-Tim

---

