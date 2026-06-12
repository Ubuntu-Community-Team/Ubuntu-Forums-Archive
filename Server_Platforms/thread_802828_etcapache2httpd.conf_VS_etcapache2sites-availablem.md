---
title: "/etc/apache2/httpd.conf VS /etc/apache2/sites-available/mysite"
date: 2008-05-21
forum: Server Platforms
---

### Post by JameoPotato on 2008-05-21
Whats the difference between the 2 files in the subject
/etc/apache2/httpd.conf VS /etc/apache2/sites-available/mysite

I want to set up a virtual host for my FQDN and I don't know where to put my:

NameVirtualHost (ip of server)
ServerName mydomain.com
<VirtualHost (ip of server)>
     ServerName
     DocumentRoot
</VirtualHost>

etc.

Do i put that in both or one or what is the difference?

---

### Post by spiderbatdad on 2008-05-21
According to apache2.conf: user configurations are included from httpd.conf. Some things just seem to work better there. For example the directive in apache2.conf to hide the .htaccess file is uncommented, but only worked when I copy it to httpd.conf. If I want to change the name of that file, I have to change it in apache2.conf. Also my AllowOveride All directive, while it should work from /sites-available/mysite in the directory section...it only works for the DocumentRoot when I add it to httpd.conf...go figure.

The virtual hosts file: /sites-available/mysite is included by link to /sites-enabled...assuming you have run: sudo a2ensite....this also a directive of apache2.conf:
> # Include the virtual host configurations:
Include /etc/apache2/sites-enabled/ 

---

