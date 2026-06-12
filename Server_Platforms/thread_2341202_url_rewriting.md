---
title: "url rewriting"
date: 2016-10-25
forum: Server Platforms
---

### Post by shad2 on 2016-10-25
Ihave apache mod rewite enabled on my machine ,and in my htaccess i have this```
<IfModule mod_rewrite.c>
# Enable mod_rewrite
RewriteEngine On
# Specify the folder in which the application resides.
# Use / if the application is in the root.
RewriteBase /testhtaccess
# Handle requests for "sign-in"
RewriteRule   ^horses.htm$   login.php 

</IfModule>


```
 but i cannot see horses.htm in the address bar.what iam i not doing? it still gives me
[http://localhost/testhtaccess/login.php](http://localhost/testhtaccess/login.php)

---

### Post by cariboo on 2016-10-26
You may get better and quicker help here.

---

