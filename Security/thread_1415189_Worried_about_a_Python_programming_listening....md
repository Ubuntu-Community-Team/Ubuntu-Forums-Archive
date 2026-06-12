---
title: "Worried about a Python programming listening..."
date: 2010-02-24
forum: Security
---

### Post by Bill Zimmerly on 2010-02-24
Here is what I get when I enter the command:

$ lsof -i | egrep LISTEN
.
conduit   4554 bzimmerly   19u  IPv4  15880       TCP *:3400 (LISTEN)
.
Etc.

All of the reported listeners were expected by me other than this one. So, I entered this to get more information about the program:

$ ps -ef | egrep conduit
1000      4554  4191  0 Feb23 ?        00:00:35 /usr/bin/python /usr/bin/conduit -i

Does anyone know what program this is and why it is listening on my machine's port 3400?

Thanks for any help,
- Bill  :confused:

---

### Post by gombadi on 2010-02-24
> 
$ ps -ef | egrep conduit
1000 4554 4191 0 Feb23 ? 00:00:35 /usr/bin/python /usr/bin/conduit -i

Does anyone know what program this is and why it is listening on my machine's port 3400?


Do the following to see what package the file is from. Then have a look at the package description to get an idea of what is does.

```

dpkg -S /usr/bin/conduit

and then

apt-cache show <package name>

```

---

### Post by Bill Zimmerly on 2010-02-24
Thanks gombadi!

Here's what I got:

bzimmerly@hp:~$ dpkg -S /usr/bin/conduit
conduit: /usr/bin/conduit

bzimmerly@hp:~$ apt-cache show conduit
Package: conduit
Priority: optional
Section: universe/devel
Installed-Size: 4480
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Jose Carlos Garcia Sogo <jsogo@debian.org>
Architecture: all
Version: 0.3.15-1ubuntu3
Depends: python (>= 2.5), python-support (>= 0.7.1), python-gtk2, python-pygoocanvas (>= 0.9), python-dbus, python-vobject, python-gnome2 (>= 2.22.0), python-glade2, python-gnome2-desktop (>= 2.22.0-1), python-pysqlite2, scrollkeeper, python-webkitgtk, python-feedparser, python-gobject (>= 2.15.3)
Recommends: python-simplejson, python-gpod
Suggests: ffmpeg, mencoder
Filename: pool/universe/c/conduit/conduit_0.3.15-1ubuntu3_all.deb
Size: 1626126
MD5sum: 2853ecc9b837f0bdcf0526fa0f72a709
SHA1: 403e47caa5a9752812a2dc8103858b4621b83199
SHA256: 1f363c459ab5ba9e3bd01af72ad3c310013c54097eec79fdca40e75f2ed717ac
Description: synchronization tool for GNOME
 A syncronization tool for GNOME which allows the user to take their
 emails, files, bookmarks, and any other type of personal information
 and synchronize that data with another computer, an online service, or
 even another electronic device.
 .
 Conduit manages the synchronization and conversion of data into other
 formats. For example, conduit allows you to;
  * Synchronize your tomboy notes to a file on a remote computer
  * Synchronize your emails to your mobile phone
  * Synchronize your bookmarks to delicious, gmail, or even your own webserver
  * and many more..
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

Hmmm ... I'll have to think about this one for a while. Off hand, I don't remember setting up any such synchronization, but at least it's good to know that it is a valid Ubuntu package!

Thanks again!
- Bill

---

