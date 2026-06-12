---
title: "Apache2 - Setup Userdir, how to change DocumentRoot"
date: 2013-01-20
forum: Server Platforms
---

### Post by playoffspc on 2013-01-20
I have setup unique User Directories in Apache, so /home/user/public_html can host a site for each user.

How can I change this so that each user directory has its unique document root? Currently document root points to /var/www, not /home/user/public_html! I've been trying to figure it out all morning :)


I tried to make a new file entry in /etc/apache2/sites-available, then run the a2ensite sitename tool, but no success. Still points to /var/www when I run the simple PHP script out of a /home/user/public_html.

The file entry was simple, as follows, I tried to simplify it just to make sure it works before making each entry more complicated:
```

<VirtualHost *:80>
  ServerName sitename
  DocumentRoot /home/user/public_html
</VirtualHost>

```Then at shell, I run
```
# sudo a2ensite sitename
Enabling site sitename
To activate the new configuration you need to run:
  service apache2 reload
```Which I do

```
# sudo service apache2 reload
* Reloading web server configuration

```Everything appears fine.

I go to /home/user/public_html

Create file, test.php

```
<?php
echo $_SERVER['DOCUMENT_ROOT']
?>

```Yet unfortunately...I can't get DOCUMENT_ROOT to point to /home/user/public_html. It always points to /var/www ... what am I doing wrong?

---

### Post by Doug S on 2013-01-20
Do you want something beyond merely enabling the userdirectories in apache? i.e. do you want something beyond:```
sudo a2enmod userdir
sudo service apache2 restart
```which enables the user public_html stuff such that, for example,:```
http://www.smythies.com/~doug/index.html
```works.

---

### Post by playoffspc on 2013-01-20
I've had userdir working for a little bit now, where I have been able to go to 

[http://localhost/](http://localhost/)
or
[http://localhost/~user/](http://localhost/~user/)
or
[http://localhost/~user2/](http://localhost/~user2/)

That part works fine. I'm trying to build a website that doesn't care where it's hosted, so long as PHP is working, I wanted to modularize my code into various PHP files and include them (from anywhere within the site directory) and I was planning on using PHP's $_SERVER['DOCUMENT_ROOT'] but it doesn't seem to be working the way I am expecting it to.

For example when hosting pages out of a userdir, I am still pointing to /var/www which is where [http://localhost/](http://localhost/) points, even though the userdir serving that page is [http://localhost/~user/test.php](http://localhost/~user/test.php)

```

<?php
# http://localhost/~user/test.php

echo $_SERVER['DOCUMENT_ROOT'];

?>
```

---

### Post by playoffspc on 2013-01-20
**UPDATE**
I followed this guide - [http://codingpad.maryspad.com/2012/03/14/how-to-create-multiple-virtual-hosts-in-ubuntu/](http://codingpad.maryspad.com/2012/03/14/how-to-create-multiple-virtual-hosts-in-ubuntu/)

Things are mostly working now.

First I created a virtual host within /var/www just to follow the guide exactly as written. That worked. When I <?php echo $_SERVER['DOCUMENT_ROOT'] ?> I get the expected /var/www/virtual-sitename

So I was so happy I almost quit. I decided to go a little farther and try and solve my initial problem. I added the entry into /etc/hosts, calling the site **user** and pointing it to 127.0.0.1. I updated my file in /etc/apache2/sites-enabled to just the bare minimum. Server name, alias, and DocumentRoot.

So now 2 things happen




If I go to [http://user/](http://user/) I get exactly what I expect. It serves files out of /home/user/public_html which is great, and it even shows the correct DOCUMENT_ROOT when I echo it in PHP.

But if I go [http://localhost/~user/](http://localhost/~user/) it still shows the same old /var/www as the DOCUMENT_ROOT.

Oh well, can't win em all. If anyone knows WHY I'd be curious, but for now my problem is solved enough that I can spend time developing and less worrying on server configs which are never my specialty.

---

### Post by chrisguk on 2013-01-20
> **playoffspc said:**
> **UPDATE**
I followed this guide - [http://codingpad.maryspad.com/2012/03/14/how-to-create-multiple-virtual-hosts-in-ubuntu/](http://codingpad.maryspad.com/2012/03/14/how-to-create-multiple-virtual-hosts-in-ubuntu/)

Things are mostly working now.

First I created a virtual host within /var/www just to follow the guide exactly as written. That worked. When I <?php echo $_SERVER['DOCUMENT_ROOT'] ?> I get the expected /var/www/virtual-sitename

So I was so happy I almost quit. I decided to go a little farther and try and solve my initial problem. I added the entry into /etc/hosts, calling the site **user** and pointing it to 127.0.0.1. I updated my file in /etc/apache2/sites-enabled to just the bare minimum. Server name, alias, and DocumentRoot.

So now 2 things happen




If I go to [http://user/](http://user/) I get exactly what I expect. It serves files out of /home/user/public_html which is great, and it even shows the correct DOCUMENT_ROOT when I echo it in PHP.

But if I go [http://localhost/~user/](http://localhost/~user/) it still shows the same old /var/www as the DOCUMENT_ROOT.

Oh well, can't win em all. If anyone knows WHY I'd be curious, but for now my problem is solved enough that I can spend time developing and less worrying on server configs which are never my specialty.

What you have described if I have read it correctly is exactly how document root should behave.  Because as the name suggests it the document root.

This would work:  [PHP]<?php echo $_SERVER ['DOCUMENT_ROOT'] . $_SERVER['PHP_SELF']?>[/PHP]

Though what you are asking about the actual document root specified in the Virtual host block if your files are actually contained with:

```
 /home/user/public_html
```

Then the declaration on the VHost block should work fine:

This is my block:

```

<VirtualHost *:80>                                                                                                           
                    ServerName mydomain                                                                                                  
                    ServerAlias mydomain.dns.com
                    ServerAdmin admin@mydomain
                    DocumentRoot /var/www/domain/
                    <Directory /var/www/domain/>
                            AllowOverride all
                            Order allow,deny
                            allow from all
                   </Directory>
            ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
                    <Directory /usr/lib/cgi-bin>
                            AllowOverride None
                            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                            Order allow,deny
                            Allow from all
                    </Directory>
ErrorLog /var/www/domains/mydomain/apache.error.log
CustomLog /var/www/domains/mydomain/apache.access.log common      


```

Hope that helps

---

