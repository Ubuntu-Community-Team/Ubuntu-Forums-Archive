---
title: "Apache not showing up in Webmin"
date: 2006-07-01
forum: Server Platforms
---

### Post by nameiwantistaken on 2006-07-01
I have webmin loaded onto the GUI in my LAMP server.  When I try to administer Apache with it, it says, "The Apache root directory /etc/apache does not exist. If you have Apache installed, adjust the module configuration to use the correct paths."  Apache packages show as installed.  Anyone know why this is happening?

---

### Post by rbalfour on 2006-07-01
the lamp server is apache2

so it's /etc/apache2

webmin hasn't been updated for the new apache2 yet.

---

