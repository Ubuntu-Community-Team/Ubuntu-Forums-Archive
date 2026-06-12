---
title: "localhost server serves unparsed files"
date: 2015-10-07
forum: Server Platforms
---

### Post by netcom61 on 2015-10-07
Hi
I've installed a localhost development server on my 14.04 desktop,  and when i access the server through localhost/wordpress, it serves the pages properly, ie: it parses the php and sends the page to the browser, however, when i access the server through local lan from another machine, ie:192.168.0.14, I'm served unparsed files.   

Any suggestion how to change this so the machine will parse the php etc when accessed from another machine, locally or through the web.   -- Thanks

---

### Post by SeijiSensei on 2015-10-07
Did you create a custom configuration for this website by creating a .conf file in /etc/apache2/sites-available/ and activating it with a2ensite, or did you simply place the wordpress installation under /var/www/html?  If you created a .conf file, please post it here inside [noparse]```

```[/noparse] tags.

---

### Post by netcom61 on 2015-10-07
no conf file... the file/folder are simply place under /var/www/html  ...  should i make one?  and what should it say?   and does it matter that the php is parsed locally, but not when viewed over the lan?

---

