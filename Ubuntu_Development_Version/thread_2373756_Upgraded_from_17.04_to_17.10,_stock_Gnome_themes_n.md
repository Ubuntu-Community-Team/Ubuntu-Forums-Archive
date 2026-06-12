---
title: "Upgraded from 17.04 to 17.10, stock Gnome themes not working"
date: 2017-10-09
forum: Ubuntu Development Version
---

### Post by mloebl on 2017-10-09
Had a rough upgrade as screen saver kicked in around 85-90% of upgrade completion, and wouldn't log back in to actually view/see the upgrade (live and learn.)  I ended up having to do reboot and finish the upgrade: ```
**dpkg --configure -a **
```  

Once I logged in, Unity session was having issues (black ground and couldn't right click on it or show icons), so switched to a Gnome session.  This had problems too, so ended up having to reset gnome settings to defaults from here; [https://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults](https://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults)

Everything **seems** to be working now in Gnome, except I cannot get any themes to display other than "Default" in the Gnome Tweak Tool (obviously I enabled the user theme extension.)  I see the themes in /usr/share/themes, and directory structure is set to 755 including the Ambiance other stock themes.  Right now I've got the fairly stock Gnome look, but really want to try out the new Ubuntu Ambiance theme for the older Unity looks.  Any thoughts what I could try?

Thanks!

---

### Post by dino99 on 2017-10-09
After dist-upgrading, dont forget to clean the system, using gtkorphan & bleachbit. Then a reboot will get a better experience.
Note that nvidia driver has problem with a wayland session (now the AA default), so boot on a x session.

---

### Post by mloebl on 2017-10-09
> **dino99 said:**
> After dist-upgrading, dont forget to clean the system, using gtkorphan & bleachbit. Then a reboot will get a better experience.
Note that nvidia driver has problem with a wayland session (now the AA default), so boot on a x session.

Thanks! I'll try this tonight and see how it works.  I tested in a VM first and it went well, so guessing my aborted upgrade didn't help.

---

### Post by mloebl on 2017-10-09
No luck, just tried it and the same issue.  By default Gnome Tweak Tool shows blank for shell theme,  and all I can select is "Default".  Anything else I can check? Thanks!

---

### Post by mloebl on 2017-10-09
Not sure which step did it, but was able to get the Ambience theme to show up.  I noticed on my VM, the Default theme is the only option there too, so may be a known-issue.

Now I realized the Desktop isn't working properly.  When it launches, instead of showing icons on the desktop if I enable them, I get a Nautilus window instead. I also only get the options for background and display settings if I right click on the desktop.

---

### Post by mloebl on 2017-10-09
I ended up booting from the latest 17.10 image, reinstalling over top and fixed the desktop issue.  Lost a bunch of packages, but was getting pretty messed up after a dozen or so upgrades.  Time to figure out why Steam is failing next :)

---

