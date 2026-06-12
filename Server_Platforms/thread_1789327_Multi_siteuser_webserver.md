---
title: "Multi site/user webserver"
date: 2011-06-23
forum: Server Platforms
---

### Post by scooterskin on 2011-06-23
I have setup a lamp server on my dedicated server using 10.04, created 3 vhosts for each domain which are located in /var/www/mysite etc which works fine.
However i would really like to have each domain linked to a different user and the files located in there directories example /home/mark/public_html how would i set this up?
In the past i have always used cpanel and CentOS. 

I have read something about prefork but could'nt find any info on setting it up.

---

### Post by falko on 2011-06-23
Just change the DocumentRoot to /home/mark/public_html in the Apache vhost configuration file.

---

### Post by ruffEdgz on 2011-06-23
> **falko said:**
> Just change the DocumentRoot to /home/mark/public_html in the Apache vhost configuration file.

To take this a step further with this post, you can make separate files for each site/domain you want to get working using that <VirtaulHost> suggested above. For example:
---
Create new apache config file related to your domain:
```

sudo touch /etc/apache/sites-available/<domain name>

```
**<domain name>** = the name of the file related to your site

Edit the new file and use the code below to start it:
```

<VirtualHost domain.com:80>
   DocumentRoot /home/mark/public_html
   ServerName domain.com
   ...
   ...
   ...
</VirtualHost>

```

Once you are done with the configuration, you can symlink of that config into the sites-enabled directory:
```

sudo ln -s /etc/apache2/sites-available/<domain name> /etc/apache2/sites-enabled/00X-<domain name>

```
**<domain name>** = the name used from the first step
**00X** = helps with making sure certain configs are above others if needed

Restart the apache service to make sure all the changes are taken:
```

sudo service apache2 restart

```

I hope this helps and here is a link to some more documentation on apache2: [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

---

### Post by scooterskin on 2011-06-24
Thanks guys that worked :) one other question is there a way to setup a limit to the amount of connections to just one of the vhosts, as its running Zsync and i need a limit so it can then go move to the next mirror.


maybe this should be in a new thread?

---

