---
title: "Apache tries to load .htaccess that doesn't exist"
date: 2009-12-24
forum: Server Platforms
---

### Post by KillerSponge on 2009-12-24
Hi,

I recently tried to install Apache on my machine. I changed the webroot in sites-available/default, but now Apache gives a 403 forbidden error, no matter what address I type in. 

When I check the error logs, it says that Apache failed to read the .htaccess file in my webroot, and that I should check if it is readable. But I don't even have a .htaccess file in my webroot...

Does anyone know how to solve this? :)

---

### Post by KillerSponge on 2009-12-25
Anyone? :(

---

### Post by Vegan on 2009-12-25
Did you make sure permissions were set properly?

That is often overlooked when moving web folders around.

---

### Post by KillerSponge on 2009-12-26
Everything, including the webroot itself, is set to 775, owner is me, and group is www-data. That should work fine, right?

---

### Post by volkswagner on 2009-12-26
I am not sure if I am crazy, or if the Apache2 package changed.  I have always been able to run sites with myself as owner and group set to www-data.

I am converting to a vps which is the same 8.04 version yet I have had to set owner and group when moving sites over to the second server.

Just a thought, you may need to set owner as www-data.

---

### Post by KillerSponge on 2009-12-27
Thanks for the suggestion, but that didn't work unfortunately :(

---

### Post by Vegan on 2009-12-27
So what settings do you have in /etc/apache2

post them here so we can take a look

---

### Post by KillerSponge on 2010-01-01
This is my configuration:

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/killersponge/dev/webdev
        <Directory /home/killersponge/dev/webdev/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order Allow,deny
                Allow from all
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

---

### Post by volkswagner on 2010-01-01
Are the files readable by www-data, user for apache2?

```
ls -alt /home/killersponge/dev/webdev

```

Unrelated:  I see you don't have the ServerName directive listed.  Are you just using your IP address, or localhost?


> **Vegan said:**
> So what settings do you have in /etc/apache2

post them here so we can take a look

As Vegan mentioned there are more config files to examine.  If you did not modify any, my guess is permission for your home folder.


```
ls -alt /etc/apache2
```

How many sites are enabled?
```
ls -alt /etc/apache2/sites-enabled
```

Any config files added to conf.d?
```
ls -alt /etc/apache2/conf.d
```

```
cat /etc/apache2/httpd.conf
```

---

### Post by KillerSponge on 2010-01-01
All files and directories in webdev are readable by the group www-data, that should be correct, right?

I only have the default site enabled (000-default), and I haven't added any conf files, at least, not by myself. The ls lists charset, localized-error-pages and security. The cat command returns nothing.

Thanks for the help so far, does this help any? :)

Edit: ServerName defaults to localhost, right? In any case, both IP adress and hostname give the same problem.

---

### Post by volkswagner on 2010-01-01
I am surprised that httpd.conf is empty.  That may be an issue.

What type of content is in your webroot, static .html or other.

Is the .htaccess error still happening or is that an old error in error.log?

If you change the default host back to webroot of /var/www do you get the "it works" page?

---

### Post by KillerSponge on 2010-01-02
This did suprise me a bit: when I changed the webroot back to /var/www it 'worked' (as in, I got the "It works!" page). When I change it back to my webdev directory, it still gives a 403, with the same error in error.log:

```
(13)Permission denied: /home/killersponge/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
```

My webroot contains mainly dynamic files, but no matter what I page I try to access (doesn't matter if the file actually exists or not), I get the 403 error. :confused:

---

### Post by volkswagner on 2010-01-02
I would say you have permission issues with

/home/killersponge/dev/webdev


You could **temporarily** chmod it to 777 to see if the site works.

Or post the output of

```
ls -alt /home/killersponge/dev/webdev
```

Print the output of the above to keep track before and after any changes.

---

### Post by KillerSponge on 2010-01-03
Alright, here you go :)

Before:
```
total 52
drwxrwxr-x  6 killersponge www-data     4096 2009-12-24 02:50 .svn
drwxrwxr-x 11 killersponge www-data     4096 2009-12-13 17:11 .
-rwxrwxr-x  1 killersponge www-data        0 2009-12-13 17:11 aap
drwxrwxr-x 13 killersponge www-data     4096 2009-12-13 16:15 sites
drwxrwxr-x 11 killersponge www-data     4096 2009-12-13 16:13 archive
drwxr-xr-x 14 killersponge killersponge 4096 2009-12-12 00:58 ..
-rwxrwxr-x  1 killersponge www-data      117 2009-12-12 00:58 index.php
-rwxrwxr-x  1 killersponge www-data     3540 2009-12-12 00:58 database.php
drwxrwxr-x 12 killersponge www-data     4096 2009-12-12 00:58 pma
drwxrwxr-x  7 killersponge www-data     4096 2009-12-12 00:58 scripts
drwxrwxr-x 19 killersponge www-data     4096 2009-12-12 00:58 temp
drwxrwxr-x  9 killersponge www-data     4096 2009-12-12 00:58 backup
drwxrwxr-x 63 killersponge www-data     4096 2009-12-12 00:56 labs
drwxrwxr-x 11 killersponge www-data     4096 2009-12-12 00:55 service
```

After:
```
total 52
drwxrwxrwx  6 killersponge www-data     4096 2009-12-24 02:50 .svn
drwxrwxrwx 11 killersponge www-data     4096 2009-12-13 17:11 .
-rwxrwxrwx  1 killersponge www-data        0 2009-12-13 17:11 aap
drwxrwxrwx 13 killersponge www-data     4096 2009-12-13 16:15 sites
drwxrwxrwx 11 killersponge www-data     4096 2009-12-13 16:13 archive
drwxr-xr-x 14 killersponge killersponge 4096 2009-12-12 00:58 ..
-rwxrwxrwx  1 killersponge www-data      117 2009-12-12 00:58 index.php
-rwxrwxrwx  1 killersponge www-data     3540 2009-12-12 00:58 database.php
drwxrwxrwx 12 killersponge www-data     4096 2009-12-12 00:58 pma
drwxrwxrwx  7 killersponge www-data     4096 2009-12-12 00:58 scripts
drwxrwxrwx 19 killersponge www-data     4096 2009-12-12 00:58 temp
drwxrwxrwx  9 killersponge www-data     4096 2009-12-12 00:58 backup
drwxrwxrwx 63 killersponge www-data     4096 2009-12-12 00:56 labs
drwxrwxrwx 11 killersponge www-data     4096 2009-12-12 00:55 service
```

Doesn't work either way :( The error in error.log also stays the same.

---

### Post by volkswagner on 2010-01-03
There may be an issue with your index.php page or other content.

Try placing a simple index.html in the webroot, such as copying /var/www/index.html to your webroot, and set yourself as owner and group to www-data.

You may temporarily rename index.php so there is no conflict.

If the simple index.html loads after, there is probably an issue with reading .php or the file itself.

Make sure php module is loaded.

```
ls -alt /etc/apache2/mods-enabled
```

look for:

```
...
lrwxrwxrwx 1 root root   27 2009-12-26 09:11 php5.conf -> ../mods-available/php5.conf
lrwxrwxrwx 1 root root   27 2009-12-26 09:11 php5.load -> ../mods-available/php5.load
```

---

### Post by KillerSponge on 2010-01-04
Changing the index file doesn't help. I didn't really expect that to work, as it doesn't matter what file I request, if it exists or not or in what subdirectory it is: it always gives a 403.

PHP module is loaded fine btw :)

---

### Post by volkswagner on 2010-01-04
Is your home folder protected in some other way?  Perhaps higher in the directory tree lives an .htaccess or other protection?

I am out of ideas.

Perhaps create a new user for htdocs and point apache vhost to their home directory.

---

### Post by someonestolemyname on 2010-06-06
I know that this thread is a bit old, but I came upon it searching for the answer to the same problem. I found the issue, figured I would post to help anyone in my situation.

For me at least the problem was that I had enabled the encrypted home directory option when I installed. According to bug #585212 ([https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/585212](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/585212)), the correct solution is to chmod -R 755 /home/$USER

Any lower permissions fails.

---

