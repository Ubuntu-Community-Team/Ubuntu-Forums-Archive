---
title: "Apache for local use only."
date: 2008-05-15
forum: Server Platforms
---

### Post by drpepper on 2008-05-15
Hi Everyone,

I want to install Apache on my Ubuntu PC to test my web pages. I am using Eclipse to dev and need a test server. I want only for myself on my machine to be able to connect to the server. No access from the outside world or other people on my network. I'd also like to be able to stop and start it at will. I know you can use the command line "/etc.init.d/apache stop/start/etc", but how to stop it running as a daemon?

I have looked on the forums, and browsed the net. Unfortunately I'm not sure what to search for. Thanks in advance.

---

### Post by drpepper on 2008-05-15
I should of also mentioned, I can already install Apache and have a little experience with setup. so I guess this post is more of a configuration issue. Thanks.

---

### Post by Monicker on 2008-05-15
A quick and dirty way to do it

```
sudo chmod -x /etc/init.d/apache
```

That prevents apache from starting at boot.  Probably not the recommended way, but it works.

Then you can you apache2ctl to manually start and stop it.

```
sudo apache2ctl start
sudo apache2ctl stop
```


As far as the local use only, you can restrict which ip addresses are allowed to connect to the server.  Modify /etc/apache2/sites-enabled/000-default, assuming you are using the default directory of /var/www.

```
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order deny,allow
                Deny from all
                Allow from 192.168.1.100
        </Directory>
```

The above will only allow connections to the default directory from the ip address of 192.168.1.100.

---

### Post by drpepper on 2008-05-18
Thanks Mon, it doesnt matter too much if it's a dirty fix, it's only a personal pc and i've got it behind a linux server aswell. I will give that a try, thanks very much :)

---

### Post by ccaaee on 2009-11-23
I'm having a big problem with this.  I'm using apache2 on ubuntu 9.04 (ver.= 2.2.11) and ubuntu 7.10 (2.2.4). Regardless of settings in /etc/apache2/sites-enabled/000-default I can still connect to the server from all other hosts on my lan.  Is there some other parameter to change?  Also, I stop and start apache after each time I edit files in /etc/apache2 - is this strictly necessary?

---

### Post by memilanuk on 2009-11-23
You may want to look at [configuring UFW]("https://help.ubuntu.com/community/UFW") to block access to port 80 if you don't want other hosts on the network to access it.  Actually, I'd highly recommend you give UFW a look and get *something* up as a barrier between you and the rest of the world.  You should be able to configure it fairly easily to block all outside access to your machine, including port 80, or to only allow certain IP addresses from your LAN access.

Another option to consider is going into httpd.conf and putting a line that says 'Listen 127.0.0.1:80' to tell apache to listen *only* on port 80 on the loopback/localhost interface - not on the outward facing network interface.  

HTH,

Monte

---

### Post by Coastalguy on 2009-11-23
Hope I'm on the right tread. Also using Web Server locally to test sites before uploading. Installed and have working Apache, Mysql and PHP on my Hardy Heron 8.04 (thanks to all of the great information here.

Anyway, I'm down to one problem. For ease of updates, I use an external file, to provide links to each of my pages, with a "php" include. Some of these files are .php and some are .html. To get the .html to run the php code within it, I have added an "AddType" command to my .htaccess to include .html. (I know this reduces performance due to every .html file having to be parsed for php code, but I didn't know of any other way other than changing all files to .php, which would cause the same slow performance?).

With the "AddType" added to my .htaccess, I have this working online, and also on my Windows XP LAMP setup. However, I am having problems with this on Ubuntu. As is, the .php pages load and display the links fine. The .html pages load, but "no links".

I have tried 2 fixes with the same result:
1. /etc/apache2/httpd.conf adding AddType application/x-http-php .php .html etc.
2. /etc/apache2/sites-available/default adding AllowOverride All to the <Directory /var/www/>

With these fixes, my .html pages load fine with the links as desired. However, when loading a .php page, I get a prompt on how Firefox should handle this page, which it then proceeds to save that page, instead of displaying it. I can't get both .php and .html to load displaying the external file links... Any suggestions?

---

### Post by memilanuk on 2009-11-23
Mmmm... well, I don't have my php stuff handy but is there any reason why just making it a .php file and echoing the html lines within wouldn't work?  That way its all just one big php file, with links to your other files... or did I miss something and thats what you already did?

---

