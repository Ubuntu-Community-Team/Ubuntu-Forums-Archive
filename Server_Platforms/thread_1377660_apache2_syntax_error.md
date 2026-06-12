---
title: "apache2 syntax error"
date: 2010-01-10
forum: Server Platforms
---

### Post by bluedrakonis on 2010-01-10
I get this error when trying to restart apache

syntax error on line 59 of /etc/apache2/sites-enabled/www..mydomain.com.v
host:
invalid command 'suPHP_Engine', perhaps misspelled or defined by a module not included   in the server configuration

                                                                                                                   [fail]

any ideas?

---

### Post by noway2 on 2010-01-10
There may be a bug that you are running into.  See: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=304018](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=304018) and try googling the term "suPHP_Engine".

---

### Post by bluedrakonis on 2010-01-12
This fixed it:

aptitude install libapache2-mod-suphp



thanks for the help though

---

