---
title: "permissions"
date: 2012-05-31
forum: Security
---

### Post by Inderpreet Singh on 2012-05-31
i have added a new user and now i want that it can run commands like svn update and svn commit in  /var/www/html but it can not delete any  directories and files from /var/www/html. 

Can anybody help me how is this possible??

---

### Post by sisco311 on 2012-05-31
In order to delete files from /var/www/html the user shall have search permission for html and for all its parent directories and write permission for html.

[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by Inderpreet Singh on 2012-05-31
ok..thanks its done using ACL and Sticky bit

---

