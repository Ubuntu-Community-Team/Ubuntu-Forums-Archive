---
title: "HTTP 404 in my virtual hosts"
date: 2012-01-11
forum: Server Platforms
---

### Post by peprex on 2012-01-11
Hi,
 
I've been searching if any of the previous threads work for me, but i'm stacked. I'm working with an VPS with ubuntu server 11.10 with ip, let's say : 40.40.40.40
 
I have already installed apache2 , php5 and mysql. And [http://40.40.40.40](http://40.40.40.40) "It works!" on the browser :D
 
So I pretended to start working with virtual hosts. In the end, when I resolve [http://40.40.40.40/mydomain.com](http://40.40.40.40/mydomain.com) in the browser, I get 404 :S . I'm telling what I did step by step :
 
First I went to /etc/hosts and add the line : 40.40.40.40      mydomain.com
 
Then, created a new file in /etc/apache2/sites-available named mydomain.com . Here you can see what the file mydomain.com contains :
 
<VirtualHost *:80>
        ServerName mydomain.com
        DocumentRoot /var/www/virtuals/mydomain.com
        <Directory /var/www/virtuals/mydomain.com/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
        </Directory>
</VirtualHost>
 
The folder /etc/apache2/sites-available also contains two more files : default and default-ssl . I did not touch them, I promise !
 
Next, I run the command : a2ensite mydomain.com
And I make sure that there are two symlinks in the /etc/apache2/sites-enabled folder , one called 000-default and the other called mydomain.com. Both seem to point the right files in the sites-available folder.
 
So I mkdir in /var/www/virtuals/mydomain.com and put a index.html there containing a "hello world".
 
Finally I /etc/init.d/apache2 reload and get to the browser with [http://40.40.40.40/mydomain.com](http://40.40.40.40/mydomain.com) . You know the rest (dammed 404).
 
Please, I need help, I don't know what's happening. Any ideas?
 
Thanks in advance,
Pep

---

### Post by volkswagner on 2012-01-11
Try just [http://mydomain.com](http://mydomain.com).

According to your vhost file to access using the ip of the machine you would need to enter the following in the url.

[http://40.40.40.40/virtuals/mydomain.com](http://40.40.40.40/virtuals/mydomain.com)

```

<VirtualHost *:80>
ServerName mydomain.com
DocumentRoot /var/www/virtuals/mydomain.com
<Directory /var/www/virtuals/mydomain.com/>
Options Indexes FollowSymLinks MultiViews
AllowOverride All
</Directory>
</VirtualHost>
```

---

### Post by peprex on 2012-01-11
Hi ,
 
Actually the domain.com we are talking about is online and running. So when I use [http://domain.com](http://domain.com) , I'm going to the actual website. What we need is [http://40.40.40.40/mydomain.com](http://40.40.40.40/mydomain.com) for testing, because we want that vps to be a server for testing and developement.
 
Why the actual sites-available configuration mydomain config file gives as a result that only [http://40.40.40.40/virtuals/mydomain.com](http://40.40.40.40/virtuals/mydomain.com) ? (because you were right, when I query that url from my home browser, it works !)
 
And how I could be able to use [http://40.40.40.40/mydomain.com]("http://40.40.40.40/virtuals/mydomain.com") ? What modifications should I do ?
 
Thanks!

---

### Post by peprex on 2012-01-11
Hi !
 
I'm glad to tell you that I finally solved it ! The problem is that when you install apache2, it creates a default config file in the sites-available folder.
 
This default config file points to /var/www folder. But I want to store all my virtual hosts stuff in the /var/www/virtuals (as you can see in my mydomai.com config file up there). So I changed the default config folder so it points now to /var/www/virtuals, and finally I can access the virtual host by [http://40.40.40.40/mydomain.com](http://40.40.40.40/mydomain.com). 
 
Do you think it will cause me problems in the future or is a good solution ?
 
Thanks !

---

### Post by volkswagner on 2012-01-11
Just realize that you are using the default config file now and not the one you created 'mydomain.com".

There are ways around developing locally.

You mentioned adding mydomain.com to your /etc/hosts file.  /etc/hosts is searched first before going to outside DNS servers.

So you can add all your virtual domain sites to your /etc/hosts file.  This will allow you to develop your sites using full url links vs. relative links if needed.  If you need to be able to view you vps then you will have to comment out the line in /etc/hosts.

---

