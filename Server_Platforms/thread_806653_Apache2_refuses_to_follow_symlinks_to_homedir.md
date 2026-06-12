---
title: "Apache2 refuses to follow symlinks to homedir"
date: 2008-05-25
forum: Server Platforms
---

### Post by randomstuff on 2008-05-25
I have just wasted one hour trying to get apache2 to show the files that I have in a folder inside my homedir. I am not using the server edition btw, plain regular 7.10 Desktop, 32bit.

I have tried everything:
 - setting the document root to be the folder in homedir as well as leaving it at /var/www
 - generously setting "FollowSymlinks" options for all Directories in the default host
 - applying 755 permissions to the folder and its contents
 - added .htaccess file in /var/www specifying "Options +FollowSymlinks"
 - set "AllowOverride All" or all Directories in the default host

It just won't work. I refuse to copy my web development projects to the stupid /var/www folder - which is not part of the /home/partition and thus requires extra backup measures.

What can I do to make it work?

---

### Post by floydwilde on 2008-05-25
I have my home directory on a raid1 partition, and var mounted on a non raid partition, so I also did not want to put my http docs in /var/www.  /var is for logs and other things I never look at.  

the only things i changed in /etc/apache2/site-available/default were:

        DocumentRoot /home/john/Working/pub_html/
     
        <Directory /home/john/Working/pub_html/>

and it works fine for me. Shouldn't have to add a .htaccess anywhere.  thats just crazy.

oh yeah and don't forget to restart Apache.

---

### Post by randomstuff on 2008-05-25
It still won't work. I keep getting 403 error messages, even though everybody has permissions to read the directory.

---

### Post by randomstuff on 2008-05-25
Ok, I don't know what's wrong with my system, but now it's completely screwed  up.

Even after selecting all "apache2" packages in synaptic, selecting "remove completely" and then reinstalling, I cannot even get the default /var/www/ directory to work any more. (error log says: "[Sun May 25 17:39:10 2008] [error] [client 127.0.0.1] File does not exist: /htdocs")

I have also tried configuring apache through webmin, but it seems to do no better than me.

Trying to get the userdir mod to work has also failed in all attempts, using webmin, a2enmod, manually symlinking - nothing works.

Could this be related to group/user permissions? what can I possibly do to get my webserver up and running? It's not really supposed to be *this* hard, is it?

---

### Post by MJN on 2008-05-25
Post your config then we can take a look.

Mathew

---

### Post by randomstuff on 2008-05-25
I have uploaded most of my /etc/apache2/ directory contents to [my webserver]("http://cornergraf.net/files/apache_config/").

I doubt it'll help much though, since I have reinstalled several times and tried many things, without any luck.

so I suspect the problem must be more general to my system. I just have no idea where to look.

Thank you for trying to help though.

---

### Post by MJN on 2008-05-25
Your config is a little confusing given you've got multiple webmin-created sites however given that **sites-enabled/000-default** is empty we'll concentrate on the only other enabled site - **sites-enabled/webmin.1211729846.conf**:

```
<VirtualHost *>
DocumentRoot /var/www/apache2-default
<Directory "/var/www/apache2-default">
allow from all
Options +Indexes
</Directory>
UserDir "public_html"
</VirtualHost>
```Change DocumentRoot to the directory in the home directory you want to serve, and edit the <Directory> directive to suit. Then make this web directory, and all parent directories, have read/execute permissions for Apache (user 'www-data') and see how you go...

Mathew

---

### Post by Surtsey on 2008-07-14
I was having a problem that sounded quite similar (I found this thread searching for a fix).  It turned out one of the parent directories of what I was trying to ask Apache to open had slightly barring permissions.  Frustratingly simple problem after all the irritation it caused.

Cheers.

---

### Post by f37u5g0d on 2008-07-15
I had this similar problem.  Create a "htdocs" folder in /.  You can make it a link to any folder you like.  Put your website in htdocs or in the dir that htdocs points to.  This is what I had to do to get my website up.  I figuered it out by reading the /var/logs/apache2/error log.  It is weird and I am trying to figure it out right now.

---

### Post by windependence on 2008-07-16
FYI, Apache 1.3 uses a default document root of /var/www/htdocs. This is probably what you were seeing.

-Tim

---

### Post by freerkkalsbeek on 2009-01-14
If you want homedirs to be accessible through Apache, then you probably best enable module userdir

a2enmod userdir

After a restart you can access the public_html in your users homedir through [http://hostname/~username/](http://hostname/~username/)

---

### Post by trungly on 2009-06-09
I had a similar problem to what the OP had.  In the end, the problem was the user's home folder where the Docroot resides had a permission of 700.  I changed it with:
    ```
chmod 755 /home/username
``` and that fixed it.

Hope that helps someone who stumbles on this thread from google (like I did).

---

### Post by ernz on 2012-03-10
Trungly's advise worked for me.

Overall steps (from clean install) were:

1) Create symlink from /var/www to /home/ernz/www

```
sudo ln -s /home/ernz/www /var/www
```

2) Change permissions on my home directory

```
chmod 755 /home/ernz
```

---

