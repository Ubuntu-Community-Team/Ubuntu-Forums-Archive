---
title: "HOWTO: Using php5 with apache2-mpm-worker"
date: 2009-01-12
forum: Tutorials
---

### Post by kkruecke on 2009-01-12
The article _[Installing Apache2 and PHP5 using mod_fcgid]("http://tinyurl.com/6jed8u")_ shows how to run php5 with apache2-mpm-worker. The advanage of apache2-mpm-worker over apache2-mpm-prefork is better overall apache2 performance.

1. Install apache2-mpm-worker and the fastcgi apache module libapache-mod-fcid
```
# apt-get install apache2-mpm-worker  libapache2-mod-fcgid
```

2. Enable the Fastcgi apache module **mod_fcgid**
```
# sudo a2enmod fcgid
```

3. Install **php5-cgi** and the command-line version **php5-cli**

```
# sudo aptitude install php5-cgi php5-cli
```

4. Add the following to /etc/apache2/httpd.conf or place these basic configuration settings in a file under /etc/apache2/conf.d. For example, /etc/apache2/conf.d/00-myconf ("00-" will help insure it is read first before other /etc/apache2/conf.d files, which is necessary).

```
<Directory /var/www>
AddHandler fcgid-script .php
FCGIWrapper /usr/lib/cgi-bin/php5 .php
Options +ExecCGI
</Directory>
# If you have Aliases provide php support for them (Here we provide php support for scripts in /usr/share's subdirectories)
Alias /aptitude /usr/share/doc/aptitude/html/en
Alias /apt /usr/share/doc/apt-doc

<Directory /usr/share>
AddHandler fcgid-script .php
FCGIWrapper /usr/lib/cgi-bin/php5 .php
Options ExecCGI FollowSymlinks Indexes
</Directory>

```

5. Then, for each virtual host configuration file you have in /etc/apache2/sites-available, add **ExecCGI** within a <Directoy /path-to-site> block (placed within your <VirtualHost> block). For example,  

# cat /etc/apache2/sites-availabe/yourdomain.com

```

<VirtualHost *:80>
ServerAdmin youremail@yourdomain.com
ServerName yoursite.tld
ServerAlias www.yourdomain.tld *.yourdomain.tld

DocumentRoot /var/www/yourdomain.com

ErrorLog        /var/log/apache2/yourdomain.tld-error.log
CustomLog       /var/log/apache2/yourdomain.tld-access.log combined

<Directory /var/www/yourdomain.com>
Options +ExecCGI 

AllowOverride All
Order Allow,Deny
allow from all
</Directory>
LogLevel warn
ServerSignature On
</VirtualHost>
```

Note: **ExecCGI** was turned on in /etc/apache2/sites-available/default for /var/www and its subdirectories, so it is not strictly necessary within the <VirtualHost > block shown here. Using **+ExecCGI** adds fastcgi support to the Options in force. Options don't merge with prior options (they replace them) unless **+** is used. You can specify entirely different **Options**, but you must at a minmum have **ExecCGI**, if you want php support for your virtual host.

6. For any other <Directory /some/other/path> blocks you have, say, for virtual hosts, which are not subdirectories of /var/www or /usr/share, add 

<Directory /some/other/path>
AddHandler fcgid-script .php
FCGIWrapper /usr/lib/cgi-bin/php5 .php
Options +ExecCGI 
# add other Options you might need, but ExecCGI is required
# . . .
</Directory>

7. Enable your virtual host

```
#sudo a2ensite yourdomain.com
```

7. And reload the apache configuration

```
# sudo /etc/init.d/apache2 force-reload
```

or just restart apache2

```
# sudo /etc/init.d/apache2 restart
```

A similar technique is shown in this _[article]("http://tinyurl.com/7wblr6")_ from Digital Nerds.

---

### Post by ppp0 on 2010-01-26
great article!

---

### Post by alex88 on 2010-05-02
it's normal that after viewing some pages there are 2 php5 processes still running?

---

### Post by MercuryStar on 2010-05-09
> **alex88 said:**
> it's normal that after viewing some pages there are 2 php5 processes still running?

That's normal.  mod_fcgid will keep a few processes running ready to serve future requests faster.  The number of processes will vary as it tries to be intelligent about it.  It'll tend to keep at minimum 3 processes per class (ie per base executable file) by default though there are lots of tweakable settings.

---

### Post by alex88 on 2010-05-09
> **MercuryStar said:**
> That's normal.  mod_fcgid will keep a few processes running ready to serve future requests faster.  The number of processes will vary as it tries to be intelligent about it.  It'll tend to keep at minimum 3 processes per class (ie per base executable file) by default though there are lots of tweakable settings.


thank you for the answer.. but i've passed to lighttpd..it uses less ram..and i need that on my 256mb ram vps..

---

### Post by alex88 on 2010-05-31
I've tried to limit the number of php processes running, but with no luck. Reading the docs i've tried to add
```
FcgidMaxProcesses 1000
```
but it says
```
Invalid command 'FCGIdMaxProcesses', perhaps misspelled or defined by a module not included in the server configuration
```

I've tried to insert it into the <Directory /var/www> and also in the file /etc/apache2/mods-enabled/fcgid.conf..

---

### Post by jfb0101 on 2010-12-09
Hello.

Sorry my bad english, i'm brasilian.

I flowed the steps to configure apache2 mpm worker on linux, like you shown.

But when I try to acess [http://localhost/index.php](http://localhost/index.php) (the file index.php is in /var/www, my default site), I get the error:

403 Forbidden
You don't have permission to access /index.php on this server.

What can I do to fix it?

Thanks a lot.

---

### Post by alex88 on 2010-12-09
> **jfb0101 said:**
> Hello.

Sorry my bad english, i'm brasilian.

I flowed the steps to configure apache2 mpm worker on linux, like you shown.

But when I try to acess [http://localhost/index.php](http://localhost/index.php) (the file index.php is in /var/www, my default site), I get the error:

403 Forbidden
You don't have permission to access /index.php on this server.

What can I do to fix it?

Thanks a lot.

Have a look at /var/log/apache2/error.log (or similar path) to check what's the error.

Regards

---

### Post by sunqs on 2010-12-12
> **jfb0101 said:**
> Hello.

Sorry my bad english, i'm brasilian.

I flowed the steps to configure apache2 mpm worker on linux, like you shown.

But when I try to acess [http://localhost/index.php](http://localhost/index.php) (the file index.php is in /var/www, my default site), I get the error:

403 Forbidden
You don't have permission to access /index.php on this server.

What can I do to fix it?

Thanks a lot.

Usually this is caused by that your fastcgi script couldn't be correctly started.

1.  Check /var/log/apache2/error.log as alex88 suggested.
2.  Check /var/log/apache2/suexec.log

---

### Post by Fader27 on 2011-09-04
After deploying this (above) config, I tried to install PHP opcode - [eAccelerator]("http://eaccelerator.net/"). Installation went without problems and eAccelerator worked.
 But what was my surprise when I noticed that eAccelerator caches all (phpmyadmin, Sypex Dumper and another web tools) except, in fact, my blogs! Another words, all that is outside of the /etc/apache2/sites-enabled/, or all that is outside <VirtualHost> container. I can not understand that I overlooked or performed incorrectly. Help please!

---

