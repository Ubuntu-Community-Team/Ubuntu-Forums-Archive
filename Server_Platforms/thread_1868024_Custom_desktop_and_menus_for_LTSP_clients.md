---
title: "Custom desktop and menus for LTSP clients?"
date: 2011-10-23
forum: Server Platforms
---

### Post by doctorbighands on 2011-10-23
I successfully got a new LTSP cluster up and running using Ubuntu 11.04. Here's what I'd like to do now, but I can't find any instructions:

The cluster will serve teenage students. I added a group on the server called "students" and changed rwx privileges in adduser.conf. Now, is there a way to create a default desktop that all students see when they log in? Basically, I want to reconfigure the Gnome desktop so that certain menus and apps show up for students, and others don't, without having to go in and manually reconfigure things every time a new user is created.

Does that make sense?

Is there a way to make it happen?

Thank you!

---

### Post by doctorbighands on 2011-10-25
le bump

I'd really like to know if there's a way to make this happen.

Thank you!

---

### Post by lykwydchykyn on 2011-10-25
Any sort of desktop settings are stored in a user's home directory.  When you create a new account, the contents of /etc/skel are copied into the new users home directory, setting default options.

You have two options:

 - Setup a student account exactly how you want it, then copy the entire home directory (including the hidden "dotfiles") to /etc/skel, causing every new account to get that configuration

or
 - Do the same, but copy it do a different directory, and edit your adduser script to use this directory instead of /etc/skel (I forget what the switch is, but check the man page it's on there).  This way, you can add non-student accounts without giving them the student configuration.

---

### Post by doctorbighands on 2011-11-01
> **lykwydchykyn said:**
> Any sort of desktop settings are stored in a user's home directory.  When you create a new account, the contents of /etc/skel are copied into the new users home directory, setting default options.

You have two options:

 - Setup a student account exactly how you want it, then copy the entire home directory (including the hidden "dotfiles") to /etc/skel, causing every new account to get that configuration

or
 - Do the same, but copy it do a different directory, and edit your adduser script to use this directory instead of /etc/skel (I forget what the switch is, but check the man page it's on there).  This way, you can add non-student accounts without giving them the student configuration.

This is awesome. Thank you, thank you, thank you!!

---

