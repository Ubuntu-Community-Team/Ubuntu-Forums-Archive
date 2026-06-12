---
title: "failing to setup nginx virtual host, custom site pointing to default welcome page"
date: 2013-01-16
forum: Server Platforms
---

### Post by xihad on 2013-01-16
This is what i did:

1. installed nginx. when i go to my ip it shows welcome page of nginx so all going fine.
2. created /var/www/mydomain folder and put a index.html there. Then i changed the document root in /etc/nginx/sites-enabled/default . it works too. it shows my custom index.htm

3. copied the default file in sites-available/mydomain.com and changed document root there to: /var/www/mydomain. Then made a symlink of this file to sites-enabled/mydomain.com

4. restarted nginx. Then i went to mydomain.com and it shows the same default welcome page of nginx. if i remove the default file from sites-enabled mydomain.com shows a blank page.

where i am doing wrong? please help.

i am using ubuntu 12.04 64 bit server.

---

