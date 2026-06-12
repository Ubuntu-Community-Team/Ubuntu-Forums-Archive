---
title: "PHP access to a system foler - how?"
date: 2007-04-01
forum: Server Platforms
---

### Post by mattiashswe on 2007-04-01
In my site users www folder I have a folder that the web app needs access to.
What owner/group shall it have and what permissons?
Right now it looks like this (and it is not working as it should):
drwxrwx--- 3 www-data pictureusers  4096 2007-04-01 00:21 pictures

---

### Post by shufla on 2007-04-24
PHP (in default configuration) is using www-data user and www-data group. You have to keep in mind, that directory above your 'pictures' have to be accesible by apache2 server. Look at tree of directories to check access.

Also look at /var/log/apache2/error.log while trying to access this resource and/or enable php logging into syslog or file to check it by PHP function.

Do you have safe_mode enabled?

Bye,
Shufla

---

