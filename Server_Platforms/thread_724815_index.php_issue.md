---
title: "index.php issue?"
date: 2008-03-15
forum: Server Platforms
---

### Post by seepage87 on 2008-03-15
I set up virtual hosting in apache so that blog.mysite.org links to /var/www/wordpress/ but if I visit that it ends up redirecting to /var/www.  If I put in index.html into /var/www/wordpress/ it displays the index.html.  I can get it to work with mysite.org/wordpress/ though.

I also have mediawiki set up the same way, but that works just fine with an index.php.  I'm not sure what's going on.  Any help?  Let me know if you need me to post anything.

---

### Post by whaley on 2008-03-15
Sounds like your VirtualHosts are overriding one another.  If you make a request to a hostname and the request file isn't there (or if a non 200 or 300 status code is returned, I think), the next VirtualHost with higher precedence handles the request.

To resolve this make sure you have a NameVirtualHost directive in your conf file. 


```
NameVirtualHost 255.255.255.255
```

Where 255.255.255.255 is the ip address of your server.

---

### Post by seepage87 on 2008-03-15
I used NameVirtualHost * once at the top of the file outside any of the virtual host blocks.  I thought this was ok, should I change the * to my ip address?  My public ip address or my router assigned address?

---

### Post by whaley on 2008-03-15
Actually, NameVirtualHost * should be ok.  I'm not sure what specifically is happening.  

Can you provide some output from 

```
sudo apachectl restart
```

and also paste some contents from the end of /var/log/apache2/error.log

---

### Post by seepage87 on 2008-03-17
Apache2ctl gives nothing when I run it, and when I restart apache via the init.d script, I get this:
```
alex@tess:/var/log/apache2$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                   [ OK ]
alex@tess:/var/log/apache2$

```

Which really isn't any help.  This is my error log:

```
[Sun Mar 16 06:25:17 2008] [notice] Digest: generating secret for digest authentication ...
[Sun Mar 16 06:25:17 2008] [notice] Digest: done
[Sun Mar 16 06:25:17 2008] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 configured -- resuming normal operations
[Sun Mar 16 11:53:11 2008] [error] [client 76.161.239.150] request failed: URI too long (longer than 8190)
[Sun Mar 16 11:53:41 2008] [error] [client 76.161.239.150] File does not exist: /var/lib/mediawiki1.10/_vti_bin
[Mon Mar 17 09:33:36 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:33:36 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:33:36 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:33:43 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:33:43 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:33:44 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:33:45 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:33:50 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:33:54 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:33:55 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:33:56 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:34:00 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:34:17 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico
[Mon Mar 17 09:34:20 2008] [error] [client 199.207.253.101] File does not exist: /var/lib/mediawiki1.10/favicon.ico

```

Which I also think probably isn't any help, especially since the wiki works fine.  Any other ideas?

---

### Post by whaley on 2008-03-17
Ok, so it's definitely not a case of VirtualHosts overriding each other.  Otherwise you would have received warnings when apache was restarted.

Can you tell us the values of the following directives in your apache2.conf, and if you have these defined in a VirtualHost or in the main section.
[LIST=1]
[*]ErrorDocument 404
[*]DirectoryIndex
[/LIST]

... or just paste your entire apache config, if it's not grossly large.

---

### Post by seepage87 on 2008-03-17
I haven't changed the apache2.conf from the default, but all errordocument 404 directives are commented out and there's no directory index.  I've included the "default" file from sites-available.  I used to have the virtual hosts split out into separate files, but they got put in here when I was debugging something.

```

NameVirtualHost *
<VirtualHost *>
        ServerAdmin alex@kormendi.org

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
               # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
        </Directory>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

<VirtualHost *>
        ServerAdmin alex@kormendi.org
        ServerName wiki.kormendi.org
        DocumentRoot /var/lib/mediawiki1.10
</VirtualHost>

<VirtualHost *>
        ServerAdmin alex@kormendi.org
        ServerName blag.kormendi.org
        DocumentRoot /var/www/wordpress
</VirtualHost>

<VirtualHost *>
        ServerAdmin alex@kormendi.org
        ServerName blog.kormendi.org
        DocumentRoot /var/www/wordpress
</VirtualHost>


```

---

### Post by whaley on 2008-03-17
In the VirtualHost for wordpress, try setting the DirectoryIndex directive to foo.php, where foo.php is the index page for wordpress.

*shrug*

---

### Post by seepage87 on 2008-03-18
Wow, sorta weird.  I do that and it displays the contents of /var/www/wordpress/ in which index.php lies.  I tried using both index.php and /var/www/wordpress/index.php as the argument.

But if I click on index.php when I'm there, it then forwards me to the main site like it did before.  So blog.kormendi.org is pointing to the right place, it's the reading of the index.php that is ruining it.  To test this I explicitly entered [http://blag.kormendi.org/wp-login.php](http://blag.kormendi.org/wp-login.php), which sent me to the login site, as expected.

I'm not sure what the index.php for wordpress is supposed to be, and I don't know php, but this is mine:
```

<?php
/* Short and sweet */
define('WP_USE_THEMES', true);
require('./wp-blog-header.php');
?>

```

This looks fine, it just calls another file, I guess.  What I don't get is why it loads fine when I do kormendi.org/wordpress/ but not when I do blog.kormendi.org, which as tested above works fine.

---

### Post by whaley on 2008-03-18
Try this for your wordpress virtual host (note the <VirtualHost> directive now).

```

<VirtualHost blog.kormendi.org>
        ServerAdmin alex@kormendi.org
        ServerName blog.kormendi.org
        DocumentRoot /var/www/wordpress
</VirtualHost>

```

You have to put hostnames in the directive itself.

---

### Post by seepage87 on 2008-03-19
No luck.  I tried it both with and without a NameVirtualHost directive specifying it, but nothing worthwhile, except when it displayed /var/www/index.html it said blog.kormendi.org instead of kormendi.org.  So basically it's not only wrong, it's also lying now.

I also tried making a copy of index.php named test.php.  When I click on that (from it displaying the contents of blog.kormendi.org), it says the file cannot be found, while index.php displays index.html from the root directory.  Weird.

---

### Post by whaley on 2008-03-19
Move the VirtualHost directive for your blog to the very top.  I  believe when apache is resolving domains, it does so top to bottom through the list of VirtualHosts.  Since your first directive specifies a wildcard domain (*), blog.kormendi.org always resolves to that VirtualHost and not the VirtualHost you have defined for it. 

Give that a shot and see what happens.

---

### Post by seepage87 on 2008-03-19
I actually already tried that a few times with no luck.

I may have solved the problem though.  I figured maybe it was wordpress since the wiki works fine without a basic virtualhost confguration.  

I had once had problems with WP because I installed it from my network using 192.168.1.103/wordpress, and every time I visited kormendi.org/wordpress from any computer it forwarded me to 192.168.1.103/wordpress which obviously wouldn't work unless I was in my network.  I had to delete the wordpress folder and database and install from scratch to fix this bahavior.

This wasn't forwarding me anywhere when I went to kormendi.org/wordpress/, or to blog.kormendi.org, for that matter, so it didn't occur to me that this was the problem.  But on a hunch I decided to reinstall it anyway.

Now I did the install from blog.kormendi.org (which was forwarding correctly all along) and when I do blog.kormendi.org it works with the original virtualhost config I had.

On a side note, due to whatever it is in the wordpress installation that cares from what address you install it, kormendi.org/wordpress/ now forwards to blog.kormendi.org/wordpress/ which doesn't exist, though I can set that to forward back to blog.kormendi.org/ easily enough.

Whaley, Thanks so much for you help, I've learned tons in the process of debugging this.

---

