---
title: "Webdav + Nautilus = Forbidden"
date: 2010-02-20
forum: Server Platforms
---

### Post by Spectre5 on 2010-02-20
I've installed webdav on my server and I can access it fine through cadaver.  However, when I try to access it via nautilus, I get Forbidden.  It is NOT secured (SSL).  When I try to access it via firefox, I get an error since I DO NOT have "Options Indexes" in my apache config file.  If I add this option in, then I can browse the root direction and webdav folder via firefox, but still not from nautilus.  Please let me know what other information you need.  I've googled and searched the forums for awhile, but not "solutions" I found have worked for me.

I want the webdav folder to just be a single folder within the direction, so this is how I have my config file setup:

```

<VirtualHost *:80>
       ServerName (servername_here)
       ServerAlias (servername_here)
       DocumentRoot /var/www/web

       <Directory /var/www/web>
                #Options Indexes Multiviews
                AllowOverride None
                Order allow,deny
                allow from all
       </Directory>
      
       Alias /webdav /var/www/web/webdav
       
       <Location /webdav>
                DAV On
                AuthType Basic
                AuthName "webdav"
                AuthUserFile /var/www/web/passwd.dav
                Require valid-user
       </Location>
       LogLevel warn
       ErrorLog /var/log/apache2/error.log
       CustomLog /var/log/apache2/access.log vhost_combined
</VirtualHost>

```

As a side-note...when I included "Option Indexes", it allowed me to view the passwd.dav file from firefox!  That doesn't seem very good...

Thanks!

---

### Post by Spectre5 on 2010-02-20
I tried making some edits to make webdavs work over SSL instead...I'm getting the exact same results.  It works over cadaver and firefox, NOT nautilus....

---

### Post by BrandonLC on 2010-02-21
Any luck with this? I'm having same problem.

Your password file is showing up because you placed it in your web root. Place it somewhere outside the web root, but in a place that Apache can still read, and that problem will go away.

---

### Post by Spectre5 on 2010-02-21
Ya - I still have this problem.  I did move that password file...I thought it was stupid to put it there but I was just blindly doing what the tutorial told me :)

If you find a solutions, PLEASE come back and let me know...I'll do the same.  I'm still searching...

My guess is it is some sort of permissions issues...just don't know what.  I've tried a lot of things to no avail.

I had a friend try connecting from Windowz Vista and he said it returned this message: "The folder you entered does not appear to be valid. Please choose another."

So I'm stuck for the moment

---

### Post by volkswagner on 2010-02-22
I recall having a similar problem.  I can't recall exactly as I have stopped using webdav.  If memory serves me, I believe I was able to connect using, Places>connect to network>choose webdav as the server.  If I filled in the username it would not work.  If I left the field blank, the server would return a query for the credentials, and I could then connect.   

I think there is a bug in Nautilus.

Hope this helps.

---

