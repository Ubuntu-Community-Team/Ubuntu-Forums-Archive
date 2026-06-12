---
title: "mod_rewrite in apache2.conf not working"
date: 2010-09-03
forum: Server Platforms
---

### Post by davemc01 on 2010-09-03
Hello - I'm wondering if someone can help me troubleshoot.

I'm on ubuntu 10 LTS, w/ apache 2.

I've got a domain: **domain.com**

I've got a subdomain via CNAME pointing to domain.com: **[www.domain.com]("http://www.domain.com")**

I want apache to take all requests to [www.domain.com]("http://www.domain.com") and send them to domain.com.

I've read that the following mod_rewrite statements *should* accomplish this:

RewriteEngine On
RewriteCond %{HTTP_HOST} ^www\.domain\.com$ [NC]
RewriteRule ^(.*)$ http://domain.com/$1 [R=301,L]

So I put the above 3 lines at the bottom of /etc/apache2/apache2.conf. However, visiting [www.domain.com]("http://www.domain.com") does not result in a redirect to domain.com.

Is there something I'm missing - shouldn't this work?

Am I missing a forward slash in one of the regex's?

I've also got the following in the same apache2.conf file:
WSGIScriptAlias / /home/user/django/app/django.wsgi

Could the wsgi alias be screwing things up? Would the order in which the rewrite rule and the wsgi statement appear matter?

Any insight is appreciated!

---

### Post by Bachstelze on 2010-09-03
The first thing to do when you have trouble with mod_rewrite is enable logging (RewriteLogLevel 9). That will tell you exactly what happens.

---

### Post by Ryan Dwyer on 2010-09-03
Did you reload or restart Apache after changing the config? "sudo /etc/init.d/apache reload" should do it.

---

### Post by davemc01 on 2010-09-03
Thanks for the replies - yes I restart apache after any config file change.

And I'm not getting anything in the log file I created. In apache2.conf I wrote:

RewriteLog /home/user/log/mod_rewrite.log
RewriteLogLevel 9

File remains blank after any requests to [www.domain.com](www.domain.com)

I'm 100% stumped.

---

### Post by davemc01 on 2010-09-03
After trying a bunch of things, I finally was able to at least get proof that mod_rewrite is working.

I edited my <VirtualHost *:80> entry in my "sites-available/default" file.

Note however that I'm not running any virtual hosts on my server. It's just 1 domain going to 1 IP address.

So I put in the following:

WSGIScriptAlias / /home/user/django/app/django.wsgi
<Directory /home/user/django/app/>
    AllowOverride all
    Order allow, deny
    allow from all
</Directory>

And in the .htaccess file in /home/user/django/app I put:

RewriteEngine On
RewriteCond %{HTTP_HOST} ^www\.domain\.com$ [NC]
RewriteRule ^(.*)$ http://domain.com/$1 [R=301,L]

The redirect now works, but apache is sending the request to domain.com/django.wsgi

1. How can I tell apache to execute django.wsgi rather than treat is as a URI
2. How can do this in apache2.conf instead of an .htaccess files?

Thanks!

---

### Post by de0xyrib0se on 2010-09-03
I dont believe mod_rewrite is installed by default, was it installed before doing this setup?

---

### Post by davemc01 on 2010-09-03
Hi de0xyrib0se, yes I installed and enabled it before I tried any of this stuff. It's for sure working right now, just not quite as I'd like. And I'm not very good with apache or mod_rewrite, so I'm probably just doing something wrong.

---

### Post by de0xyrib0se on 2010-09-03
I'd suggest checking with the guys at freenode, channel httpd. There are some rewrite gurus in there.

---

### Post by davemc01 on 2010-09-04
I've solved the problem. 

Earlier in the apache2.conf file is the line:

Include /etc/apache2/sites-enabled/

..which imports a bunch of config info for virtual hosts - namely, by default, a file called default (which i believe is an alias or symlink to 000-default, which might be more familiar to some people). Seems like apache2 automatically assumes people want to use virtual hosts and just goes ahead and includes that file.

Since I'm not using virtual hosts, I just commented out this line, and the code in my original post now works.

Hope that helps someone -- took me 8hrs to figure out :|

---

