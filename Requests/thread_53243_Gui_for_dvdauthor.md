---
title: "Gui for dvdauthor"
date: 2005-07-30
forum: Requests
---

### Post by strikeforce on 2005-07-30
[http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)

This has a deb package.

[http://dvdstyler.sourceforge.net/](http://dvdstyler.sourceforge.net/)

Or this one.

[http://polidori.sourceforge.net/](http://polidori.sourceforge.net/)

I tried to install the deb package from dvd styler and this is the error generated.

```

marc@ubuntu:~$ sudo dpkg -i dvdstyler_1.4-1_i386.deb
Password:
Selecting previously deselected package dvdstyler.
(Reading database ... 86257 files and directories currently installed.)
Unpacking dvdstyler (from dvdstyler_1.4-1_i386.deb) ...
dpkg: dependency problems prevent configuration of dvdstyler:
 dvdstyler depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 dvdstyler depends on libwxgtk2.4 (>= 2.4.3.1); however:
  Version of libwxgtk2.4 on system is 2.4.2.6ubuntu1.
dpkg: error processing dvdstyler (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

```

I haven't had a look at upgrading those packages due to the fact I think that if I do install them I will have to install a hell of a lot of more packages.

---

### Post by mr_pouit on 2005-07-31
[QUOTE=strikeforce][http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)

This has a deb package.

[http://dvdstyler.sourceforge.net/](http://dvdstyler.sourceforge.net/)

Or this one.

[http://polidori.sourceforge.net/](http://polidori.sourceforge.net/)

I tried to install the deb package from dvd styler and this is the error generated.

```

marc@ubuntu:~$ sudo dpkg -i dvdstyler_1.4-1_i386.deb
Password:
Selecting previously deselected package dvdstyler.
(Reading database ... 86257 files and directories currently installed.)
Unpacking dvdstyler (from dvdstyler_1.4-1_i386.deb) ...
dpkg: dependency problems prevent configuration of dvdstyler:
 dvdstyler depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 dvdstyler depends on libwxgtk2.4 (>= 2.4.3.1); however:
  Version of libwxgtk2.4 on system is 2.4.2.6ubuntu1.
dpkg: error processing dvdstyler (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

```

I haven't had a look at upgrading those packages due to the fact I think that if I do install them I will have to install a hell of a lot of more packages.[/QUOTE]
 qdvdauthor is the only one in breezy :( :
[http://packages.ubuntu.com/breezy/graphics/qdvdauthor](http://packages.ubuntu.com/breezy/graphics/qdvdauthor)

---

### Post by rwabel on 2005-08-05
have a look at the following [wiki](https://wiki.ubuntu.com/DVDAuthoring)

Furthermore if you need newer versions, you can always try to compile it yourself

---

