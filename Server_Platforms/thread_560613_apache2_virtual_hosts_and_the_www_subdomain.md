---
title: "apache2 virtual hosts and the www subdomain"
date: 2007-09-26
forum: Server Platforms
---

### Post by swiftsam on 2007-09-26
I have a server hosting two sites with different domains.  Both sites work fine at their root domain, but I can't get them to work with a preceding "www."

for example, [http://swiftsam.com](http://swiftsam.com) works, but [http://www.swiftsam.com](http://www.swiftsam.com) will not (it 404's).

In /etc/apache2/apache2.conf I have:
```

NameVirtualHost *:80
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```

and then in /etc/apache2/sites-enabled/000-default I have:
```

<VirtualHost *:80>
        ServerName www.swiftsam.com
        ServerAlias swiftsam.com *.swiftsam.com
        DocumentRoot /home/www/

</VirtualHost>

```
and the same sort thing for my other site which is having the same problem.
```
<VirtualHost *:80>
        ServerName www.obtnotes.com
        ServerAlias obtnotes.com *.obnotes.com
        DocumentRoot /var/lib/mediawiki1.7/
        <Directory /var/lib/mediawiki1.7/>
                Options +FollowSymLinks
                AllowOverride All
                order allow,deny
                allow from all
        </Directory>

        # some directories must be protected
        <Directory /var/lib/mediawiki1.7/config>
                Options -FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/lib/mediawiki1.7/upload>
                Options -FollowSymLinks
                AllowOverride None
        </Directory>
</VirtualHost>

```

pinging [www.swiftsam.com](www.swiftsam.com) resolves to the right ip, but gets no responses.

I have tried to copy the set up advice [here on the apache site]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html") as well as the ubuntu server documentation.

any ideas what the problem is?

thanks

---

### Post by MJN on 2007-09-26
Your virtualhost config is correct, however it is not being parsed:

> **swiftsam said:**
> In /etc/apache2/apache2.conf I have:
```
# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

```

You need:
```
Include /etc/apache2/sites-enabled/[^.#]*
```

...to capture all the files in the sites-enabled directory.

Mathew

---

### Post by swiftsam on 2007-09-26
thanks for your reply MJN,

I wondered about that, so i made some changes, and if I change the DocumentRoot it does break the sites.  Also if I remove the included sites completely, the domains don't respond at all.  

So it does seem like they are being parsed, the part about the www just isn't sticking.

I did try your suggestion in apache2.conf verbatim, but it did not change the behavior.

thanks very much for your help, I hope you or somebody has another idea

---

### Post by MJN on 2007-09-27
Hmm... you got me there then!

The config looks fine, so I'm guessing it must be something in your main config that's amiss - but the default should work fine though.

I'm curious though why you didn't have the default regular expression listed in the Include directive - have you modified apache2.conf significantly? Perhaps that's where the problem lies...

Mathew

---

### Post by twistedtwig on 2007-09-27
not sure if this is right or will fix your issue but I always had servername being mydomain.com and serveralias being [www.mydomain.com](www.mydomain.com)  which works. But as I say this might not be the fix for you

---

