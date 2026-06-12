---
title: "apache2 + php =&gt; routing error"
date: 2005-12-23
forum: Server Platforms
---

### Post by goneskiing on 2005-12-23
when I type "http://localhost/mytest.php" I get an error "routing error /mytest.php"  My mytest.php file is in /var/www - do I need to specify something in apache2.conf ?  I don't see a DocumentRoot setting in the conf file.   thks for any help.

---

### Post by Koybe on 2005-12-24
The DocumentRoot directive is set ine the default website of apache2, you can have a look [here](https://wiki.ubuntu.com/ApacheMySQLPHP) if you want to know howto.

---

### Post by goneskiing on 2005-12-24
sorry, but I just do not know where that setting is.  I do not see it in userdir.conf.  btw, I had previously created a ruby rails app that created a file in sites-available with a link to enabled-sites which specified a document root - maybe that is overriding ?  If so, I'm wondering how I keep my ruby and php apps apart?

---

### Post by Koybe on 2005-12-24
Yes it's probably overriding with the default website.
You'll find userdir as a mod in /etc/apache2/mods-available ;)

---

### Post by goneskiing on 2005-12-24
okay, I guess the <Directory /home/*/public_html> is what gets changed to something like <Directory /var/www> ?

---

