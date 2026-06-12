---
title: "htaccess help"
date: 2008-02-19
forum: Server Platforms
---

### Post by timboellis on 2008-02-19
I have tried all the foums and cannto seem to get it working, all i am trying to do is setup my server so that you have to enter a password as soon as anyone hits it just 1 username/password to var/www

Any help

---

### Post by lncoll on 2008-02-19
Is not very clear but I suppose you want password access to selected directories not all the web.
To do this create an .htaccess in the directory you want password access and include in it:

```

AuthType Basic
AuthName "Restricted Files"
AuthUserFile /usr/local/apache/passwd/passwords
Require user username

```

Also you must create the password for the user this way:

```

# htpasswd -c /usr/local/apache/passwd/passwords username

```

This must be done in a perfolder basis not in the webroot folder.

---

