---
title: "php5-imap and apache2-common both do something with a php imap module?"
date: 2007-07-23
forum: Server Platforms
---

### Post by D43m0n on 2007-07-23
Hi everyone,

I'm running Feisty Fawn with apache2 and php5 installed. I'd like to use this server as a webmail server with IMP. In order to get IMP working, I need a working php5-imap setup.

When I enable the imap module with a2enmod, I can choose the imap module from the presented list. When I reload apache2 however, I get the following error message:

 /etc/init.d/apache2 force-reload
 * Forcing reload of web server (apache2)...                                                                            apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/imap.load: Cannot load /usr/lib/apache2/modules/mod_imap.so into server: /usr/lib/apache2/modules/mod_imap.so: cannot open shared object file: No such file or directory
                                                                                                                 [fail]

When I check the location mentioned in the /etc/apache2/mods-enabled/imap.load file, there is no such file in /usr/lib/apache2/modules called mod_imap.so or anything else that resembles an imap module. That's weird...
When I check which package put that module file in the available modules directory it turns out to be: 

dpkg --search imap.load
apache2-common: /etc/apache2/mods-available/imap.load

That's funny, I thought I installed php5-imap that (according to its name) should install something like imap support for php5. But when I check the contents of that php5-imap package, it's doing something else:

dpkg --listfiles php5-imap
/.
/usr
/usr/lib
/usr/lib/php5
/usr/lib/php5/20060613+lfs
/usr/lib/php5/20060613+lfs/imap.so
/usr/share
/usr/share/doc
/usr/share/doc/php5-imap
/usr/share/doc/php5-imap/copyright
/usr/share/doc/php5-imap/changelog.Debian.gz

OK, still a bit strange to do it in this way, but I thought I'd try to load that shared object file into apache, so I edited /etc/apache2/mods-available and changed the location of that non-extisting file with this .so file, and restarted apache:

/etc/init.d/apache2 start
 * Starting web server (apache2)...                                                                                     apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 2 of /etc/apache2/mods-enabled/imap.load: Cannot load /usr/lib/php5/20060613+lfs/imap.so into server: /usr/lib/php5/20060613+lfs/imap.so: undefined symbol: file_globals
                                                                                                                 [fail]

That doesn't seem to be any better either...

I've searched the forums and googled around, but I can't find anything that even looks close to the problem I'm experiencing. My conclusion must be that I'm doing something terribly wrong, but I can't figure out what it is I'm doing wrong...

Does anyone have an idea?

Thanks in advance,

Dennis

---

### Post by paulpas on 2008-06-04
Any update on this?  I'm experiencing the same issues and I'd like to avoid compiling if I can.

---

