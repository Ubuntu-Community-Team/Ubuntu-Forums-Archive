---
title: "Help with a blogging server - WordPress"
date: 2005-02-04
forum: Server Platforms
---

### Post by Locutus on 2005-02-04
I would like to host my own blog on an old Duron 800. I found a blog called wordpress that I really like. I was wondering if anyone could guide me how to set it up. I am a complete newbie when it comes to mySQL and PHP. Would anyone have some step by step instructions?

Any help or tips would be greatly appreciated.

---

### Post by llamakc on 2005-02-05
The instructions included in the Wordpress tarball should be able to help you. First off, install apache and MySQL. Then if you want a frontend for MySQL, apt-get install phpmyadmin.
 
 Now follow the directions in the wordpress tarball. I strongly suggest using their latest tarball instead of the .deb, and after make sure you get spamkarma up and running. The trackback and comment spam is ridiculous.

---

### Post by Locutus on 2005-02-09
Got it working without too much trouble.

apt-get install mysql apache2 php...

Got to love apt.

Thanks again

---

### Post by cblack on 2005-02-11
If you have universe enabled in /etc/apt/sources.list wordpress is available via:

```
sudo apt-get install wordpress
```

---

### Post by senectus on 2005-11-16
ok.. that's just great.. but what do you do to get it working??

apt-get install wordpress
worked a treat.. but now I have wordpress, php, postfix, Apache installed and have no idea on how to get wordpress functional... :-P

---

### Post by grendelkhan on 2005-11-16
I've never used it by apt getting it, given that the tarball just drops in and practically installs itself, I've done it that way to get more control over where it's loaded.

Something to look at is the LAMP howto for Ubuntu:

[https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29](https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29)

Make sure after doing this you uncomment these lines in /etc/apache2/apache2.conf:

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

Restart apache after doing that and you will be set to jet.

Remember your machines default directory for html is /var/www/ so if you want wordpress to be your default website, untar it unto there.

---

### Post by tmilam on 2006-05-03
So nobody knows how to use the wordpress package provided by ubuntu? 

](*,) 

Guess I'll install it from source....

---

### Post by simplyw00x on 2006-05-05
It's written in PHP so no compilation or installation is necessary; simply untar into a folder.

---

### Post by airtonix on 2006-05-22
Yep i've used it.....i would recomend Drupal 4.7 Instead.

Not because its more user friendly than wordpress(which it could be if you become proficient with php and mysql), but because its code base and template system gives rise to so much more variations than wordpress ever could.....

you want to keep your options as open as possible, and this becomes more achievable when you explore what drupal can offer.

really though, 
+ go to the wordpress website, download the files. 
+ wipe the apache-default folder from your /var/www 
+ extract the wordpress archvie to the '/var/www' so that 'index.php' sits under the 'www' directory.
+ open up phpmyadmin htt://localhost/phpmyadmin
+ make a database remember the name.
+ open up [http://localhost](http://localhost) .... a page with an error should come up, which depending on the success of your **lamp** installation, this should be a page that also contains a button or link saying [B]next.
+ [/B]click it.
+ it will ask you some questions, to which you have created the answer to one already threes steps above.
+ if al goes well, you should be looking at your frontpage of wordpress toting the kubrick theme, which is a rounded corner style not too disimilar to the clearlooks window theme.

enjoy
+

---

### Post by Crimguy on 2006-05-22
[QUOTE=tmilam]So nobody knows how to use the wordpress package provided by ubuntu? 

](*,) 

Guess I'll install it from source....[/QUOTE]

Is your problem with installation or usage?

When I installed wp, it was simply a matter of installing php, apache, and wp.  

For usage, open a browser, goto the rootdirectory of the site, e.g. 192.16.1.100, and you should see the wp site.  To edit things go to the /wpadmin directory of the site, e.g. 192.168.1.100/wpadmin.

Goood luck.

---

### Post by adamkane on 2006-05-24
Install LAMP this way:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Then install WordPress.

Open an account on wordpress.com to make your life easier.

---

### Post by thomas.mcmahon on 2007-01-08
Hey everyone,

I tried installing the Ubuntu wordpress package today, and it didn't work at all. I went through the instructions on the wordpress site and ended up just getting errors whilst trying to logon to localhost.

"Your PHP installation appears to be missing the MySQL which is required for WordPress."

I got this error even though I had everything installed through apt.

I don't understand why this package is so broken. LAMP should be a one click install, this is rediculous.

Anyway hopefully something is done to fix this package as obviously it doesn't work.

Tom

---

### Post by chrisfay on 2007-01-08
How did you install Wordpress? Via apt-get or manual download from the Wordpress site?

I would recommend getting it from Wordpress, then just drop the files wherever you want on your web server. Did you create the database before trying to install? Are you sure you have a functioning MySQL install?

Maybe try creating a new php file, and input:

[PHP]<?php phpinfo(); ?>[/PHP]

....then navigate to that file through a web browser. Make sure you have everything you need.

More info would be needed to narrow it down...

---

### Post by Carl H on 2007-01-09
> **Crimguy said:**
>  To edit things go to the /wpadmin directory of the site, e.g. 192.168.1.100/wpadmin.

That should be /wp-admin  ;) 

I've been using WordPress for a while, and find it to be pretty darned good.  My only complaint would be that a lot of the billions of themes are very similar. :neutral:

---

### Post by blackapple on 2007-01-28
Please follow the documentation of debianised WordPress.

[INDENT]**/usr/share/doc/wordpress/README.Debian**
#### Quick setup

Setup apache to point to /usr/share/wordpress. See the examples/apache.conf

Database setup can be done with the help of a script in examples/setup-mysql

#### A little more about the (multiple blog) configuration

The default wp-config.php searches for a (mysql) configuration filename based
on the blog's host. This allows you to host more than one blog on a Debian
system.

#### Upgrading from 1.5-1 and below

If you would like to use the optional default multiple blog configuration from
version 1.5-2 then:

Backup your database. [http://codex.wordpress.org/Backing_up_your_database](http://codex.wordpress.org/Backing_up_your_database)
Backup your configs, sudo cp -r /etc/wordpress/ ~/asafeplace
Purge wordpress, apt-get remove --purge wordpress
Install wordpress, apt-get install wordpress
Point your browser to your blog and you should get an error message similar to above.
Copy in your backed up wp-config.php to what it failed to open in the Fatal error, e.g. /etc/wordpress/config-my.blog.example.com.php
Ensure correct permissions, sudo chown :www-data /etc/wordpress/*

#### Plugins, themes and extra bits related to Wordpress

Currently plugins and themes need to be dropped in by root into:
/usr/share/wordpress/wp-content
Or better by utilising symbolic links. e.g.
ln -s /home/user/mytheme /usr/share/wordpress/wp-content/themes/mytheme
[/INDENT]

---

### Post by crouton on 2007-01-31
> **thomas.mcmahon said:**
> 
"Your PHP installation appears to be missing the MySQL which is required for WordPress."

I got this error even though I had everything installed through apt.


Although a LAMP install should have gotten this, it's possible that it did not install the PHP-MySQL interop module.  

Either
>  apt-get install php4-mysql 
or
>  apt-get install php5-mysql 
should get you up and running (or further along) depending on which version of php you want to use.

---

