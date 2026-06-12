---
title: "Adding gnome extension in 17.10"
date: 2017-08-13
forum: Ubuntu Development Version
---

### Post by geovino on 2017-08-13
How do you add gnome extensions to the tweak took in Ubuntu 17.10? 

why does tweak tool come with no extensions?

Thanks

---

### Post by wildmanne39 on 2017-08-13
*Thread moved to **Ubuntu Development Version**.*

---

### Post by P-I H on 2017-08-13
Tweak tool shows installed extensions.
I have found two ways to install extensions
- In a browser from page [https://extensions.gnome.org/](https://extensions.gnome.org/)
- In Ubuntu Software from Add-ons/Shell Extensions

---

### Post by geovino on 2017-08-13
Thanks, was able to add Places but Applications Menu would not install. But this is the daily build of 17.10 so not everything will work. ;)

---

### Post by dino99 on 2017-08-14
Ubuntu 17.10 archive have its own list of available gnome-shell-extension-* packages.
Its the main source for installing them (checked with synaptic), as they are installed into a specific path (/usr/share/gnome-shell/extensions/)
Extensions from the gnome-shell.org url are installed into an other path: .local/share/gnome-shell/extensions/ , so avoid installing/upgrading these extensions from that url if they also come with the archive list.
(aka, dont have the same extension installed twice (both paths) with different version)

---

### Post by geovino on 2017-08-14
Thanks, I tried installing synaptic, but it won't open! Too many bugs in this daily build.

---

### Post by dino99 on 2017-08-14
I suppose you are using a wayland session; with x11 synaptic works well

---

### Post by rrnbtter on 2017-08-15
Greetings,
Synaptic works fine on my Gnome Wayland system

From Terminal
xhost +si:localuser:root
sudo synaptic

This is a bit non conventional but seems to be the current work around until some things get fixed.

---

### Post by P-I H on 2017-08-15
What's the advantage using synaptic?
Most users will probably use Ubuntu Software to install programs.
To download applications using a browser will probably also be more common.
Both this methods install the extensions in [COLOR=#000000].local/share/gnome-shell/extensions/[/COLOR]

---

### Post by #&amp;thj^% on 2017-08-15
Speaking just for myself, I can't remember using Gnome Software ever.
Not a fan of the new package managers at all... as far as advantage goes>>>maybe a better term would be preference is all. :)

---

### Post by jbicha on 2017-08-15
There are hundreds more GNOME Shell extensions available through the Ubuntu/GNOME Software app (in Addons > Shell Extensions) than through Synaptic or apt.

---

### Post by #&amp;thj^% on 2017-08-15
> **jbicha said:**
> There are hundreds more GNOME Shell extensions available through the Ubuntu/GNOME Software app (in Addons > Shell Extensions) than through Synaptic or apt.

Sounds like you guys are thinking some where down the road to dump synaptic then.

---

### Post by rrnbtter on 2017-08-15
Greetings,
The Gnome Software Center is nice, in fact much nicer than I thought it would be.  I use synaptic to install some non channel apps like Kompozer as a for instance.  The question with synaptic was how to get it to work in a wayland session, and it in fact works.

---

### Post by Cavsfan on 2017-08-15
> **rrnbtter said:**
> Greetings,
Synaptic works fine on my Gnome Wayland system

From Terminal
xhost +si:localuser:root
sudo synaptic

This is a bit non conventional but seems to be the current work around until some things get fixed.

Actually, once you have entered xhost +si:localuser:root
Synaptic will open by clicking on it. At least on my system it does.

Alias:
#temorary session fix for root
alias root-fix='xhost +si:localuser:root'

---

### Post by mc4man on 2017-08-15
> **jbicha said:**
> There are hundreds more GNOME Shell extensions available through the Ubuntu/GNOME Software app (in Addons > Shell Extensions) than through Synaptic or apt.

Ubuntu/GNOME Software is certainly improved, at least for apps & apparntly extensions. Still & maybe? forever useless for libraries & cli binaries.

One current almost flaw can be seen by simple example

Go to Add -Ons > Shell Extensions, it populates rather quickly. 
Then go 'back' > Hardware drivers > Open the  Beignet description. From there 'back' > Shell Extensions. Now it takes about 15-20 sec to populate here.

---

### Post by dino99 on 2017-08-16
Speaking about Gnome-software/Ubuntu-software, i have purged these packages & dependencies because i have found them running in the background (at least sometimes) and fully using a cpu core (100%) without ending. The worst is they surely be never running as i only work with synaptic. Synaptic does not list (useless/not tested) third parties packages if you does not enter ppa(s); that is much more stable and secure.

---

### Post by travis-falkenberg on 2017-08-16
> **geovino said:**
> Thanks, was able to add Places but Applications Menu would not install. But this is the daily build of 17.10 so not everything will work. ;)

If you install the package "gnome-shell-extensions" it also installs some files that many extensions on the extensions.gnome website depend on!

After doing this I could install any extension from the website.

---

### Post by jbicha on 2017-08-16
> **mc4man said:**
> 

One current almost flaw can be seen by simple example



Please file a bug.

> **travis-falkenberg said:**
> If you install the package  "gnome-shell-extensions" it also installs some files that many  extensions on the extensions.gnome website depend on!

After doing this I could install any extension from the website.

Please file a bug against ubuntu-meta. We may want to install some of those extra gir packages by default then.

---

### Post by rrnbtter on 2017-08-16
Greetings,
The website and PPA connector works perfect on my Opera Browser. I installed it just to get the "removable drive" extension. I also installed the gnome-shell-extensions.
However the software center addons/extensions doesn't work at all. The page won't populate even if I just leave it up.  As a result I have had to add the word "almost" to my perfect computer.

---

