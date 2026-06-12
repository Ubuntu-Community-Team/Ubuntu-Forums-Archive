---
title: "Apache Virtual Host, mod_rewrite and PHP problem"
date: 2008-06-15
forum: Server Platforms
---

### Post by hodge24 on 2008-06-15
Hi all,

I have an interesting problem in my LAMP development environment setup, in that having set up a virtual host, enabled mod_rewrite, and written a rule that seems to work (and actually does work on my test server, which is hosted elsewhere), the file that the rule is supposed to rewrite to, isn't being processed by PHP. Instead, when I enter the "clean" url into my browser, e.g. [www.mydevserver.com/xyx/the-passed-variable](www.mydevserver.com/xyx/the-passed-variable), in return, I get Firefox asking me if I want to download the file "the-passed-variable which is a PHTML file".

Now, in my access.log file, it tells me:

```

"GET /xyx/the-passed-variable HTTP/1.1" 200 7132 "-" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008060309 Firefox/3.0"
```

and there is nothing in the error.log, so on the surface, it seems to be working. Kind of...

OK, now for the setup procedure. The relevant symlink exists in /etc/apache2/mods-enabled to /etc/apache2/mods-available/rewrite.load

I also have the following config information in a file /etc/apache2/sites-available/mydevserver.com

```

<VirtualHost *>
        ServerName mydevserver.com
        ServerAlias www.mydevserver.com
        DocumentRoot /var/www/mydevserver
	DirectoryIndex index.php
        <Directory /var/www/mydevserver>
            AllowOverride all
	    Options Indexes FollowSymLinks MultiViews
	    Order allow,deny
	    Allow from all
        </Directory>  
        CustomLog /var/log/apache2/mydevserver.com-access.log combined
</VirtualHost>

```

and of course, the symlink /etc/apache2/sites-enabled/mydevserver.com pointing to this config file. In addition, AllowOverride is set to "all" in /etc/apache2/sites-available/default in both the / and /var/www Directory declarations.

I have also added:

```

127.0.0.1 localhost mydevserver.com www.mydevserver.com

```

to the /etc/hosts file.

/etc/apache/apache2.conf hasn't been changed.

/var/www/mydevserver/.htaccess contains the following rewrite rule (which works on my hosted server)

```

RewriteEngine On

RewriteRule ^xyz/([^/\.]+)/?$ xyzscript.php?variable=$1 [L]

```

Finally, pointing my browser to ```
www.mydevserver.com/xyzscript.php?variable=the-passed-variable
``` works, and PHP processes it correctly. But, for some reason, ```
www.mydevserver.com/xyz/the-passed-variable
``` is forcing me to download a PHTML file...

I should probably also mention that I have x64 Ubuntu Hardy (upgraded from x64 Gutsy), with all the latest updates.

Erm, I think that's it - It's all very frustrating, and I've become blinded to it all from looking at it so much! So, if anyone can help me track down the missing semi-colon, I'd very much appreciate it, lol!

**Edit:** Solved. Kind of - I'm not sure how, but things seem to have clicked into place, and the lights have come on. Even after running "sudo /etc/init.d/apache2 force-reload" a few times, the problem still occurred, so I just switched off and gave up for the night. However, upon booting this morning, all is well... Very strange...

---

### Post by kotor on 2010-07-21
Hello,

your case is not a singular one, the whole issue is browser dependent.
I had similar situation, firefox just gave me the download window, while
konqueror displayed the page - as he should.

This is really strange when you consider that it all should have been parsed on
the server (the file FF downloads is not parsed php).

There is the catch:
1. You must have made some first error, that made FF get the real, unparsed PHP
2. later, on your request, FF just gives you the same cashed file !!
3. other browser, that doesn't have the cashed file, displays the web.

Cure:
After you make configuration changes to the virtual server or php settings, clear your primary browser cache.

---

### Post by Ryan Dwyer on 2010-07-21
In the future, use /etc/init.d/apache2 restart instead of reload or force-reload. Unless you're on a production server and you can't afford to have a few seconds of downtime.

---

