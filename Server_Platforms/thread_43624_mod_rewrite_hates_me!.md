---
title: "mod_rewrite hates me!"
date: 2005-06-22
forum: Server Platforms
---

### Post by stack on 2005-06-22
I have Hoary installed along with apache2 and I am trying to setup [TRAC](http://projects.edgewall.com/trac/).  Part of the setup is to enable mod_rewrite, so I did the following

```
sudo a2enmod rewrite
sudo /etc/init.d/apache2 force-reload
``` 

All of my rewrite rules are ignored.  I've tested the regular expressions in perl and they still do not seem to work.  My rules look like this:

```
RewriteEngine On

RewriteLog /var/log/apache2/rewrite.log
RewriteLogLevel 9

RewriteRule ^/projects/+$                       /projects/index.cgi [L]
RewriteCond /var/trac/$1                        -d

RewriteRule ^/projects/([[:alnum:]]+)(/?.*)     /projects/trac.cgi$2 [S=1,E=TRAC_ENV:/var/trac/$1]
RewriteRule ^/projects/(.*)                     /projects/index.cgi

Alias /trac "/usr/share/trac/htdocs"
```

Even the first one, which is quite simple, doesn't work.  Also, the rewrite.log files does get created, but never written to, no matter what the log level.

Can someone please help me out with this?

---

### Post by jdonnell on 2005-06-23
Start with a simple rewrite rule and make sure that mod_rewrite is working in that folder. We'll look at your rewrite rules once we know that mod_rewrite is working in that folder.

---

### Post by netjackal on 2005-08-12
[QUOTE=stack]I have Hoary installed along with apache2 and I am trying to setup [TRAC](http://projects.edgewall.com/trac/).  Part of the setup is to enable mod_rewrite, so I did the following

```
sudo a2enmod rewrite
sudo /etc/init.d/apache2 force-reload
``` 

All of my rewrite rules are ignored.  I've tested the regular expressions in perl and they still do not seem to work.  My rules look like this:

```
RewriteEngine On

RewriteLog /var/log/apache2/rewrite.log
RewriteLogLevel 9

RewriteRule ^/projects/+$                       /projects/index.cgi [L]
RewriteCond /var/trac/$1                        -d

RewriteRule ^/projects/([[:alnum:]]+)(/?.*)     /projects/trac.cgi$2 [S=1,E=TRAC_ENV:/var/trac/$1]
RewriteRule ^/projects/(.*)                     /projects/index.cgi

Alias /trac "/usr/share/trac/htdocs"
```

Even the first one, which is quite simple, doesn't work.  Also, the rewrite.log files does get created, but never written to, no matter what the log level.

Can someone please help me out with this?[/QUOTE]
 I had the same problem as well until I discovered what was behind the sites-enabled and sites-disabled directories. What happens is that the default 'site' has a virtualhost in it .. so all your request are being directedto within the virtualhost's configurations. You would need to stick your rewrite directives within the virtualhost.

So what I did was to make a copy of the file default under the sites-available directory (called it 'mydomain' or something). Added my rewrite configs to the new mydomain file. ran a2dissite default .. so that the default site is disabled. then ran a2ensite mydomain. worked perfectly after that

---

### Post by schauba on 2006-01-19
Thanks for this post.  I have been beating my head against the monitor for the last 24 hours wondering why some changes to *apache2.conf *applied and other didn't.  As soon as I commented out the **Include **statement for virtual hosts, everything worked as expected.

---

### Post by MJN on 2006-01-19
As I was reading this thread I was getting feelings of deja vu as I had a similar 'head scratching' oddity myself.

Well done Netjackal for sussing out the issues, however I'd like to explore this a little further to get my head round it...

My particular problem was related to the correct MIME handling for files without extensions. I required the inclusion of the MIME_MAGIC module and whilst I activated it using a2enmod which, in turn, put the necessary Include into apache2.conf it still didn't seem to want to play. I ended up putting the additional config into my virtual site config (the default one as it happens).... but WHY???

It was my understanding, based on plenty of configuration of non-Debain Apache config files (i.e. the use of the non-modularised httpd.conf), that all directives **oustide of site-specific config in the *virtual* sections** were essentially regarded as the 'default' and that only if the directives were repeated in an altered fashion inside a *virtual* directive would they be overridden.

Basically, in case my waffling has blurred my intended point, why does the config need entering in to the virtual site-specific container, and not merely allowed in the main config file to thus apply to **all** sites?

So why is the Debian modularised approach apparently breaking this philosophy? Of course, it isn't for the vast majority of the configuration, only seemingly for things I'm/we're adding! This naturally points the finger back to the user... so as a confused one can anyone shed any light?

Mathew

---

