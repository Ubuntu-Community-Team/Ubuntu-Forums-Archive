---
title: "I installed arch, need to install E17 and create a new user"
date: 2010-10-21
forum: The Cafe
---

### Post by barbedsaber on 2010-10-21
ok, I have a really old computer that I'm trying to get up and running since my ubuntu laptop's motherboard fried.

I downloaded the arch i686 image, and installed that without too much trouble

booted for the first time, updated pacman (a quick look at the wiki told me to enter ```
pacman -Sy
```

installed E17 ```
pacman -S e-svn

``` (which I want to use rather than gnome because it's an older machine, and I wanted to try something new)

but now I don't know how to make it run my newly downloaded desktop environment.:(

Obviously I didn't have a desktop manager, I have installed SliM and XDM, but I don't know how to make either of them start at boot, so I can select E17 and get a desktop :confused::confused::confused:

also, I need to create my own user account, so that once I have it set up with the packages I want, I can stop using the root account.

thanks for reading.

---

### Post by tarps87 on 2010-10-21
To create a new user:
```
adduser *<username>*
```

For the desktop environment try looking here:
[http://wiki.archlinux.org/index.php/Beginners%27_Guide#Step_2:_Install_a_Desktop_Environment](http://wiki.archlinux.org/index.php/Beginners%27_Guide#Step_2:_Install_a_Desktop_Environment)

In short edit /etc/inittab at the top you will see:
id:3:initdefault:
commet out and uncomnet the line:
id:5:initdefault:
e.g.
#id:3:initdefault:
id:5:initdefault:

now at the bottom of this file uncomment your login manager.

After creating a new user login in using this user and type:
```
nano ~/.xinitrc
```
and add the line
exec <*desktop environment*>
e.g exec startlxde
for lxde
I can not remember the command for E17 (might be enlightenment)

---

### Post by uRock on 2010-10-21
Reopened and moved to the Cafe.

Good luck,
uRock

---

### Post by Spice Weasel on 2010-10-21
"xinit enlighenment"

---

### Post by JP121 on 2010-10-21
If you look at the arch wiki, there should be some line you need to add to the x11 configuration file.  Then you just type startx

---

