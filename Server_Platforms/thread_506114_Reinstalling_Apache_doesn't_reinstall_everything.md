---
title: "Reinstalling Apache doesn't reinstall everything?"
date: 2007-07-21
forum: Server Platforms
---

### Post by siDDis on 2007-07-21
I was showing a friend of mine how reliable Linux is today.

I was going to demonstrate an example where I deleted a file(/etc/init.d/apache2) and show him the packet manager easily reinstalled everything again.

However this didn't happen, the script file never comes back no matter what I do...is it not possible to reinstall the script file?

---

### Post by elst on 2007-07-21
It may be that you didn't specify the exact package required. FWIW, "dpkg -S <full/path/of/file>" will tell you the source package for a given file:

```

me@mywebserver:~$ dpkg -S /etc/init.d/apache2 
apache2.2-common: /etc/init.d/apache2

```

EDIT: I was curious and actually tried your experiment on a test machine, with the same result. I guess that since the package manager knows that it already installed the file, it won't put it back, even with the "--reinstall" option, and I couldn't see an option to force this. You can extract individual files from packages, and copy them into place yourself, though, if there isn't a better way of doing this.

---

### Post by siDDis on 2007-07-21
Well, I've tried that :)

There seems to be two packages for Apache2
However if I install the Apache2 not common packageI alway get that HTTPD not found error :/

---

### Post by koenn on 2007-07-21
> **siDDis said:**
> I was showing a friend of mine how reliable Linux is today.

I was going to demonstrate an example where I deleted a file(/etc/init.d/apache2) and show him the packet manager easily reinstalled everything again.

However this didn't happen, the script file never comes back no matter what I do...is it not possible to reinstall the script file?
depends on "no matter what i do" includes. 
When you delete a config file, you haven't uninstalled the (apache2) package, so if you ask the package manager to reinstall it, it will just go "package is already installed & latest version", so it doesn't do anything; your config file doesn't come back. 

You might try ```
dpkg-reconfigure apache2
```. This will reconfigure an installed package, and probably put a new, default, config file to replace the missing file. 

On a side note : it's never a good idea to do a live demo in public  that you haven't tried first.

---

### Post by elst on 2007-07-21
I solved it this way:

```

mkdir ~/recover
dpkg -x /var/cache/apt/archives/apache2.2-common_2.2.3-3.2build1_i386.deb ~/recover
sudo cp ~/recover/etc/init.d/apache2 /etc/init.d/apache2
rm -fr ~/recover

```

This relies on the fact that APT keeps a copy of every package that you install in /var/cache/apt/archives/.

Apache isn't configured with debconf, so unfortunately dpkg-reconfigure doesn't do anything with apache2.

---

### Post by henryhynd on 2007-07-21
Something I just learned today from having to reinstall apache and php5, I'm not sure if this applies to you but if you go:

> sudo aptitude purge apache2

aptitude will delete everything to do with your apache2 installation (standard install that is, prob not modifications) and tell the DB it's not there anymore.

you can then do:
> sudo aptitude install apache2

which will then give you a fresh install with the standard settings. This is how i got my webserver up and running after a bogged up email server installation earlier today.

and i have to agree with koenn: never a good idea to do public demos!

hope this helps (next time)

Henry

---

### Post by almostlinux on 2007-07-21
apache2-common

---

### Post by siDDis on 2007-07-22
Great, I got it work again now thanks to you guys! :)

---

