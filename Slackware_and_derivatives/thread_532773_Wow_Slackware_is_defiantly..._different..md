---
title: "Wow Slackware is defiantly... different."
date: 2007-08-23
forum: Slackware and derivatives
---

### Post by blithen on 2007-08-23
The boot process is a lot different then Ubuntu.
You have to sign in , and the even do 'startx'
Which is kind of different.
So far I like it though.

---

### Post by Bachstelze on 2007-08-23
You can have X and your graphical login manager start automatically on boot if you want. Just edit /etc/inittab and change the default runlevel from 3 to 4 :)

---

### Post by RageOfOrder on 2007-08-24
> **HymnToLife said:**
> You can have X and your graphical login manager start automatically on boot if you want. Just edit /etc/inittab and change the default runlevel from 3 to 4 :)

Or you know... do it they way I do it :P

# ln -s /usr/bin/kdm /etc/rc3.d/S01kdm

symlink the login manager to runlevel 3.

---

### Post by Bachstelze on 2007-08-24
I advise against this, it is awfully unelegant... Moreover, typing *sudo telinit 3* is a nice way to stop X without going single-user, which no longer works after your little trick.

---

### Post by RageOfOrder on 2007-08-25
I'm an awefully unelegent linux user :)

I just tend to do a killall kdm if I want to kill X. It just brings me to the terminal login anyways, which is usually exactly where I want to be.

---

### Post by bonzodog on 2007-08-25
um...not just that, but..um..that command would not work on Slackware.
It's the BSD init system, and it's simply a combination of scripts under /etc/rc.d. 

There is no rc3.d dir and we do not use the levelled directories like the system V init does.

---

### Post by RageOfOrder on 2007-08-25
> **bonzodog said:**
> um...not just that, but..um..that command would not work on Slackware.
It's the BSD init system, and it's simply a combination of scripts under /etc/rc.d. 

There is no rc3.d dir and we do not use the levelled directories like the system V init does.

[img]http://omploader.org/vMmJs/snapshot19.png[/img]

---

### Post by WishingWell on 2007-08-25
> **HymnToLife said:**
> I advise against this, it is awfully unelegant... Moreover, typing *sudo telinit 3* is a nice way to stop X without going single-user, which no longer works after your little trick.

Four is limited, use 5 which is full user mode with X.

It's BSD init, not regular Unix. ;)

---

### Post by Bachstelze on 2007-08-25
Oh, my mistake, I haven't used it for a while. Anyway, switching between runlevels is the most convenient way of switching X on/off.

---

### Post by WishingWell on 2007-08-25
> **RageOfOrder said:**
> [img]http://omploader.org/vMmJs/snapshot19.png[/img]

Do a ln -s of that directory, he's right.

BSD init works differently, those symlinks are only there for compatibility.

---

### Post by RageOfOrder on 2007-08-25
> **WishingWell said:**
> Do a ln -s of that directory, he's right.

BSD init works differently, those symlinks are only there for compatibility.

Ok so he's right, and wrong.
The command still works, and that's really all that matters to me at this point.

But I will keep switching runlevels in mind for later on.

---

### Post by WishingWell on 2007-08-25
> **HymnToLife said:**
> Oh, my mistake, I haven't used it for a while. Anyway, switching between runlevels is the most convenient way of switching X on/off.

Definently, init 3 to go to regular user mode without X is something that confused the heck out of me when i installed Ubuntu and that didn't work.

Slackware is very easy if you get to know the system, it's also a lot easier than most other distros when it comes to fix or even find what is wrong.

That is also the reason why Patrick Volkerding doesn't include gnome in the distro, gconf is just a lesser copy of the register in windows, they both suck, one little thing and you will be locked out, the Slackware way is that everything has it's own file and all files are in /etc, Gnome does not follow the Unix ideal.

I really like your user name btw.

---

### Post by WishingWell on 2007-08-25
> **RageOfOrder said:**
> Ok so he's right, and wrong.
The command still works, and that's really all that matters to me at this point.

But I will keep switching runlevels in mind for later on.

init 3 will take ou to multiuser without X on any system that isn't Debian based, including Minix, Unix and Xenix but Debian wants to be soooo fancy and not use that.

That is a real downside to Ubuntu for me, i can't just put a bunch of scripts in one place and choose what will be run in different runlevels like i can do with pretty much every other distro, leaving your history behind you (in this case leaving Unix runlevels) behind you to try to become something else (the Ubuntu way is aiming for windows type of startup, where it is hell to even find something that starts up instead of just using it as a script in one place where all scripts have the name of their runlevel and are easily found, you can just do chmod -x on any of them and it won't run).

I think Ubuntu and Gnome have a strange aim, it will never be a better Window version than MS can produce so STOP TRYING.

---

### Post by bonzodog on 2007-08-26
interestingly enough, zenwalk does not have those directories, and yet I was under the impression that Zenwalk 4.6 was synced with the slack 12 tree.
it only has /etc/rc.d in there.

---

### Post by WishingWell on 2007-08-27
> **bonzodog said:**
> interestingly enough, zenwalk does not have those directories, and yet I was under the impression that Zenwalk 4.6 was synced with the slack 12 tree.
it only has /etc/rc.d in there.

I checked my old install and my new and my new doesn't have it, i think it's a VMWare thing, i checked the script and it does create them.

I checked under FreeBSD too and as soon as i had installed VMWare it created those symlinks (all point to ./ which would be rc.d).

There are probably other package installs that do the same thing though, but it's not really used by slackpacks.

---

### Post by saulgoode on 2007-08-29
The runlevel directories would also be created if the sysvinit-scripts pkg is installed. While no Slackware-native packages would use SysV-type config files (except maybe Dropline GNOME?), installing sysvinit permits Slackware to install a great many Debian packages unmodified and some proprietary software expects the presence of those directories.

FWIW, the BSD-style runtime configuration (RC) approach is generally easier for a human to maintain, whereas the SysV init scripts generally make it simpler for a *program* to modify things (the program doesn't have to parse the script file).

---

