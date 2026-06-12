---
title: "How to enable .htaccess file on apache2"
date: 2009-12-11
forum: Server Platforms
---

### Post by tapas_mishra on 2009-12-11
I want to know how can we enable .htaccess file in apache2 is there any option in /etc/apache2/sites-available/
site configuration file that I need to mention it to be able to access .htaccess file.

---

### Post by Bachstelze on 2009-12-11
You have to put AllowOverrids directives in your Apache config file to allow settings to be overridden in a .htaccess.

---

