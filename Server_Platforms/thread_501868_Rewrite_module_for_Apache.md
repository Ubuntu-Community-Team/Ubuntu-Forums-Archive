---
title: "Rewrite module for Apache"
date: 2007-07-15
forum: Server Platforms
---

### Post by p_quarles on 2007-07-15
I'm trying to figure out how to use Apache, so that I can publish a small, low-traffic web site on my home server. The main page uses a PHP script to create a tabbing effect, so that all of the sub-pages appear as tabs, a la Firefox/Opera.

As a security/usability measure, I want to change the way the URLs appear in the client browser. Instead of "home/index.php?tabindex=1", for instance, I would like it to say "home/index.html/resume". 

I've already created an .htaccess file that should implement the rules I want. What I can't figure out is how to enable the rewrite module in Apache so that this file does something.

I've followed several tutorials I've found online to attempt to do this, but I'm getting errors with each one. Most recently, I added a "LoadModule" command to my httpd.conf file, and on a restart of Apache I was informed that this was an invalid command. Given all of this, I'm beginning to wonder if the Debian version of Apache is, perhaps, different from the others. 

On to my specific questions:
1) Does the Debian packaging of Apache come with different defaults than others?
2) If so, does anyone know of a good reference for Debian's implementation of Apache?
3) Would it be better to uninstall the current version and then compile Apache from source? This seems counterintuitive, but maybe it would help?
4) Is there a really good and comprehensive explanation out there (online or paper book) of exactly how the Apache config files work? If so, I would happily reconfigure everything manually to get it working.

Any help appreciated.

---

### Post by twistedtwig on 2007-07-16
I had issues doing something similar.. see my thread here: [http://ubuntuforums.org/showthread.php?t=498680](http://ubuntuforums.org/showthread.php?t=498680)

do ask questions if you don't understand or get it... although I don't know much more than I learnt but sure we / people can help

---

### Post by p_quarles on 2007-07-16
Hey, thanks for the reply. One thing I'm unclear on, though, you marked ```
a2enmod rewrite
``` as PHP code. So, before I try this, can you tell me if this is something I need to run in a PHP interpreter shell, or that I should include in a configuration file somewhere? 

I'm really starting to love PHP's capabilities, but I'm still very new to it, and am treading gingerly. 
[FONT=monospace][FONT=Tahoma][/FONT]  [/FONT]

---

### Post by p_quarles on 2007-07-17
Bump. I keep looking, but I'm still unable to find a working solution for this. I'm happy to share my .htaccess file if anyone wants to look it over.

---

### Post by az on 2007-07-17
sudo a2enmod rewrite
will enable apache2's rewrite module.  You need to restart the server to make it take effect

sudo apche2ctl restart

Both those need to be run from the command line.  You do not need to enable the module every time, the configuration is saved.  To dissable the module

sudo a2dismod rewrite

---

### Post by p_quarles on 2007-07-17
Thanks for the response. The "a2enmod" command tells me it's already enabled. I then tried disabling, reenabling, then restarting, but that had no effect either. 

I should mention, also, that I've tried various things with the site itself: manually typing each of the "actual" URLs that I want redirected (=no effect), manually typing the "new" URLs (=404 error).

Anyway, I'll post the .htaccess file in hopes that someone will spot a problem in there. This is posted in the same directory as the site itself, as I read I should do ```
 
RewriteEngine on
RewriteBase /

RewriteRule ^index\.php$ home.htm
RewriteRule ^index\.php?tabindex=0$ home.htm
RewriteRule ^index\.php?tabindex=1$ resume.htm
RewriteRule ^index\.php?tabindex=2$ webdesign.htm
RewriteRule ^index\.php?tabindex=3$ photos.htm
RewriteRule ^index\.php?tabindex=4$ links.htm 
```

From *everything *I've read, this should be correct. But, maybe not. Anyway, I saw what looked like a really comprehensive guide to working with AMP at the bookstore the other day, and I think that may be the solution.

---

