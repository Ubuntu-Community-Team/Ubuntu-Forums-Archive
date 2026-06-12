---
title: "Help! Apache2 wrong default page"
date: 2012-03-06
forum: Server Platforms
---

### Post by charlie363 on 2012-03-06
Hi everyone, firstly I would like to say that I am an absolute newbie at this.

Here is my dilemma:

When I type in localhost, the default page doesn't show up, instead the page of a program I installed [RT4] shows up. Also, I can access any of my other websites. All my sites are in sites-available the folder including this one. 

Here is the config file for this site:

<VirtualHost *:80>

ServerName localhost/rt/
ServerAdmin [EMAIL="Charlie.liu361@gmail.com"]Charlie.liu361@gmail.com[/EMAIL]

### Optional apache logs for RT
# ErrorLog /opt/rt4/var/log/apache2.error
# TransferLog /opt/rt4/var/log/apache2.access
# LogLevel debug

AddDefaultCharset UTF-8

Alias /rt/ "/opt/rt4/share/html/"
DocumentRoot "/opt/rt4/share/html"
<Location />

Order allow,deny
Allow from all

SetHandler perl-script
PerlResponseHandler Plack::Handler::Apache2
PerlSetVar psgi_app /opt/rt4/sbin/rt-server
</Location>

<Perl>
use Plack::Handler::Apache2;
Plack::Handler::Apache2->preload("/opt/rt4/sbin/rt-server");
</Perl>

</VirtualHost>

Please help me!

---

### Post by d4m1r on 2012-03-06
^That entire virtualhost file points to /var/www/rt or localhost/rt/ which means you will NOT see the default Apache "hey, it works!" page....

In default virtualhost file, alias should be just localhost, yours is "localhost/rt".

If you just want to start over, I'd take a look @ [https://help.ubuntu.com/](https://help.ubuntu.com/). Pick the version of Ubuntu you are using > Server > Guides > Apache2 (httpd) will give you a step by step process on how to install apache.

Hope this helps.

---

### Post by volkswagner on 2012-03-06
I'm not sure if "localhost/rt" is legitimate syntax for servername.

Perhaps you can try "localhost.rt" instead.

What do your other vhost ServerName directives look like?

Also I don't think you will need the alias /rt since that is pointing to your document root.

If you Change your ServerName to localhost.rt you should be able to access that site as
```
http://localhost.rt
```

You may need to add entry to /etc/hosts for the name resolution unless you are running a local DNS server.

---

