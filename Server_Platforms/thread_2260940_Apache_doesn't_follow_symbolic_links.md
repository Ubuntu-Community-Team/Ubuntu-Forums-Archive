---
title: "Apache doesn't follow symbolic links"
date: 2015-01-15
forum: Server Platforms
---

### Post by mbnoimi on 2015-01-15
Apache doesn't follow symbolic links for some unknown reason although I configured it to accept them as following:

```
mbnoimi-laptop Projects # ls -l
total 4
drwxrwxr-x 2 www-data www-data 4096 &#1603;&#1575;&#1606;&#1608;&#1606; 15 14:31 MyBlog
mbnoimi-laptop Projects # cd MyBlog/
mbnoimi-laptop MyBlog # ls -l
total 20
-rwxrwxr-x 1 www-data www-data 11510 &#1603;&#1575;&#1606;&#1608;&#1606; 10 07:09 index.html
mbnoimi-laptop MyBlog # nano .htaccess
mbnoimi-laptop MyBlog # cat .htaccess 
Option Indexes
mbnoimi-laptop MyBlog # cd ..
mbnoimi-laptop Projects # ln -s '/home/mbnoimi/Desktop/Projects/MyBlog' /var/www/html/
mbnoimi-laptop Projects # ls -l /var/www/html/
total 12
-rwxrwxr-x 1 mbnoimi www-data 11510 &#1603;&#1575;&#1606;&#1608;&#1606; 10 07:09 index_.html
lrwxrwxrwx 1 root    root        37 &#1603;&#1575;&#1606;&#1608;&#1606; 15 14:48 MyBlog -> /home/mbnoimi/Desktop/Projects/MyBlog
mbnoimi-laptop Projects # chown -R www-data:www-data /var/www/html/MyBlog
mbnoimi-laptop Projects # ls -l /var/www/html/
total 12
-rwxrwxr-x 1 mbnoimi  www-data 11510 &#1603;&#1575;&#1606;&#1608;&#1606; 10 07:09 index_.html
lrwxrwxrwx 1 www-data www-data    37 &#1603;&#1575;&#1606;&#1608;&#1606; 15 14:48 MyBlog -> /home/mbnoimi/Desktop/Projects/MyBlog
mbnoimi-laptop Projects #
```

When I browse [http://localhost/MyBlog](http://localhost/MyBlog) I get:
```
Forbidden

You don't have permission to access /MyBlog on this server.
Apache/2.4.7 (Ubuntu) Server at localhost Port 80
```

/etc/apache2/sites-enabled/000-default.conf
```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/html
        <Directory />
                Options FollowSymLinks Indexes
                AllowOverride None
        </Directory>
        <Directory /var/www/html/>
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

My I get some help please?

---

### Post by mbnoimi on 2015-01-15
BTW, I read [this post](https://superuser.com/questions/244245/how-do-i-get-apache-to-follow-symlinks) but unfortunately it didn't help me to fix this issue :(

---

### Post by SeijiSensei on 2015-01-16
What does /var/log/apache2/error.log report?

You could use an alias instead of a symlink like this:
```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/html

        Alias /MyBlog /home/mbnoimi/Desktop/Projects/MyBlog
        <Directory "/home/mbnoimi/Desktop/Projects/MyBlog">
        [stuff]
        </Directory>
  
        <Directory />
                Options FollowSymLinks Indexes
                AllowOverride None
        </Directory>
        <Directory /var/www/html/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```
Also that .htaccess is being ignored since you have "AllowOverride None" set.

---

### Post by Doug S on 2015-01-16
I wonder if the problem (or one of the problems) might be with permissions of parent directories. For example:

I set up this:```
doug@s15:/home$ ls -l /var/www/html
total 28
lrwxrwxrwx 1 doug doug   14 Jan 16 11:35 bla -> /home/doug/bla
... deleted the rest...
```Which worked fine with this:```
doug@s15:/home$ ls -l
total 8
drwxr-xr-x 79 doug    doug    4096 Jan 16 11:34 doug
```but didn't work with this:```
doug@s15:/home$ chmod 700 doug
doug@s15:/home$ ls -l
total 8
drwx------ 79 doug    doug    4096 Jan 16 11:34 doug
```giving this:```
doug@s15:/home$ tail -1 /var/log/apache2/error.log
[Fri Jan 16 11:38:06.247259 2015] [core:error] [pid 23809] [client 192.168.111.101:60360] AH00037: Symbolic link not allowed or link target not accessible: /var/www/html/bla
```and this:```
Forbidden

You don't have permission to access /bla/index.html on this server.
Apache/2.4.7 (Ubuntu) Server at s15.smythies.com Port 80
```

---

### Post by mbnoimi on 2015-01-16
>  What does /var/log/apache2/error.log report?
I got:
```
[Fri Jan 16 22:03:53.004502 2015] [core:error] [pid 1983:tid 139872387987200] [client 127.0.0.1:44349] AH00037: Symbolic link not allowed or link target not accessible: /var/www/html/MyBlog
```

>  You could use an alias instead of a symlink like this:
I don't want to use ALIAS because it's not a practical solution for daily programming. I want to use symlinks because it's very easy to create a link to development project on outside apache data folder.

---

### Post by mbnoimi on 2015-01-16
>  I wonder if the problem (or one of the problems) might be with permissions of parent directories. For example:
I doubt that because I set the permission to the parent folder as mentioned before like that:
```
mbnoimi-laptop Projects # ls -l
total 4
drwxrwxr-x 2 www-data www-data 4096 &#1603;&#1575;&#1606;&#1608;&#1606; 15 14:31 MyBlog
```

---

### Post by Doug S on 2015-01-16
> **mbnoimi said:**
> I doubt that because I set the permission to the parent folder as mentioned before like that:
```
mbnoimi-laptop Projects # ls -l
total 4
drwxrwxr-x 2 www-data www-data 4096 &#1603;&#1575;&#1606;&#1608;&#1606; 15 14:31 MyBlog
```I meant the parent(s) of the symlink destination not its source, as per my very detailed example.

---

### Post by mbnoimi on 2015-01-16
```
mbnoimi@mbnoimi-laptop ~/Desktop/Projects $ ls -l .
total 4
drwxrwxr-x 2 www-data www-data 4096 Jan 15 14:41 MyBlog
mbnoimi@mbnoimi-laptop ~/Desktop/Projects $ cd ..
mbnoimi@mbnoimi-laptop ~/Desktop $ ls -l .
total 40
-rw-r--r-- 1 mbnoimi  mbnoimi    147 Jan  3 23:45 1sec.txt
-rw-r--r-- 1 mbnoimi  mbnoimi  16291 Jan  5 07:12 jun.odt
drwxrwxr-x 3 www-data www-data  4096 Jan 15 14:33 Projects
mbnoimi@mbnoimi-laptop ~/Desktop $
```

---

### Post by Doug S on 2015-01-16
Keep going.
You need to also look at permissions for /home/mbnoimi and /home.

---

### Post by mbnoimi on 2015-01-16
Come on! Do I've to set a permission for all my home director to 775 and own by www-data for accepting it in apache?!

---

### Post by Doug S on 2015-01-16
> **mbnoimi said:**
> Do I've to set a permission for all my home director to 775No. You just have to do enough to make it work. Notice in my example the permissions are set to 755, not 775. I didn't test the absolute minimum permissions to make it work, I leave that to you.> **mbnoimi said:**
> and own by www-data for accepting it in apache?!No, you don't have to do that, and you wouldn't want to in the higher level directories anyhow. Notice owner and group in my example, its me, not www-data.

Others might have different opinions. I'm just trying to help you figure out what might be wrong, I'm not commenting on if it is a good idea to do it this way or not.

---

### Post by SeijiSensei on 2015-01-19
Both /home and /home/mbnoimi must have the execute permission set for all users to let www-data see files in /home/mbnoimi/subdirectory/.

```

$ cd /
ls -l home
drwxr-xr-x  50 mbnoimi   mbnoimi   4096 Jan 17 08:13 mbnoimi
cd home/mbnoimi
ls -l  Desktop
[etc.]

```
All the directories' permissions have to include "r-x" at end like the above.

---

