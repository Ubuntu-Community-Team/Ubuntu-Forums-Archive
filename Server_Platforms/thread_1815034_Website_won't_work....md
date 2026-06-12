---
title: "Website won't work..."
date: 2011-07-30
forum: Server Platforms
---

### Post by Terwax1 on 2011-07-30
Ok first time setting up my website.

I was with hostgator before that provided cPanel and i "believe" they used CentOS. 

Now that i have moved to a different host, unmanaged, i installed copy of ubuntu 10.04 LTS 32 bit.

the website is [www.terwax.com](www.terwax.com).

I have to put files under /var/www. So i put all the files there, including index.html (a file of joomla), but if you see the website yourself, it shows up blank page with some weird stuff.

Is there something i did wrong or missing?

---

### Post by tristrambrelstaff on 2011-07-30
Have you set up the file permissions so the web-server (group www-data) can read them?

---

### Post by brighty22 on 2011-07-30
Post the 'weird stuff'.

---

### Post by Terwax1 on 2011-07-30
I think not.

I am very new to this stuff and been following tutorials only.

When i contacted support, they said :The page that I see when I visit [www.terwax.com](www.terwax.com) appears to be an empty document root. You will want to make sure that you have your document root in your apache configuration set to /var/www. I hope this helps!

I re did everything and still no luck..
Theses are the tutorials i've been doing: [http://library.linode.com/](http://library.linode.com/)

---

### Post by Terwax1 on 2011-07-30
> **brighty22 said:**
> Post the 'weird stuff'.

Index of /

	Name	Last modified	Size	Description
Apache/2.2.14 (Ubuntu) Server at [www.terwax.com](www.terwax.com) Port 80

---

### Post by Terwax1 on 2011-07-30
If someone wants access to the website through ssh, i can provide user and password through PM.

---

### Post by lisati on 2011-07-30
I had a look and got what looks to me like an empty directory list. This can happen if there are no files in the directory. One possibility is that Apache has been directed to look somewhere other than /var/www for the content to serve.

---

### Post by Terwax1 on 2011-07-30
How can i get apache to look at var/www?

The whole joomla site is stored there.

I am using PuTTY. Exact command would be greatly appreciated.

---

### Post by Terwax1 on 2011-07-30
```
<VirtualHost 96.126.111.159:80>
     ServerAdmin webmaster@terwax.com
     ServerName terwax.com
     ServerAlias www.terwax.com
     DocumentRoot /srv/www/terwax.com/public_html/
     ErrorLog /srv/www/terwax.com/logs/error.log
     CustomLog /srv/www/terwax.com/logs/access.log combined
</VirtualHost>


```


That is what i put under /etc/apache2/sites-available/terwax.com

Also the tutorial says to do same thing for terwax.org as well, but i don't own terwax.org. Should i delete everything related to that or its necessary?

---

### Post by lisati on 2011-07-30
The line "DocumentRoot /srv/www/terwax.com/public_html/" is what is telling Apache where to look for the web content. If you've put your content somewhere else, you'll need to adjust that line to suit.

---

### Post by Terwax1 on 2011-07-30
```

<VirtualHost 96.126.111.159:80>
     ServerAdmin webmaster@terwax.com
     ServerName terwax.com
     ServerAlias www.terwax.com
     DocumentRoot /var/www/
     ErrorLog /srv/www/terwax.com/logs/error.log
     CustomLog /srv/www/terwax.com/logs/access.log combined
</VirtualHost>
```

Ok, so i "only" changed it to /var/www/ and left others the same. Still no luck.

I expected this to be fairly easy, but been quite a few days and people have no idea whats going on and can't check their status for profiles (there is a database behind for games)

---

### Post by Terwax1 on 2011-07-30
```
<VirtualHost 96.126.111.159:80>
ServerAdmin webmaster@terwax.com
ServerName terwax.com
ServerAlias www.terwax.com
DocumentRoot /srv/www/terwax.com/public_html/
ErrorLog /srv/www/terwax.com/logs/error.log
CustomLog /srv/www/terwax.com/logs/access.log combined
</VirtualHost>
<VirtualHost 96.126.111.159:80>
ServerAdmin webmaster@terwax.com
ServerName terwax.com
ServerAlias www.terwax.com
DocumentRoot /var/www/
ErrorLog /srv/www/terwax.com/logs/error.log
CustomLog /srv/www/terwax.com/logs/access.log combined
</VirtualHost>
<VirtualHost 96.126.111.159:80>
ServerAdmin webmaster@terwax.org
ServerName terwax.org
ServerAlias www.terwax.org
DocumentRoot /srv/www/terwax.org/public_html/
ErrorLog /srv/www/terwax.org/logs/error.log
CustomLog /srv/www/terwax.org/logs/access.log combined
</VirtualHost>
root@alphalinodiawano:~# /etc/apache2/sites-available/terwax.org
-bash: /etc/apache2/sites-available/terwax.org: Permission denied
root@alphalinodiawano:~# nano /etc/apache2/sites-available/terwax.org
root@alphalinodiawano:~# cat /etc/apache2/sites-enabled/*
<VirtualHost 96.126.111.159:80>
ServerAdmin webmaster@terwax.com
ServerName terwax.com
ServerAlias www.terwax.com
DocumentRoot /srv/www/terwax.com/public_html/
ErrorLog /srv/www/terwax.com/logs/error.log
CustomLog /srv/www/terwax.com/logs/access.log combined
</VirtualHost>
<VirtualHost 96.126.111.159:80>
ServerAdmin webmaster@terwax.com
ServerName terwax.com
ServerAlias www.terwax.com
DocumentRoot /var/www/
ErrorLog /srv/www/terwax.com/logs/error.log
CustomLog /srv/www/terwax.com/logs/access.log combined
</VirtualHost>
<VirtualHost 96.126.111.159:80>
ServerAdmin webmaster@terwax.org
ServerName terwax.org
ServerAlias www.terwax.org
DocumentRoot /var/www/
ErrorLog /srv/www/terwax.org/logs/error.log
CustomLog /srv/www/terwax.org/logs/access.log combined
</VirtualHost>
```

after running: cat /etc/apache2/sites-enabled/*

---

### Post by Terwax1 on 2011-07-30
ok this is the code now after i deleted example.org, example.com, terwax.net.

```
root@alphalinodiawano:~# cat /etc/apache2/sites-enabled/*
<VirtualHost 96.126.111.159:80>
     ServerAdmin webmaster@terwax.com
     ServerName terwax.com
     ServerAlias www.terwax.com
     DocumentRoot /var/www/
     ErrorLog /srv/www/terwax.com/logs/error.log
     CustomLog /srv/www/terwax.com/logs/access.log combined
</VirtualHost>
<VirtualHost 96.126.111.159:80>
     ServerAdmin webmaster@terwax.org
     ServerName terwax.org
     ServerAlias www.terwax.org
     DocumentRoot /var/www/
     ErrorLog /srv/www/terwax.org/logs/error.log
     CustomLog /srv/www/terwax.org/logs/access.log combined
</VirtualHost>

```


Still no luck :(

---

### Post by Terwax1 on 2011-07-30
Ok after changing few things i wanted to restart to see if it worked, but now getting this error


```
root@alphalinodiawano:~# /etc/init.d/apache2 restart
 * Restarting web server apache2                                         [fail]

```

---

### Post by Terwax1 on 2011-07-30
I had to delete the example.org and terwax.org within etc/apache2 folder as well.

After that i was able to restart and reload but now i get ```
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@terwax.com and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
```

This is what it says in the logs > Jul 30 14:17:31 2011] [alert] [client 119.63.196.89] /var/www/.htaccess: Invalid command 'RewriteEngine', perhaps misspelled or defined by a module not included in the server configuration


---

### Post by brighty22 on 2011-07-30
Rename the .htaccess file in the document root to something like htaccess.temp

---

### Post by Terwax1 on 2011-07-30
> It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

But where the heck is my website???

Also since joomla is based off MySQL, i need help finding that folder so i can transfer the data there. So far only put everything in the var/www.

---

### Post by brighty22 on 2011-07-30
You really need to start using Google. Delete index.html in /var/www

Export your current mysql database, then import it into the new server:
[http://www.google.co.uk/search?sourceid=chrome&ie=UTF-8&q=transfer+mysql+database]("http://www.google.co.uk/search?sourceid=chrome&ie=UTF-8&q=transfer+mysql+database")

---

### Post by Terwax1 on 2011-08-01
i just did a clean install of joomla because it wasn't working out.

Now i had the website forums.mysite.com.

How can i create the sub domain for that? I searched google and its just too confusing and i don't want to screw up my website further :(

I know it goes in .../site-available and then i have to enable the website.

Also [www.mysite.com](www.mysite.com) works but mysite.com doesn't. Is it to do with DNS or what? I did create 2 links under hosts with my registrar for the same IP that is used.

---

