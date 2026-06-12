---
title: "awstats icon"
date: 2010-08-19
forum: Server Platforms
---

### Post by MatsB on 2010-08-19
Hi,

The icons are not showing up on my awstats webpage. Everything els seems to be working just fine. Any ideas?

Running on Ubuntu 10.04
Installed with apt-get install awstats

server:~$ ls -l /usr/share/awstats/

drwxrwxr-x 9 root root 4096 2010-08-15 14:45 icon
drwxr-xr-x 5 root root 4096 2010-08-15 14:45 lang
drwxr-xr-x 2 root root 4096 2010-08-15 14:45 lib
drwxr-xr-x 2 root root 4096 2010-08-15 14:45 plugins

awstats config file
/etc/awstats/awstats.conf

#DirIcons="/awstats-icon"
DirIcons="/usr/share/awstats/icon"
...

---

### Post by sanderd17 on 2010-08-19
try the firebug add-on (in firefox) to find your error.

---

### Post by MatsB on 2010-08-20
> **sanderd17 said:**
> try the firebug add-on (in firefox) to find your error.

Firebug didn't help much. Firebug only acknowledge that the path is correct as specified in the awstats.conf file. 

This is one example i html code.
<img width="6" height="37" align="bottom" title="Unique visitors: 4" alt="Unique visitors: 4" src="/usr/share/awstats/icon/other/vu.png">

---

### Post by schapman43 on 2011-01-23
I realize this is a little old but did anyone find a solution?

---

### Post by Ceyx on 2011-03-12
Here is a solution, if you are using apache2.   Add this to your default configuration in /etc/apache2/sites-available:

# This is to permit URL access to scripts/files in AWStats directory.
# 
	<Directory "/usr/share/awstats">
	Options None
	AllowOverride None
	Order allow,deny
	Allow from all
	</Directory> 

# end edit

Use at your own risk - works for me. 

Ciao !

---

