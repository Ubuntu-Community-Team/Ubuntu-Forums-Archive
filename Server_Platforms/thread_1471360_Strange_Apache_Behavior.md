---
title: "Strange Apache Behavior"
date: 2010-05-03
forum: Server Platforms
---

### Post by shoaibi on 2010-05-03
I did a fresh install of ubuntu 10.04 Lucid Lynx and then setup a lamp server like:

```

tasksel install lamp-server

```

Created:
# /var/www/info.php
```

<?php
phpinfo();
?>

```

and verified by going to [http://localhost/info.php](http://localhost/info.php) that php works.

Enabled rewrite mod, downloaded latest drupal e.g. 6.16, extracted and moved it to /var/www, created vhost using following configurations:

# /etc/hosts --- CLIPPED
```

127.0.0.1 localhost drupal.loc www.drupal.loc

```

# /etc/apache2/ports.conf --- CLIPPED
```

NameVirtualHost localhost:80

```

# /etc/apache2/conf.d/servername.conf
```

ServerName localhost

```


# drupal vhost config
```

<VirtualHost localhost:80>
        ServerName drupal.loc
        ServerAlias www.drupal.loc
        ServerAdmin webmaster@drupal.loc
        DocumentRoot /var/www/drupal/

        <Directory />
                Options -Indexes FollowSymLinks
                AllowOverride All

                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/drupal-error_log
        CustomLog /var/log/apache2/drupal-access_log common


</VirtualHost>

```



Now when i visit [http://drupal.loc/](http://drupal.loc/) :
- I am offered to download a file called "download" which contains text from index.php from drupal

If i visit [http://drupal.loc/user](http://drupal.loc/user)
- I am offered to download a file called "user" which contains text from index.php from drupal.

I have tried everything but can't figure out what possibly is wrong here. Any ideas?

---

### Post by cdenley on 2010-05-03
Did you install drupal from the repos?
```

sudo apt-get install drupal6

```

---

### Post by tgalati4 on 2010-05-03
You have verified that everything in /var/www/drupal is www-data:www-data ownership?

---

### Post by shoaibi on 2010-05-03
@cdenley:
thats not a solution, thats a workaround.

@tgalati4:
even tried with that, though thats a security risk, you know... But doesn't work..

---

### Post by cdenley on 2010-05-03
> **shoaibi said:**
> @cdenley:
thats not a solution, thats a workaround.


It is neither. It is a suggestion for avoiding problems such as this in the future. Why would you bother with third party software when it is already packaged specifically for ubuntu, tested, and supported? Also, you never specified where you installed from, so I though it would help if that were clarified in case someone else wanted to help you get your unsupported non-ubuntu software working.

---

### Post by shoaibi on 2010-05-03
@cdenley:
I am sorry if i offended you...
I though when i said downloaded, everyone would consider me smart enough to download it from drupal.org, because if i did an apt-get i would have included the command like all other things in my first post.
Then why bother, because its latest, plus you can easily managed multiple installations. What if you are to clone a site from a webserver with latest drupal running to your ubuntu-box to debug some issues? the version is repository is generally a bit outdated and in my case has always caused more problems.
And as a last note, in my personal opinion installing webapps/cms or such from repos is never a good idea if you want to get to bleeding edge technology, PPAs are an option in some cases though.

---

### Post by cdenley on 2010-05-03
> **shoaibi said:**
> @cdenley:
I am sorry if i offended you...
I though when i said downloaded, everyone would consider me smart enough to download it from drupal.org, because if i did an apt-get i would have included the command like all other things in my first post.
Then why bother, because its latest, plus you can easily managed multiple installations. What if you are to clone a site from a webserver with latest drupal running to your ubuntu-box to debug some issues? the version is repository is generally a bit outdated and in my case has always caused more problems.
And as a last note, in my personal opinion installing webapps/cms or such from repos is never a good idea if you want to get to bleeding edge technology, PPAs are an option in some cases though.

I understand sometimes people insist on having "bleeding edge technology". I strongly disagree with this, since stable, supported, and tested software is more reliable, which is most important when it comes to servers. In rare situations, the stable version may be missing newer features which may be needed, but in this case, 6.16 is in the repos! By downloading from drupal.org, you gain nothing, but lose ubuntu's security updates, packaging, testing, and support. So how is that the smart option?

If that is what you prefer, though, then good luck.

---

### Post by shoaibi on 2010-05-03
@cdenley:
hmmmm, well it all comes down to choice...
Can i create multiple drupal setups using the drupal in repos?

Thanks for taking out time to read and reply...

---

### Post by cdenley on 2010-05-03
> **shoaibi said:**
> @cdenley:
hmmmm, well it all comes down to choice...
Can i create multiple drupal setups using the drupal in repos?

Thanks for taking out time to read and reply...

I never used drupal, so I couldn't say for sure.

---

### Post by wojox on 2010-05-03
Try:

```
sudo apt-get install libapache2-mod-php5
```

```
sudo a2enmod php5
```

```
sudo /etc/init.d/apache2 restart
```

---

### Post by tgalati4 on 2010-05-03
What happens when you:

[http://drupal.loc/drupal](http://drupal.loc/drupal)

Using /var/www/drupal will be awkward in the future.  Perhaps:

/var/www/shoaibi

[http://drupal.loc/shoaibi](http://drupal.loc/shoaibi)

---

### Post by hotbelgo on 2010-05-04
I am having a similar issue after upgrading a working Jaunty install.  In my case the /var/www/testphp.php works fine but [http://www.xxx/~name/site](http://www.xxx/~name/site) is leading to the downloading of the php file instead of it's processing.

Consequently I know that the right module is installed properly but doubt know how to troubleshoot this different problem.

---

### Post by shoaibi on 2010-05-04
wojox:
plain php file works just fine...

tgalati:
actually it was previously ~shoaibi/public_html/ but after a lot of hit and trail i moved it to /var/www for testing and to not complicate stuff by adding userdir and enabling .htaccess in userdir.conf and all that...

---

### Post by shoaibi on 2010-05-04
@tgalati4:
strange if i do:
[http://drupal.loc/drupal](http://drupal.loc/drupal)

it goes to the install page.
# default .htaccess of drupal
```

#
# Apache/PHP/Drupal settings:
#

# Protect files and directories from prying eyes.
<FilesMatch "\.(engine|inc|info|install|make|module|profile|test|po|sh|.*sql|theme|tpl(\.php)?|xtmpl|svn-base)$|^(code-style\.pl|Entries.*|Repository|Root|Tag|Template|all-wcprops|entries|format)$">
  Order allow,deny
</FilesMatch>

# Don't show directory listings for URLs which map to a directory.
Options -Indexes

# Follow symbolic links in this directory.
Options +FollowSymLinks

# Make Drupal handle any 404 errors.
ErrorDocument 404 /index.php

# Force simple error message for requests for non-existent favicon.ico.
<Files favicon.ico>
  # There is no end quote below, for compatibility with Apache 1.3.
  ErrorDocument 404 "The requested file favicon.ico was not found.
</Files>

# Set the default handler.
DirectoryIndex index.php

# Override PHP settings. More in sites/default/settings.php
# but the following cannot be changed at runtime.

# PHP 4, Apache 1.
<IfModule mod_php4.c>
  php_value magic_quotes_gpc                0
  php_value register_globals                0
  php_value session.auto_start              0
  php_value mbstring.http_input             pass
  php_value mbstring.http_output            pass
  php_value mbstring.encoding_translation   0
</IfModule>

# PHP 4, Apache 2.
<IfModule sapi_apache2.c>
  php_value magic_quotes_gpc                0
  php_value register_globals                0
  php_value session.auto_start              0
  php_value mbstring.http_input             pass
  php_value mbstring.http_output            pass
  php_value mbstring.encoding_translation   0
</IfModule>

# PHP 5, Apache 1 and 2.
<IfModule mod_php5.c>
  php_value magic_quotes_gpc                0
  php_value register_globals                0
  php_value session.auto_start              0
  php_value mbstring.http_input             pass
  php_value mbstring.http_output            pass
  php_value mbstring.encoding_translation   0
</IfModule>

# Requires mod_expires to be enabled.
<IfModule mod_expires.c>
  # Enable expirations.
  ExpiresActive On

  # Cache all files for 2 weeks after access (A).
  ExpiresDefault A1209600

  <FilesMatch \.php$>
    # Do not allow PHP scripts to be cached unless they explicitly send cache
    # headers themselves. Otherwise all scripts would have to overwrite the
    # headers set by mod_expires if they want another caching behavior. This may
    # fail if an error occurs early in the bootstrap process, and it may cause
    # problems if a non-Drupal PHP file is installed in a subdirectory.
    ExpiresActive Off
  </FilesMatch>
</IfModule>

# Various rewrite rules.
<IfModule mod_rewrite.c>
  RewriteEngine on

  # If your site can be accessed both with and without the 'www.' prefix, you
  # can use one of the following settings to redirect users to your preferred
  # URL, either WITH or WITHOUT the 'www.' prefix. Choose ONLY one option:
  #
  # To redirect all users to access the site WITH the 'www.' prefix,
  # (http://example.com/... will be redirected to http://www.example.com/...)
  # adapt and uncomment the following:
  # RewriteCond %{HTTP_HOST} ^example\.com$ [NC]
  # RewriteRule ^(.*)$ http://www.example.com/$1 [L,R=301]
  #
  # To redirect all users to access the site WITHOUT the 'www.' prefix,
  # (http://www.example.com/... will be redirected to http://example.com/...)
  # uncomment and adapt the following:
  # RewriteCond %{HTTP_HOST} ^www\.example\.com$ [NC]
  # RewriteRule ^(.*)$ http://example.com/$1 [L,R=301]

  # Modify the RewriteBase if you are using Drupal in a subdirectory or in a
  # VirtualDocumentRoot and the rewrite rules are not working properly.
  # For example if your site is at http://example.com/drupal uncomment and
  # modify the following line:
  # RewriteBase /drupal
  #
  # If your site is running in a VirtualDocumentRoot at http://example.com/,
  # uncomment the following line:
  # RewriteBase /

  # Rewrite URLs of the form 'x' to the form 'index.php?q=x'.
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_URI} !=/favicon.ico
  RewriteRule ^(.*)$ index.php?q=$1 [L,QSA]
</IfModule>


```

If i change rewritebase to "/", it does download the file.

---

### Post by shoaibi on 2010-05-04
I did a fresh install of drupal, after setup gets complete and i try to access the real site e.g. [http://drupal.loc](http://drupal.loc) i again face the same problem.
I have tried with "Clean URLs" enabled as well as disabled.

---

### Post by tgalati4 on 2010-05-04
You need an index.html in the www home directory that redirects to http:://drupal.loc/mysite (and have a valid /var/www/mysite drupal installation).

Using "drupal" as your mysite can create strange behavior as I suspected.

You can use multiple sites:  /var/www/mysite1, mysite2, mysite3, etc:  You can use index.html to point to different ones.  It's complicated yet flexible.  Once you get it set up properly, drupal sort of runs itself.

It runs out-of-the-box on Hardy server, so that is what I am familiar with.  You might want to set up a box with Hardy server and drupal and print out the apache2.conf files and compare to Lucid for troubleshooting.

All it takes is one tweak of apache or php configuration between distros and your service falls over.

Note to folks learning apache and drupal:  stick to hardy.

Otherwise you will be chasing new distro bugs, new apache bugs (html5 issues?), and new drupal bugs.  Hard to learn when you can't get things to even run in the first place.

If you like pain, there's always a new distro for you.

---

### Post by hotbelgo on 2010-05-08
Turned out the answer was tucked away in the php5.conf file


    # To re-enable php in user directories comment the following lines
    # (from <IfModule ...> to </IfModule>.) Do NOT set it to On as it
    # prevents .htaccess files from disabling it.
    # <IfModule mod_userdir.c>
    #     <Directory /home/*/public_html>
    #         php_admin_value engine Off
    #     </Directory>
    # </IfModule>

---

