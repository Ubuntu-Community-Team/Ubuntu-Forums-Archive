---
title: "managing services"
date: 2005-04-09
forum: Server Platforms
---

### Post by ke han on 2005-04-09
I am using the latest ubuntu 5.04.  I notice  this distro doesn't have commanbds like "chkconfig" and "service".
What are the recommended tools for managing services in a ubuntu/debian distro?
thanks, Jon

---

### Post by p!=f on 2005-04-09
I use wajig
```

[~] > wajig show wajig ;)
Package: wajig
Priority: optional
Section: universe/admin
Installed-Size: 364
Maintainer: Dirk Eddelbuettel <edd@debian.org>
Architecture: all
Version: 2.0.17-1ubuntu1
Depends: python (<< 2.5), python (>= 2.4), apt, python-apt
Suggests: wget, fping, debconf, reportbug, apt-move, dpkg-repack, alien, fakeroot, gkdebconf, lynx, python-gtk2, python-glade2, python-gnome2, gnome-terminal, base-config, gnome-tasksel, deborphan, vrms, sudo
Filename: pool/universe/w/wajig/wajig_2.0.17-1ubuntu1_all.deb
Size: 74598
MD5sum: 67a0dcdf9479c0772c90c05ab85f139d
Description: Simplified Debian package management front end
 Wajig is a single commandline wrapper around apt, apt-cache, dpkg,
 /etc/init.d scripts and more, intended to be easy to use and providing
 extensive documentation for all of its functions.
 .
 With a suitable sudo(1) configuration, most (if not all) package installation
 as well as creation tasks can be done from a user shell. Wajig is also
 suitable for general system administration.
 .
 Since release 2.0.0, a GUI command 'gjig' is also included in the package.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```
Wajig is primarily used for the package management but also offers easy and quick service management.
ie:
```
[~] > wajig restart samba
 * Stopping Samba daemons...                                                                                            [ ok ]
 * Starting Samba daemons..                                                                                             [ ok ]

```
Note that wajig is "sudo ready" so there's no need to use
```

sudo wajig <options>

```
For more infromations type
```

wajig help
wajig list-commands

```
for a complete commands listing
Also, taking a look at the [homepage](http://www.togaware.com/wajig) might be useful.

There could be other tools to work with but I'm happy with wajig so perhaps someone else can add some more.

For chkconfig consult update-rc.d manpages.

---

### Post by jdong on 2005-04-09
sysv-rc-conf is a nice, console, menu/checkbox-driven interface to configuring runlevels.

Do apt-get install sysv-rc-conf, then run sysv-rc-conf.

Remember that Ubuntu only uses Runlevel 2 by default.



BTW, the standard, somewhat primitive chkconfig-type tool for Debian is called **update-rc.d**.

---

