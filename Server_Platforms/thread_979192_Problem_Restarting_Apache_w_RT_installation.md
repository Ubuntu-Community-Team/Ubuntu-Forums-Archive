---
title: "Problem Restarting Apache w/ RT installation"
date: 2008-11-11
forum: Server Platforms
---

### Post by MaindotC on 2008-11-11
I'm following the [Request Tracker Hardy Installation Guide](http://wiki.bestpractical.com/view/UbuntuHardyInstallGuide) and I'm trying to follow the part where it says I have to restart apache and I'm getting the following error:
```

root@rt3-desktop:/etc/apache2/mods-enabled# /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 
* We failed to correctly shutdown apache, so we're now killing all running apache
processes. This is almost certainly suboptimal, so please make sure your system is 
working as you'd expect now!
apache2: Syntax error on line 298 of /etc/apache2/apache2.conf: Syntax error on line 42 
of /etc/apache2/sites-enabled/000-default: Could not open configuration file 
/etc/apache2/\xe2\x80\x9c/etc/request-tracker3.6/apache2-modperl2.conf\xe2\x80\x9d: 
No such file or 
directory

                                                                         [fail]


```

How can I fix this problem?  THanks!

---

### Post by cariboo on 2008-11-11
Have you checked to see what these errors are?

> Syntax error on line 298 of /etc/apache2/apache2.conf

and

> Syntax error on line 42 
of /etc/apache2/sites-enabled/000-default

Plus the missing configuration files 

> /etc/apache2/\xe2\x80\x9c/etc/request-tracker3.6/apache2-modperl2.conf\xe2\x80\x9d: 
No such file or 
directory



Jim

---

### Post by MaindotC on 2008-11-12
The configuration file, per the wiki, was supposed to have this pasted in it:
```

Include "/etc/request-tracker3.6/apache2-modperl2.conf"

```
The problem is that this is enclosed in quotes.  Unquote it and you're good until it says:
```

Unknown command: Enable

```
There's more to the output than that but if you just comment out the line that has "Enable rewrite" or just remove it altogether you're good.  I hope they fix that wiki.

---

