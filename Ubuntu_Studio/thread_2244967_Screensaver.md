---
title: "Screensaver"
date: 2014-09-20
forum: Ubuntu Studio
---

### Post by davidgrz on 2014-09-20
I am using Ubuntu Studio 14.04 and I would like to install the screen savers that are grayed out when I go to change the screen saver. How would I go about doing this. 

I also wouldn't mind adding some other options for the splash screen.

Any help would be greatly appreciated.

Thank you,

David

---

### Post by ajgreeny on 2014-09-20
I think Ubuntu-Studio uses xfce, in which case you need to make sure you have **xscreensaver** and **xscreensaver-gl** for most of the usual ones, and also possibly **xscreensaver-gl-extra** for even more options.

I can't help with the splash screen.

---

### Post by olliemonster on 2014-09-20
To edit the splash screen you need to research Plymouth. The things you would need to find out are the splash screen you want and how to change splash screen.
If you want to edit the grub boot screen you could researdch and learn how to use a program callled grub-customizer. You need to add a repo which is [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer) By the way i didn't make grub customizer i just use it if i don't like a distro default boot screen.

---

### Post by Dennis N on 2014-09-20
To have all the screensavers, you need to install these packages:

xscreensaver
xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra
rss-glx

xscreensaver-data comes with xscreensaver, but the others are installed separately and will provide the missing screensavers. rss-glx requires some extra steps. read the file /usr/share/doc/rss-glx/README.xscreensaver

As to the spash screen, search for "plymouth-theme" in Ubuntu Software Center. There are several you can install. Best: **solar theme**. After installing, run the command:
```
sudo update-alternatives --config default.plymouth
```
to select the theme.

The selection in the repository is limited. If you are interested in additional themes, visit gnome-look.org and select category "splash screens" on the left. These can require more steps to manually install, but it's not difficult.

---

### Post by cfhowlett-a on 2014-09-28
Be aware that using xscreensaver can cause conflicts with lightdm ...

That said, the "official" looking ubuntustudio xscreensaver plugin is at [http://spreadubuntu.org/en/material/poster/usa-sized-your-free-alternative](http://spreadubuntu.org/en/material/poster/usa-sized-your-free-alternative)

---

### Post by Dennis N on 2014-09-28
> Be aware that using xscreensaver can cause conflicts with lightdm ...

Absolutely. You only want one screensaver active on your system. If your system uses light locker, you can disable it by moving all the "sliders" setting times to "never" and setting enable light locker to off. That has worked for me in Lubuntu recently. Another option is to uninstall light locker. For Ubuntu, the conflicting screensaver is gnome-screensaver.

---

