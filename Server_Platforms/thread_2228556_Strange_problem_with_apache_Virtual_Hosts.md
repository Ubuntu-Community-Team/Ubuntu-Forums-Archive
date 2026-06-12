---
title: "Strange problem with apache Virtual Hosts"
date: 2014-06-08
forum: Server Platforms
---

### Post by Stefan_Ashwell on 2014-06-08
I have an ubuntu 14.04 server set up with apache, and set up a subdomain A record to point to it (lets call it demo.). I also set up a virtual host in **/etc/apache2/sites-available** called **demo.domain.com.conf** that looks like this:


```
<VirtualHost *:80>
        ServerAdmin webmaster@domain.com
        ServerName demo.domain.com
        ServerAlias demo.domain.com
        DocumentRoot /var/www/html/demo.domain.com/httpdocs


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```


This has been running fine for around a month while I've been developing new things.


Now, to continue my work on the project I need a new subdomain (this one api.), so again I set up an A record to point to the server, and also created **api.domain.com.conf** in **/etc/apache2/sites-available** that looks like so:


```
<VirtualHost *:80>
        ServerAdmin webmaster@domain.com
        ServerName api.domain.com
        ServerAlias api.domain.com
        DocumentRoot /var/www/html/api.domain.com/httpdocs


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```


used **a2ensite api.domain.com.conf** to activate and restarted apache. However visiting the subdomain shows an apache2 ubuntu default page, not the contents of **/var/www/html/api.domain.com/httpdocs**. Much to my confusion!


After having a think about things, I decided that maybe the two subdomains needed to be in one conf file for the domain rather than one for each subdomain. So, I deactivated both virtual hosts with **a2dissite**, and created a new conf file in sites-available called **domain.com.conf** like so:


```
<VirtualHost *:80>
        ServerAdmin webmaster@domain.com
        ServerName demo.domain.com
        ServerAlias demo.domain.com
        DocumentRoot /var/www/html/demo.domain.com/httpdocs


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>


<VirtualHost *:80>
        ServerAdmin webmaster@domain.com
        ServerName api.domain.com
        ServerAlias api.domain.com
        DocumentRoot /var/www/html/api.domain.com/httpdocs


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```


Again, activated with **a2ensite** and restarted apache.


This is where the biggest confusion started. Nothing had changed. If I go to the demo subdomain I see exactly what I expect to see, but if I go to the api subdomain I still see the apache2 default page. To add to this confusion I deactivated my new virtual host too with **a2dissite** and restarted apache. Still the same - demo. works, api. doesn't.


This now doesn't make any sense at all, if I run the following command:


```
source /etc/apache2/envvars
/usr/sbin/apache2 -S
```


it tells me that there are no virtual hosts set up, but I can still visit demo. and see my development site, and still visit api. and see the default page. I'm now at a loss as to what's happening. I'm unable to troubleshoot and figure out any issues with my virtual host configuration because it seems virtual hosts are stuck in the old configuration somehow.


So, my main questions are A) how do I go about troubleshooting this issue in the first place, and B) if anyone has any ideas as to how I can get this resolved so I can continue working on the project itself rather than something as simple as setting up a new subdomain!


Any help much appreciated :)

---

### Post by TheFu on 2014-06-08
I think you are missing the "Directory" stanzas inside each v-host. For example:
```

        <Directory /var/www/html/api.domain.com/httpdocs/ >
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
                AddType text/html .shtml
                AddOutputFilter INCLUDES .shtml
                DirectoryIndex index.shtml index.html
        </Directory>

```

---

### Post by Stefan_Ashwell on 2014-06-09
I knew it would be something simple. Previously I was restarting apache with

```
service apache2 reload
```

However using

```
sudo service apache2 reload
```

has activated my virtual hosts and now everythings working!

---

### Post by TheFu on 2014-06-09
So - was it the missing stanzas or not?
Also, if you aren't certain when to use or not use sudo - time for a refresher course in multi-user OS permissions.

If things are solved, please close the thread as solved.

---

