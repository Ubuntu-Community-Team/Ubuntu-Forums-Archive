---
title: "Apache MPM ITK - AssignUserId as Variables, Is It Possible?"
date: 2012-05-01
forum: Server Platforms
---

### Post by robson9776 on 2012-05-01
Hi,

I heard that MPM-ITK module for Apache can change Apache server's behaviour to access some folder / file using UID or GID from default UID (www-data) into given UID on the configuration.

for example :
<IfModule mpm_itk_module>
AssignUserId user group
</IfModule>

my question is… is it possible to make the username and group as variable?

Because I want to make Apache to access /home folder as its owner. For example /home/me can be access only by username 'me'. While /home/you can be access only by 'you'.

thanks!

---

