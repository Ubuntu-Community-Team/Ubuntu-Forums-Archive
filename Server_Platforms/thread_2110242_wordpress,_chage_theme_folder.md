---
title: "wordpress, chage theme folder"
date: 2013-01-29
forum: Server Platforms
---

### Post by anerDev on 2013-01-29
Hi guys !

I installed wordpress on this directory: /var/www/wordpress 
How can I set this folder /media/hd-dati/www/wp-theme for the default wp theme ?

Thank you

---

### Post by anerDev on 2013-01-30
Up

---

### Post by volkswagner on 2013-01-30
Perhaps it would help to explain why you would want to do this.

You may also get more expert help from Wordpress forum.

I'm not sure about the inner workings of Wordpress, but this does not seem like a good idea to me.  I think you will be creating a delicate environment which could easily break during updates/upgrades.

I'd suggest move or copy the content to the proper location.

cp   /media/hd-dati/www/wp-theme  /var/www/wordpress/wp-content/themes/

---

### Post by anerDev on 2013-01-30
Thank you !

I go to hask to WP forum

---

### Post by anerDev on 2013-01-31
Resolved with this:

```
ln -s /media/hd-dati/www/wp-theme /var/www/wordpress/wp-content/themes
```

---

### Post by SeijiSensei on 2013-01-31
Why don't you just use the built-in Wordpress functions to manage themes?

---

