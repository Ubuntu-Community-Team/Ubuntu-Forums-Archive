---
title: "Problems whit httpd.conf and Wordpress installation"
date: 2011-06-17
forum: Server Platforms
---

### Post by mirna89 on 2011-06-17
I'm installing Wordpress and I want Hosting Multiple Sites with them. For that I need modify the httpd.conf file but it's empty. Where I can make that changes?
These are the  changes: 
1. Type:
LoadModule rewrite_module /libexec/mod_rewrite.so

2.  Find the <VirtualHost> section in the httpd.conf file.

3. Find a line in the <VirtualHost> section of the httpd.conf that 
looks like this:
AllowOverride None

3. Replace that line with this line:
AllowOverride FileInfo Options

4. On a new line, type ServerAlias *.yourdomain.com.
 
5.  Save the httpd.conf file and close it.

Please,](*,) Helpme!!!

---

### Post by cariboo on 2011-06-17
You don't enable sites in /etc/apache2/http.conf any more, use sites available instead. Use a2ensite to enable more web sites. For more info, have a look [here]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html")

---

