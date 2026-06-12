---
title: "Installation of dokuwiki after apt-get"
date: 2008-09-02
forum: Server Platforms
---

### Post by kurellajunior on 2008-09-02
Hi,

I scrambled through the forum and finally got dokuwiki working after using ```
sudo apt-get install dokuwiki
```. I changed the appropiate rights in the dokuwiki/apache.conf to access from everywhere and set the file owner to the apache user.

Fine that way. Now I tried to go through the install script /dokuwiki/install.php

Unfortunately it stops on 3 Errors: ```
    * unrecognised or modified dokuwiki.php (hash=9100fa9a18424bd097b5ab972d66412d)
    * /usr/share/dokuwiki/conf/users.auth.php already exists
    * /usr/share/dokuwiki/conf/acl.auth.php already exists
```
I can solve the last two by moving theses files to *.old. But I cannot solve the first one.

How it is ment to be to setup rights and Users the first time in dokuwiki on Ubuntu?

---

