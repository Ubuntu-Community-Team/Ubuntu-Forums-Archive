---
title: "Php can't create files"
date: 2009-12-05
forum: Server Platforms
---

### Post by shiggydiggy on 2009-12-05
Lighttpd & PHP runs but it can't create files. For example if I had an image upload script. It can't create files on the webserver.
I'm running lighttpd as root, what else is there to do?

---

### Post by shiggydiggy on 2009-12-05
bump

---

### Post by BkkBonanza on 2009-12-05
This is probably a permissions problem. Even though Lighttpd starts as root it usually doesn't run as root for handling web requests. I don't recall off hand what it does for PHP but I'm quite sure it also drops root privileges for that as it would be a huge security threat. 

You should look for what user it runs PHP as. This should show up in ps afx or top. That is the user that needs to have write privileges. Often this is user www or www-data or apache sometimes. Note also that you can't create files in a directory without having execute privileges on the directory. So the privileges would typically be 750 admin:www or similar.

---

### Post by shiggydiggy on 2009-12-06
how do i check which user it runs php as?

---

