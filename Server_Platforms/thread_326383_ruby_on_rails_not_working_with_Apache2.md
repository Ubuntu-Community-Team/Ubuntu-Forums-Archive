---
title: "ruby on rails not working with Apache2"
date: 2006-12-27
forum: Server Platforms
---

### Post by paket on 2006-12-27
Hello everyone.

I'm in the process of learning Ruby on Rails, so I have installed it onto my test server using the instructions I found at [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails). My test app works fine if I access it using the WEBbrick server ([http://devtest:3000/appname)](http://devtest:3000/appname)), but not if I try going through Apache. According to /server-info, the ruby, rewrite and fcgid modules are loaded. Here's what the rewrite section is telling me:

```
    <Directory </var/www/alarms/public>>
        RewriteEngine On
    <Directory </var/www/alarms/public>>
        RewriteBase /alarms
        RewriteRule ^$ index.html [QSA]
        RewriteRule ^([^.]+)$ $1.html [QSA]
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteRule ^(.*)$ dispatch.fcgi [QSA,L]
    </Directory>
```

and here's the relevant section from 'default' in the sites-available directory:

```
    Alias /alarms "/var/www/alarms/public"
    <Directory </var/www/alarms/public>>
        Options +FollowSymlinks +ExecCGI
        Order allow,deny
        Allow from all
        AddHandler fcgid-script .fcgi
        RewriteEngine On
        RewriteBase /alarms
        RewriteRule ^$ index.html [QSA]
        RewriteRule ^([^.]+)$ $1.html [QSA]
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteRule ^(.*)$ dispatch.fcgi [QSA,L]
        ErrorDocument 500 /500.html
    </Directory>
```

Could anyone out there shed some light on why my application isn't working through Apache? How is Apache supposed to know to execute the controllers in app/controllers anyway?

thanks

---

### Post by Brazen on 2006-12-28
I've not been able to get the RewriteBase rule to work unless it is in the .htaccess file.  However you MIGHT just need to add an "AllowOverride None" under your Directory section.

Personally, I suggest creating a site like this:```
Alias /alarms /var/www/alarms/public

<Directory /var/www/alarms/public>
   SetEnv RAILS_ENV development

   Options ExecCGI FollowSymLinks
   AddHandler fcgid-script .fcgi
   AllowOverride all
   Order allow,deny
   Allow from all
</Directory>
```
And then changing the "RewriteRule ^(.*)$ dispatch.fcgi [QSA,L]" and "AddHandler fcgid-script .fcgi" lines and add the "RewriteBase /alarms" line in the .htaccess file.

---

### Post by calvinpriest on 2007-02-14
I'm having this exact same problem.  Were you able to resolve this?

Thanks!

---

### Post by Pionner on 2007-02-15
This configuration works for me on a default Dapper installation, with my RoR application on /var/apps/application/ 
```

Alias /application "/var/apps/application/public/"

<Directory "/var/apps/application/public">
                Options All ExecCGI
                AllowOverride All
                Order allow,deny
                Allow from all
                AddHandler fcgid-script .fcgi
                RewriteBase /application
 </Directory>

<Location /application>
                RewriteEngine On
                RewriteCond %{REQUEST_FILENAME} !-f
                RewriteRule ^(.*)$ dispatch.fcgi [QSA,L]
</Location>

```

In order to get apache to work you need to rename .htaccess file to htaccess on the /public directory of your application.  Check the permissions so apache can read the application files too.

---

### Post by asmweb on 2007-06-29
I ran into the exact problem and could not manage to make it work... did you guys succeed? thanks

---

### Post by hairyhi on 2007-07-01
i have followed the same steps and have configured ruby on rails on apache2
Now when I click the link on home page of "About your application’s environment", i get an Internal server error". The entries in the error log are as follows:
```
[Mon Jul 02 01:04:52 2007] [warn] (104)Connection reset by peer: mod_fcgid: read data from fastcgi server error.
[Mon Jul 02 01:04:52 2007] [error] [client 127.0.0.1] Premature end of script headers: dispatch.fcgi, referer: http://first/
```

---

### Post by Pionner on 2007-07-02
Maybe you should try with [mongrel,]("http://mongrel.rubyforge.org/docs/apache.html") it's easier to configure and seems to be the preferred way to set up small rails applications.

[http://mongrel.rubyforge.org/docs/apache.html](http://mongrel.rubyforge.org/docs/apache.html)

---

### Post by hairyhi on 2007-07-02
> **Pionner said:**
> Maybe you should try with [mongrel,]("http://mongrel.rubyforge.org/docs/apache.html") it's easier to configure and seems to be the preferred way to set up small rails applications.

[http://mongrel.rubyforge.org/docs/apache.html](http://mongrel.rubyforge.org/docs/apache.html)

Well I cannot use mongrel because i want to develop an application that wud also use php and thus use of apache is  a must..

---

### Post by Pionner on 2007-07-03
> **hairyhi said:**
> Well I cannot use mongrel because i want to develop an application that wud also use php and thus use of apache is  a must..

Follow the link on my previous post, It explains how to configure Mongrel behind an Apache server (that can be serving php pages if you want).

My actual setup is: mongrel for dynamic rails content, and Apache serving static rails content and php pages.

I hope this helps.

---

### Post by jumpslu7 on 2008-02-14
hi there, I had this exact same problem; I initially had apache mod_ruby and fastcgi running

but it was a slow as a dog!

so I installed mod_cgid, but couldn't get it going.  Here's how I fixed it.

Try executing dispatch.fcgi 

if you get a lot of error messages, starting with something similar to this:
gem_original_require no such file to load -- fcgi (MissingSourceFile)

its because your messing some ruby gem.

Here's the cure:

sudo gem install fcgi

I didn't even have to do a force-reload on apache2 after that, it just worked.  And ******* its fast!

[http://belfastgeek.net](http://belfastgeek.net)

---

