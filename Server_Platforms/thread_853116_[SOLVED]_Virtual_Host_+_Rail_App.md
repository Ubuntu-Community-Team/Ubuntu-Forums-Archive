---
title: "[SOLVED] Virtual Host + Rail App"
date: 2008-07-08
forum: Server Platforms
---

### Post by Titan8990 on 2008-07-08
Is it possible to have virtual hosts with one of those hosts running a Ruby on Rails application? 

I configured my RoR app from this guide: [http://ubuntuforums.org/showthread.php?t=674598&highlight=redmine](http://ubuntuforums.org/showthread.php?t=674598&highlight=redmine).

It requires a change to .htaccess that looks like this:

```
# General Apache options
AddHandler fastcgi-script .fcgi
AddHandler fcgid-script .fcgi
AddHandler cgi-script .cgi
Options +FollowSymLinks +ExecCGI

RewriteEngine On
RewriteRule ^$ index.html [QSA]
RewriteRule ^([^.]+)$ $1.html [QSA]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.*)$ dispatch.fcgi [QSA,L] 

ErrorDocument 500 "<h2>Application error</h2>Rails application failed to start properly"
```

So now I have two virtual servers. One should host webmail and the other should host Redmine but they both hit the Redmine site. Here is what my httpd config files look like:

For Redmine:

```
<VirtualHost *>

ServerAdmin root@foo.bar
ServerName foo.bar.com 
ServerAlias foo.bar.com

RewriteEngine On 
# Redirect all non-static requests to cluster 
RewriteCond %{DOCUMENT_ROOT}/%{REQUEST_FILENAME} !-f 
RewriteRule ^/(.*)$ balancer://redminecluster%{REQUEST_URI} [P,QSA,L] 

</VirtualHost>

<Proxy balancer://redminecluster>

BalancerMember http://127.0.0.1:8000 
BalancerMember http://127.0.0.1:8001 
BalancerMember http://127.0.0.1:8002 

</Proxy>

```

And for our webmail:

```
<VirtualHost *>

ServerAdmin root@binaryse.com
ServerAlias example.com
DocumentRoot /var/www/mail

</VirtualHost>
```

If I got to example.com it actually displays the application at foo.bar. I have a feeling this is an issue with .htaccess.

Has anyone got something like this to work before? Do I need to host the webmail on a different port? Also, I would be happy if someone explained to me a little better on how this works.

Thanks in advance.

---

### Post by Titan8990 on 2008-07-10
bump and update

I tried including the proxy balancer in the virtual host "<>" with now luck:

```
<VirtualHost *>

ServerAdmin root@foo.bar
ServerName foo.bar.com 
ServerAlias foo.bar.com

RewriteEngine On 
# Redirect all non-static requests to cluster 
RewriteCond %{DOCUMENT_ROOT}/%{REQUEST_FILENAME} !-f 
RewriteRule ^/(.*)$ balancer://redminecluster%{REQUEST_URI} [P,QSA,L] 

<Proxy balancer://redminecluster>

BalancerMember http://127.0.0.1:8000 
BalancerMember http://127.0.0.1:8001 
BalancerMember http://127.0.0.1:8002 

</Proxy>


</VirtualHost>
```

---

### Post by Titan8990 on 2008-07-11
Bump and another update.

I tried setting example.com to a different port than 80 and then tried visiting it like example.com:8080 with no luck. Stumped here, beginning to think I will not be able to run both of these web servers at the same time...

---

### Post by puelly on 2008-07-11
You should have another VirtualHost entry for your webmail subdomain.  What I did was copy the default setup and created two separate ones for the two subdomains that I have then I disabled the default site using

```
sudo a2dissite default
```

and enabled the other subdomains using.

```
sudo a2ensite webmail
sudo a2ensite foo
```

---

### Post by Titan8990 on 2008-07-14
Problem solved. I had to add NameVirtualHost to the top of my rail application virtual host file. Apache gives me an error but it works and that is all that matters. Thank you for your assistance.

---

