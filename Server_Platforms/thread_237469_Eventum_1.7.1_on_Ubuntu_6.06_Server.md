---
title: "Eventum 1.7.1 on Ubuntu 6.06 Server"
date: 2006-08-16
forum: Server Platforms
---

### Post by bricktop on 2006-08-16
[B]Hi There,

I am trying to install eventum 1.7 on my Ubuntu 6.06 server. I downloaded the tarball, extracted it, read the install and readme files for install instruction but all it says is that it is easy. There is no configure file in the directory so ./configure just returns "./configure: No such file or directory" make returns "make: *** No targets specified and no makefile found.  Stop." and make install returns "make: *** No rule to make target `install'.  Stop."

I have no idea what to d and as you may be able to tell I am a bit of a noob.

The contents of the README is as follows:
[/B]
Eventum Issue Tracking System
=============================

Eventum is a user friendly and very flexible issue tracking system, that can
be used by a support department to track incoming technical support requests,
or by a software development team to quickly organize tasks and bugs. Eventum
is used by MySQL AB for its support needs, and has allowed us to increase our
response times by leaps and bounds.

It is being released as a GPL project to gather community involvement in its
development. The BitKeeper source tree is available from the following URL:

  [http://mysql.bkbits.net/](http://mysql.bkbits.net/)

We have also provided mailing lists related to Eventum, both for users and
potential developers at [http://lists.mysql.com/:](http://lists.mysql.com/:)

  [email]eventum-users@lists.mysql.com[/email]
  [email]eventum-devel@lists.mysql.com[/email]

We welcome you to send patches, bug fixes and other contributions to Eventum.
Please see the CONTRIB file for more details into how to do so.

João Prado Maia & Bryan Alsdorf
The Eventum Team
MySQL AB
  

**The INSTALL File Contents**

Installation Process
====================

Installation is pretty simple and quick. Eventum already bundles the libraries
that it needs to work properly:

- JpGraph 1.5.3 (last GPL version)
- Smarty 2.3.0 ([http://smarty.php.net](http://smarty.php.net))
- PEAR packages
- dTree 2.0.5 ([http://www.destroydrop.com/javascript/tree/](http://www.destroydrop.com/javascript/tree/))
- dynCalendar.js ([http://www.phpguru.org/dyncalendar.html](http://www.phpguru.org/dyncalendar.html))
- overLIB 3.5.1 ([http://www.bosrup.com/web/overlib/](http://www.bosrup.com/web/overlib/))
- A few other small javascript libraries

Anyway, all you should have to do is place the Eventum files in a directory that
is viewable from the web, and open it up with your browser. Eventum should
redirect you to the installation screen, and it will try to guess some of
required parameters, like path in the server and etc.

  [http://yourserver.com/eventum/](http://yourserver.com/eventum/)

If Eventum's installation script finds that it needs a few directories or
permissions changed, it will print the warnings before actually displaying
the installation screen. So just fix what it says it's wrong/missing and
everything should go well.

After the installation is done, you should go and take all of the available
privileges from the '/setup' directory, so other people are not allowed to
go in there and mess with your configuration.

IMPORTANT: If you already have an installation of Eventum, please read the
UPGRADE file.

IMPORTANT: If you are having trouble getting Eventum to work, please read
the trouble shooting section of the FAQ file.


"INSTALL" [readonly] 235L, 10149C                                                                          

[B]I tried searching for a bout 3 hours and all i get is the same as the README and INSTALL files.

Any Ideas
[/B]

---

### Post by Uluen on 2006-08-16
I read really quick through the docs, didn't see anything about compiling anything?
> Anyway, all you should have to do is place the Eventum files in a directory that
is viewable from the web, and open it up with your browser.

---

### Post by dbarbour on 2006-08-16
Uuummm... yeah. Eventum is a web-based application. Place the files in a folder below the document root and visit that folder with your favorite web browser. You should know what to do after that. Simple.

---

