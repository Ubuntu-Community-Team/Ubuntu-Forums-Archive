---
title: "Applications menu"
date: 2008-08-05
forum: Ubuntu Customization Guide
---

### Post by fazavon on 2008-08-05
I am tying to build a base distro for general purpose at my school

Their are a couple of tool/apps that I would like to be install by default.

That I have figured out.. what I am needing help with is setting up the Applications menu to reflect this on a new install.

Example I install lat and add it to Applications > LDAP > lat on my install.. i then run remastersys dist

When I boot the ISO I would like the Applications > LDAP > lat to be there for the Live/Install CD.

Any help would be awesome

thanks

//j

---

### Post by sisco311 on 2008-08-05
replace the default Application menu configuration file from
the /etc directory with the config file from your home directory.

i don't have gnome installed, so i don't know the exact location
of the files.

---

### Post by fazavon on 2008-08-05
yeah that was my first guess.. but all I found was exclude files..

Like the apps I have chosen not to show

---

### Post by fazavon on 2008-08-06
any body have any ideas?

---

### Post by fazavon on 2009-01-01
I figured it out...

---

### Post by Sef on 2009-01-03
> I figured it out...

Could you please post what you did to resolve your problem so others may benefit from your experience.

---

### Post by fazavon on 2009-09-23
you need to copy /home/*username*/.config/menus/app /etc/skel/.config

This will add all of your current "Custom" apps from the Applications menu to any new user created, it also works after running Remamstery.

//j

---

