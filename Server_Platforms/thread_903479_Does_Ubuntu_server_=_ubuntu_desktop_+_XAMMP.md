---
title: "Does Ubuntu server = ubuntu desktop + XAMMP?"
date: 2008-08-28
forum: Server Platforms
---

### Post by dimarec on 2008-08-28
I am completely new to Ubuntu and Linux.  I am trying to create a server for a virtual course based in moodle. (I assume that Ubuntu server is the way to go).I installed ubuntu desktop (8.04 x386) instead of Ubuntu server in my Windows based pentium machine.  Now I need to do the server thing.  Should I uninstall desktop or can I just keep the Ubuntu desktop and install the remaining applications included in XAMPP. I appreciate all comments!  (I don't know if edubuntu is better than ubuntu for moodle, but it looks to me like a different thing).
have a nice day!:)

---

### Post by cdenley on 2008-08-28
You can uninstall the desktop if you want, or just prevent it from starting automatically.
```

sudo update-rc.d -f gdm remove

```

Ubuntu server has no desktop environments. It is a minimal CLI install with whatever server configurations you select. You can always change different configurations options (server/desktop) regardless of which version you are running.
```

sudo tasksel

```

---

### Post by Nythain on 2008-08-28
all ubuntu-server really is, is a command line ubuntu install, using an smp kernel, with extra LAMP packages installed and config'd during the initial system install.

if you arent familiar enough with the command line, then you could just install a desktop system and either
A. install the lamp package
B. install each individual server app you need, like apache2, mysql, an ftp server, samba, etc

---

### Post by brad8266 on 2008-08-28
I just installed ubuntu server then installed the ubuntu desktop on top of it.

---

### Post by az on 2008-08-28
> **dimarec said:**
> Now I need to do the server thing.  Should I uninstall desktop or can I just keep the Ubuntu desktop and install the remaining applications included in XAMPP. I appreciate all comments!  

The desktop packages will not interfere with the server packages, nor will the server packages interfere with the desktop packages.

However, on a production server, you would follow best security practices and run a lean environment, and than means not having anything you don't need on the machine.

Also note that installing from the Ubuntu server CD and adding the desktop on top of that will leave with with the same thing as installing the desktop CD and adding the server packages on top of that but with one exception:

The server CD will default to the server kernel which is not optimized for the desktop.  You may find some hardware doesn't work properly (or even at all) with that kernel.  The solution to the problem is to install the linux-generic package which will install the desktop (generic) kernel.

Again, a non-production server will run fine with the generic kernel.

---

