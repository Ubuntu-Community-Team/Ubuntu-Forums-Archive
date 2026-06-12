---
title: "Apache2.2 denies access to home folders?"
date: 2010-01-14
forum: Server Platforms
---

### Post by badSheep8 on 2010-01-14
Yesterday I configured my apache2. On my Intrepid I had apache2.0 while on my Karmic I have a apache2.2. Aftere configuring I tested it and got a an error page when I tested it in my web browser.

I looked into the log file that showed the following error "[client 127.0.0.1] (13)Permission denied: access to /my_dir/ denied".

It appears apache2.2 can't access directories in my home folder.

[LIST]
[*]File system rights for the files and folders are correct.
[*]There is no AppArmor profile for Apache.
[*]User settings in "/etc/apache2/apache2.conf" file are correct.
[/LIST]

The inaccessible folder in "/etc/apache2/sites-available/default" looks as follows:

        Alias /my_dir/ "/home/me/www/"
        <Directory "/home/me/www/">
        Options Indexes MultiViews +FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
        </Directory>

A trick using symbolic links didn't work either. On my previous Intrepid with Apache 2.0 my pages worked like a charm. Now on my current Karmic (before apache2.conf was pre configured, now it's not) with Apache 2.2 my pages are wrecked.

Anybody who has a clue how I can make Apache2.2 access folders in my home folder and which settings are needed in default file for that?

---

### Post by cdenley on 2010-01-14
Works fine for me.

```

cdenley@ubuntu:~$ cat /etc/apache2/sites-available/default
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
    Alias /my_dir/ "/home/cdenley/www/"
    <Directory "/home/cdenley/www/">
       Options Indexes MultiViews +FollowSymLinks
       AllowOverride None
       Order deny,allow
       Deny from all
       Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>
cdenley@ubuntu:~$ ls -ld ~/www
drwxr-xr-x 2 root root 4096 2010-01-14 09:38 /home/cdenley/www
cdenley@ubuntu:~$ echo -e "GET /my_dir/ HTTP/1.0\n"|nc 127.0.0.1 80
HTTP/1.1 200 OK
Date: Thu, 14 Jan 2010 15:41:37 GMT
Server: Apache/2.2.12 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 691
Connection: close
Content-Type: text/html;charset=UTF-8

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<html>
 <head>
  <title>Index of /my_dir</title>
 </head>
 <body>
<h1>Index of /my_dir</h1>
<table><tr><th><img src="/icons/blank.gif" alt="[ICO]"></th><th><a href="?C=N;O=D">Name</a></th><th><a href="?C=M;O=A">Last modified</a></th><th><a href="?C=S;O=A">Size</a></th><th><a href="?C=D;O=A">Description</a></th></tr><tr><th colspan="5"><hr></th></tr>
<tr><td valign="top"><img src="/icons/back.gif" alt="[DIR]"></td><td><a href="/">Parent Directory</a></td><td>&nbsp;</td><td align="right">  - </td></tr>
<tr><th colspan="5"><hr></th></tr>
</table>
<address>Apache/2.2.12 (Ubuntu) Server at 127.0.0.1 Port 80</address>
</body></html>

```
Are you sure the permissions are all correct?
```

webfile="/home/me/www"
ls -l "$webfile"
while [ "$webfile" != "/" ]
do
    webfile=`dirname "$webfile"`
    ls -ld "$webfile"
done

```

---

### Post by Vegan on 2010-01-14
First mistake, you web page code does not go into the default settings, it goes into /var/www which is the location of "it works" when you launch a browser.

Next, always put special settings in httpd.conf which is meant for users.

For vhosts, search google for examples. In brief you make a separate file for each, there are examples in this forum.

When I get around to it, I may post a complete tutorial on using Apache.

---

### Post by cdenley on 2010-01-14
> **Vegan said:**
> 
Next, always put special settings in httpd.conf which is meant for users.


httpd.conf shouldn't be used at all. It is only there for backwards compatibility.

---

### Post by badSheep8 on 2010-01-15
Thanks for the respones.

> **cdenley said:**
> 
Works fine for me.


So you have you have Apache2.2 on Ubuntu9.10 and your home folder is encrypted (done by Ubuntu upon installation)?

> **Vegan said:**
> First mistake, you web page code does not go into the default settings, it goes into /var/www which is the location of "it works" when you launch a browser.

Next, always put special settings in httpd.conf which is meant for users.

For vhosts, search google for examples. In brief you make a separate file for each, there are examples in this forum.

When I get around to it, I may post a complete tutorial on using Apache.

I assume "/var/www" will work but that's not how I'd like it. I want my main things in my encoded home folder. This also make it easier to make backups and so on.

---

### Post by cdenley on 2010-01-15
> **badSheep8 said:**
> 
So you have you have Apache2.2 on Ubuntu9.10 and your home folder is encrypted (done by Ubuntu upon installation)?


I do not have an encrypted home, but that should be irrelevant. One mounted filesystem is the same as another as far as apache is concerned. All that matters is the permissions on the mounted filesystem. It is mounted, right? Once again, are you sure all the permissions are correct? Could you post the output I requested?

---

### Post by badSheep8 on 2010-01-18
Thanks cdenley for your reply.

I gave it another try and came up with the following result:

-rw-r--r-- 1 x x 14 2010-01-18 23:13 new_text_file.txt
drwx------ 53 x x 16384 2010-01-18 23:14 /home/me
drwxr-xr-x 2 x x 4096 2010-01-18 23:13 /home/me/www/

As you might have noticed, www only contains one file. User rights seem to be ok. I even tried 744 for both "home" and "me" but that didn't work. It's as if my home folder is a no go area for Apache2.2

---

### Post by cdenley on 2010-01-19
> **badSheep8 said:**
> Thanks cdenley for your reply.

I gave it another try and came up with the following result:

-rw-r--r-- 1 x x 14 2010-01-18 23:13 new_text_file.txt
drwx------ 53 x x 16384 2010-01-18 23:14 /home/me
drwxr-xr-x 2 x x 4096 2010-01-18 23:13 /home/me/www/

As you might have noticed, www only contains one file. User rights seem to be ok. I even tried 744 for both "home" and "me" but that didn't work. It's as if my home folder is a no go area for Apache2.2

If a user does not have permission set for the access/execute bit on any of the parent directories, that user cannot access that directory.
```

sudo chmod o+x /home
sudo chmod o+x /home/me

```

```

webfile="/home/me/www"
ls -l "$webfile"
while [ "$webfile" != "/" ]
do
    webfile=`dirname "$webfile"`
    ls -ld "$webfile"
done

```

---

### Post by badSheep8 on 2010-01-20
Thanks cdenley, your solution worked.

I thought that one could enter directories if the user rights on that particular directory were correct, despite what user rights on higher directories were but I was completely wrong.

Also Karmic gives the home folder 700 user rights by default it seems (which is good) and Intrepid put user rights in 755 so that's why I didn't faced my problem earlier.

---

