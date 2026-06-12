---
title: "authentication in apache2"
date: 2009-10-22
forum: Server Platforms
---

### Post by dfgxcvrty on 2009-10-22
Hello,

I got a problem with authentication in Apache2. I put authentication to my page but i want that my page does not require a password when i connected to my page from a host with a dedicated ip address like 192.168.54.58  in Apache configuration so here is an example configuration:

[html]
<Directory /var/www/ee3.com/>
Options -Indexes +FollowSymLinks
AuthType Basic
AuthName "Login required"
AuthUserFile /var/www/users
AuthGroupFile /var/www/groups
require valid-user
require group cp_2
</Directory>
[/html]What i must add in the configuration?

Thanks.

---

