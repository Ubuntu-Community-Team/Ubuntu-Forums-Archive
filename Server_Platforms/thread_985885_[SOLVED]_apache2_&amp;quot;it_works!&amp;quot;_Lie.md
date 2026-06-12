---
title: "[SOLVED] apache2 &amp;quot;it works!&amp;quot; Lies!"
date: 2008-11-18
forum: Server Platforms
---

### Post by Deadmode on 2008-11-18
Ok I've been trying to get my blog back up and running and I've been having a hell of a time.   As far as I know I've done everything right, but no matter what apache refuses post my blog.  Right now apache is bent on saying "it works!" ...but the cake is a lie :-({|=. It just seems like apache needs to be pointed to the right directory path or could just be a problem with wordpress.  The port is set correctly on the router.  I get weird errors in /var/log/apache2/error.log 

```
[error] [client 192.168.1.1] File does not exist: /var/www/wp_admin
```

No, that file is definitely there Mr error.log!

/etc/apache2/sites-enabled/000-default
```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
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
        ServerSignature On

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

/etc/apache2/ports.conf
```
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>
```

---

### Post by hyper_ch on 2008-11-18
(1) When you post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

(2) When you can see "it works" it means that apache is working. However you have not set it up right to you desires. Saying that it lies is completely wrong.

(3) what's the index name of that (php) program you want to run? Where is that index file and how did you set apache to handle index files?

---

### Post by MJN on 2008-11-18
[Edit: Hyper_ch beat me to it! You really need to provide more information as to what you're trying to do, what you expected to happen, and what actually happened. This problem will turn out to be user error and so by being as descriptive as you can means we can find at what point your error/misunderstanding occurs.]
 
> **Deadmode said:**
> ```
[error] [client 192.168.1.1] File does not exist: /var/www/wp_admin
```
-------------------------------------------------------------
No, that file is definitely there Mr error.log!Post the output of **ls -l /var/www**
 
What URL is you requesting?
 
Mathew

---

### Post by Techinica on 2008-11-18
Sounds like the exact same problem I´m having...

Apache is loading your /var/www directory content instead of that of any of your subdirectories...

---

### Post by JKHinton CPBD on 2008-11-18
I am having the same problem no content in any subdirectory below
/var/www directory can be viewed from localhost.  As long as it is in /var/www directory no problems but when I extend /var/www/next/directory no pages can be viewed from localhost.

---

### Post by cdenley on 2008-11-18
Why isn't anybody posting the output of "ls -l /var/www" as MJN suggested? We can't help you if you don't provide enough information. It works fine for me.

Also, post the output of the command "wget -O - http://localhost/wp_admin/", or replace that url with whichever one you are having trouble with.

/etc/apache2/sites-available/default
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/
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

</VirtualHost>

```

```

cdenley@ubuntu:~$ ls -lR /var/www
/var/www:
total 12
-rw-r--r-- 1 root root   45 2008-10-27 11:07 index.html
drwxr-xr-x 2 root root 4096 2008-11-18 09:19 test1
drwxr-xr-x 2 root root 4096 2008-11-18 09:19 test2

/var/www/test1:
total 4
-rw-r--r-- 1 root root 51 2008-11-18 09:20 index.php

/var/www/test2:
total 4
-rw-r--r-- 1 root root 51 2008-11-18 09:19 index.php

```

```

cdenley@ubuntu:~$ wget -O - http://localhost/
--2008-11-18 09:26:28--  http://localhost/
Resolving localhost... 127.0.0.1
Connecting to localhost|127.0.0.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45 [text/html]
Saving to: `STDOUT'

 0% [                                       ] 0           --.-K/s              <html><body><h1>It works!</h1></body></html>
100%[======================================>] 45          --.-K/s   in 0s      

2008-11-18 09:26:28 (4.69 MB/s) - `-' saved [45/45]

cdenley@ubuntu:~$ wget -O - http://localhost/test1/
--2008-11-18 09:26:31--  http://localhost/test1/
Resolving localhost... 127.0.0.1
Connecting to localhost|127.0.0.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7 [text/plain]
Saving to: `STDOUT'

 0% [                                       ] 0           --.-K/s              
test1
100%[======================================>] 7           --.-K/s   in 0s      

2008-11-18 09:26:31 (779 KB/s) - `-' saved [7/7]

cdenley@ubuntu:~$ wget -O - http://localhost/test2/
--2008-11-18 09:26:36--  http://localhost/test2/
Resolving localhost... 127.0.0.1
Connecting to localhost|127.0.0.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7 [text/plain]
Saving to: `STDOUT'

 0% [                                       ] 0           --.-K/s              
test2
100%[======================================>] 7           --.-K/s   in 0s      

2008-11-18 09:26:36 (667 KB/s) - `-' saved [7/7]

```

---

### Post by Deadmode on 2008-11-18
> **hyper_ch said:**
> (1) When you post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

(2) When you can see "it works" it means that apache is working. However you have not set it up right to you desires. Saying that it lies is completely wrong.

(3) what's the index name of that (php) program you want to run? Where is that index file and how did you set apache to handle index files?

Ya sorry I will use ```

``` to make it easier to read.  Yes I understand apache is working, but I can't get it broadcast the right info.  It's just irritating because I spent the whole day searching and testing out different things before I came here.  I'm trying to get my wordpress blog up and running again. I threw all the files that I had backed up before in /var/www/. But ya I don't know whether the name is index.html or index.php.
[QUOTE=MJN]Post the output of ls -l /var/www

What URL is you requesting?

Mathew[/QUOTE]
I'm just requesting localhost. This is what ls -l /var/www looks like 
```
:~$ ls -l /var/www
total 248
-rw-r--r-- 1 root root  1406 2008-11-18 02:34 favicon.ico
-rw-r--r-- 1 root root    45 2008-11-18 01:15 index.html
-rw-r--r-- 1 root root    94 2008-11-18 01:14 index.php
-rw-r--r-- 1 root root 15127 2008-11-18 01:14 license.txt
drwxr-xr-x 3 root root  4096 2008-11-18 01:14 munin
-rw-r--r-- 1 root root  7631 2008-11-18 01:14 readme.html
-rw-r--r-- 1 root root    19 2008-11-18 01:14 test.php
drwxr-xr-x 4 root root  4096 2008-11-18 01:14 wp-admin
-rw-r--r-- 1 root root 36399 2008-11-18 01:14 wp-app.php
-rw-r--r-- 1 root root   127 2008-11-18 01:14 wp-atom.php
-rw-r--r-- 1 root root   997 2008-11-18 01:14 wp-blog-header.php
-rw-r--r-- 1 root root  2905 2008-11-18 01:14 wp-comments-post.php
-rw-r--r-- 1 root root   151 2008-11-18 01:14 wp-commentsrss2.php
-rw-r--r-- 1 root root   926 2008-11-18 01:44 wp-config.php
-rw-r--r-- 1 root root   942 2008-11-18 01:14 wp-config-sample.php
drwxr-xr-x 6 root root  4096 2008-11-18 01:14 wp-content
-rw-r--r-- 1 root root   849 2008-11-18 01:14 wp-cron.php
-rw-r--r-- 1 root root   120 2008-11-18 01:14 wp-feed.php
drwxr-xr-x 4 root root  4096 2008-11-18 01:14 wp-includes
-rw-r--r-- 1 root root  1517 2008-11-18 01:14 wp-links-opml.php
-rw-r--r-- 1 root root 16022 2008-11-18 01:14 wp-login.php
-rw-r--r-- 1 root root  5674 2008-11-18 01:14 wp-mail.php
-rw-r--r-- 1 root root   291 2008-11-18 01:14 wp-pass.php
-rw-r--r-- 1 root root   188 2008-11-18 01:14 wp-rdf.php
-rw-r--r-- 1 root root   251 2008-11-18 01:14 wp-register.php
-rw-r--r-- 1 root root   127 2008-11-18 01:14 wp-rss2.php
-rw-r--r-- 1 root root   125 2008-11-18 01:14 wp-rss.php
-rw-r--r-- 1 root root  9279 2008-11-18 01:14 wp-settings.php
-rw-r--r-- 1 root root  3518 2008-11-18 01:14 wp-trackback.php
-rw-r--r-- 1 root root 56885 2008-11-18 01:14 xmlrpc.php
```

[QUOTE=cdenley]Also, post the output of the command "wget -O - http://localhost/wp_admin/", or replace that url with whichever one you are having trouble with.[/QUOTE]
```
:~$ wget -O - http://localhost/wp-admin
--14:38:51--  http://localhost/wp-admin
           => `-'
Resolving localhost... 127.0.0.1
Connecting to localhost|127.0.0.1|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://localhost/wp-admin/ [following]
--14:38:51--  http://localhost/wp-admin/
           => `-'

```
I get a response with /wp-admin not /wp_admin.  I wonder if all my folders in /var/www are named incorrectly due to an older version of wordpress that I once had?  Also my blog pops right up if I put [http://localhost/index.php](http://localhost/index.php) in the url.  How can I make it point to index.php by just typing in [http://localhost/](http://localhost/) ?

---

### Post by cdenley on 2008-11-18
Try [http://localhost/wp-admin/](http://localhost/wp-admin/)

---

### Post by Deadmode on 2008-11-18
> **cdenley said:**
> Try [http://localhost/wp-admin/](http://localhost/wp-admin/)

I get my wordpress login screen. I can log in and everthing.  But it still is being stubborn to just load using [http://localhost](http://localhost).

---

### Post by cdenley on 2008-11-18
> **Deadmode said:**
> I get my wordpress login screen. I can log in and everthing.  But it still is being stubborn to just load using [http://localhost](http://localhost).

What? You mean you're getting redirected? Apache seems to be working properly. Your script is redirecting you.

---

### Post by Deadmode on 2008-11-18
> **cdenley said:**
> What? You mean you're getting redirected? Apache seems to be working properly. Your script is redirecting you.

Ah alright.  How can I change this?  Thank you very much for all your help.

---

### Post by cdenley on 2008-11-18
> **Deadmode said:**
> Ah alright.  How can I change this?  Thank you very much for all your help.

I don't know. I never used wordpress. It's probably a configuration variable you set incorrectly.

---

### Post by Deadmode on 2008-11-18
hmm ok I'll look around and see if I can find anything.

---

### Post by cdenley on 2008-11-18
> **Deadmode said:**
> Also my blog pops right up if I put [http://localhost/index.php](http://localhost/index.php) in the url.  How can I make it point to index.php by just typing in [http://localhost/](http://localhost/) ?

By default, it should use index.php as a default page.

/etc/apache2/mods-enabled/dir.conf
```

<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

</IfModule>

```

---

### Post by Deadmode on 2008-11-18
> **cdenley said:**
> By default, it should use index.php as a default page.

/etc/apache2/mods-enabled/dir.conf
```

<IfModule mod_dir.c>

          DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm

</IfModule>

```

Ya my dir.conf looks just like that.  Like you said it must be wordpress.  I'll research.  Throw me a line if anyone can think of anything.  Thanks again.

---

### Post by hyper_ch on 2008-11-18
in the index directive of apache2 you have also the order in which it checks for index files. Now compare that order to the existing index files in your root webfolder: which one is going to be served first?

---

### Post by flashgc on 2008-11-18
Well lets see.... the ls of your /var/www/ directory showed an index.html file as well as an index.php.

Now looking at the listing posted from 'mod_dir.c' it shows a list of file names. Notice that index.html is in the list prior to index.php? Try renaming the index.html to something else or mebbe just rearrange the order of the list in 'mod_dir.c' so the php file type comes before the html type. You might have to restart Apache for that to work. Make a difference?

---

### Post by Deadmode on 2008-11-18
> **flashgc said:**
> Well lets see.... the ls of your /var/www/ directory showed an index.html file as well as an index.php.

Now looking at the listing posted from 'mod_dir.c' it shows a list of file names. Notice that index.html is in the list prior to index.php? Try renaming the index.html to something else or mebbe just rearrange the order of the list in 'mod_dir.c' so the php file type comes before the html type. You might have to restart Apache for that to work. Make a difference?

Rearranging index.php with index.html in the /etc/apache2/mods-enabled/dir.conf restarted apache now everything is up and working!  Thank you so much!

---

