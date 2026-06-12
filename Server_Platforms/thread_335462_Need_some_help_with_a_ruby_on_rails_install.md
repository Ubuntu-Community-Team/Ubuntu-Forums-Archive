---
title: "Need some help with a ruby on rails install"
date: 2007-01-10
forum: Server Platforms
---

### Post by Tipo on 2007-01-10
hello all,

I was trying to get ruby on rails installed on my server by following the guide here: [http://www.urbanpuddle.com/articles/2006/06/10/install-ruby-rails-on-ubuntu-dapper-drake]("http://www.urbanpuddle.com/articles/2006/06/10/install-ruby-rails-on-ubuntu-dapper-drake")

I've followed all the steps, but starting up my lighttpd server returns these errors:

```
 * Starting web server lighttpd                                          [ ok ] 
thranduil@mirkwood:~$ 2007-01-10 10:31:44: (mod_fastcgi.c.1014) the fastcgi-backend /usr/bin/php4-cgi failed to start: 
2007-01-10 10:31:44: (mod_fastcgi.c.1029) terminated by signal: 11 
2007-01-10 10:31:44: (mod_fastcgi.c.1034) to be exact: it seg-fault, crashed, died, ... you get the idea. 
2007-01-10 10:31:44: (mod_fastcgi.c.1036) If this is PHP try to remove the byte-code caches for now and try again. 
2007-01-10 10:31:44: (mod_fastcgi.c.1322) [ERROR]: spawning fcgi failed. 
2007-01-10 10:31:44: (server.c.832) Configuration of plugins failed. Going down.
```

Any idea what's going on here? 

Thanks in advance!

---

### Post by Brazen on 2007-01-10
Are you using Ubuntu 6.06 Dapper?

---

### Post by Brazen on 2007-01-10
Wipe out your server, reinstall Ubunter Dapper, and do this:

```
sudo apt-get update && sudo apt-get -y install php5-mysql php5-mcrypt php5-gd
sudo apt-get &#8211;y install ruby irb libapache2-mod-fcgid ruby1.8-dev libfcgi-dev g++ libmysqlclient15-dev

wget http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz
tar &#8211;xzf rubygems-0.9.0.tgz
cd rubygems-0.9.0/
sudo ruby setup.rb
cd ..
rm &#8211;rdf rubygems-0.9.0*

sudo gem update &#8211;system
sudo gem install rails --include-dependencies
sudo gem install fcgi
sudo gem install mysql

sudo mkdir /var/www/rails
```

Rails is now ready to go.  You just need to create an application and add it to Apache.

---

### Post by Brazen on 2007-01-10
> create an application and add it to Apache.And here is how you do that (using the OnLamp Cookbook Tutorial application as an example):

```
cd /var/www/rails/
sudo rails cookbook

sudo chgrp &#8211;R www-data cookbook/
sudo chmod &#8211;R g+r cookbook/
sudo chmod &#8211;R g+w cookbook/log/
sudo chmod &#8211;R g+w cookbook/tmp/
sudo find /var/www/rails/cookbook/ -type d &#8211;exec chmod g+x {} \;

sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/default.original
sudo nano /etc/apache2/sites-available/default
```

Add this to the VirtualHost:
```
########################
##### RoR Cookbook #####

Alias /cookbook /var/www/rails/cookbook/public

<Directory /var/www/rails/cookbook/public>
   SetEnv RAILS_ENV development

   AllowOverride all
   Order allow,deny
   Allow from all
</Directory>
########################
```

Now do this:
```
sudo /etc/init.d/apache2 restart
sudo nano /var/www/rails/cookbook/public/.htaccess
```

In that .htaccess change this:```
RewriteRule ^(.*)$ dispatch.cgi [QSA,L]
```
to this:```
RewriteRule ^(.*)$ dispatch.fcgi [QSA,L]
```
and change this:```
AddHandler fastcgi-script .fcgi
```
to this:```
AddHandler fcgid-script .fcgi
```
and add this somewhere:```
RewriteBase /cookbook
```


Do that and your men shall live.  Do it not, and every one of you will die today.

You can now access your rails application at [http://servernameorip/cookbook](http://servernameorip/cookbook)

---

### Post by Tipo on 2007-01-10
Hey Brazen,

I was using Edgy, but it seems like your suggestion worked.

Thanks!

---

### Post by Brazen on 2007-01-10
Well I suggested installing Dapper because it is a better server distro.  It is the distro that Ubuntu is primarily pushing, and supporting, as their server distro, and it will have updates until 2010.  I've experienced some "funky" behavior in Edgy with things that just work like normal in Dapper.  Edgy was meant to be a little more bleeding edge, which is great for a desktop, but not so great for a server.

---

