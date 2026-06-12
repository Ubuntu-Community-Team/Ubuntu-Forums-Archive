---
title: "[SOLVED] Locally Developed Websites Not Showing"
date: 2009-01-06
forum: Server Platforms
---

### Post by arnold.pietersen on 2009-01-06
Hi

When I used 7.04, all my locally developed websites will show when I typed [http://localhost](http://localhost).

I have upgraded to 8.10, installed LAMP using Synaptic and the message: **It works!** came up when I typed [http://localhost](http://localhost).  I have subsequently restored the /var/www from the backup to /var/www on the laptop.  However, it does not show the websites; only the **It works!** message.

Any help will be appreciated.

---

### Post by Vegan on 2009-01-06
I use a different location. Try:

```
sudo chmod 777 /var/www
```

and see if that works

also check you vhost files

---

### Post by arnold.pietersen on 2009-01-06
Hi Vegan

I tried the command you gave.  It still says: It works!

Also, where do I locate the vhost file and what should I be looking for.

Thanks

---

### Post by volkswagner on 2009-01-06
Vhost configs go in /etc/apache2/sites-available.  Active sites go into /etc/apache2/sites-enabled when using the a2ensite command.

Perhaps your restored www folder did not overwrite the index.html.  Without knowing your setup, how many sites etc. you may just need to disable the default site.

First list your enabled sites
```
ls -alt /etc/apache2/sites-enabled
```


```

sudo a2dissite default
```

If the default site is the only one enabled you may just want to list your www folder and see if it is an index.html issue.

---

### Post by Iowan on 2009-01-06
> **volkswagner said:**
> 

...Perhaps your restored www folder did not overwrite the index.html...   Or perhaps it didn't originally have one? You can rename index.html (remember to use **sudo)** just to see what happens.
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP") help page should provide some useful tips about creating virtual sites.

---

### Post by arnold.pietersen on 2009-01-07
Hi 

The problem has been solved. I proceeded as follows:

1. There is no vhost file in the /etc/apache2/sites-available folder.  Instead it shows 2 files, namely: default and default-ssl

2. The /etc/apache2/sites-enabled folder shows the following line:
lrwxrwxrwx 1 root root   26 2008-12-30 17:07 000-default -> ../sites-available/default

3. There is no index.html file in the restored (/var/www) folder.

4. The following are the results for the command **$ ls -alt /etc/apache2/sites-enabled**:
total 8
drwxr-xr-x 7 root root 4096 2008-12-30 17:07 ..
drwxr-xr-x 2 root root 4096 2008-12-30 17:07 .
lrwxrwxrwx 1 root root   26 2008-12-30 17:07 000-default -> ../sites-available/default

5. For the command **$ sudo a2dissite default** it indicates that the site default has been disabled.

6. When I type **$ /etc/init.d/apache2 reload**, the following information appears:

 * Reloading web server config apache2                                                                                                                       apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Jan 07 08:26:50 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

Is there anything to worry about the information which appeared?

Thanks for the assistance, it is appreciated

Now I need to sort out the phpMyAdmin.

---

### Post by arnold.pietersen on 2009-01-07
Hi 

I now get a **404 Not found** messages.  I most probably need to create a new thread.  But just to let you know.

phpMyAdmin did not appear on the list.  I subsequently installed phpMyAdmin using **$ sudo apt-get install phpmyadmin**. Now I get the 404 message.  Typing in the IP address: [http://41.213.36.123](http://41.213.36.123) does not help either.

Cheers

---

### Post by volkswagner on 2009-01-07
Trying to follow what you did.  If you had only the default site enabled, then disabled it, do you have any sites currently enabled?

---

### Post by Iowan on 2009-01-07
> **arnold.pietersen said:**
> 
 * Reloading web server config apache2                                                                                                                       apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
That one is covered in the link I gave you... but it's cleaner to edit your **hosts** file and add (or modify) the line:```
127.0.1.1 <hostname>.<domainname>  <hostname>

```
You can probably do without the <hostname>.<domainname> portion. <hostname> represents your server name.

As **volkswagner** pointed out, the other error message(s) might be due to having no sites enabled.

---

