---
title: "Apache does not recognize .php extention"
date: 2008-06-18
forum: Server Platforms
---

### Post by coolclu3 on 2008-06-18
Hi all,
I have a Ubuntu 7. (Feisty) box running on my desktop
Here are the packages I have installed to get Apache2 running with PHP

apache2
apache2-mpm-prefork
apache2-utils
apache2.2-common

libapache2-mod-php5

php5
php5-cgi
php5-cli
php5-common
php5-dev
php5-mysql

I have enabled php5 module by 
a2enmod php5
And I have seen php5.load under /etc/apache2/mods-enabled/

I have added .php type by having the following lines in /etc/apache2/apache2.conf

<IfModule mod_mime.c>
    AddType text/html .shtml
    AddType application/x-httpd-php .php
    AddOutputFilter INCLUDES .shtml

I have also checked mime module is loaded.
I have restarted apache a thousand times

But when loading [http://localhost/test.php](http://localhost/test.php) , firefox still tries to *SAVE* the file, not opening it.



Am I missing something crucial??
Please help me out.
Cheers everyone.

---

### Post by ad_267 on 2008-06-18
Try removing the "AddType application/x-httpd-php .php" and see if it helps. I don't think you should need to add that.

---

### Post by windependence on 2008-06-18
This is a dumb question but did you restart Apache after enabling the module?

-Tim

---

### Post by coolclu3 on 2008-06-18
> **ad_267 said:**
> Try removing the "AddType application/x-httpd-php .php" and see if it helps. I don't think you should need to add that.

Agreed, I just thought so too because apache2.conf has the following line
TypesConfig /etc/mime.types

And my mime.types has that "php" line already

About restarting, I restarted it a "thousand" times :(

However, still the same thing happens :(

---

### Post by ad_267 on 2008-06-18
Hmm well that's weird. All I can say is it looks like you have too much installed. All I installed to get apache + php was apache2, php5 and libapache2-mod-php5. Didn't even need to use a2enmod or anything, it just worked. This was with Gutsy and Hardy though, so might be something else required with Fiesty.

---

### Post by coolclu3 on 2008-06-18
> **ad_267 said:**
> Hmm well that's weird. All I can say is it looks like you have too much installed. All I installed to get apache + php was apache2, php5 and libapache2-mod-php5. Didn't even need to use a2enmod or anything, it just worked.

Well, that's what I did too, but my apt installed the other packages as well
I have only "trusted" official repo sources in my sources.list by the way...

I was running apache 6. before and i recall not having this strange package "apache2-mpm-prefork" (Multi Processing Module)

But anyway....what could be wrong here ? It can't be firefox settings because I tried with wget and returns the script, not the output :(

---

### Post by coolclu3 on 2008-06-18
[Wed Jun 18 14:44:07 2008] [warn] [client 127.0.0.1] mod_include: Options +Includes (or IncludesNoExec) wasn't set, INCLUDES 
filter removed

I got this line in apache error.log

I don't know what this is....

---

### Post by windependence on 2008-06-18
In order for includes to work, you need the following in your apache2.conf file:

The Options directive after the <Directory ....> directive that defines
your Document Root must have Includes or IncludesNoExec
IncludesNoExec is safer as it doesn't allow executables in shtml
files.

Can you post your apache configuration file?

Also try running ```
sudo /etc/init.d/apache2 configtest
```

-Tim

---

### Post by coolclu3 on 2008-06-18
Hi Tim
/etc/init.d/apache2 doesn't have configtest option 

I also have included IncludesNoExec to the Options under DocumentRoot in /etc/apache2/sites-enabled/000-default

I'm attaching my /etc/apache2/apache2.conf . Please have a look. Please note this is all *DEFAULT* configuration except for that "php" line I mentioned above, which is commented out in this file.
My Feisty box is also only 1 week old.

A similar problem :(
[http://ubuntuforums.org/showthread.php?t=416820](http://ubuntuforums.org/showthread.php?t=416820)

Thanks for reading

---

### Post by coolclu3 on 2008-06-18
OK
I got it solved.

I removed the packages with apt-get --purge remove, not dpkg --remove (which is what i did before)

After reinstalling, it works well.
Some sh** must have gone wrong :(

See how I came up with the apt-get --purge here
[http://www.howtoforge.com/forums/showthread.php?t=7689](http://www.howtoforge.com/forums/showthread.php?t=7689)

---

### Post by windependence on 2008-06-18
I believe you need to uncomment the lines I have in bold and restart Apache:

```
 #
    # AddHandler allows you to map certain file extensions to "handlers":
    # actions unrelated to filetype. These can be either built into the server
    # or added with the Action directive (see below)
    #
    # To use CGI scripts outside of ScriptAliased directories:
    # (You will also need to add "ExecCGI" to the "Options" directive.)
    #
    #AddHandler cgi-script .cgi

    #
    # For files that include their own HTTP headers:
    #
    #AddHandler send-as-is asis

    #
    # For server-parsed imagemap files:
    #
    #AddHandler imap-file map

    #
    # For type maps (negotiated resources):
    # (This is enabled by default to allow the Apache "It Worked" page
    #  to be distributed in multiple languages.)
    #
    AddHandler type-map var

    #
    # Filters allow you to process content before it is sent to the client.
    #
    # To parse .shtml files for server-side includes (SSI):
    # (You will also need to add "Includes" to the "Options" directive.)
    #
    AddType text/html .shtml 
    [B][COLOR="Red"]# AddType application/x-httpd-php .php
    # AddType application/x-httpd-php .php5[/COLOR][/B]    
    # AddOutputFilter INCLUDES .shtml .php
```

-Tim

---

### Post by firecat53 on 2008-06-18
I also found once that Firefox was messing it up .... as soon as I cleared all my private data, it stopped trying to download the php file and allowed the page to process! Very frustrating, as typically it works right out of the box! I had made several changes in the apache config like you did, but after it started working, I undid all the changes....and it still worked.

Scott

---

### Post by mmatte on 2011-03-14
I had the same problem after I reinstalled apache2 as lamp-server and libapache2-mod-php5.

You have to restart apache with:
    sudo apache2 force-reload or sudo apache2 restart

But you also have to clear the history inside the browser to force the browser to make a fresh read on the server. It also works if you change the server adress from FQDN to localhost for example.

---

