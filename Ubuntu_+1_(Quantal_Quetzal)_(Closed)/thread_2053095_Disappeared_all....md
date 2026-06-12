---
title: "Disappeared all..."
date: 2012-09-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by panciluca on 2012-09-04
Hello everybody,
I hope to be in the right section.
My problem is related to the new GNOME-SHELL (GNOME 3, I use ubuntu 12.10) and I have experienced the following when installing a new gnome extension:

just after the installation of an extension everything is disappeared from my desktop (also if I reboot): upper bar, keyboard functionality (only works crtl-alt-del combination keys), mouse right-click doesn't work, alt-f2 doesn't work and any other combinations. I can see only the desktop background image and I can do nothing.

Do you know a way to reinstall and or "reset" gnome? (I have tried to remove and install again the packages gnome, gnome-panel and gnome-shell but nothing to do).

Thank you in advance for your help.

LP

---

### Post by Elfy on 2012-09-04
*Thread moved to **Ubuntu +1 (Quantal Quetzal)**.*

---

### Post by panciluca on 2012-09-04
Hi,
I have tried to perform the following actions:

sudo apt-get purge gnome-shell
sudo apt-get purge gnome-panel
sudo apt-get purge gnome
apt-get autoremove

and I have re-installed all the components (from unity) but, again, nothing to do. May be I have to remove some configuration files related to gnome-shell.

---

### Post by cbanakis on 2012-09-04
If you can manage to get into a terminal...

Try quiting nautilus
```
nautilus -q
```

Then re-launch
```
nautilus
```

That may temporarily solve your issue, but once you close terminal, nautilus will quit again.

Normally, you can re-launch it by opening any folder, but if you don't have any folders to open...

I use Cairo-Dock, so I can always open folders/launch apps, even without nautilus.

---

### Post by panciluca on 2012-09-04
Thanks a lot cbanakis for your time,
but it doesn't work.

After to have googled for two hours now I have tried (with no real motivation) to delete the content of the folder ~/.local/share/gnome-shell

Now the problem seems to be solved.

Thank you a lot,
LP

---

### Post by cbanakis on 2012-09-04
Hmmm, maybe I should try that.

As it stands, I need to restart nautilus almost every time I boot up.

Glad you figured it out though.

---

