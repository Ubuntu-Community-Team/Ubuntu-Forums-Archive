---
title: "Can't remove aolserver4"
date: 2009-08-03
forum: Server Platforms
---

### Post by Jago6060 on 2009-08-03
Title pretty much says it all.  I messed up during a Project-Open install, and just to make me feel better, I wanted to do a clean reinstall, but I can't remove aolserver4.  Any ideas why?

```

root@compaq-ubuntu8:/# apt-get remove aolserver4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev automake1.7 debhelper intltool-debian x11proto-kb-dev
  m4 po-debconf autoconf libxdmcp-dev python2.5-dev python2.4 xtrans-dev
  intltool x11proto-core-dev gettext fdupes autotools-dev libxt-dev
  x11proto-input-dev libpthread-stubs0-dev libtimedate-perl libxau-dev
  dpkg-dev libpthread-stubs0 libncurses5-dev html2text libx11-dev
  libxcb-xlib0-dev patch libxcb1-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  aolserver4
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1573kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 114848 files and directories currently installed.)
Removing aolserver4 ...
 * Stopping web server aolserver4                                               aolserver4-nsd: no process killed
                                                                         [fail]
invoke-rc.d: initscript aolserver4, action "stop" failed.
dpkg: error processing aolserver4 (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 aolserver4
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Thirtysixway on 2009-08-03
hm.  You could try stopping it first, and see if any processes of it are still running and kill those processes, then try removing it.

---

### Post by Jago6060 on 2009-08-04
> **Thirtysixway said:**
> hm.  You could try stopping it first, and see if any processes of it are still running and kill those processes, then try removing it.

It won't let me stop it.  I do...
```
service aolserver4 stop
```

and it hangs for a bit then fails.

---

### Post by kayvortex on 2009-08-04
Do you have root privileges? It looks like you're running a terminal as root (which isn't really a good idea); so you should have the necessary privileges, but can you make sure. (You could enter the command "whoami" to make sure).

Have there been any problems with that init script when you shut your system down? Maybe post it's contents and also
```
ls /etc/rc0.d
```

I would have said that the easiest thing to do would be to remove the init script from your system boot-up procedure and just restart your system, but if you're having problems stopping it, then maybe your system will have too.

---

