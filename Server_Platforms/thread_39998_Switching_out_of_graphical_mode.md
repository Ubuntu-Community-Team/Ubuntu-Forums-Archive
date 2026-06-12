---
title: "Switching out of graphical mode?"
date: 2005-06-07
forum: Server Platforms
---

### Post by niyogi on 2005-06-07
Hi:

I'd like ubuntu to boot to console instead of X.  Where do I make the simple change so that it will do this?  Thanks in advance for your help!

Roj

---

### Post by lt_kije on 2005-06-07
Modifying your /etc/inittab and setting a lower runlevel (eg 2) will help; removing/altering the symlinks in /etc/rcX.d will help, too.

inittab uses the rc directories to find the shell scripts it uses to start your system. If you set inittab to runlevel 2, make sure the links in /etc/rc2.d that point to the XDM/KDM/GDM startup scripts are removed, eg:
```

$ sudo mv /etc/rc2.d/S40gdm /etc/rc2.d/X40gdm

```

I don't remember what the default names of the links are, but they're similar to the above.

HTH,
lt_kije

---

### Post by LordHunter317 on 2005-06-07
> **lt_kije]Modifying your /etc/inittab and setting a lower runlevel (eg 2) will help said:**
> No, it won't, this isn't Red Hat.

[quote]```

$ sudo mv /etc/rc2.d/S40gdm /etc/rc2.d/X40gdm

```No, this is bad advice.  If you don't want to run something at a runlevel, remove the symbolic link, don't change it's name.

Anyway, to stop GDM from loading at boot, just doing:```
sudo rm /etc/rc2.d/S99gdm
``` should suffice.  If the name is wrong, it will end in gdm, so find it in that directory.  To stop it on a running system, hit Ctrl-Alt-F1, login, and type:```
sudo /etc/init.d/gdm stop
```GDM may support shutting itself off from the login screen, but I don't know about that, as I don't use it.

---

### Post by tread on 2005-06-07
I dont remember, and I'm not on Linux, so I cant confirm but:

Isnt it possible to do this through the gdm configuration tool? Its there somewhere in the rightmost dropdown menu.

---

### Post by az on 2005-06-07
I do not htink that there is a switch which prevents gdm from running that you can set from within the package manager.  All you can do (and this is the simplest no-hassle way) is to remove the gdm package.

It will take the ubuntu-desktop meta-package with it, but you do not need this.

The more complicated way to do it would be to use update-rc to change the gdm setting in your runlevel.

---

