---
title: "[SOLVED] PHP Issue"
date: 2008-06-05
forum: Server Platforms
---

### Post by TheAddict on 2008-06-05
So I have just installed a LAMP server on Gutsy server, and am having trouble with PHP. 

Basically, there is an issue with the "include_path" variable in the php.ini file, so that when I try to access any php file with code other than ```
<?php phpinfo(); ?>
``` I get the error

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/html/wordpress/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

I have found the offending line in the php.ini file, but regardless of what path I put in there, the error doesn't change, it simply reflects the new path.

I have webmin installed, and php is enabled, and I have tried 
```
sudo a2enmod mod_php
```and get the response that "This module does not exist!"

can anyone enlighten me as to how to fix this issue?

---

### Post by quelx on 2008-06-05
You've installed php5 but have you installed the apache2 module **libapache2-mod-php5**?  Also the mod is called **php5**

```
sudo a2enmod mod_php5[COLOR="Red"]*[/COLOR]
```

[COLOR="Red"]*[/COLOR]EDIT: The above is wrong... it's 
```
sudo a2enmod php5
```

---

### Post by TheAddict on 2008-06-05
Thanks for the response.

Yes I have libapache2-mod-php5 installed (I just tryied to apt-get install and it told me it is the newest version), and I also entered a2enmod mod_php5 and got the same module does not exist response

---

### Post by quelx on 2008-06-05
what does ```
ls -l /etc/apache2/mods-available/
``` show?

EDIT: Oh it's ```
sudo a2enmod php5
``` oops

---

### Post by TheAddict on 2008-06-05
list is as follows:

```
-rw-r--r-- 1 root root  332 2007-10-05 08:42 actions.conf
-rw-r--r-- 1 root root   66 2007-10-05 08:42 actions.load
-rw-r--r-- 1 root root  815 2007-10-05 08:42 alias.conf
-rw-r--r-- 1 root root   62 2007-10-05 08:42 alias.load
-rw-r--r-- 1 root root   60 2007-10-05 08:42 asis.load
-rw-r--r-- 1 root root   72 2007-10-05 08:42 auth_basic.load
-rw-r--r-- 1 root root   74 2007-10-05 08:42 auth_digest.load
-rw-r--r-- 1 root root   74 2007-10-05 08:42 authn_alias.load
-rw-r--r-- 1 root root   72 2007-10-05 08:42 authn_anon.load
-rw-r--r-- 1 root root   85 2007-10-05 08:42 authn_dbd.load
-rw-r--r-- 1 root root   70 2007-10-05 08:42 authn_dbm.load
-rw-r--r-- 1 root root   78 2007-10-05 08:42 authn_default.load
-rw-r--r-- 1 root root   72 2007-10-05 08:42 authn_file.load
-rw-r--r-- 1 root root   90 2007-10-05 08:42 authnz_ldap.load
-rw-r--r-- 1 root root   70 2007-10-05 08:42 authz_dbm.load
-rw-r--r-- 1 root root   78 2007-10-05 08:42 authz_default.load
-rw-r--r-- 1 root root   82 2007-10-05 08:42 authz_groupfile.load
-rw-r--r-- 1 root root   72 2007-10-05 08:42 authz_host.load
-rw-r--r-- 1 root root   74 2007-10-05 08:42 authz_owner.load
-rw-r--r-- 1 root root   72 2007-10-05 08:42 authz_user.load
-rw-r--r-- 1 root root 2335 2007-10-05 08:42 autoindex.conf
-rw-r--r-- 1 root root   70 2007-10-05 08:42 autoindex.load
-rw-r--r-- 1 root root   62 2007-10-05 08:42 cache.load
-rw-r--r-- 1 root root   70 2007-10-05 08:42 cern_meta.load
-rw-r--r-- 1 root root   68 2007-10-05 08:42 cgid.conf
-rw-r--r-- 1 root root   60 2007-10-05 08:42 cgid.load
-rw-r--r-- 1 root root   58 2007-10-05 08:42 cgi.load
-rw-r--r-- 1 root root   76 2007-10-05 08:42 charset_lite.load
-rw-r--r-- 1 root root   36 2007-10-05 08:42 dav_fs.conf
-rw-r--r-- 1 root root   79 2007-10-05 08:42 dav_fs.load
-rw-r--r-- 1 root root   58 2007-10-05 08:42 dav.load
-rw-r--r-- 1 root root   68 2007-10-05 08:42 dav_lock.load
-rw-r--r-- 1 root root   58 2007-10-05 08:42 dbd.load
-rw-r--r-- 1 root root  107 2007-10-05 08:42 deflate.conf
-rw-r--r-- 1 root root   66 2007-10-05 08:42 deflate.load
-rw-r--r-- 1 root root  112 2007-10-05 08:42 dir.conf
-rw-r--r-- 1 root root   58 2007-10-05 08:42 dir.load
-rw-r--r-- 1 root root  475 2007-10-05 08:42 disk_cache.conf
-rw-r--r-- 1 root root   89 2007-10-05 08:42 disk_cache.load
-rw-r--r-- 1 root root   64 2007-10-05 08:42 dump_io.load
-rw-r--r-- 1 root root   58 2007-10-05 08:42 env.load
-rw-r--r-- 1 root root   66 2007-10-05 08:42 expires.load
-rw-r--r-- 1 root root   72 2007-10-05 08:42 ext_filter.load
-rw-r--r-- 1 root root   89 2007-10-05 08:42 file_cache.load
-rw-r--r-- 1 root root   64 2007-10-05 08:42 filter.load
-rw-r--r-- 1 root root   66 2007-10-05 08:42 headers.load
-rw-r--r-- 1 root root   62 2007-10-05 08:42 ident.load
-rw-r--r-- 1 root root   68 2007-10-05 08:42 imagemap.load
-rw-r--r-- 1 root root   66 2007-10-05 08:42 include.load
-rw-r--r-- 1 root root  420 2007-10-05 08:42 info.conf
-rw-r--r-- 1 root root   60 2007-10-05 08:42 info.load
-rw-r--r-- 1 root root   60 2007-10-05 08:42 ldap.load
-rw-r--r-- 1 root root   76 2007-10-05 08:42 log_forensic.load
-rw-r--r-- 1 root root  185 2007-10-05 08:42 mem_cache.conf
-rw-r--r-- 1 root root   87 2007-10-05 08:42 mem_cache.load
-rw-r--r-- 1 root root 6279 2007-10-05 08:42 mime.conf
-rw-r--r-- 1 root root   60 2007-10-05 08:42 mime.load
-rw-r--r-- 1 root root   89 2007-10-05 08:42 mime_magic.conf
-rw-r--r-- 1 root root   72 2007-10-05 08:42 mime_magic.load
-rw-r--r-- 1 root root  663 2007-10-05 08:42 negotiation.conf
-rw-r--r-- 1 root root   74 2007-10-05 08:42 negotiation.load
-rw-r--r-- 1 root root  133 2007-10-05 09:36 php5.conf
-rw-r--r-- 1 root root   59 2007-10-05 09:36 php5.load
-rw-r--r-- 1 root root   87 2007-10-05 08:42 proxy_ajp.load
-rw-r--r-- 1 root root  103 2007-10-05 08:42 proxy_balancer.load
-rw-r--r-- 1 root root  589 2007-10-05 08:42 proxy.conf
-rw-r--r-- 1 root root   95 2007-10-05 08:42 proxy_connect.load
-rw-r--r-- 1 root root   87 2007-10-05 08:42 proxy_ftp.load
-rw-r--r-- 1 root root   89 2007-10-05 08:42 proxy_http.load
-rw-r--r-- 1 root root   62 2007-10-05 08:42 proxy.load
-rw-r--r-- 1 root root   66 2007-10-05 08:42 rewrite.load
-rw-r--r-- 1 root root 1122 2007-10-05 08:42 setenvif.conf
-rw-r--r-- 1 root root   68 2007-10-05 08:42 setenvif.load
-rw-r--r-- 1 root root   66 2007-10-05 08:42 speling.load
-rw-r--r-- 1 root root 2158 2007-10-05 08:42 ssl.conf
-rw-r--r-- 1 root root   58 2007-10-05 08:42 ssl.load
-rw-r--r-- 1 root root  398 2007-10-05 08:42 status.conf
-rw-r--r-- 1 root root   64 2007-10-05 08:42 status.load
-rw-r--r-- 1 root root   64 2007-10-05 08:42 suexec.load
-rw-r--r-- 1 root root   70 2007-10-05 08:42 unique_id.load
-rw-r--r-- 1 root root  293 2007-10-05 08:42 userdir.conf
-rw-r--r-- 1 root root   66 2007-10-05 08:42 userdir.load
-rw-r--r-- 1 root root   70 2007-10-05 08:42 usertrack.load
-rw-r--r-- 1 root root   66 2007-10-05 08:42 version.load
-rw-r--r-- 1 root root   74 2007-10-05 08:42 vhost_alias.load
```

---

### Post by TheAddict on 2008-06-05
and the correct a2enmod returns "This module is already enabled"

---

### Post by quelx on 2008-06-05
Is **wordpress** installed from the repos or is it your own?  Are the files in */var/www/html/wordpress* at least readable by the webserver (**sudo chmod 644 -[COLOR="Red"]R[/COLOR] /vaw/www/html/wordpress**  or something) and the wordpress directory itself 755?

---

### Post by Valsodar on 2008-06-05
I would recommend to uninstall LAMP and do a seperate installation for each:
apache2, php, myslq, phpmyadmin

I remember running into problems with LAMP so I switched to seperate installations and no more problems.

---

### Post by TheAddict on 2008-06-05
Wordpress is a local version i downloaded on my m$ machine about 6 months ago, so no not from the repo's, and I don't understand what you mean by readable by the web server. they are all php files and all give me the same error, with slightly different paths (due to different files obviously).

As for uninstalling LAMP. I had thought of that, and I had similar issues with this when I first set it up yesterday, but I played with too many .conf files and ended up starting from scratch again. which was a pain in the *** due to the time I spent configuring SAMBA. I might give that a try if we can't fix it easily

[EDIT] I just did the chmod 644, and now I don't have permission to access the folder via firefox

---

### Post by quelx on 2008-06-05
> **TheAddict said:**
> 
[EDIT] I just did the chmod 644, and now I don't have permission to access the folder via firefox

```
sudo chmod 755 /var/www/html/wordpress
``` no **-R**, to get access back

is **php5-suhosin** installed? If yes, try removing it and reloading apache.

---

### Post by TheAddict on 2008-06-05
Okay, got access back

tried ```
apt-get remove php-suhosin
``` returned that it wasn't installed, so it didn't remove the package

---

### Post by quelx on 2008-06-05
> **TheAddict said:**
> Okay, got access back

tried ```
apt-get remove php-suhosin
``` returned that it wasn't installed, so it didn't remove the package

php[COLOR="Red"]**5**[/COLOR]-suhosin

---

### Post by TheAddict on 2008-06-05
Sorry, my bad.. I did type php5-suhosin, and it wasn't installed...

---

### Post by quelx on 2008-06-05
For giggles can you (temporarily) allow global access to */var/www/html/wordpress*, al la 
```
sudo cp -ra /var/www/html/wordpress /var/www/html/wordpress.bak
sudo chmod 777 -R /var/www/html/wordpress
```
restart apache and try it in FF
then get it back to "normal"
```
sudo rm -rf /var/www/html/wordpress
sudo mv /var/www/html/wordpress.bak /var/www/html/wordpress 
```

---

### Post by TheAddict on 2008-06-05
alright, I tried that, with no result....

I gotta go out for about an hour, but thanks for your help... would youthink that trying Valsodar's idea of removing LAMP, and reinstalling the components serperately would be of any worth?


[EDIT]
This feels like something that would a simpler task with a GUI, but I refuse to install one on a server.../rant

---

### Post by quelx on 2008-06-05
> would youthink that trying Valsodar's idea of removing LAMP, and reinstalling the components serperately would be of any worth? 

Yes, it never hurts to go back to bare metal and start over.  I can't help but think that there is something in your **wordpress** installation that's mis-configured since the move from Windows.  If you really don't want to reinstall the LAMP stack, I would start with downloading the **wordpress** tar matching the version you had on windows, backup */var/www/html/wordpress* and reinstall, just wordpress, there.

EDIT: If you stick with the command line and get comfortable with it you may find it's much *easier* and *convenient* to work with.

---

### Post by TheAddict on 2008-06-05
I'm back (less than an hour - the dole queue was short today). I will try to download wordpress.tar and see how that goes, but to be honest, I'm not holding my breath because wordpress isn't the only CMS I have tried to install on it - i.e., tried expression engine too.

no gui. I already find myself becoming increasingly comfortable using the CLI

---

### Post by quelx on 2008-06-05
It just occurred to me, since all your .php are acting broken maybe reinstalling wordpress won't help.  What else did you move over from Windows?  Anything that could be affecting PHP (.ini, .conf files)?  What did you change in the php config files?

---

### Post by TheAddict on 2008-06-05
the only other thing I moved accross from windows was another CMS - ExpressionEngine... and in the php.ini file, the only thing i changed was the include_path, where i uncommented the line, and tried a few different paths, then when that didn't work, commented it out again

I have tried to download the latest wordpress, but i haven't had to untar anything yet, so I am just checking the tar --help file

[EDIT] - downloading the tar.gz file has worked a treat! thanks for all your help man

---

### Post by TheAddict on 2008-06-05
Okay, so I have worked out what the issue with everything was...

I was unzipping/untaring/extracxting the archives on my windows machine, then transferring the files accross. This is the only explanation I can come up with, becuase once I downloaded WP again, and untarred it through the terminal, she was apples, and then I transfered another CMS accross as a zip archive, and unzipped it using unzip, it was ace.. so thanks go to quelx for his patience and help... I love this community!

---

