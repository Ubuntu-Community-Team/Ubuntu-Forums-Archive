---
title: "Setting Apache Docroot to a folder in home dir"
date: 2010-01-09
forum: Server Platforms
---

### Post by sambojam on 2010-01-09
Hi guys and gals,

This has got to be an easy one!!

Vanilla install of Karmic (64 bit) - would like to change the Apache doc root to point to /home/sam/www as it's my web development machine. (Default install is working fine)

Created copy of 'default' to 'mylocal' in '/etc/apache2/sites-available'

```

<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/sam/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/sam/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
...


```

The permissions on the folder in my home dir:

```

sam@rocket:~$ ls -la ww*
total 16
drwxrwxrwx  2 sam sam  4096 2010-01-09 22:26 .
drwx------ 35 sam sam 12288 2010-01-09 22:11 ..
-rwxrwxrwx  1 sam sam   100 2010-01-09 22:27 index.html
sam@rocket:~$ pwd
/home/sam
sam@rocket:~$

```

The sites enabled set up:
```

root@rocket:/etc/apache2# ls -la sites-enabled/
total 8
drwxr-xr-x 2 root root 4096 2010-01-09 22:24 .
drwxr-xr-x 7 root root 4096 2009-12-20 00:22 ..
lrwxrwxrwx 1 root root   26 2010-01-09 22:24 mylocal -> ../sites-available/mylocal

```

But I still get:
"Forbidden
You don't have permission to access / on this server"

I've had a really good crack at this but have hit a brick wall.
Using the following tutorial as an example:[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If anyone can help my with this seemingly simple problem - I'd really appreciate it!

Many thanks in advance

---

### Post by sambojam on 2010-01-09
Attached my apache2.conf and vhost file - might help anyone spot where I've gone wrong.

Cheers

---

### Post by stlsaint on 2010-01-10
you need to change your apache2 conf to show that document root is /home/you/www

i wasnt seeing it done unless im just missing it.

---

### Post by sambojam on 2010-01-10
Hey thanks for your reply stlsaint - but I'm not sure what you mean? 

Are you saying that the 'DocumentRoot /home/sam/www/' directive should be in my apache.conf file and not the default (mylocal) vhost file?

I haven't seen a set up like that before? Can you post an example?

Cheers

Sam

---

### Post by BkkBonanza on 2010-01-10
This is likely just a simple permissions issue.
Your doc root has to have read permissions for the user that apache runs as.
Check what name httpd is running as (ignore the root one as it spawns the others),

ps aux | grep httpd

Lets' say it's www-data as default, then,

sudo chown -R sam:www-data /home/sam/www
sudo chmod -R 750 /home/sam/www

---

### Post by sambojam on 2010-01-11
Hi BkkBonaza,

Permissions is exactly what I thought? But no joy. Even when I make the doc root fully permissible '777' I still get a 403?!

```

sam@rocket:~$ ps aux | grep httpd
sam       2825  0.0  0.0   7340   880 pts/1    R+   08:03   0:00 grep --color=auto httpd

```


```

www-data  2091  0.0  0.1 266656  6524 ?        S    07:30   0:00 /usr/sbin/apache2 -k start
www-data  2092  0.0  0.1 266656  6524 ?        S    07:30   0:00 /usr/sbin/apache2 -k start
www-data  2093  0.0  0.1 266656  6524 ?        S    07:30   0:00 /usr/sbin/apache2 -k start

```

I've even attached my default vhost file which works perfectly.

Thanks for you time though.

---

### Post by BkkBonanza on 2010-01-11
The only thing I can think of is that your /home or /home/sam have no exec perms for group www-data. I think that exec needs to be present all the way up for apache to be able to get access. I haven't checked this but I think a long time ago a ran into an issue like that. If a private /home/sam 700 it may stop it. Try 750 with group www-data.

Something to check, just in case.

---

### Post by sambojam on 2010-01-12
Very good BkkBonaza! You're a genius! 

I was really pulling my hair out on this one....

My home dir was set to 700? - I haven't done a completely fresh build on one of my machines for a couple of years -  running 8.04 LTS on my other box so am not sure if these are the normal permissions for the primary user?

Broken:
```

sam@rocket:/home$ ls -la
total 28
drwxr-xr-x  5 root     root  4096 2010-01-05 05:01 .
drwxr-xr-x 23 root     root  4096 2010-01-12 09:13 ..
lrwxrwxrwx  1 root     root    44 2009-12-11 23:27 .directory -> /etc/kubuntu-default-settings/directory-home
drwxr-xr-x  3 root     root  4096 2009-12-11 23:31 .ecryptfs
drwx------ 36 sam      sam  12288 2010-01-12 09:18 sam

```

Working:
```

sam@rocket:/home$ sudo chmod 751 sam/
sam@rocket:/home$ ls -la
total 28
drwxr-xr-x  5 root     root  4096 2010-01-05 05:01 .
drwxr-xr-x 23 root     root  4096 2010-01-12 09:13 ..
lrwxrwxrwx  1 root     root    44 2009-12-11 23:27 .directory -> /etc/kubuntu-default-settings/directory-home
drwxr-xr-x  3 root     root  4096 2009-12-11 23:31 .ecryptfs
drwxr-x--x 36 sam      sam  12288 2010-01-12 09:18 sam

```

Anyway I can get back on with my life now.

Many thanks

---

### Post by BkkBonanza on 2010-01-12
Genius? Proven not. But I'm glad it worked out.

Another thing you might consider that would allow keeping the same apache config between a dev system and live system is to use a symlink. Like this,

ln -s /home/sam/www /var/www/sam

Then leave your site cfg as usual /var/www/sam. The symlink maps that directory into your home where it will get caught by ecryptfs (which is my guess why you want it there). The advantage with this is you don't have to maintain different site cfg files and update changes manually.

---

