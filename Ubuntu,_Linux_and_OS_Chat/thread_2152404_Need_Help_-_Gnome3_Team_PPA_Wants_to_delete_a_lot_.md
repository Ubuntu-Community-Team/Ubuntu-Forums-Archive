---
title: "Need Help - Gnome3 Team PPA Wants to delete a lot of Software"
date: 2013-06-07
forum: Ubuntu, Linux and OS Chat
---

### Post by SurfaceUnits on 2013-06-07
Been using Ubuntu Gnome Shell since the unofficial 12.04 Gnome Shell Remix. I'm now at 13.04. Today, the Gnome3 Team ppa ([https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)) update is wanting to delete a lot of packages, including account-plugins, Cairo dock, caribou, cheese, compiz, empathy, eog, firefox, gdebi, gdm, gedit, gimp, a lot of gir1.2 items, more disconcerting - gnome-control-center, gnome-core, gnome-icon-***, gnome-panel, packagekit, session, gnome-shell, icedtea, libreoffice, and a lot more. It looks as if it is wanting to uninstall gnome. Any ideas.

[[IMG]http://i45.tinypic.com/2uqj677_th.png[/IMG]]("http://i45.tinypic.com/2uqj677.png")

---

### Post by cariboo on 2013-06-07
> **SurfaceUnits said:**
> Been using Ubuntu Gnome Shell since the unofficial 12.04 Gnome Shell Remix. I'm now at 13.04. Today, the Gnome3 Team ppa ([https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)) update is wanting to delete a lot of packages, including account-plugins, Cairo dock, caribou, cheese, compiz, empathy, eog, firefox, gdebi, gdm, gedit, gimp, a lot of gir1.2 items, more disconcerting - gnome-control-center, gnome-core, gnome-icon-***, gnome-panel, packagekit, session, gnome-shell, icedtea, libreoffice, and a lot more. It looks as if it is wanting to uninstall gnome. Any ideas.

[[IMG]http://i45.tinypic.com/2uqj677_th.png[/IMG]]("http://i45.tinypic.com/2uqj677.png")

Obviously there are some broken dependencies, I'd suggest you wait a couple of days, and then try again.

---

### Post by markbl on 2013-06-07
OP, I have been seeing this problem for the last week also. I had looked around these forums and not seen anybody else reporting it so I suspected it was something local to my system. I mainly use aptitude and found it had gotten confused by recent updates from the gnome 3 ppa. I updated my system using synaptic and then did an "sudo aptitude keep-all" and all was good again.

---

### Post by SurfaceUnits on 2013-06-07
found this at debian forum

This is a well-known issue. In a nutshell, you installed Gnome via a  metapackage. Metapackages are wrappers that help you to install and  update a huge collection of items easily. The price you pay is that each  of the individual packages is required in order for aptitude to keep  all the rest. Therefore, if you remove even a small, apparently  inconsequential piece of Gnome (which you probably did inadvertently),  aptitude will cheerfully tell you "Ok, Gnome's got to go."

---

### Post by SurfaceUnits on 2013-06-07
Might an "apt-get install --reinstall gnome" help or hurt?

---

### Post by SurfaceUnits on 2013-06-07
Follow up:

~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  account-plugin-facebook account-plugin-flickr account-plugin-google
  account-plugin-windows-live gir1.2-pango-1.0 libjavascriptcoregtk-1.0-0
  libjavascriptcoregtk-3.0-0 libpango-1.0-0 libpango-1.0-0:i386 libpango1.0-0
  libpango1.0-0:i386 libpangocairo-1.0-0 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0 libpangoft2-1.0-0:i386 libpangoxft-1.0-0
  libpangoxft-1.0-0:i386 libwebkitgtk-1.0-0 libwebkitgtk-3.0-0
The following packages will be upgraded:
  brasero brasero-cdrkit brasero-common evince evince-common gir1.2-evince-3.0
  gir1.2-goa-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-webkit-3.0 gnome-contacts
  gnome-online-accounts libaccounts-glib0 libbrasero-media3-1 libevdocument3-4
  libevview3-3 libgoa-1.0-0 libgoa-1.0-common libwebkitgtk-1.0-common
  libwebkitgtk-3.0-common
19 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

It appears to be something in the packages held back that is causing the removal issue. Will try to upgrade each one.

---

### Post by SurfaceUnits on 2013-06-07
OK, it is the libjavascriptgtk and libpango updates causing the problem

---

### Post by VinDSL on 2013-06-07
> **cariboo907 said:**
> Obviously there are some broken dependencies, I'd suggest you wait a couple of days, and then try again.
Golden!  That's what I do...

Recent GS 3.9.2 dist-upgrade wanted to remove packages back to a bare-metal install.

I just waited a day or two, and ricotz came up with a fix.


[INDENT]**[COLOR="#A52A2A"]Screenie from yesterday / fully upgraded / no package removal(s)[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-desktop-6-jun-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-6-jun-2013-1.png")[/INDENT]

---

### Post by montag dp on 2013-06-11
So any suggestions on what I should do?  Mine is still doing this, or at least I think it's the same thing.  The software updater keeps suggesting to do a partial upgrade, but I don't think that's a good idea.

---

### Post by SurfaceUnits on 2013-06-11
Looks like they have the repo back ontrack. If it doesn't crash my peecee, I'll be right back.

---

### Post by SurfaceUnits on 2013-06-14
Well, my fossbox is in good shape. Love the gnome extensions available.

---

