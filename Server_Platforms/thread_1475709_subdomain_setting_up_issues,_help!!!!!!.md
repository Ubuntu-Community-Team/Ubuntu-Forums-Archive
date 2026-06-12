---
title: "subdomain setting up issues, help!!!!!!"
date: 2010-05-07
forum: Server Platforms
---

### Post by AresArtemis1 on 2010-05-07
**hi, any professionals, friends, I have been reading many** **Virtual Hosts configuration** [B]article  such as the following help link: 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[http://www.freelydifferent.com/self-hosting/lamp-for-linux-apache-mysql-php/](http://www.freelydifferent.com/self-hosting/lamp-for-linux-apache-mysql-php/)

almost all article are tutoring how to setting up a subdomain name like this:

subdomainwebsitename.my domain name(FQDN).com

any professional please tell me how to setting up a subdomain name like this:

[/B][B]my domain name(FQDN).com/subdomainwebsit

I want the url subdomainname is put behind the my domain name, not in front of my domain name, help!

best thanks,
:guitar::guitar:
[/B]

---

### Post by volkswagner on 2010-05-07
I don't see the need for setting up individual virtual hosts, if they are all the same domain.  You should just set up one virtual host with your domain, and all requests with the trailing slash will work.

Just put the web files in each subdirectory and you should be very happy.

---

### Post by terazen on 2010-05-07
If the documentroot for your site (somesite.com) is /var/www and you are looking to create somesite.com/foo then create a folder called foo and copy it to the /var/www directory.

When you go to somesite.com/foo in your web browser the apache process will look in /var/www/foo and serve the first index file it finds.  The list of index files is configurable in /etc/apache2/apache2.conf.  The line to look for looks like: ```
DirectoryIndex index.html index.cgi index.pl index.htm index.php index.xhtml
```

You can also create aliases and links, but that's usually unnecessarily complicated unless you have a reason.

---

