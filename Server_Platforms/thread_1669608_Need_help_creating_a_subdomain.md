---
title: "Need help creating a subdomain"
date: 2011-01-18
forum: Server Platforms
---

### Post by shnippy on 2011-01-18
Hello,

I am running a production site on ubuntu 8.04. 

We have a site that has been online for over a year, and is accessible using both [www.xxxxx.com](www.xxxxx.com), and xxxxx.com.

I have been trying for 3 days to create a subdomain (sub.xxxx.com) for a new projext that needs its own webroot. 

I have searched google, and have tried many, many (24 different ones to be exact), walkthroughs, and how to's, but I have had not one of them work out the way it is supposed to.

I have just added a, "A" record with my domain (dns) host Godaddy.

What i would appreciate help with, is creating a new subdomain, that is accessible from the internet, yet leaving my main website unscathed, and still accessible from [www.xxxx.com](www.xxxx.com), and xxxx.com. (example of subdomain: newbie.xxxx.com)

Can anyone explain how to do this in laymens terms, or terms that a regular joe can understand?

I have been trying to do this all through Webmin.


Thank you very much for any assistance.

Shnippy

---

### Post by R.Bucky on 2011-01-18
I host around 3 dozen domains using the Apache VirtualHost directive. First step, navigate to your sites-available directory and create the necessary file for Apache.

```

cd /etc/apache2/sites-available/
sudo nano sub.domain.com

```

The directive below needs to be in the sub.domain.com file. You will have your file at /etc/apache2/sites-available/sub.domain.com. Make sure you change your DocumentRoot to match your own.

```
<VirtualHost *:80>
ServerName sub.domain.com
ServerAlias www.sub.domain.com
DocumentRoot /SERVER/sub_ubunttoo/
</VirtualHost>
<Directory /SERVER/sub_domain/>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
</Directory>
```

Next, enable the site with the following:

```
sudo a2ensite sub.domain.com
sudo /etc/init.d/apache2 reload

```

Someone correct me, however you may also have to enable the Apache host module with the following.

```
sudo a2enmod vhost_alias
sudo /etc/init.d/apache2 reload
```

The only other caveat with viewing sites within your network is DNS. Wordpress and other sites typically don't resolve unless you have a router that processes NAT internally. Otherwise, you can add an /etc/hosts entry like 192.168.0.100 sub.domain.com or something similar.

---

### Post by James78 on 2011-01-18
> **R.Bucky said:**
> **Someone correct me**, however you may also have to enable the Apache host module with the following.

```
sudo a2enmod vhost_alias
sudo /etc/init.d/apache2 reload
```
Ya, you don't need to have that module enabled.
[http://httpd.apache.org/docs/2.2/mod/mod_vhost_alias.html](http://httpd.apache.org/docs/2.2/mod/mod_vhost_alias.html)

---

### Post by shnippy on 2011-01-18
Excellent, thank you both for the help.

I can now schedule an appointment to have the hair I pulled out, put back in ;).



Thank you very much,
Shnippy

---

### Post by ubudog on 2011-01-18
> **R.Bucky said:**
> I host around 3 dozen domains using the Apache VirtualHost directive. First step, navigate to your sites-available directory and create the necessary file for Apache.

```

cd /etc/apache2/sites-available/
sudo nano sub.domain.com

```

The directive below needs to be in the sub.domain.com file. You will have your file at /etc/apache2/sites-available/sub.domain.com. Make sure you change your DocumentRoot to match your own.

```
<VirtualHost *:80>
ServerName sub.domain.com
ServerAlias www.sub.domain.com
DocumentRoot /SERVER/sub_ubunttoo/
</VirtualHost>
<Directory /SERVER/sub_domain/>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
</Directory>
```

Next, enable the site with the following:

```
sudo a2ensite sub.domain.com
sudo /etc/init.d/apache2 reload

```

Someone correct me, however you may also have to enable the Apache host module with the following.

```
sudo a2enmod vhost_alias
sudo /etc/init.d/apache2 reload
```

The only other caveat with viewing sites within your network is DNS. Wordpress and other sites typically don't resolve unless you have a router that processes NAT internally. Otherwise, you can add an /etc/hosts entry like 192.168.0.100 sub.domain.com or something similar.

Thanks!  I was looking for the same thing...

---

### Post by ubudog on 2011-01-18
There is also this:

[http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/](http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/)

Seems like a good guide.

---

### Post by Vegan on 2011-01-18
If you can a vhost file into a PHP script, you can build a web site to allow anyone who wants to have a web page to create their own. Its almost trivial.

You can store all the subsites in a text file or MySQL and its not very hard.

sky is the limit for subdomains

---

### Post by koenn on 2011-01-18
> **shnippy said:**
> Hello,


I have been trying for 3 days to create a subdomain (sub.xxxx.com) for a new projext that needs its own webroot. 

I have just added a, "A" record with my domain (dns) host Godaddy.

(example of subdomain: newbie.xxxx.com)


strictly speaking, "newbie.xxxx.com" can be either the host "newbie" in the domain xxx.com, or the subdomain "newbie" in the domain xxx.com, so you'd have to be specific about what you mean. Seeing that you're talking about websites, you probably mean "host". 

Apart from all the stuff about apache virtual hosts, you'Ll also need DNS for those additional) websites if theY have to be reachable from the internet. Those browsers out there need a way of finding out what address newbie.xxx.com is at. 
You need A or CNAME records for them (is that what you meant with" added a, "A" record with my domain (dns) host Godaddy" ?)

---

### Post by Vegan on 2011-01-18
This is why I prefer the mechanized approach, every config file can be managed.

---

### Post by shnippy on 2011-01-19
hi,

that "A" record saved the last couple hairs on my head lol.

it was kind of like trying to start a car with no gas in it.

thank you all for the help. 

i owe you a cup of ubuntu ;)

cheers,
shnippy

---

