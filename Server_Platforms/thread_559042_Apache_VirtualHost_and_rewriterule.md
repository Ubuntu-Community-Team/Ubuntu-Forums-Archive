---
title: "Apache VirtualHost and rewriterule"
date: 2007-09-24
forum: Server Platforms
---

### Post by twistedtwig on 2007-09-24
Hi all,

So I have been trying to get proxypassreverse to work for a while.. turned out to be my iptables playing silly buggers.  Got this to work and my world was once again a happy place.......

UNTIL!!! I remembered reading about the trailing slash problem.  So in an effort to save my world again I have tried to put this rewrite in to add the slash.

But with NO success!!!

I have writes working in .htaccess files so I know the mod is up and running.

```
<VirtualHost *>

 ProxyRequests Off
 <Proxy *>
   Order deny,allow
   Deny from all
   Allow from all
 </Proxy>

 <Directory />
   Options +FollowSymlinks
   Order deny,allow
   Deny from all
   Allow from all
 </Directory>

 ErrorLog /var/log/apache2/error.log

 #Possible values include: debug, info, notice, warn, error, crit, alert, emerg
 logLevel warn

 ProxyPass        /bobby_2003/home/ http://192.168.10.100/
 ProxyPassReverse /bobby_2003/home/ http://192.168.10.100/

 CustomLog /var/log/apache2/access.log combined
 ServerSignature On
</VirtualHost>

<VirtualHost *>
 RewriteEngine on
 RewriteOptions Inherit
 RewriteRule ^/bobby_2003/home$ home/ [R]
</VirtualHost>

```

Above is cut from my vhosts.conf file. (lots at top left out as I didn't think they are relevant).  The first VirtualHost is just for the proxy, the second to try and get the rewrite to work.

I did have them in the same one but it didn't work so I tried to seperate them in a hope it might.

the proxypass works if it has the slash but without it I just get a 404 error.

I have spent some time on google and tried a number of options but have got no where, my understanding of the whole rewrite thing is very limited.

Does the rewrite write to a log by default if it fails or not?  I couldn't find anything.

Any and all help would be gratefully received.

Thanks all

Twiggy

---

### Post by twistedtwig on 2007-09-25
/bump... still very confused over this one... got an apache book on the way to have a GOOD read over, but if anyone knows how to solve this then I would be MOST grateful

---

### Post by twistedtwig on 2007-09-25
Oh, it turns out putting the proxypass in the virtual host like I have has killed it.  I did have it just in the apache.conf file and that works....

OH pooop!

---

### Post by twistedtwig on 2007-09-25
Ok,

so I put all the proxypass parts back into apache.conf just on their own (i.e. not in a location, directory, virtualhost or what ever).  These are now working again ;)

As for this pescy modrewrite!!!!

I have this virtualhost:

```
<VirtualHost *>
ServerName houseofhawkins.com
ServerAlias www.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/root
<Directory />
Options FollowSymLinks +ExecCGI
AllowOverride all
</Directory>

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn
CustomLog /var/log/apache2/access.log combined
ServerSignature On

<IfModule mod_rewrite.c>
 Options +FollowSymlinks
 RewriteEngine on
 RewriteLog "/var/log/apache2/rewrite_log"
 RewriteLogLevel 3
 RewriteRule ^sick.xml$ index.html [R]
</IfModule>

</VirtualHost>

```

The reason I put it in a the default virtualhost is because the logging only seemed to work from there so I presume thats where it is supposed to go?!?!?!?

This is the output of the log file when I try and use it:

```
192.168.10.200 - - [25/Sep/2007:23:20:20 +0100] [houseofhawkins.com/sid#81b43f0][rid#836d380/initial] (2) init rewrite engine with requested uri /sick.xml
192.168.10.200 - - [25/Sep/2007:23:20:20 +0100] [houseofhawkins.com/sid#81b43f0][rid#836d380/initial] (3) applying pattern '^sick.xml$' to uri '/sick.xml'
192.168.10.200 - - [25/Sep/2007:23:20:20 +0100] [houseofhawkins.com/sid#81b43f0][rid#836d380/initial] (1) pass through /sick.xml
192.168.10.200 - - [25/Sep/2007:23:20:20 +0100] [houseofhawkins.com/sid#81b43f0][rid#8371408/initial/redir#1] (2) init rewrite engine with requested uri /404.php
192.168.10.200 - - [25/Sep/2007:23:20:20 +0100] [houseofhawkins.com/sid#81b43f0][rid#8371408/initial/redir#1] (3) applying pattern '^sick.xml$' to uri '/404.php'
192.168.10.200 - - [25/Sep/2007:23:20:20 +0100] [houseofhawkins.com/sid#81b43f0][rid#8371408/initial/redir#1] (1) pass through /404.php

```

the problem is I get 404 page not found everytime.

I am so confused.  It would seem to be so simple but it isn't  (at least to me at the mo)....

Can anyone help please?

Thank you

---

### Post by pyrosama on 2007-10-24
I am having similar issues. I have followed the hundreds of explanations on how to enable mod_rewrite to no avail.

I have chanced the AllowOverride to All and installed and verified that mod_rewrite is loaded. However I have been unable to get any rewrites to actually work.

I've tried placing the IfModule in my apache2.conf, httpd.conf, and my .htaccess and still return no sign of a functioning rewrite module.

---

