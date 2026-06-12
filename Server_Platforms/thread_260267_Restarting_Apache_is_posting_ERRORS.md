---
title: "Restarting Apache is posting ERRORS"
date: 2006-09-18
forum: Server Platforms
---

### Post by MystaMax on 2006-09-18
I've successfully installed a LAMP stack on my server, and all is well except for when I restart my apache server. I receive these errors:

```

[Sat Sep 16 10:00:34 2006] [warn] module php4_module is already loaded, skipping
[Sat Sep 16 10:00:34 2006] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sat Sep 16 10:00:34 2006] [warn] NameVirtualHost *:0 has no VirtualHosts
``` 

I'm not sure why the 1st is reporting @ all. The last two worry me, as I'm not sure what I'm looking for. I assuming it has something to do with with the way I defined my Virtualhost, but I'm reluctant to change something b/c it works, and I'm not exactly sure what to do.  I want to resolve these errors so they dont report and to learn whats going on. Any ideas, any help is appreciated. Thanks.

Here is the beginning of my Vhost file:

```
NameVirtualHost *
<VirtualHost *:80>
        ServerAdmin admin@DOMAIN.com
        ServerAlias subdomain.DOMAIN.com
        DocumentRoot /var/www/webapp

```

---

### Post by Nixed0 on 2006-09-18
Did you define a 'ServerName' for your virtual host?

Check out [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html) for more info.

---

### Post by chrisfay on 2006-09-18
> [Sat Sep 16 10:00:34 2006] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

Apache defaults to using port 80. There is no reason to add that in your virtual host directive. 

> NameVirtualHost *
<VirtualHost *:80>
        ServerAdmin [email]admin@DOMAIN.com[/email]
        ServerAlias subdomain.DOMAIN.com
        DocumentRoot /var/www/webapp

I know you said this was the 'beginning' of your virtual host file, but did you close with the correct syntax? Should look something like:

NameVirtualHost *

<VirtualHost *>
DocumentRoot "/var/www/docroot"
ServerName domain.tld
ServerAlias [www.domain.tld](www.domain.tld)
<Directory "/var/www/docroot">
allow from all
Options -Indexes
</Directory>
ServerAdmin [email]youremail@domain.com[/email]
</VirtualHost>

---

### Post by MystaMax on 2006-09-19
[quote=chrisfay]

NameVirtualHost *

<VirtualHost *>
DocumentRoot "/var/www/docroot"
ServerName domain.tld
ServerAlias [www.domain.tld]("http://www.domain.tld/")
<Directory "/var/www/docroot">
allow from all
Options -Indexes
</Directory>
ServerAdmin [EMAIL="youremail@domain.com"]youremail@domain.com[/EMAIL]
</VirtualHost>[/quote]

Yep, I posted the parts of the file which I think were causing the problem.

Are NameVirutalHost and VirtualHost needed in each vhost file? In ubuntu, each vhost has its own file, but apache docs make it seem like its one file. I've heard that each distro handles this differently. 

I should specify the IP of the server in NameVirutalHost directive only once (if my server only has one IP)? Or do I have to specify a NameVirtualHost w/ each VirtualHost Directive (or in ubuntu, in each file)?

Heres my breakdown.

NameVirtualHost SERVERIP:PORT_TO_LISTEN_ON
<VirtualHost SERVERIP:80>
   ServerName [www.practice.com]("http://www.practice.com")
   Server Alias [www.practice.com]("http://www.practice.com")
   DocumentRoot /var/www/practice
</VirtualHost>

I feel more comfortable specifying an IP for both NameVirtualHost and VirtualHost Directives, which shouldn't be a problem, b/c the server only has one IP (@ this time). 

After reading the docs 3 or 4 times, i started to make sense. I also read the [ubuntu server guide]("https://help.ubuntu.com/") which also helped me understand.

```
[Sun Sep 17 08:57:08 2006] [warn] module php4_module is already loaded, skipping
```That above error seems like apache is trying to load php4_module twice, so I'm assuming its reading it from two config files? How apache load modules? are they reloaded on a restart?

Thanks for the help guys.

---

### Post by Nem Chua on 2007-04-15
The Apache2 docs state one actually _should_ use * rather than an explicit IP address except where the contents served should depend on the IP it is requested from.

I hit the same snag and don't know why.

On a Debian nearby, the same files run OK, no error, and on my development Ubuntu, I see the Apache2 complaining.

Best,
NC

---

