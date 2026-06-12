---
title: "Default user Menus"
date: 2006-10-09
forum: Server Platforms
---

### Post by cgardner on 2006-10-09
I'm setting up a LTSP server on Ubuntu. When I create new users, I don't want to have to go into the alacarte menu editor and disable the applications I don't want available.  Is there any way I can set up a default menu structure so I don't have to do this repeatedly?

---

### Post by Mr Frosti on 2006-10-09
New user profiles are pulled from what is contained in the "/etc/skel" directory. You can find where the Gnome menu settings are stored at, and copy these files / folders into the "/etc/skel" directory. This will prevent you from having to manually remove entries for new users.

I know I didn't give a complete solution, but it should be a step in the right direction.

---

### Post by bluefrog on 2006-10-10
yes have a look at .gnome2 and another one, sry can't be more specific either as I am not on my linux box at work.

once they were in my /etc/skel I chmod them to root.user iirc -or root.root (not sure, long time have done this and to be honest with you I haven't tried leaving the default owner after copying and see what it was doing)

to do it the empiric way:
remove an app from the menu and see what has changed and where in your .files under /home/user

James

---

### Post by cgardner on 2006-10-10
OK, that was actually it.  I just made the mistake of copying /home/user to /etc/skel rather than /home/user/*.

It did work just perfectly though.

Thanks.

---

