---
title: "Use Ubuntu Edgy as a server for Users."
date: 2007-01-16
forum: Server Platforms
---

### Post by Shinkan on 2007-01-16
Hi there :mrgreen: 

I have a machine on which I've put **Ubuntu Edgy**.
It serves a lot of things, but particularly, users should be able to use their laptops as a terminal : they connect my server with NXClient, and they access their system account on my machine.
So they have access to a "local desktop", as if they were on the machine.

To ensure a minimum security policy, I would like to :
- **Disable reboot** to selected users through graphical Gnome buttons, or at least, make it needing user to be sudoer.
- **Disable menu editing** (or at least ...).

Other question (thinly related) : can I modify what "Administrative Tasks" check box in graphical user manager on Gnome affects ??

Then, I would like to **set a "base" user** who will be representative of the default session I would like all my guest users to have.
So I think I must create and configure an account, copy its folder to /etc/skel/ and create new users that will automatically have the same default home than /etc/skel.
Is it the good solution ?

Thanks in advance ...

---

### Post by peabody on 2007-01-16
Yes, it's a good approach.  I believe that as long as the users aren't administrative users they won't be able to shutdown the machine.  As for locking out menu eding, you may have to change the permissions of some settings files for gnome for that.  Wish I could say I knew how.

---

### Post by Shinkan on 2007-01-16
They ARE actually able to SHUTDOWN and RESTART the machine through appropriate buttons on Ubuntu Gnome Shutdown ...
But thanks to some policy or to the NXServer (I don't know), theses buttons are not available with a distant connection.
So I just had to disable suspend/hibernate (using gconf-editor with sudo, and seting "forced values" and "default values").
Problem concerning Reboot/Shutdown is away, but if there is other techniques to disable shutdown/reboot for users through Gnome, I would like to know.

I still search a solution for menu editing...

---

