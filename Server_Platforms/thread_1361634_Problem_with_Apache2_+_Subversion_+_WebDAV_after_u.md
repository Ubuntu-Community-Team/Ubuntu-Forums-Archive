---
title: "Problem with Apache2 + Subversion + WebDAV after upgrade"
date: 2009-12-22
forum: Server Platforms
---

### Post by pontusn on 2009-12-22
I recently upgraded from Ubuntu Server 9.04 (Jaunty Jackalope) to 9.10 (Karmic Koala) with the 'sudo do-release-upgrade' command. Everything went ok, I thought. The problem is that I can't start the Apache2 server anymore. I get this error message:

apache2: Syntax error on line 203 of /etc/apache2/apache2.conf: Syntax error on line 2 of /etc/apache2/mods-enabled/dav_svn.load: Cannot load /usr/lib/apache2/modules/mod_dav_svn.so into server: /usr/lib/libsvn_subr-1.so.1: undefined symbol: sqlite3_config

It seems as if the different dynamic libraries related to Subversion, Apache2 and WebDAV aren't compatible anymore and therefore I get a link error. I haven't built and installed anything from source, everything come from stable packages.

I have checked dependencies of installed packages, tried to reinstall various packages and things like that. I don't have any more good ideas other than reinstall the machine from scratch.

Does anyone have any clue what went wrong here and how to fix it?

BR
Pontus

---

### Post by hessiess on 2009-12-22
You could try renaming your Apache configuration file then restart/reinstall Apache so that it creates a new config file an work from there.

With servers, if its working, don't upgrade/reinstall unless you have a good reason for doing so. If you do need to upgrae, its always better to reinstall than to upgrade, which isnt any more difficult assuming you have your data stored on a different partition to the OS.

---

