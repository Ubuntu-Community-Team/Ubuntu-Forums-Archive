---
title: "PHP not parsing after server upgrade (8.04 to 12.04)"
date: 2013-01-24
forum: Server Platforms
---

### Post by tengri on 2013-01-24
I've been using my server set up for years running PHP scripts but after finally getting round to a server upgrade the PHP files that used to open correctly are now downloaded instead.

Have had a search around already but many solutions are old or don't fix my problem.

I have even tried removing and reinstalling PHP5 but with no success, although I'm not convinced I'm doing that correctly.

Any other help appreciated.

---

### Post by louis vitton on 2013-01-24
Is it working in command line but just not in the browser?
Or is it both?

please try 
```
php -r 'phpinfo();'

php -v

```for the phpinfo command you will get also of info if it works
for php -v please post the result so we can see if it is the latest version.

---

### Post by tengri on 2013-01-24
> **louis vitton said:**
> Is it working in command line but just not in the browser?
Or is it both?

please try 
```
php -r 'phpinfo();'

php -v

```for the phpinfo command you will get also of info if it works
for php -v please post the result so we can see if it is the latest version.

It works OK in command line, just the browser has problems. I get all the info when I try php -r 'phpinfo();'

For php -v:

> PHP 5.3.10-1ubuntu3.5 with Suhosin-Patch (cli) (built: Jan 18 2013 23:45:59)
Copyright (c) 1997-2012 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2012 Zend Technologies

Thanks

---

### Post by steeldriver on 2013-01-24
DISCLAIMER: I'm pretty much a php n00b (just have it running on a test server to play with)  

Are the scripts in a user directory? or in /var/www? I *think* there's been a change in the default conf that disable execution of user php (for security reasons presumably)

---

### Post by tengri on 2013-01-24
> **steeldriver said:**
> DISCLAIMER: I'm pretty much a php n00b (just have it running on a test server to play with)  

Are the scripts in a user directory? or in /var/www? I *think* there's been a change in the default conf that disable execution of user php (for security reasons presumably)

Yes they are in a user directory. Do you know how to get round that security? It is only a test server for playing around with things before uploading to my web host.

---

### Post by Doug S on 2013-01-24
edit /etc/apache2/mods-available/php5.conf
there are notes in the file saying what to do.

---

### Post by tengri on 2013-01-24
Sorted - Thanks all for your help!

---

