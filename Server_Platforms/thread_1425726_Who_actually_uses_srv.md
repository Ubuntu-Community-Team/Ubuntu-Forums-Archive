---
title: "Who actually uses /srv"
date: 2010-03-09
forum: Server Platforms
---

### Post by Lucky. on 2010-03-09
When I began running a web server, I was trying to find a place to put my web files.  Looking in the [filesystem hierarchy standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard), I noticed the "/srv" directory.  This looked fine, so I put my stuff there.

Then later I notice everybody putting their web files in "/var/www", as this seems to be the standard.  But the "/var" directory is full of logs and print spoolers and...I dunno, it just seems weird...like sticking my web site in a temp directory.

Likewise I share my network files in /srv/files.

Is it terribly dumb to put my web sites in /srv/www instead of /var/www?  What about shared network files?  Where do you guys put these things?

---

### Post by hessiess on 2010-03-09
It just seams to be a Ubuntu (Debian?) thing to put the web root in /var/www, Arch, for example uses /srv/http by default. If you are running any kind of shared hosting server keeping things in /var/www gets a bit messy. Its not difficult to change it to serve the files from any directory in the file system.

All the contents of my server, including some mysql databases, a bunch of SVN repositories and a few virtual websites are stored in various subdirectories of /srv

---

### Post by koenn on 2010-03-09
/srv is relatively new. According to the FHS, "/srv contains data served by this system" so /srv/www makes perfect sense for a webserver. 


/var is an older convention. It was meant for data that changes over time ("variable data") such as caches, spool, logs, all sorts of housekeeping and administration files, while "user data" would be in home directories,  ... but at some point, probably by lack of any other suitable place, /var become also the place to "data" that daemons would serve to other systems and users (such as databases and web pages). Granted, those files would also 'change over time' but I agree there's a difference between a website and a system log. 

Debian still defaults to /var for data, but probably most 'old' linuxes do (eg Redhat) and most documentation assumes /var for this sort of stuff as well, although I've seen examples of /srv as data directory in some (less traditional) applications' admin guides. 

I use both. /srv seems like an ideal place to keep samba shares, while mysql databases usually stay were they are, and for web, it varies ...
There's more to it that just convention - disks,  partitions, available space, backup strategy, etc ... sometimes need to be factored in as well.

---

### Post by capscrew on 2010-03-09
> **koenn said:**
>  ...
There's more to it that just convention - disks,  partitions, available space, backup strategy, etc ... sometimes need to be factored in as well.

+1

there is no advantage technically between [FONT="Courier New"]/var[/FONT] and [FONT="Courier New"]/srv[/FONT] (or any other).  I use [FONT="Courier New"]/smb[/FONT] for all of my Samba shared files.  It is also on a separate disk (spindle).

---

### Post by Lucky. on 2010-03-09
Ah beautiful.  Thanks everyone!

---

