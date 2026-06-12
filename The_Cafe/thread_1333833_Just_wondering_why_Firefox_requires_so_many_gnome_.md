---
title: "Just wondering why Firefox requires so many gnome packages."
date: 2009-11-21
forum: The Cafe
---

### Post by Psumi on 2009-11-21
I was just wondering why Firefox requires so many gnome packages. It certainly is not a gnome application, is it?

Similarly, why does flashplugin-nonfree require gnome packages?

---

### Post by steveneddy on 2009-11-21
You can always install FF from the web site and Flash from adobe.

---

### Post by Psumi on 2009-11-21
> **steveneddy said:**
> You can always install FF from the web site and Flash from adobe.

But would it not it be easier to just package it without gnome dependencies in the first place?

---

### Post by NoaHall on 2009-11-21
What gnome packages does it use?
You can always use "sudo apt-get install blahblah --no-install-recommends"

---

### Post by Psumi on 2009-11-21
> **NoaHall said:**
> What gnome packages does it use?
You can always use "sudo apt-get install blahblah --no-install-recommends"

Here's what it says that wilol be installed extra:

```
  apt-xapian-index apturl apturl-common esound-clients esound-common
  firefox-3.5 firefox-3.5-branding gksu gnome-mime-data launchpad-integration
  libart-2.0-2 libaudiofile0 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libcairo-perl libesd-alsa0 libgail-common libgksu2-0
  libglib-perl libgnome2-0 libgnome2-canvas-perl libgnome2-common
  libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0 libgnomecanvas2-common
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgtk2-perl libgtkhtml2-0 libgtop2-7 libgtop2-common
  liblaunchpad-integration1 libpango-perl librarian0 python-debian
  python-gtkhtml2 python-software-properties python-vte python-xapian
  rarian-compat software-properties-gtk synaptic ubufox unattended-upgrades
```

But using the no-recommends doesn't show all that, only firefox-3.5 and whatnot, thanks :3

---

### Post by chucky chuckaluck on 2009-11-21
the dependencies listed for firefox on arch are xulrunner and desktop-file-utils (whatever that is), so maybe this is some ubuntu/gnome plot to sap the precious bodily fluids of the innocent user.

---

### Post by SomeGuyDude on 2009-11-21
> **chucky chuckaluck said:**
> the dependencies listed for firefox on arch are xulrunner and desktop-file-utils (whatever that is), so maybe this is some ubuntu/gnome plot to sap the precious bodily fluids of the innocent user.

And Firefox-PGO in the AUR doesn't even need xulrunner. Just a handful of stuff for compiling.

---

### Post by Skripka on 2009-11-21
> **chucky chuckaluck said:**
> the dependencies listed for firefox on arch are xulrunner and desktop-file-utils (whatever that is), so maybe this is some ubuntu/gnome plot to sap the precious bodily fluids of the innocent user.

XULRunner depends on GTk2 though.

[http://www.archlinux.org/packages/extra/x86_64/xulrunner/](http://www.archlinux.org/packages/extra/x86_64/xulrunner/)

---

### Post by 3rdalbum on 2009-11-21
The optional "firefox-3.5-gnome-support" extension is what requires those extra Gnome packages. If you have a look at the actual firefox-3.5 package, it doesn't require any Gnome at all.

---

### Post by Psumi on 2009-11-21
> **3rdalbum said:**
> The optional "firefox-3.5-gnome-support" extension is what requires those extra Gnome packages. If you have a look at the actual firefox-3.5 package, it doesn't require any Gnome at all.

That is why --no-install-recommends is nice :)

---

### Post by Psumi on 2009-11-21
Another problem I see is the following:

compiz, gksu, pidgin, gstreamer-plugins-good, notification-daemon all need gconf apparently.

Compiz, I don't see why it would need gconf, as I have it set to flat-file, not gconf.

gksu should be a gtk app, not a gconf-backend based app. Thus it should be compatible with xfconf.

pidgin should also use a flat-file database rather than to use gconf. You can still encrypt with flat-file.

gstreamer-plugins-good should be using gstreamer-settings to store data.

---

### Post by SunnyRabbiera on 2009-11-22
For ubuntu firefox is included alongside gnome, but in other distros this is not fully the case.

---

### Post by Psumi on 2009-11-22
> **SunnyRabbiera said:**
> For ubuntu firefox is included alongside gnome, but in other distros this is not fully the case.

The problem with gnome as it stands now, is GNOME Shell. No applets, no indicator for evolution/empathy, etc.

Yes, it is in early stages, but if it has this many problems, then it shouldn't even have been released in ubuntu repos.

Docky does not even have a gnome menu applet, so how can we add more launchers to docky if we cannot drag anything? (gnome shell disallows dragging straight to a specific part of the desktop, so you canot drag from the gnome shell menu and put it on docky.)

If all of these things were solved magically, I would be all for Gnome Shell.

---

