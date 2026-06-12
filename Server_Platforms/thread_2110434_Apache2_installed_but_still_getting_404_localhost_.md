---
title: "Apache2 installed but still getting 404 localhost error"
date: 2013-01-30
forum: Server Platforms
---

### Post by phooboo on 2013-01-30
OK. Please forgive me in advance for any stupid mistakes. I am a complete Newbie to linux/ubuntu, (and need help with the jargon too ;)....)

(I am trying to install wordpress.....)

I am following online instructions, that i first have to install apache2. I have done this. But when I test to see if it is working, by pointing browser to local host, instead of the "it works" page i am getting "the URL was not found on this server" error.

I have spent hours trying to find a solution online, so i have finally decided to ask my question directly.

In the apache2/sites-enabled folder this is what i am getting:
> namevirtualhost *:80
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

in the var/www folder i have an index.php folder which looks like this:

> <?
phpinfo();
?>

If some kind soul could help me get this right... (please don't use too much jargon.... don't want to tire out google ;) )

Thank you kindly in advance

---

### Post by omeomi on 2013-01-30
Maybe obvious but did you (re)start the server after installing it?

```
sudo /etc/init.d/apache2 start
```
or
```
sudo /etc/init.d/apache2 restart
```

---

### Post by phooboo on 2013-01-30
Thanks. Yes I did restart it. In fact i also uninstalled it and reinstalled it too, and still doesn't work.

---

### Post by CharlesA on 2013-01-30
How did you install apache?

The apache logs should tell you what the problem is, they are located in:

```
/var/log/apache2/error.log
```

If you are indeed getting a 404 error (aka not found), it should look something like this:

```
[Sun Jan 27 10:22:59 2013] [error] [client 192.168.1.15] File does not exist: /var/www/phpvirtualbox/images/vbox/vmw_first_run_bg.png
```

---

### Post by phooboo on 2013-01-30
I installed apace2 using this command
> sudo apt-get install apache2

I am indeed getting an error in the log
> [Wed Jan 30 15:29:07 2013] [error] [client ::1] File does not exist: /etc/apache2/htdocs

And indeed there is no htdocs in that file.... So what does that mean I have to do.....

---

### Post by CharlesA on 2013-01-30
That looks like the default file in /etc/apache2/sites-available/default.

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
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

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

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

If you are trying to run a php file, you will need the php5 package installed in addition to apache2. I do not think that is the problem, but it can't hurt.

See here:
[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)

Also run this and post the output, please:

```
ls -l ls -l /etc/apache2/sites-available/
```
```
ls -l /etc/apache2/sites-enabled/
```

---

### Post by phooboo on 2013-01-30
Here is the output for the sites-available

> ls: cannot access ls: No such file or directory
/etc/apache2/sites-available/:
total 16
-rw-r--r-- 1 root root  971 2013-01-29 16:39 default
-rw-r--r-- 1 root root 7469 2012-02-14 17:58 default-ssl
-rw-r--r-- 1 root root 1114 2013-01-27 16:12 examplename


Here is the output for sites-enabled
> total 0
lrwxrwxrwx 1 root root 26 2013-01-26 23:41 000-default -> ../sites-available/default
lrwxrwxrwx 1 root root 36 2013-01-29 14:37 default -> /etc/apache2/sites-available/default
lrwxrwxrwx 1 root root 30 2013-01-27 16:12 examplename -> ../sites-available/examplename


---

### Post by kanikilu on 2013-01-30
> **CharlesA said:**
> That looks like the default file in /etc/apache2/sites-available/default. With one exception: the "namevirtualhost" directive on the first line of his file. OP: Is there a reason you are using that directive? It's not in my default file, and given the all-lowercase (not the standard convention in Apache config files), I'm guessing you added it. I'm not sure that it's necessarily related to your problem, though, since when I added that to my config, I just get a warning...

If I were you, I'd try removing that line, restarting the apache2 service, and then trying to hit the localhost URL again.

Also, as CharlesA said, you aren't going to get a PHP file to work without installing the PHP package. Wordpress also requires MySQL, so you might as well just install the "LAMP" stack all at once...

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

---

### Post by phooboo on 2013-01-30
Firstly thank you to everyone for trying to help.

I assume that from my hours of crawling around the web I saw some advice to add that line "namevirtualhost".

I have deleted that line, and restarted apache2, but still getting the same error.

(I know about php/mysql... etc I am following the great tutorial over here [http://www.jonathanmoeller.com/screed/?p=3005](http://www.jonathanmoeller.com/screed/?p=3005)

only problem is that i can't get past the first stage of installing apache2 correctly (or at least getting it to work))

---

### Post by CharlesA on 2013-01-30
> **phooboo said:**
> only problem is that i can't get past the first stage of installing apache2 correctly (or at least getting it to work))

If there a reason you have "examplename" in sites-available?

If you are only going to be serving one site, you can use the default site, which should be stored in /var/www/

---

### Post by phooboo on 2013-01-30
I only have examplename in sites available because i was following a different tutorial... all in the name of getting this apache2 to work......

I have now deleted those files.... restarted.... no difference....

---

### Post by kanikilu on 2013-01-30
Personally, I'd recommend removing apache - and do a purge to get rid of the config files: ```
sudo apt-get purge apache2
```

Then reinstall the lamp stack using tasksel (see the wiki page I linked to earlier).

There's something to be said for setting everything up manually, but since you need PHP and MySQL anyways, you really are making it harder on yourself by not using the lamp-server metapackage. Just my 2 cents...

---

### Post by steeldriver on 2013-01-30
^^^ fwiw I kinda agree - I set up a minimal lamp stack using

```
sudo apt-get install lamp-server^
```(tasksel not required) and don't remember having to do ANYTHING to configure it (bar setting a mysql root password as prompted during the install) - it works right out of the box e.g.

```
$ wget -qO- http://localhost | html2text
****** It works! ******
This is the default web page for this server.
The web server software is running but no content has been added, yet.

```I then dropped a minimal phpinfo script into /var/www:

```
$ cat /var/www/phpinfo.php 
<html>
<head>
<title> PHP Test Script </title>
</head>
<body>
<?php
phpinfo( );
?>
</body>
</html>
```and that 'just works' as well - maybe the tutorial you are following is a bit out of date?

---

### Post by kanikilu on 2013-01-30
Good point, I forgot tasksel's not included anymore - no need to add the extra step if you know the package name.

OP: I looked at the tutorial you linked, and it doesn't say anything about changing any apache config files, so somewhere along the way I think you've gotten off-track...

---

### Post by phooboo on 2013-01-30
I definitely got off track! I started with the tutorial but when it didn't show the "it works" page, i started looking for a way to get it to work.... along the way i have come across so many different websites... each one trying to answer a different problem some of them connected to my issue..... That is why i have tried changing the config etc....

I tried to follow your advice, i uninstalled apache2. i then installed tasksel - no prob. installed lamp-server..... how can i check that everything has been installed properly?

---

### Post by phooboo on 2013-01-30
Still not working after installing LAMP-SERVER...?

Any ideas on what to do next?

---

### Post by CharlesA on 2013-01-30
What does the error.log say this time?

---

### Post by phooboo on 2013-01-30
I am still getting the same error:> File does not exist: /etc/apache2/htdocs

Just a thought: when i uninstall/purge apache2 all the files are still left, so the reinstall is not resetting the core apache2 settings.... is there a way of getting rid of ALL the config files attached to apache2, and then reinstalling... maybe that might help?

---

### Post by CharlesA on 2013-01-30
Purge apache2 again and it should have gotten rid of everything. After purging it, check to see if there is anything in /etc/apache2

---

### Post by phooboo on 2013-01-30
nope. i have re purged it with > sudo apt-get purge apache2 and all the files are still there in etc/apache2.

I tried to re purge it immediately again but got back the message "package apache2 is not installed".....

---

### Post by phooboo on 2013-01-30
would it make a difference that i am using ubuntu 11.04?

---

### Post by kanikilu on 2013-01-30
> **phooboo said:**
> would it make a difference that i am using ubuntu 11.04? Shouldn't matter. After purging, can you just manually delete the apache files? Or actually, just move them - that way I don't get in trouble for posting how to recursively delete files as root ;-)

```
sudo mv /etc/apache2 /etc/apache2.old
```

---

### Post by phooboo on 2013-01-30
Thats weird. I just followed your advice, i purged and then renamed remaining file apache2 apache2.old, then i downloaded apache2 again, it says it downloaded fine, but there is no apace2 folder in /etc ?!?!

I tried to restart apache2 and got error message "can't find file /etc/apache2/envvars.......?

---

### Post by CharlesA on 2013-01-30
Try this:
[http://askubuntu.com/questions/26228/how-can-i-replace-missing-configuration-files-after-removing-a-package](http://askubuntu.com/questions/26228/how-can-i-replace-missing-configuration-files-after-removing-a-package)

---

### Post by phooboo on 2013-01-30
Reinstalled Apache2 files.... still localhost not working... tried to restart apache2 and get this error > Syntax error on line 160 of /etc/apache2/apache2.conf:
Invalid command 'Order', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!


and in the log i'm getting the same... > File does not exist: /etc/apache2/htdocs

What AM i doing wrong?!?

---

### Post by steeldriver on 2013-01-30
I think the config files are actually in package apache2.2-common, and you're supposed to autoremove them after the main apache2 package

If you manually renamed / deleted the conf files without doing an autoremove, then the package manager probably thinks apache2.2-common is still installed and isn't regenerating those files - you may need to do

```
sudo apt-get install --reinstall apache2.2-common
```There's also a -utils package and a -worker package which may similarly have been broken by the manual rename / delete

```
$ sudo apt-get remove --purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]The following packages were automatically installed and are no longer required:
  apache2-utils apache2.2-common apache2-mpm-worker
Use 'apt-get autoremove' to remove them.[/B]

```Or you could do

```
sudo apt-get purge apache2 # yes again!
sudo apt-get autoremove # removes apache2.2-common but does NOT purge /etc/apache2 - I tried it
sudo apt-get purge apache2.2-common # really removes the whole /etc/apache2 dir
sudo apt-get install --reinstall apache2
```

---

### Post by CharlesA on 2013-01-30
> **steeldriver said:**
> 
```
sudo apt-get purge apache2 # yes again!
sudo apt-get autoremove # removes apache2.2-common but does NOT purge /etc/apache2 - I tried it
sudo apt-get purge apache2.2-common # really removes the whole /etc/apache2 dir
sudo apt-get install --reinstall apache2
```

Run this ^ and then reinstall Apache (or LAMP) and it should be fixed.

---

### Post by steeldriver on 2013-01-30
apolgies - that second command should have been

```
sudo **apt-get** autoremove
```

of course

---

### Post by phooboo on 2013-01-30
Fantastic getting somewhere!!!! I don't get the error anymore! 

Thank you all for your help!!!

---

### Post by phooboo on 2013-01-30
its now downloading the php instead of opening it.... i assume this is a different issue for a different day.... (just writing it here in case you think it might be connected....)

g'night all. 

and thanks once again

---

### Post by CharlesA on 2013-01-30
> **phooboo said:**
> its now downloading the php instead of opening it.... i assume this is a different issue for a different day.... (just writing it here in case you think it might be connected....)

g'night all. 

and thanks once again

Did you install just apache or did you install php as well?

If it is downloading the php file instead of displaying it, check to make sure php5 is installed and enabled.

[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)

---

### Post by phooboo on 2013-01-30
yes i do have php installed.

followed directions in your link to double check... and said it was already installed...

restarted, and again it downloading the php instead of running it... 

(this is a different issue thought isn't it?)

---

### Post by steeldriver on 2013-01-30
are you sure the index file has the correct suffix?

```

# wget -qO- http://192.168.1.102/ | html2text | head
[PHP_Logo]
****** PHP Version 5.3.10-1ubuntu3.5 ******

                                        Linux think60p 3.2.0-29-generic-pae
System                                  #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC
                                        2012 i686
Build Date                              Jan 18 2013 23:27:45
Server API                              Apache 2.0 Handler
Virtual Directory Support               disabled
Configuration File (php.ini) Path       /etc/php5/apache2

```but

```

# mv index.php index.html
# wget -qO- http://192.168.1.102/ | html2text
<? phpinfo(); ?>
#

```

---

### Post by volkswagner on 2013-01-30
Check your installed version of php5.

```
php5 -v
```

Make sure apache2 mod is enabled.

```
ls /etc/apache2/mods-enabled
```

---

### Post by phooboo on 2013-01-31
God bless you all!!!

Solved! 

Fantastic!

Thank you all!

---

