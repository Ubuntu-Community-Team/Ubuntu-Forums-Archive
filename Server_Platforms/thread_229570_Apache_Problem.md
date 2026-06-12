---
title: "Apache Problem"
date: 2006-08-04
forum: Server Platforms
---

### Post by TimeKiller on 2006-08-04
Whenever I attempt to access these by name or IP I get a "you do not have permission to access / on this server" error. I'm not sure what the problem is. I don't get any errors when i reload apache. Anyone? Anyone? Beuller?



NameVirtualHost 0.0.0.0:80
<VirtualHost 0.0.0.0:80>
        ServerAdmin [email]webmaster@site1.com[/email]
        DocumentRoot /web1/site1.site1.com
        ServerName site1.site1.com
	ServerAlias site1.site1.com


        CustomLog /var/log/apache2/site1.site1-com.access_log combined
        ErrorLog /var/log/apache2/site1.site1-com.error_log
        AddType application/x-httpd-php .phtml
        DirectoryIndex index.phtml index.php index.html

        <Directory /web1/site1.icorpsdev.com>
                AddHandler server-parsed .html
                Options +IncludesNOEXEC
        </Directory>
</VirtualHost>

<VirtualHost 0.0.0.0:80>
        ServerAdmin [email]webmaster@site1.com[/email]
        DocumentRoot /web1/site2.site1.com
        ServerName site2.site1.com
	ServerAlias site2.site1.com

        CustomLog /var/log/apache2/site2.site1-com.access_log combined
        ErrorLog /var/log/apache2/site2.site1-com.error_log
        AddType application/x-httpd-php .phtml
        DirectoryIndex index.phtml index.php index.html

        <Directory /web1/site2.site1.com>
                AddHandler server-parsed .html
                Options +IncludesNOEXEC
        </Directory>
</VirtualHost>

---

### Post by chrisfay on 2006-08-05
This may be too obvious or something but have you tried to "chmod" the directories with a less restrictive permission setting? 

sudo chmod 777 -R /web1/site1.site1.com

Test it, then change it to something more restrictive once you know it works.

---

### Post by TimeKiller on 2006-08-07
> **chrisfay said:**
> This may be too obvious or something but have you tried to "chmod" the directories with a less restrictive permission setting? 

sudo chmod 777 -R /web1/site1.site1.com

Test it, then change it to something more restrictive once you know it works.

Yep been there done that. It still doesn't work. I'm pretty stumped at this point.

---

