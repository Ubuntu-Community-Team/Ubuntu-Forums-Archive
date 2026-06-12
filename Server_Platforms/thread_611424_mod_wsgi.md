---
title: "mod_wsgi"
date: 2007-11-12
forum: Server Platforms
---

### Post by portalcake on 2007-11-12
I am currently using 7.10 Server edition with apache2 and mod_python for web development.  I want to play around with mod_wsgi for apache, but it isn't already precompiled for me (like mod_python), so I can't just apt-get it.  I saw that there was a [[color=blue]Debian package[/color]](http://packages.debian.org/unstable/python/libapache2-mod-wsgi), and I know Ubuntu is debian-based. The files that this package installs match up with my current directory structure and it looks like it would work :)
The other option would be to compile mod_wsgi myself, which would require installing development packages on my server machine -- which I don't have a problem with, it just requires more work.
Also, it would be great to make mod_wsgi retrievable via apt-get, but alas I don't have the knowledge of contributing like that (yet).
Comments/suggestions?

---

### Post by foxylad on 2007-11-13
I use mod_python, but probably ought to get into mod_wsgi one of these days. 

I think mod_wsgi is still under fairly active development, so I'd compile from the latest source. Installing the build tools (apt-get install build-essential) isn't a big deal, and if you are concerned about security on a production server you can uninstall them easily afterwards.

---

### Post by portalcake on 2007-11-13
I wound up adding debian sid to my sources.list and then grabbing the mod_wsgi 1.2 package, which worked great.  Now I just have to figure out if I want to use apache2 + mod_wsgi or some other server setup.  :-)

---

