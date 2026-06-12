---
title: "apache2 run 3 domins on one server quetion"
date: 2010-03-27
forum: Server Platforms
---

### Post by usererror on 2010-03-27
I have 3 domains:

[www.daggettstaff.com](www.daggettstaff.com)
[www.etarq.com](www.etarq.com)
[www.iametarq.com](www.iametarq.com)

I had all of them running on one server, with one IP, and each site would be served out from their own /var/www/site____ folder.

My question now is how come if I delete one of the site-enabled configs the domain will come up using the first one in the list alphabetically i.e...

I deleted the iametarq.com config from /etc/apache2/sites-enabled/

and now if i type in [www.iametarq.com](www.iametarq.com) it gives me the document root for [www.daggettstaff.com](www.daggettstaff.com) 

I am very confused.  I have read this: [http://httpd.apache.org/docs/2.2/vhosts/examples.html](http://httpd.apache.org/docs/2.2/vhosts/examples.html)

but its of no help, or i don't understand correctly.

I want it so that if i type in [www.iametarq.com](www.iametarq.com) now I get a "site not found" error, not the document root for my first domain in sites-enabled by alphabetical list order.

Thanks in advance! :D

I have to assume I'm not setting up my <VirtualHost> config or NamedVirtualHost correctly...

---

### Post by inphektion on 2010-03-27
exactly.  you have something wrong.  post config of the main one.
daggettstaff.com

---

### Post by usererror on 2010-03-28
here is what i have for daggettstaff.com i have tried so many variations with the virtualhost portions, i am posting exactly as i have now.

```

#NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        ServerName www.daggettstaff.com
        ServerAlias daggettstaff.com

        DocumentRoot /var/www/daggettstaff/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/daggettstaff>
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
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

```

---

### Post by Rulesy on 2010-03-28
As you've discovered, Apache will use the first vhost it finds (sorted alphabetically from your sites-enabled folder) if it can't find a suitable match for ServerName.

There should be (or certainly used to be) a vhost in your  sites-available folder called "default". The link to this in your  sites-enabled folder is (or was) called "000-default", and will  *automatically* be given this name if you use the typical command "a2ensite  default". The 000 solves the alphabetical issue. My own "default" vhost points  to an empty folder, this setup sounds similar to what you want, but bear in mind it will give a 403 error because of the Deny from all directive, rather than a simple "site not found" error. If you really, really need that, you'll need to remove the DNS entry that points to your server.

Here is my "default" file

```

ServerName localhost
NameVirtualHost *

<VirtualHost *>
        DocumentRoot /var/www/empty/

        <Directory />
                ServerSignature off
                Order allow,deny
                Deny from all
        </Directory>
</VirtualHost>

```

---

### Post by usererror on 2010-03-28
Rulesy,

Thanks for the point regarding the default, I did indeed remove it.  I have mimicked yours for now, naming it 000-default in my sites-enabled.

now i have an entry for iametarq.com in sites enabled and also one for daggettstaff.com.

I continually get the "NameVirtualHost *:0 has no VirtualHosts" error now.  and NameVirtualhost matches what is in <VirtualHost>, which is just an *

```

 * Restarting web server apache2                                                                                                                                             [Sun Mar 28 10:28:10 2010] [warn] NameVirtualHost *:0 has no VirtualHosts
[Sun Mar 28 10:28:10 2010] [warn] NameVirtualHost *:0 has no VirtualHosts
 ... waiting [Sun Mar 28 10:28:11 2010] [warn] NameVirtualHost *:0 has no VirtualHosts
[Sun Mar 28 10:28:11 2010] [warn] NameVirtualHost *:0 has no VirtualHosts

```

It also seems that the 000-default is taking presidence for all the virtual hosts.

So here's some more background.

I have "ServerName" commented out in /etc/apache2/apache2.conf because it's being declared in each site under "sites-enabled" now.  Does this need to be changed?

I also have "VirtualHost" commented out in the ports.conf file

My domains are registered at GoDaddy.com using their DNS Tools, I have the @ or www. set to point to the IP address of my static IP of my WAN connection.

My Apache Server uses Port Forwarding on 80 to get to the Apache server on my internal network.

Here are the configs now:

000-default in sites-enabled (via sym link to sites-available)
```

ServerName localhost
NameVirtualHost *

<VirtualHost *>
        DocumentRoot /var/www/empty/
        ServerAdmin support@etarq.com

        <Directory />
                ServerSignature off
                Order allow,deny
                Deny from all
        </Directory>
</VirtualHost>

```

daggettstaff.com
```

ServerName www.daggettstaff.com
NameVirtualHost *

<VirtualHost *>
        ServerAdmin support@etarq.com
        ServerAlias daggettstaff.com

        DocumentRoot /var/www/daggettstaff/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/daggettstaff>
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
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

```

iametarq.com (i am 99% sure you can disregard the Apache::Gallery stuff here.
```

ServerName www.iametarq.com
NameVirtualHost *

<VirtualHost *>
    ServerAlias www.iametarq.com
        ServerAdmin support@etarq.com
        DocumentRoot /var/www/iametarq
        <Directory />
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog     /var/log/apache2/gallery-error_log
        TransferLog  /var/log/apache2/gallery-access_log
        PerlSetVar   GalleryTemplateDir '/usr/share/libapache-gallery-perl/templates/bright/'
        PerlSetVar   GalleryInfo 'Picture Taken => DateTimeOriginal, Flash => Flash'
        PerlSetVar   GallerySizes '640 1024 1600 2272'
        #PerlSetVar   GalleryDirSortBy 'ctime'
        #PerlSetVar   GallerySortBy 'ctime'
        PerlSetVar   GalleryThumbnailSize '100x75'
        #PerlSetVar   GalleryCopyrightImage '/usr/share/libapache-gallery-perl/icons/c.png'
        PerlSetVar   GalleryCopyrightText '(c) Mark Tarquini'
        PerlSetVar   GalleryTTFDir '/usr/share/fonts/truetype/msttcorefonts/'
        PerlSetVar   GalleryTTFFile 'verdana.ttf'
        PerlSetVar   GalleryTTFSize '8'
        PerlSetVar   GalleryCopyrightColor '255,255,255,255'
        PerlSetVar   GalleryQuality '75'
        PerlSetVar   GalleryRootText 'gallery'
        PerlSetVar   GalleryCacheDir '/var/cache/apache2/apache-gallery/'
        PerlOptions +GlobalRequest
        <Directory /var/www/iametarq/gallery/>
                SetHandler        modperl
                PerlResponseHandler       Apache::Gallery
        </Directory>

        Alias /icons/gallery/ "/usr/share/libapache-gallery-perl/icons/"


        <Directory /var/www/iametarq/update/>
                AuthType Basic
                AuthName "Updates: Restricted Access"
                AuthUserFile /etc/apache2/passwd/passwords
                Require user mark
        </Directory>
        <Directory /var/www/iametarq/contacts/list/>
                AuthType Basic
                AuthName "View Contact List"
                AuthUserFile /etc/apache2/passwd/passwords
                Require user mark
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

```

---

### Post by inphektion on 2010-03-28
Basically what you want is for your servers to only respond on their name, not dropping back to some default.  you don't need the 000-default stuff to do that, you need to define your virtual hosts differently.
For one, don't put ServerName directive outside of the <virtualhost> definition.
Put it in with ServerAdmin and DocumentRoot.

Then i would do one
```

NameVirtualHost daggetstaff.com:80

<VirtualHost daggettstaff.com:80>
ServerName daggettstaff.com
ServerAlias www.daggetstaff.com
... rest of it....

```
Then for the other sites, don't declare another NameVirtualHost just do the 
```

<VirtualHost othersite.com:80>
ServerName othersite.com
ServerAlias www.othersite.com
...etc.

```

---

### Post by usererror on 2010-03-28
Ok, here's what I've done now.

I temporarily removed the 000-default from sites-enabled

left iametarq.com and daggettstaff.com

here is iametarq.com:

```

NameVirtualHost iametarq.com:80

<VirtualHost iametarq.com:80>
        ServerName iametarq.com
        ServerAlias www.iametarq.com
        ServerAdmin support@etarq.com
        DocumentRoot /var/www/iametarq
        <Directory />
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

daggettstaff.com
```

<VirtualHost daggettstaff.com:80>
        ServerName daggettstaff.com
        ServerAlias www.daggettstaff.com

        DocumentRoot /var/www/daggettstaff/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

```

when i try the domains I get
```

Not Found

The requested URL / was not found on this server.

```

No errors at all when restarting the Apache service.  No useful errors listed in error.log in /var/log/apache2/ except something about "htdocs" not existing.

---

### Post by usererror on 2010-03-28
Also,

my error.log for /var/log/apache2/ has tons of "htdoc" does not exist.

I added a

```

DocumentRoot "/var/www"

```

and now ALL the websites default to /var/www!

so i took that out.

Even more confused since I have a document root declared in the virtualhost files.

---

### Post by usererror on 2010-03-28
I've been battling this all morning.  After more research it appears that Apache IS functioning properly...

Found this post:

[http://www.debian-administration.org/articles/412#comment_18](http://www.debian-administration.org/articles/412#comment_18) comment 19 also helps.

So what I really need is a 000-default (As Rulesy suggested) that "black holes" all other wildcard domains and domains pointed to my server that I don't want to use anymore but are linked to out on the web.  I have 6 domains pointed to the IP of my server right now...

In doing this I have managed to make it so my multiple public domains work from the ousite, while wildcard domains get blackholed, and ALSO set my internal website ONLY work internally and now be accessible from the wildcard domains which was also happening before.

---

