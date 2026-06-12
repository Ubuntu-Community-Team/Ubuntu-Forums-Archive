---
title: "permissions"
date: 2008-07-05
forum: The Cafe
---

### Post by Riffer on 2008-07-05
I've trying to resurrect some old machines (PIII 196 megs RAM) at school using Ubuntu/Linux.  And while there is great distros out there that would "almost" be great, I keep running into the same problem, locking down the desktop.

The goal is to have stand alone machines with very few apps (browser, word processor, etc.) and have the desktop locked down so that a guest user cannot change any of the settings.  This machine while having internet access, will not have access to the school network, other then printing to a set printer.

And while this can be accomplished using Gnome or KDE, I haven't been able to find a way to do it in the smaller desktop environments.  

I was thinking though that it might be just a case of setting folder and file permissions.  If I set it so that ALL files and folder can only be change by a super user, will that stop the ability for guest users from changing desktop settings?  And if thats the case is there a way that I can set these permissions quickly and easily.

Thanks

---

### Post by scragar on 2008-07-05
you need to keep the home folders perms the same, as well as the perms for .dmcr

after that however just set the perms for everything to 000...

---

### Post by coolaj86 on 2008-07-05
Yay! My favorite topic! I worked at a school doing this sort of thing so I have some advice.

Locking down apps:
Right-click Edit Menus on Apps (or similar in whatever DE you choose - even fluxbox has a config file for this). It's generally sufficient to remove Terminal and any apps that you don't want them to have access to. Of course people can find ways around it, so if you want it more strict you can move certain binaries to a custom directory and only have that in the PATH variable of certain users.

Prism also provides a nice way to provide a browser, but only with access to certain sites or online apps.

Locking down changes:
You can use gconf:
[http://gentoo-wiki.com/HOWTO_Gnome_Desktop_Admin_Guide](http://gentoo-wiki.com/HOWTO_Gnome_Desktop_Admin_Guide)

You can create a script that cleans out /home/KIOSK_USER/*.* and put it in /etc/rc.local too

The only folders that users can change are /tmp and /home so as long as your kiosk user isn't a sudoer, you don't have to worry about other changes.

I would recommend that you let the users make changes, but script a way so that the machine logs out / logs in after each use and replaces the changed files with the default ones simply because causing permission errors all of the time just isn't very user friendly.

---

### Post by coolaj86 on 2008-07-05
XFCE is more lightweight than Gnome or KDE, looks relatively nice, and has some kiosk features.

[http://svn.xfce.org/svn/xfce/xfdesktop/trunk/doc/README.kiosk](http://svn.xfce.org/svn/xfce/xfdesktop/trunk/doc/README.kiosk)

---

### Post by Riffer on 2008-07-05
Thanks for your replies.

scragar   I'm not sure what you mean,

> after that however just set the perms for everything to 000... 

is that a user ID?

coolaj86

Thanks for the gentoo guide that has alot of useful stuff.  I did look at that guide for XFCE Kiosk module.  What I couldn't figure out is if the module comes pre-loaded or if you have to add it and if so whats the name of the module.

---

### Post by coolaj86 on 2008-07-05
Google a bit for 'xfce' and 'kiosk' and see what you come up with.

[This looks good]("http://www.synack.info/xfce4-kiosk-mode/")
[and so does this]("http://wiki.xfce.org/howto/kiosk_mode")

---

