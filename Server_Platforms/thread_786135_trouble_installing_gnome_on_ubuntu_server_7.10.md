---
title: "trouble installing gnome on ubuntu server 7.10"
date: 2008-05-07
forum: Server Platforms
---

### Post by wparsons on 2008-05-07
I recently tried to install gnome(ubuntu-desktop package), but no matter what I try I get an error on 4 packages.  These are the 4 trouble makers:

 acpid
 ubuntu-desktop
 acpi-support
 powermanagement-interface

If I try to reconfigure via dpkg-reconfigure, it says the package is broken or not fully installed.  If I try to install any one of the 4 through either aptitude or apt-get, I get the same error.  I've run apt-get clean, update, etc but all to the same result.

Now, gnome runs just fine even with that, and power management seems fine(monitor powers down after the set time, everything is set to stay powered up).  I find that the errors are sometimes interfering with installing other packages/updates.

Any help would be greatly appreciated.

---

### Post by quelx on 2008-05-08
Have you tried re-installing or downloading the packages and installing them in two steps?

Try removing the *.deb files in /var/cache/apt/archives/

then one of these

```
sudo apt-get reinstall ubuntu-desktop
```
or
```
sudo apt-get -d ubuntu-desktop
sudo apt-get install ubuntu-desktop
```

---

### Post by dmizer on 2008-05-08
the server install is tuned to server specific application, and does not lend itself well to gui install.  if you must have a gui, you should install full ubuntu, and then install whatever server packages you need after that.

if you want a web (lamp) server in your ubuntu, it's a simple matter of performing the following command:
```
sudo aptitude install lamp-server
```

it is similarly painless to install any number of other server based necessities once you have installed ubuntu.

that said, if your computer is a dedicated server, you should stick to a command line interface because there are not many gui interfaces for configuring server applications (since, wisely, not many dedicated servers have gui).  so, you'll end up using the command line anyway.

---

### Post by wparsons on 2008-05-08
It is a dedicated server(its my development testing server), but a relative is temporarily needed a home computer, so they're using it.  I didn't have time to do a full installation of ubuntu home, so I just tried the package.

I haven't tried all the suggestions yet, but I'll try the ones I haven't tried right now.

---

