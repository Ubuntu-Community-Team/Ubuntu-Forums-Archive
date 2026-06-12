---
title: "Auto enable /home/www for Apache"
date: 2008-09-15
forum: Server Platforms
---

### Post by anjanesh on 2008-09-15
Hi

After installing Apache2 on Ubuntu, the default website location is [COLOR=Green]/var/www[/COLOR].

How do I make this such that it automatically reads only [COLOR=Green]/home/**<username>**/www[/COLOR] ?

Thanks

---

### Post by ngmachado on 2008-09-15
Hi anjanesh,

It's very simple:

Edit the file: /etc/apache2/sites-available/default

Change the line ```
DocumentRoot /var/www/
``` to whatever location you want.

Then run the command ```
sudo a2ensite default
``` then ```
sudo /etc/init.d/apache2 reload
```

Check if it works.

P.S.: You might want to read this very useful article:

[http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1](http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1)

---

### Post by anjanesh on 2008-10-12
I want to **add** to DocumentRoot.
```
DocumentRoot /home/user1/www/ /home/user2/www/ /home/user3/www/
```

So in my browser these should work :
localhost/user1/somefile.php
localhost/user1/somefile.html
localhost/user2/folder1/file1.php
localhost/user3/dir1/dir2/index.html

Without creating symlinks in /var/www/.

---

### Post by windependence on 2008-10-12
> **anjanesh said:**
> Hi

After installing Apache2 on Ubuntu, the default website location is [COLOR=Green]/var/www[/COLOR].

How do I make this such that it automatically reads only [COLOR=Green]/home/**<username>**/www[/COLOR] ?

Thanks

What are you trying to accomplish by doing this? What I THINK you want to do is set up some virtual hosts.

-Tim

---

### Post by anjanesh on 2008-10-12
Yes I do - but using localhost. I cant give domain1.com because my browser will actually goto domain1.com url.
Is there anyway to setup Virtual Hosts but giving the domain as localhost.username ?

---

### Post by windependence on 2008-10-12
Sure, you can call it anything you want as long as you set up the hosts file on your client machine to resolve to your server's IP address. If you are plannng to work directly on the server (not recommended for development) then you can just put entries in the hosts file on your server.

-Tim

---

### Post by lykwydchykyn on 2008-10-12
What you want is to enable the "userdir" module:
```

a2enmod userdir

```

This will automatically publish the contents of /home/user/public_html to [http://server/~user/](http://server/~user/).  I don't know if you can change "public_html" to "www" instead, but probably it can be done if you edit /etc/apache2/mods-available/userdir.conf.

This way, you don't need to make a special directive for every user.

---

