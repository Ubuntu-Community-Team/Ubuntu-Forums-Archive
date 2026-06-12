---
title: "Enabling CGI in all /var/www subdirectories (Apache, LAMP)"
date: 2011-01-05
forum: Server Platforms
---

### Post by happysinger on 2011-01-05
Hi there,

I am trying to set up my local development environment to mimic the behaviour of my webhost: namely executing *.cgi files as CGI scripts, regardless of their location.

If I'm not mistaken, the default setup of Apache on Ubuntu has this set up for /usr/lib/cgi-bin only.

I have tried adding +ExecCGI to the /var/www directory settings in /etc/apache2/sites-enabled/000-default.

I have also tried AddHandler cgi-script .cgi in the same <directory> block.

Both to no avail. Could someone advise me what I should try next?

Thanks in advanks.

---

### Post by happysinger on 2011-01-05
I might add that I have symlinks in /var/www pointing to directories in my development directory under /home/user, so if that will make a difference, please let me know too!

---

### Post by happysinger on 2011-01-06
I'm slightly embarrassed to admit that I needed to add both 'AddHandler cgi-script .cgi' and 'ExecCGI' *at the same time*. Silly me.

However, I can only get *.cgi working if the file is actually located under /var/www, not symlinked there from its real location in my home directory. If anyone has a simple solution for this, I'd be keen to hear it (other than hardcoding my home dir into Apache config?)

---

### Post by wojox on 2011-01-06
See if this helps at all [http://ubuntuforums.org/showthread.php?t=1285019](http://ubuntuforums.org/showthread.php?t=1285019)

---

