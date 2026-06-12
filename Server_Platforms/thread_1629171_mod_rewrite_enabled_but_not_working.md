---
title: "mod_rewrite enabled but not working"
date: 2010-11-23
forum: Server Platforms
---

### Post by ZaHACKieL on 2010-11-23
Hi everyone!

I'm having some trouble with the mod_rewrite in my Ubuntu 9.10 running LAMP.

I followed the instructions from here:

[http://ubuntuforums.org/showthread.php?t=255556](http://ubuntuforums.org/showthread.php?t=255556)

and here: [http://ubuntuforums.org/showthread.php?t=255556](http://ubuntuforums.org/showthread.php?t=255556)

But still not working. When I check my phpinfo file, the mod_rewrite shows as enabled.

If I do sudo a2enmod rewrite it says Module rewrite already enabled

I changed the AllowOverride None to AllowOverride all in the default file. In that file it says: DocumentRoot /var/www  , but actually my default path is /home/yulia/server . I tried changing that too in the default file but still not working.

I have my .htaccess with one simple rule in the same folder as my tests files

Any suggestion would be extremely appreciated. Thanx!

---

### Post by ZaHACKieL on 2010-11-23
BTW, I also tried changing the line: 

Order allow,deny to 
Order allow,all  

but no luck at all.

The rule I'm using in the .htaccess is:

RewriteEngine on
RewriteRule ^alice.html$ bob.html

it's located directly in my localhost root folder and yes, I restarted the apache server after every new modification of default file.

=]

---

### Post by wongo888 on 2010-11-23
Is there anything in your Apache error log?

Is this a virtual host?

Can you paste your complete .htaccess file?

---

### Post by ZaHACKieL on 2010-11-23
Hi wongo888, thanx for answering. Well there's nothing unusual in the apache logs, at least nothing related to the mod_rewrite.

Correct me if I'm wrong but yes this is a virtual host, I'm running the Apache in my laptop to work on some websites locally. When I installed the LAMP I changed the localhost default folder from /var/www to /home/yulia/server.

My .htaccess file is just this:

RewriteEngine on
RewriteRule ^alice.html$ bob.html

Thanx again for answering, this situation is really frustrating because I'm running out of ideas.

---

### Post by wongo888 on 2010-11-23
I wouldn't get too creative with the location of the webroot unless you are willing to work through permission errors (Apache usually runs as "www-data" not you). Further, you can easily set symlinks from your home dir to your real webroot if you want an easy way to get to your web files.

```

$ ln -s /var/www/vhosts/example.com/ /home/yulia/example.com

```

In the folder /etc/apache2/sites-available you should check your config file for your domain (using example.com):

```
<VirtualHost *:80>
        ServerAdmin webmaster@example.com
        ServerName www.example.com
        ServerAlias example.com
        DocumentRoot /var/www/vhosts/example.com
        <Directory /var/www/vhosts/example.com>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
</VirtualHost>

```

In your htaccess file, you can check if the Rewrite directive is being parsed by changing it to an invalid entry:

```

ReDELETEMEwriteEngine on

```

If the htaccess file is being parsed then viewing the directory should raise a HTTP 500 Internal Server Error.

Ensure your htaccess file is readable by www-data:

```
 $ ls -la .htaccess
-rw-r--r-- 1 yulia yulia   11 2010-11-24 01:06 .htaccess

```

---

### Post by ZaHACKieL on 2010-11-24
Hi wongo. I didn't know about those symlinks, I will definitely try that but in case I want to keep my actual default directory, do you have any other ideas to try? I really appreciate your help.

Thanx!

---

### Post by wongo888 on 2010-11-24
Did you check if the Rewrite directive is being parsed?

---

### Post by James78 on 2010-11-25
> **ZaHACKieL said:**
> Hi wongo888, thanx for answering. Well there's nothing unusual in the apache logs, at least nothing related to the mod_rewrite.

Correct me if I'm wrong but yes this is a virtual host, I'm running the Apache in my laptop to work on some websites locally. When I installed the LAMP I changed the localhost default folder from /var/www to /home/yulia/server.

My .htaccess file is just this:

RewriteEngine on
RewriteRule ^alice.html$ bob.html

Thanx again for answering, this situation is really frustrating because I'm running out of ideas.
. is a special character in regex. You need to escape it.
```
RewriteEngine on
RewriteRule ^alice\.html$ bob.html
```

[http://httpd.apache.org/docs/2.2/misc/rewriteguide.html](http://httpd.apache.org/docs/2.2/misc/rewriteguide.html)

---

### Post by SeijiSensei on 2010-11-25
You'll probably want to add a [RewriteLog]("http://httpd.apache.org/docs/current/mod/mod_rewrite.html#rewritelog") directive if you continue to have problems.

---

### Post by ZaHACKieL on 2010-11-25
Thanx guys for your help. I'll try all your suggestions and tell my results =]

---

