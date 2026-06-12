---
title: "Gnome Shell Theme Help"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kbizzle on 2012-04-15
Brief overview. I am running the latest beta 12.04 Ubuntu. I have spent the last 3 hours reading, searching, terminaling and I am stumped. Hell, I might be asking too much from my current build of Ubuntu. I found this theme...

[http://www.omgubuntu.co.uk/2012/01/gnome-shell-ice-cream-sandwich-theme-is-all-kinds-of-delicious/](http://www.omgubuntu.co.uk/2012/01/gnome-shell-ice-cream-sandwich-theme-is-all-kinds-of-delicious/)

I followed this guide...

[http://www.omgubuntu.co.uk/2011/10/how-to-install-gnome-shell-themes-in-ubuntu-11-10/](http://www.omgubuntu.co.uk/2011/10/how-to-install-gnome-shell-themes-in-ubuntu-11-10/)

I am getting this...

[http://tinypic.com/r/zsonyx/5](http://tinypic.com/r/zsonyx/5)

I have tried uninstalling extensions, upgrading, uninstalling tweak tool, etc... If anyone can point me in the right direction, it would be much appreciated. I am new to Ubuntu but I am not new to technology and have a really good ability at figuring things out. That is why posting was my last resort. TIA.

---

### Post by lovinglinux on 2012-04-15
That is because those packages are not updated to work with precise.

Top solve this issue, first remove gnome-shell-extensions-user-theme, gnome-shell-extensions-common and gnome-shell-extensions.

```
sudo apt-get remove gnome-shell-extensions gnome-shell-extensions-common gnome-shell-extensions-user-theme
```

Then install this:

[https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions_3.4.0~git20120325.98403dfc-0ubuntu1~webupd8~precise2_all.deb](https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions_3.4.0~git20120325.98403dfc-0ubuntu1~webupd8~precise2_all.deb)

Then install this:

[https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-common_3.4.0~git20120325.98403dfc-0ubuntu1~webupd8~precise2_all.deb](https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-common_3.4.0~git20120325.98403dfc-0ubuntu1~webupd8~precise2_all.deb)

Then install and activate this:

[https://extensions.gnome.org/extension/19/user-themes/](https://extensions.gnome.org/extension/19/user-themes/)

Then restart Advanced Settings (gnome-tweak-tool) and you should be able to configure the shell theme.

After configuring the theme, remove *gnome-shell-extensions* and *gnome-shell-extensions-common* again, because they are causing failure in loading gnome-shell after rebooting.

```
sudo apt-get remove gnome-shell-extensions gnome-shell-extensions-common
```

---

### Post by kbizzle on 2012-04-15
> **lovinglinux said:**
> That is because those packages are not updated to work with precise.

Top solve this issue, first remove gnome-shell-extensions-user-theme, gnome-shell-extensions-common and gnome-shell-extensions.

```
sudo apt-get remove gnome-shell-extensions gnome-shell-extensions-common gnome-shell-extensions-user-theme
```

Then install this:

[https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions_3.4.0~git20120325.98403dfc-0ubuntu1~webupd8~precise2_all.deb](https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions_3.4.0~git20120325.98403dfc-0ubuntu1~webupd8~precise2_all.deb)

Then install this:

[https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-common_3.4.0~git20120325.98403dfc-0ubuntu1~webupd8~precise2_all.deb](https://launchpad.net/~webupd8team/+archive/gnome3/+files/gnome-shell-extensions-common_3.4.0~git20120325.98403dfc-0ubuntu1~webupd8~precise2_all.deb)

Then install and activate this:

[https://extensions.gnome.org/extension/19/user-themes/](https://extensions.gnome.org/extension/19/user-themes/)

Then restart Advanced Settings (gnome-tweak-tool) and you should be able to configure the shell theme.

After configuring the theme, remove *gnome-shell-extensions* and *gnome-shell-extensions-common* again, because they are causing failure in loading gnome-shell after rebooting.

```
sudo apt-get remove gnome-shell-extensions gnome-shell-extensions-common
```

Thank you. I will give it a try. Is this something that has just recently happened with Ubuntu 12.04?

---

### Post by kbizzle on 2012-04-15
Ok. That worked but I am still a bit confused. It seems to have changed the appearance of my bar and the activities menu but the windows still look like the ambien theme. How do I get the windows to look like the one on the theme??

---

### Post by lovinglinux on 2012-04-15
> **kbizzle said:**
> Ok. That worked but I am still a bit confused. It seems to have changed the appearance of my bar and the activities menu but the windows still look like the ambien theme. How do I get the windows to look like the one on the theme??

That is a Gnome Shell theme. You need to change the window decoration theme. I don't remember the exact name, because I can't open that tool right now, but there are other 2 theme selections there, one for window decoration and other for the widgets.

---

### Post by kbizzle on 2012-04-16
Ok. Makes sense. I didnt see the window or widget decoration with the download. Will I need a program in order to change the windows and widgets?

Ok, take that back. Im assuming it is the metacity folder. Now to figure out how to handle it. lol.

---

