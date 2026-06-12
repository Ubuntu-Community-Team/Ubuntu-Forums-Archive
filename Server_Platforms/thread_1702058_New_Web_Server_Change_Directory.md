---
title: "New Web Server Change Directory"
date: 2011-03-07
forum: Server Platforms
---

### Post by cosine_omerta on 2011-03-07
I have read a hundred tutorials but I must be missing something. I have setup an Ubuntu Server with lamp and I have a web server working with Apache2. I can connect to the server and get the "It works" page.

I want to make it so that I can add web pages to my home directory, and not have to use var/www.  The path is /home/myname/www/nameofwebsite/websitepage.html. I want to have multiple directories for different web sites on my server.  I cannot get the new directory to work.

I have copied the default file from sites-available in the apache2 folder, renamed it to mysite, and then modified the DocumentRoot area:

DocumentRoot /home/myname/www/nameofwebsite

and the directory area

<Directory /home/myname/www/nameofwebsite/>

[FONT=Verdana]I have used [/FONT][FONT=monospace][FONT=Verdana]/usr/sbin/a2ensite mysite, then I used /etc/init.d/apache2 reload with no errors.

When I try to access [www.myhost.com/nameofwebsite/websitepage.html](www.myhost.com/nameofwebsite/websitepage.html) I get the 404 error.

What have I done wrong?[/FONT]
[/FONT]

---

### Post by bsntech on 2011-03-07
I'd recommend doing something like this in your /etc/apache2/httpd.conf file.  I have VirtualHosts setup on my systems:

<VirtualHost *:80>
ServerName <DOMAIN_HERE>
ServerAlias <ALIAS_HERE>
DocumentRoot /home/myname/www/nameofwebsite
</VirtualHost>

Change DOMAIN_HERE to your domain name.  So if your domain is just domain.com, put in "domain.com" (without quotes) there.

For the ServerAlias - this is the alias that indicates this VirtualHost will be used for configuration.  So if you want the configuration above for [www.domain.com](www.domain.com) - ensure you put "www.domain.com" (without quotes) on that line.  You can separate additional names with spaces - such as:

ServerAlias [www.domain.com](www.domain.com) *.domain.com

Now - if you are using only one domain name and you want different websites, the only way I know how to do this is to make different VirtualHosts with subdomains - such as:

ServerAlias sub1.domain.com
...

Serveralias sub2.domain.com
...

Of course, those would be wrapped in VirtualHost tags along with the DocumentRoot.

Brian S.
BsnTech Networks
[http;//www.bsntech.com]("http://www.bsntech.com/services-provided.html")

---

### Post by cosine_omerta on 2011-03-07
Ok, so when I disable the default, it works fine.:P

They should really add that to the tutorials.

---

