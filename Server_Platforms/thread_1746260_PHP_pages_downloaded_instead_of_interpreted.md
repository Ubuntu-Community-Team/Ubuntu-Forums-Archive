---
title: "PHP pages downloaded instead of interpreted"
date: 2011-05-01
forum: Server Platforms
---

### Post by OyoKooN on 2011-05-01
Hello,

I'm trying to configure Apache2 with mod_fcgid and PHP5.

I wrote the wrapper scripts according to the following how-to: [http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-apache2-with-mod_fcgid-and-php5-on-ubuntu-10.04)

However, I'm stuck with my browser trying to download the PHP pages when I go to my website.

Do you know where is the problem?

In advance, thank you.

---

### Post by thegodfaza on 2011-05-01
Can you post the output of:
```
apachectl -t -D DUMP_MODULES | grep php
```

---

### Post by OyoKooN on 2011-05-01
Hello thegodfaza,

I don't have the command apachectl on my system.

I'm running Ubuntu 10.04 LTS Lucid.

Thank you for your answer.

---

### Post by thegodfaza on 2011-05-01
Well that seems a bit odd. What is the output of:
```
ls -la /usr/sbin | grep apache
```

Should be similar to:
```
justin@singularity-vm:~$ ls -la /usr/sbin | grep apache
lrwxrwxrwx  1 root    root          34 2010-11-27 06:52 apache2 -> ../lib/apache2/mpm-prefork/apache2
-rwxr-xr-x  1 root    root        5326 2010-11-18 15:16 apache2ctl
lrwxrwxrwx  1 root    root          10 2010-11-27 06:52 apachectl -> apache2ctl

```

---

### Post by OyoKooN on 2011-05-01
I don't have the third line =)

---

### Post by thegodfaza on 2011-05-01
I guess apache didn't make a symlink for you. If you want you can make your own by running these commands:
```
cd /usr/sbin
sudo ln -s apache2ctl apachectl
```

Having the symlink would be useful if you end up running any older programs / scripts that attempt to use that command.

Anyway, post the output of the first command after you make the symlink or if not, post the output of:
```
apache2ctl -t -D DUMP_MODULES | grep php
```

---

### Post by OyoKooN on 2011-05-01
The command show:
```
Syntax OK
  php5_module (shared)
```

---

### Post by thegodfaza on 2011-05-01
Can you post the output of:
```
dpkg -l | grep php
```

---

### Post by OyoKooN on 2011-05-01
```
ii  libapache2-mod-php5             5.3.2-1ubuntu4.8            server-side, HTML-embedded scripting languag
ii  php5                            5.3.2-1ubuntu4.8            server-side, HTML-embedded scripting languag
ii  php5-cgi                        5.3.2-1ubuntu4.8            server-side, HTML-embedded scripting languag
ii  php5-cli                        5.3.2-1ubuntu4.8            command-line interpreter for the php5 script
ii  php5-common                     5.3.2-1ubuntu4.8            Common files for packages built from the php
ii  php5-curl                       5.3.2-1ubuntu4.8            CURL module for php5
ii  php5-dev                        5.3.2-1ubuntu4.8            Files for PHP5 module development
ii  php5-gd                         5.3.2-1ubuntu4.8            GD module for php5
ii  php5-imagick                    2.1.1RC1-1build3            ImageMagick module for php5
ii  php5-imap                       5.3.2-0ubuntu2              IMAP module for php5
ii  php5-mcrypt                     5.3.2-0ubuntu1              MCrypt module for php5
ii  php5-mysql                      5.3.2-1ubuntu4.8            MySQL module for php5
```

---

### Post by thegodfaza on 2011-05-01
Can you post your virtual server's config file. Should be /etc/apache2/sites-available/default-000 or default.
EDIT: Doh, just remembered. Did you set the php files that your trying to execute to have the execute flag? Post "ls -la /var/www/your_web_root".

---

### Post by OyoKooN on 2011-05-01
I don't use default, I have independent virtualhost files.

I show you the default

```
<VirtualHost 64.207.154.91:80>
	ServerName default.syrinxoon.net
	ServerAdmin oyokoon@syrinxoon.net

	DocumentRoot /var/www/syrinxoon.net/html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	        AddHandler fcgid-script .php
	</Directory>
	<Directory /var/www/syrinxoon.net/html/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

and the one I use for my website

```
<VirtualHost 64.207.154.91:80>

  ServerAdmin oyokoon@syrinxoon.net
  ServerName syrinxoon.net
  ServerAlias www.syrinxoon.net
  DocumentRoot /var/www/syrinxoon.net/html/

  <IfModule mod_fcgid.c>
    SuexecUserGroup syrinxoon.net syrinxoon.net
    <Directory /var/www/syrinxoon.net/html/>
      Options +ExecCGI
      AllowOverride All
      AddHandler fcgid-script .php
      FCGIWrapper /var/www/php-fcgi-scripts/syrinxoon.net/php-fcgi-starter .php
      Order allow,deny
      Allow from all
    </Directory>
  </IfModule>

  ErrorLog /var/www/syrinxoon.net/logs/error.log
  CustomLog /var/www/syrinxoon.net/logs/access.log combined
  ServerSignature Off

</VirtualHost>
```

---

### Post by thegodfaza on 2011-05-01
I edited my last post before you posted. Can you check to make sure that the php files your trying to execute have the execute flag. Do a "ls -la /dir/to/the/php/file/dir" and post the output.

---

### Post by OyoKooN on 2011-05-01
The files are
```
-rw-r--r--
```

---

### Post by thegodfaza on 2011-05-01
There's the problem. In order for php to execute the php files they need to have the executable flag. A security warning though, only mark things that need to be executable with the execute flag. To mark something with the execute flag run:
```
sudo chmod a+x file.php - for one file
sudo chmod a+x *.php - for all php files in that dir
sudo chmod -R a+x *.php - on your webroot dir for all php files
```

Also if this is your first webserver setup you might want to install some sort of bruteforce detection system, such as fail2ban.

EDIT: If your using an FTP client to upload your files to the server you can just add the execute flag there. Some tools such as DreamWeaver handle this for you though you can still edit permissions if you need to.

---

### Post by OyoKooN on 2011-05-01
Thank you, I'll try that.
I tell you in a minute I everything work.

---

### Post by OyoKooN on 2011-05-01
That do not solve the problem.

If you try to go on [http://syrinxoon.net](http://syrinxoon.net), you'll see.

However, I don't know what I did, I managed to make everything works properly 2 days ago, then I did something and since, it doesn't work... =S

---

### Post by thegodfaza on 2011-05-01
You can try adding this to your config:
```
AddType application/x-httpd-php .php
```

I had this happen a while back on 10.04 before I upgraded my server to 10.10. Everything I tried didn't work until I did a full reinstall of php5 which was not fun.

---

### Post by OyoKooN on 2011-05-01
I added the AddType directive, nothing happen...

There is something weird, I use a feed reader called fever.
It is located at [http://feeds.syrinxoon.net/oyokoon/](http://feeds.syrinxoon.net/oyokoon/) and works properly.

So I added a phpinfo();

[http://feeds.syrinxoon.net/oyokoon/infos.php](http://feeds.syrinxoon.net/oyokoon/infos.php)

And... it works...

---

### Post by alexend on 2011-05-01
Are You Using Google Chrome. This Is A Bug In Chrome and Chromium. If So What Version Of Chrome?

---

### Post by OyoKooN on 2011-05-01
No I'm using a lot of brother and I have this result (the error and the phhinfo()) with IE9, Firefox 4, Chrome 12 and so on..

---

### Post by thegodfaza on 2011-05-01
> **alexend said:**
> Are You Using Google Chrome. This Is A Bug In Chrome and Chromium. If So What Version Of Chrome?

If you go to their site, [http://syrinxoon.net/](http://syrinxoon.net/), you get the raw php. That would be an amazing bug if it let you download any websites raw PHP.

EDIT: Are you sure you set the execute flag on the php file your trying to execute? Check the file permissions using ls -la.

---

### Post by OyoKooN on 2011-05-01
The PHP file containing the phpinfo() is chmod 644, I tried to put all files in 755 and it do not change anything =/

---

### Post by thegodfaza on 2011-05-01
Well everything looks right. I don't know why it wont work. I suppose you could try reinstalling php.
```
sudo apt-get purge php5
sudo apt-get autoremove
sudo apt-get install php5 libapache2-mod-php5
sudo service apache2 restart
```

---

### Post by OyoKooN on 2011-05-01
Done.

Don't solve the problem.

I give up for tonight, I'm bored ^^

Thank you for your help.

---

### Post by thegodfaza on 2011-05-01
Hope you get it working. The fun of linux where everything looks right but it just won't work.

---

