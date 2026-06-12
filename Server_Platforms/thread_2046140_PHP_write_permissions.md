---
title: "PHP write permissions"
date: 2012-08-22
forum: Server Platforms
---

### Post by soundguyfyi on 2012-08-22
So I have a php script that I am installing on my ubuntu server. The php script that I have has an install via browser after copying the code files in. I go through the setup and on the last page it says it cannot write (create) the .htaccess file or the config.cfg file. 

Any ideas what I need to do to get permissions for the files to be made?

---

### Post by SeijiSensei on 2012-08-22
Any files written by the apache web server will have user and group "www-data", the user and group that the server runs under.  So any directory into which such files need to be written must be writable by the www-data user.

---

### Post by soundguyfyi on 2012-08-22
Okay that solve the config file issue. But I'm still having issue with the .htaccess. Would that need something different?

---

### Post by SeijiSensei on 2012-08-22
.htaccess files are disabled by default in Ubuntu.  If you look at /etc/apache2/sites-available/default, you'll see an "AllowOverride None" entry for both / and /var/www.  You can either [change]("http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride") these defaults or, better, place the directives that would have gone into .htaccess in the <Directory> stanza of the virtual host that pertains to the software you're installing.  If you change the defaults, you'll need to restart apache with "sudo service apache2 restart".

---

### Post by soundguyfyi on 2012-08-22
Sweet I went ahead and just changed the defaults to "AllowOverride All". Thanks a ton!

---

