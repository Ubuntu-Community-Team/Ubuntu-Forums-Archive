---
title: "phpmyadmin to https only"
date: 2009-03-18
forum: Server Platforms
---

### Post by daboroe on 2009-03-18
I have just installed phpmyadmin but i want it to be accessible via https only. How can I set this up?

Thanks for the help in advance

M. Brown

---

### Post by deeq on 2009-03-18
You can use .htaccess

```

RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}

```

---

### Post by daboroe on 2009-03-18
that would be put in where though? where would that .htaccess file be? i see HTTPS off which would mean only http would be able to get phpmyadmin that is reverse of what i want to do.

---

### Post by deeq on 2009-03-18
File:
/usr/share/phpmyadmin/.htaccess

---

### Post by jazzcatgab on 2009-04-05
deeq, I'm trying to do this also. I've done as you have suggested in the .htaccess file (which I found in the library directory in that same path btw).

I've copied your lines literally. It isn't working for me. Still access via http, not https.

Any ideas what I should do now?

Thanks,

---

### Post by jesuschris on 2009-04-19
hi! just had to do this myself. in addition to dumping the above .htaccess in your phpmyadmin root directory you'll also have to tell apache to use the .htaccess

on my 8.04/8.10 machines with aptitude installed junks i edited the /etc/phpmyadmin/apache.conf file to allow .htaccess overrides.

---

### Post by daboroe on 2009-04-19
> **jesuschris said:**
> hi! just had to do this myself. in addition to dumping the above .htaccess in your phpmyadmin root directory you'll also have to tell apache to use the .htaccess

on my 8.04/8.10 machines with aptitude installed junks i edited the /etc/phpmyadmin/apache.conf file to allow .htaccess overrides.

Jesuschris: Thank you! I will try that here shortly when I get ubuntu back on my one computer when jaunty is finally released.

---

### Post by jazzcatgab on 2009-04-20
Thanks for the reply, jeasuschris. I'm a bit of a noob, so I have two questions for you:
1) when you say to move the .htaccess file to the root of phpmyadmin, do you mean at the /etc/ path, or the /usr/ path?
2) What do I add to the apache.conf file to allow .htaccess overrides?

I appreciate your patience,

---

### Post by jesuschris on 2009-05-02
Sorry for the slow reply! I have been enjoying patios!

So. Basically you have to throw the .htaccess in the folder that serves up your phpmyadmin... could be in a bunch of places depending on how/where it was installed.

on a default hardy/intrepid install i had apache serving phpmyadmin from /usr/share/phpmyadmin so that's where my .htaccess is.

and for apache to use the .htaccess i edited the /etc/phpmyadmin/apache.conf and turned on the AllowOveride.

my /etc/phpmyadmin/apache.conf has this at the top of it to allow usage of an .htaccess file:
> 
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
        Options Indexes FollowSymLinks
        AllowOverride All
        DirectoryIndex index.php



Good luck! Hope that helped!

---

### Post by daboroe on 2009-05-02
almost completely forgot about this topic i posted about. i will definately try this. i ahve finals coming up and luckily i do not have only 1. lol.

---

### Post by jazzcatgab on 2009-05-03
Thanks jesuschris, that did, indeed, help. Now I think I have all that sorted out, but right now I'm researching an error in Firefox I get when I try to use the https for this: Error code: ssl_error_rx_record_too_long
BTW, I think all should be well, because I use https to access Webmin. Did you have to deal with this issue?

---

### Post by bakegoodz on 2010-03-11
I tried it but I get the error:
Secure Connection Failed

SSL received a record that exceeded the maximum permissible length.

(Error code: ssl_error_rx_record_too_long)

Anybody now how I can fix that?

---

### Post by bakegoodz on 2010-03-11
I found this and it worked, kinda
 sudo a2ensite default-ssl
sudo /etc/init.d/apache2 reload

But it enabled the default Virtual Domain, how do I set phpmyadmin to work though my virtual domain?
Or does https have to be enabled for the entire Virtual Domain?

---

### Post by adieb on 2010-03-26
> **deeq said:**
> You can use .htaccess

```

RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}

```

Very cool and easy solution! Thanks a lot!!

Just need to make .htaccess files work:
[https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

After that don´t forget to enable rewrite:
```
a2enmod rewrite && /etc/init.d/apache2 restart
```

---

### Post by wikiterra on 2010-06-17
I have rewrite set up but I get a warning when I restart apache:

```
:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2
[Thu Jun 17 23:27:04 2010] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 10 will probably never match because it overlaps an earlier Alias.
 ... waiting [Thu Jun 17 23:27:05 2010] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 10 will probably never match because it overlaps an earlier Alias.

```It successfully restarts apache and the rewrite works, so when I go to [http://myserver.net/phpmyadmin](http://myserver.net/phpmyadmin) it immediately gets redirected to [https://.](https://.)..

But I still have that warning niggling me every time I restart.

This is my apache.conf in /etc/phpmyadmin :

```
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
        Options Indexes FollowSymLinks
        DirectoryIndex index.php

        <IfModule mod_php5.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_value include_path .
        </IfModule>

        # Rewrite url for phpmyadmin
        RewriteEngine on
        RewriteCond %{HTTPS} off
        RewriteRule ^(.*)$ https://%{HTTP_HOST}/phpmyadmin/ [R]

</Directory>
```(That's only the relevant part, which includes the rewrite lines I added at the end).

Does anyone have any advice?

---

### Post by jp19online on 2010-10-15
Try grepping in /etc/apache2 folder.

grep -i "alias.*phpmyadmin" /etc/apache2

you might have entries in multiple files.

---

### Post by fvm2000 on 2011-05-30
Reviving an old thread here. I'm having some problems getting phpMyAdmin served up via https.

Before starting, webmin was working fine under https, and I could only log onto phpMyAdmin via http.

I then tried the following:

[LIST]
[*]entered the rewrite directives in .htaccess (and set allowoverride all in apache.conf
[*]ran a2ensite default-ssl and restarted apache
[/LIST]
After this, webmin was still working, and phpMyAdmin was still being served up as http. If I entered the address with https, I got the same error reported by some above ("SSL received a record that exceeded the maximum permissible length.").

I then did the following:


[LIST]
[*]moved the rewrite directives from .htaccess to apache.conf (and saved to /etc/phpmyadmin)
[*]restarted apache
[/LIST]
Now, webmin is no longer working (connection timeout), I get a 500 error if I try to go to phpMyAdmin via http, and I still get the same "SSL received a record that exceeded the maximum permissible length." error if I try https.

BTW, I'm running Ubuntu 11.04

I'm not a linux noob, but I've been away from the hands-on stuff for a couple of years, so I'm a little rusty...

Would appreciate any help.

Thanks!

---

### Post by Nap_BlownApart on 2012-07-11
Spent hours trying to find the solution to this, but got it working here now.

edit your phpmyadmin.conf file as follows:
```
# phpMyAdmin default Apache configuration

<IfModule mod_rewrite.c>
<IfModule mod_ssl.c>
<Location /phpmyadmin>
RewriteEngine on
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI}
</Location>
</IfModule>
</IfModule>

Alias /phpmyadmin /usr/share/phpmyadmin
..... everything below remains as per the default file

```

Note there is no '/' between %{HTTP_HOST}%{REQUEST_URI}

Next step is to turn on Apache2 HTTPS and restart it.
```
a2ensite default-ssl
/etc/init.d/apache2 restart
```
You might need to enable mod_rewrite using:
```
sudo a2enmod rewrite
```

This gets its working, albeit with the 'snake-oil' certificates which will cause your browser to display a TRUST warning.  Get a 'real' certificate to solve that one.

Cheers,
Nap

---

