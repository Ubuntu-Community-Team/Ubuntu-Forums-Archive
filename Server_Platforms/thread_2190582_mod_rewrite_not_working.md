---
title: "mod_rewrite not working"
date: 2013-11-28
forum: Server Platforms
---

### Post by Maheriano on 2013-11-28
I've got apache2 set up on my desktop computer with an alias named test. When I want to view the website, I simply visit 192.168.1.166/test and I see the website. I've been wanting to learn mod_rewrite so I followed a very simple tutorial online but it doesn't seem to be working. I've made 2 HTML pages:
- alice.html
- bob.html
Both of them have nothing but the words alice or bob inside them, no markup. I placed a .htaccess file in my /var/www/test directory where the website files are and this is what's inside it: ```
RewriteEngine on
RewriteRule ^alice.html$ bob.html
``` Then I try to visit 192.168.1.166/test/alice.html and it shows me the alice page. It should be showing me bob but it isn't. What have I got done wrong? Is it because I'm using an alias instead of an actual hosting server?

---

### Post by kenetik on 2013-11-28
Have you installed & enabled the mod?

```

sudo a2enmod rewrite

```

---

### Post by Maheriano on 2013-11-28
Yes sorry, I forgot to mention I just installed it, restarted Apache and checked the phpinfo to confirm it's running.

---

