---
title: "Firefox on KDE"
date: 2009-02-01
forum: The Cafe
---

### Post by igknighted on 2009-02-01
```
The following NEW packages will be installed:
  apturl docbook-xml firefox firefox-3.0 firefox-3.0-branding gamin gconf2
  gconf2-common gksu gnome-app-install gnome-icon-theme gnome-keyring
  gnome-mime-data gnome-mount libavahi-glib1 libbonobo2-0 libbonobo2-common
  libbonoboui2-0 libbonoboui2-common libcairo-perl libgamin0 libgconf2-4
  libgksu2-0 libglade2-0 libglib-perl libgnome-keyring0 libgnome2-0
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgp11-0 libgtk2-perl
  libgtkhtml2-0 libgtop2-7 libgtop2-common libidl0 liblaunchpad-integration1
  libnotify1 liborbit2 libpam-gnome-keyring libpolkit-gnome0 librsvg2-common
  libscrollkeeper0 libsexy2 libstartup-notification0 libvte-common libvte9
  libwnck-common libwnck22 libxres1 notification-daemon policykit-gnome
  python-cairo python-gconf python-glade2 python-gst0.10 python-gtk2
  python-gtkhtml2 python-launchpad-integration python-numeric python-pyorbit
  python-sexy python-vte scrollkeeper sgml-data software-properties-gtk
  synaptic ubufox xulrunner-1.9
0 upgraded, 77 newly installed, 0 to remove and 1 not upgraded.
```

I went to install firefox on a clean Kubuntu install (well, upgraded to kde 4.2), and firefox wants to bring all this stuff in.  Does firefox **really** need all this stuff?  I could compile firefox myself from the sources on the mozilla site and not need this stuff, so clearly firefox can work without it.  So why does Ubuntu require it?

---

### Post by Namtabmai on 2009-02-01
Short answer? Yes.

Long answer. Yes, Firefox is a Gnome application on Linux so it needs to bring all that stuff in to work. I believe someone branched Firefox at some point to use QT4 but I don't think it's been actively maintained.

---

### Post by p_quarles on 2009-02-01
I think the "Firefox" package is just a metapackage that includes a lot of other stuff like Gnome support and Ubufox. I'm not sure which package is just the browser, but my money would be on "firfox-3.0." Try
```
sudo apt-get install firefox-3.0p
```
and see if that resolves the issue.

> **Namtabmai said:**
> Firefox is a Gnome application on Linux so it needs to bring all that stuff in to work. 
No, it's not. The Gnome integration is an afterthought, and not necessary for Firefox itself to work at all.

---

### Post by OutOfReach on 2009-02-01
Yes, Firefox does need a lot of that stuff since it is closely developed with GNOME and GTK.
But there are some packages in there that do seem unnecessary for a web browser.

---

### Post by RiceMonster on 2009-02-01
That's odd; it shouldn't need all those dependencies. I'm guessing they provide additional functionality or something?

Check this out:

```
$ pacman -Si firefox
Repository     : extra
Name           : firefox
Version        : 3.0.5-1
URL            : http://www.mozilla.org/projects/firefox
Licenses       : MPL  GPL  LGPL  
Groups         : None
Provides       : None
**Depends On     : xulrunner=1.9.0.5  desktop-file-utils  shared-mime-info**  
Optional Deps  : None
Conflicts With : None
Replaces       : firefox3  
Download Size  : 958.80 K
Installed Size : 3432.00 K
Packager       : Jan de Groot <jgc@archlinux.org>
Architecture   : i686
Build Date     : Sun 21 Dec 2008 09:13:50 AM EST
MD5 Sum        : 033db66c4720e080980f74cf4bc1107a
Description    : Standalone web browser from mozilla.org
```

---

### Post by igknighted on 2009-02-01
> **Namtabmai said:**
> Short answer? Yes.

Long answer. Yes, Firefox is a Gnome application on Linux so it needs to bring all that stuff in to work. I believe someone branched Firefox at some point to use QT4 but I don't think it's been actively maintained.

From my understanding (and I could certainly be wrong, wouldn't be the first time), Firefox simply uses the GTK window toolkit.  Very different from being a Gnome app.  I would expect to need the GTK toolkit dependencies, but all this stuff from gnome just seems rather wasteful.

I can certainly understand wanting to add the integration features, but put that all in some metapackage (firefox-gnome or something).  Then let the firefox package itself just have the bear minimum dependencies.

---

### Post by capink on 2009-02-01
Firefox can run fine without gnome. If you want you can go and download the binaries (you need not compile form source) from [here]("http://www.mozilla.com/en-US/products/download.html"). To run this binary you only need the following:

```
GTK+ 2.10 or higher
GLib 2.12 or higher
Pango 1.14 or higher
X.Org 1.0 or higher
```

---

### Post by Skripka on 2009-02-01
> **Namtabmai said:**
> Short answer? Yes.

Long answer. Yes, Firefox is a Gnome application on Linux so it needs to bring all that stuff in to work. I believe someone branched Firefox at some point to use QT4 but I don't think it's been actively maintained.

The Qt port of Firefox is very much at "Minefield" status wight now, and is under development.

That being said-Firefox looks awful under KDE...it may not be a "Gnome App"...but it's window decor sure renders poorly under KDE.

---

### Post by FuturePilot on 2009-02-01
Part of the reason it needs all that stuff is because of the apt-url stuff. The package responsible for apt-url depends on Synaptic which depends on a load of Gnome and GTK stuff. So then you end up with all that stuff. But I'm pretty sure you can install just Firefox like p_quarles mentioned.

---

### Post by stmiller on 2009-02-01
You would get the same list of requirements when trying to install any GTK program for the first time. Such as gimp, etc.

It's not Firefox specific, per say. :)

---

### Post by igknighted on 2009-02-01
> **FuturePilot said:**
> Part of the reason it needs all that stuff is because of the apt-url stuff. The package responsible for apt-url depends on Synaptic which depends on a load of Gnome and GTK stuff. So then you end up with all that stuff. But I'm pretty sure you can install just Firefox like p_quarles mentioned.

p_quarles package could not be found, and firefox and firefox-3.0 all had the same dependencies.


> **capink said:**
> Firefox can run fine without gnome. If you want you can go and download the binaries (you need not compile form source) from [here]("http://www.mozilla.com/en-US/products/download.html"). To run this binary you only need the following:

```
GTK+ 2.10 or higher
GLib 2.12 or higher
Pango 1.14 or higher
X.Org 1.0 or higher
```

There's no 64bit binaries available anywhere (that I can find at least), so I would have to compile.



> **stmiller said:**
> You would get the same list of requirements when trying to install any GTK program for the first time. Such as gimp, etc.

It's not Firefox specific, per say. :)

I tried installing other gtk apps, without bringing in all that mess.  For example, Midroi brought in 3 packages total.

---

### Post by p_quarles on 2009-02-01
> **igknighted said:**
> p_quarles package could not be found, and firefox and firefox-3.0 all had the same dependencies.
I did a little more digging, and found that the unnecessary packages are not actually hard dependencies, but firefox-gnome-support is actually suggested, and ubufox is listed as recommends. With a bit of tweaking, it should be easy enough to apt-get/aptitude to install only the real dependencies.

---

### Post by igknighted on 2009-02-01
> **p_quarles said:**
> I did a little more digging, and found that the unnecessary packages are not actually hard dependencies, but firefox-gnome-support is actually suggested, and ubufox is listed as recommends. With a bit of tweaking, it should be easy enough to apt-get/aptitude to install only the real dependencies.

Thank you!  This wasn't even really intended to be a support thread, but thanks!  This is how I got it:

```
sudo apt-get install --no-install-recommends firefox
```

---

### Post by lzfy on 2009-02-02
> **igknighted said:**
> Thank you!  This wasn't even really intended to be a support thread, but thanks!  This is how I got it:

```
sudo apt-get install --no-install-recommends firefox
```

Thanks, I really needed this :)

---

### Post by Foster Grant on 2009-02-02
> **Skripka said:**
> The Qt port of Firefox is very much at "Minefield" status wight now, and is under development.

That being said-Firefox looks awful under KDE...it may not be a "Gnome App"...but it's window decor sure renders poorly under KDE.

I've set KDE's GTK settings to use Tahoma rather than Deja Sans, which always looks awful under GTK but very good under KDE.

Here's a Google cache of last summer's interview with the Nokia developer who was working on porting Firefox to Qt.

[http://74.125.47.132/search?q=cache:_rZSrHddiuQJ:dot.kde.org/1218543988/+firefox+qt&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a](http://74.125.47.132/search?q=cache:_rZSrHddiuQJ:dot.kde.org/1218543988/+firefox+qt&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a)

Wonder if there's any way to get Konqueror to use Firefox extensions?

---

### Post by Skripka on 2009-02-02
> **Foster Grant said:**
> I've set KDE's GTK settings to use Tahoma rather than Deja Sans, which always looks awful under GTK but very good under KDE.

Here's a Google cache of last summer's interview with the Nokia developer who was working on porting Firefox to Qt.

[http://74.125.47.132/search?q=cache:_rZSrHddiuQJ:dot.kde.org/1218543988/+firefox+qt&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a](http://74.125.47.132/search?q=cache:_rZSrHddiuQJ:dot.kde.org/1218543988/+firefox+qt&hl=en&ct=clnk&cd=1&gl=us&client=firefox-a)

Wonder if there's any way to get Konqueror to use Firefox extensions?

It isn't a font problem by appearances--scrollbars don't render consistently or well (despite the KDE "scrollbar fix" in the Sys Preferences), and the tab bar looks gawdawful-regardless of what skin one uses....besides I immediately ditched all of the standard fonts in KDE and my browsers to use better fonts anyway (From my Adobe CS3 purchase I got Hypatia Sans Pro, which is a great font).

Most of the functionality I want I'm getting in Konqueror, apart from more fine-tooth session management, and something like Opera speed dial. There are several Konqueror extensions in the repos too.   I've sworn off using Opera until they finally issue a 64-bit Qt4 build, otherwise I'd use Opera (there hasn't been one yet in either stable or Opera10 Alpha builds).  Most important things are there in Konqueror, in terms of Firefox Extensions (Ad Block etc)-and with xbindkeys to handle multibutton-mice Konqueror is quite usable...unfortunately Konqueror doesn't get along well with Privoxy, and things Privoxy filters out causes things like YouTube embed players to not show (they show fine on Youtube.com though), I might try reverting to Adblock-but I prefer Privoxy as a better solution to WWW spam.

I tried the last Qt Firefox Minefield build last week and it was quite buggy on the Qt side of things...and prone to crashing easily.

---

