---
title: "apache2"
date: 2009-07-13
forum: Server Platforms
---

### Post by sagar on 2009-07-13
hai friends .
I am new familiar with Ubuntu,but i am new to using it in a server environment.I have 3 domains, for simplicitys sake domain1,domain2, and domain3.i want to run domain1 in one vhost and domaine in another domain . 

can any one help me out ..........

---

### Post by Wim Sturkenboom on 2009-07-13
```

#
# Use name-based virtual hosting.
#
NameVirtualHost *:80

# catch-all
<VirtualHost *:80>
    ServerAdmin me@mydomain
    DocumentRoot /srv/httpd/htdocs
    ServerName btd-techweb02
</VirtualHost>

# site 1
<VirtualHost *:80>
    ServerAdmin me@mydomain
    DocumentRoot /home/wim/www/site1/web
    ServerName site1.btd-techweb02
    ErrorLog /var/log/httpd/error_log
    CustomLog /var/log/httpd/access_log common

#WimS
# this is required to prevent message 403 "Forbidden"
    <Directory "/home/wim/www/site1/web">
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>

# site2
<VirtualHost *:80>
    ServerAdmin me@mydomain
    DocumentRoot /home/wim/www/site2/web
    ServerName site2.btd-techweb02
    ErrorLog /var/log/httpd/error_log
    CustomLog /var/log/httpd/access_log common

#WimS
# this is required to prevent message 403 "Forbidden"
    <Directory "/home/wim/www/site2/web">
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>

```
Although Ubuntu uses a slightly different approach, the above is the general idea.

You can dump something like that in a file and include that file from the main configuration (httpd.conf), you can dump it directly in httpd.conf or you can follow the official Ubuntu route that I don't know (something with a2ensite and several files). Don't forget to restart apache after the changes.

---

### Post by R.Bucky on 2009-07-13
I use Name Based Virtual Hosting to host a little over a half-dozen sites with 1 ip. I would recommend having individual .conf files for each domain.
I wrote a blog posting about the configuration and extra steps needed [here]("http://buckycomputing.net/blog/hosting-2-domains-with-1-server/").Below is the stripped down code of what I use for each domain in the individual .conf files.

```
ServerName sitename.com
DocumentRoot /server/directory/
</VirtualHost>
<Directory /server/directory/>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

```

---

### Post by sagar on 2009-07-14
thanz for replies ..

---

