---
title: "Can't get apache access directives working properly"
date: 2009-11-25
forum: Server Platforms
---

### Post by (-NINJ4-) on 2009-11-25
Previously I had been requiring a password from every user, but now I would rather just allow all connections from the local network, and a password from anyone attempting to connect from outside.  This is what I put in my httpd.conf:

```
<Directory /var/www>
        AuthName ""
        AuthType Basic
        AuthUserFile /etc/apache2/.htpasswd
        Require valid-user
        Allow from 10.1.1
        Satisfy Any
</Directory>

```
This configuration, for whatever reason, is allowing all connections even remotely with no login requirement.  This is definitely caused by the "Allow from" and Satisfy lines, as my former httpd.conf works perfectly for requiring passwords from everyone:
```
<Directory /var/www>
        AuthName ""
        AuthType Basic
        AuthUserFile /etc/apache2/.htpasswd
        Require valid-user
</Directory>
```

I thought it might be because the webserver is behind a NAT with port forwarding, but the access logs show that the server is receiving the IP address information from the outside world properly.  How can I fix this so that only computers on the local network can access the server without needing to log in?

Thanks in advance!

---

### Post by spikyjt on 2009-11-25
I would try adding
```
Order deny,allow
Deny all 
```
Above your Allow directive. That should do the trick.

---

### Post by (-NINJ4-) on 2009-11-25
Assuming that you meant "deny from all" (as deny all gave a failure to restart), I was still able to access the server from outside the network without logging in.  Thanks for the advice though.

---

### Post by HighCommander540 on 2009-12-01
I'm not sure if this will help, but don't you need the Allow from to look like this to work for all your local network:

Allow from 10.1.1.*

---

### Post by (-NINJ4-) on 2009-12-01
> **HighCommander540 said:**
> I'm not sure if this will help, but don't you need the Allow from to look like this to work for all your local network:

Allow from 10.1.1.*
Thanks for the advice, but this gives me the same result as before, any IP address can access the site with no login info. :\

Interestingly, I get this same result even if I take the latter httpd.conf (the one that require passwords and has no other options for authorization) and add "Satisfy Any".  This happens even after I add these two lines:
```
        Order Allow,Deny
        Deny from all
```Even if I alter the httpd.conf to ONLY accept connections from my local network, I can still access it from outside.  What is going on here? 

Right now my httpd.conf is as follows:```
<Directory /var/www>
        AuthName "home control"
        AuthType Basic
        AuthUserFile /etc/apache2/.htpasswd
        Require valid-user
        Order Allow,Deny
        Deny from all
#       Satisfy Any
#       Allow from 10.1.1
</Directory>
```If I uncomment both, or even just the Satisfy Any line, the password protection evaporates and anyone can access the site.  This happens both with the second line reading 10.1.1 and 10.1.1.*.
Thanks again if anyone can help. :)

---

### Post by HighCommander540 on 2009-12-01
**_*edit*_** So I think I figured out how to fix it. I was having the same problem as you were. For something similar. Please, post your entire configuration. And I might be able to help.

Also, for he OP when you actually manage to make this work. You will need the * (wildcard). Otherwise it won't work properly.

---

### Post by (-NINJ4-) on 2009-12-01
> **HighCommander540 said:**
> Also, for he OP when you actually manage to make this work. You will need the * (wildcard). Otherwise it won't work properly.
I was doing some searches on the Apache documentation and found this: [http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html#allow](http://httpd.apache.org/docs/2.2/mod/mod_authz_host.html#allow)
I'll continue to try it with the * as a wildcard, but that page seems to indicate that is not how it is done, unless it is out of date or something?

---

### Post by (-NINJ4-) on 2009-12-01
> **HighCommander540 said:**
> **_*edit*_** So I think I figured out how to fix it. I was having the same problem as you were. For something similar. Please, post your entire configuration. And I might be able to help.
Sorry for the double post, here's my entire config file httpd.conf as I am using it currently, without any IP stipulations:

```
<Directory /var/www>
        AuthName "home control"
        AuthType Basic
        AuthUserFile /etc/apache2/.htpasswd
        Require valid-user
</Directory>
```


Here's the httpd.conf I am trying to get to work:
```
<Directory /var/www>
        AuthName "home control"
        AuthType Basic
        AuthUserFile /etc/apache2/.htpasswd
        Require valid-user
        Allow from 10.1.1
        Satisfy Any
        Order Allow,Deny
</Directory>
```

---

### Post by HighCommander540 on 2009-12-01
Ok, so that is your entire config? 

You don't have an entry like this?:

```
<Directory />
       Options FollowSymLinks Multiviews
       AllowOverride None
</Directory>
```

---

### Post by (-NINJ4-) on 2009-12-02
I have no such section in my httpd.conf file, no.

---

### Post by HighCommander540 on 2009-12-02
> **(-NINJ4-) said:**
> I have no such section in my httpd.conf file, no.

Ok, well. Have you checked to see if the /etc/apache2/sites-available/default file is interfering?

---

### Post by (-NINJ4-) on 2009-12-02
Ah, I hadn't looked there, yes I found the following:
```
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
```Aside from these sections I don't see anything that would seem to be related to what we were discussing.  What do I have to do regarding these sections to get this to work?  Thanks for the help, HighCommander :)

---

### Post by HighCommander540 on 2009-12-07
> **(-NINJ4-) said:**
> Ah, I hadn't looked there, yes I found the following:
```
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
```Aside from these sections I don't see anything that would seem to be related to what we were discussing.  What do I have to do regarding these sections to get this to work?  Thanks for the help, HighCommander :)

Hey, dude sorry I didn't respond to your post earlier. I found out when I was talking earlier that what the problem is. You have your settings setup in the way that it auto-allows access from everywhere. Which I had to (its the Ubuntu default). So you need to change a few things to make it so it wont.

First, you need to change your default file. To look like this:

```
        <Directory />
                Options FollowSymLinks
                AllowOverride None
                Deny from All
        </Directory>
        <Directory /var/www/>
                AuthName "home control"
                AuthType Basic
                AuthUserFile /etc/apache2/.htpasswd
                Require valid-user
                Allow from 10.1.1
                Satisfy Any
                Order Allow,Deny
        </Directory>
```

Second, you actually need to get rid of the entry that you have set up in your httpd.conf file. The thing is Ubuntu has it setup to use the site-avaiable files. And it is a much better managment system. It also allows or easy virtual hosts. After that it should work if it doesn't post again.

---

### Post by (-NINJ4-) on 2009-12-08
No worries, I'm just glad someone cares enough to help at all. :D

[edit]
Thank you for being awesome, everything worked perfectly once I actually read your post!

---

### Post by HighCommander540 on 2009-12-08
> **(-NINJ4-) said:**
> No worries, I'm just glad someone cares enough to help at all. :D

[edit]
Thank you for being awesome, everything worked perfectly once I actually read your post!

Your welcome, I am glad I could help. Yeah, I couldn't figure out my problem either. It took me awhile, but I found a wiki on Ubuntu on this issue. Sadly I can't find it now.

I can explain the whole thing how it works if you want...

---

