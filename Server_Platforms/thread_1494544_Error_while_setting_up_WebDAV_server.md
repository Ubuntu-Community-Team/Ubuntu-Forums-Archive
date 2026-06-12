---
title: "Error while setting up WebDAV server"
date: 2010-05-27
forum: Server Platforms
---

### Post by markbahnman on 2010-05-27
I've been trying to set up a webDAV server on my remote server and while trying to enable a vhost 'webdav' with the command

```
sudo a2ensite webdav
sudo /etc/init.d/apache2 restart
```I get 

```
Syntax error on line 9 of /etc/apache2/sites-enabled/webdav:
Invalid command '\xe2\x80\x82\xe2\x80\x82\xe2\x80\x82', perhaps 
misspelled or defined by a module not included in the server configuration
   ...fail!
```I'm just trying to enable webDAV on a custom port with access to it's own folder, could anyone give me a tip or hint? My webdav file is as such

```
<VirtualHost *:customPort>
        ServerAdmin webhost@localhost
        DocumentRoot /var/www/webdav
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/webdav/>
&#8194;&#8194;&#8194;             Options Indexes FollowSymLinks
&#8194;&#8194;&#8194;             AllowOverride None
&#8194;&#8194;&#8194;             Order allow,deny
&#8194;&#8194;&#8194;             allow from all
        </Directory>
        <Location />
&#8194;&#8194;&#8194;        DAV On
&#8194;&#8194;&#8194;        AuthType Basic
&#8194;&#8194;&#8194;        AuthName forwardslash
&#8194;&#8194;&#8194;        AuthUserFile userfilelocation
&#8194;&#8194;&#8194;        Require valid-user
           DavMinTimeout 600
&#8194;&#8194;&#8194;        <LimitExcept GET PUT HEAD OPTIONS POST>
&#8194;&#8194;&#8194;&#8194;&#8194;&#8194;        Require valid-user
&#8194;&#8194;&#8194;        </LimitExcept>
        </Location>
</VirtualHost>
```

---

### Post by volkswagner on 2010-05-27
Hmn, just to make sure there is no blank line....line 9 of the file is "Options Indexes FollowSymLinks" ?

List your mods-enabled.

```
ls /etc/apache2/mods-enabled
```


Perhaps you are missing "autoindex.load"

---

### Post by markbahnman on 2010-05-28
> **volkswagner said:**
> Hmn, just to make sure there is no blank line....line 9 of the file is "Options Indexes FollowSymLinks" ?

List your mods-enabled.

```
ls /etc/apache2/mods-enabled
```
Perhaps you are missing "autoindex.load"

autoindex.load is in the mods-enabled folder, and I tried removing the OPTIONS line and I get the exact same error when trying to enabled the site again.

---

### Post by markbahnman on 2010-05-28
I recopied the default virtual host file and slowly made it the exact same as the one I posted, enabling and disabling the site with reloads of apache2 in between to see when I got the same error and I never did. This kinda baffles me.

Now while I have the virtual host file working well, I can't access the dav server. I try

```
cadaver http://ip.address.of.server:customport/
``` and I get connection refused even though the virtual site is running.

When I change the port to 80 and run it again I get a 405 error and the folder not being accessible (not WebDAV-enabled) though I've ran

```
chown www-data /var/www/webdav
```

Also added NameVirtualHost *:customport to the start of the file and still connection refused

---

### Post by markbahnman on 2010-05-28
D'oh, just realized my apache2 server wasn't listening for connections on my customport so I added

```
Listen customport
```to my ports.conf file. Now I can actually attempt to make a connection to my server but I get the 405 error again. How do I webDAV enable a folder? Is it just a wrong line in the virtual host file, or an attribute of a file?

---

### Post by volkswagner on 2010-05-28
I am not sure, with versions changing and documentation lagging.

Check out [this thread]("http://ubuntuforums.org/showthread.php?t=1240886").  Notice the how to link in post #2.  Try moving the directives out of your vhost file as described in the how to.

---

### Post by markbahnman on 2010-06-01
Solved it, the options in the <Location> tag needed to be in the <Directory> tag, don't know why the guide I used had both used in it's config file.

---

### Post by andymurn on 2010-07-08
I ran into the exact same error as you and tried your fix but without luck. I believe the answer lies in this post you made. 

> I recopied the default virtual host file and slowly made it the exact same as the one I posted, enabling and disabling the site with reloads of apache2 in between to see when I got the same error and I never did. This kinda baffles me.

When I went into my virtual host file and deleted and reentered each of the spaces and returns between elements that I copy-pasted in the error was fixed.

---

