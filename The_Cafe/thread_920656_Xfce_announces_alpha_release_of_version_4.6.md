---
title: "Xfce announces alpha release of version 4.6"
date: 2008-09-15
forum: The Cafe
---

### Post by cardinals_fan on 2008-09-15
From the mailing lists (sorry, I know it's long):> Message: 2
Date: Sun, 14 Sep 2008 14:16:57 +0200
From: "Stephan Arts" <stephan@xfce.org>
Subject: Xfce 4.6 ALPHA ('Pinkie') Released!!!
To: "XFCE4 development list" <xfce4-dev@xfce.org>,      "XFCE general
       discussion list" <xfce@xfce.org>, [email]xfce-announce@xfce.org[/email]
Message-ID:
       <74b8614e0809140516u73342119iff53d4e0860dbf64@mail.gmail.com>
Content-Type: text/plain; charset=ISO-8859-1

Hello everybody,

After about 18 months of development, we are pleased to announce the release
of Xfce 4.6 ALPHA, codename 'Pinkie'.

Xfce 4.6 is going to be the next major release of the Xfce desktop
environment. The previous release was 4.4 with the last bugfix release
being 4.4.2 released in December 2007.

The release schedule for Xfce 4.6 is available to the public on
[http://wiki.xfce.org/milestones_to_46](http://wiki.xfce.org/milestones_to_46).


What's new?
===========

Xfce 4.6 comes with a lot of new components, some of them replacing old
code and some of them being completely new. A preliminary ChangeLog for
the alpha release can be found at

 [http://www.xfce.org/documentation/changelogs/4.5.90](http://www.xfce.org/documentation/changelogs/4.5.90)

There is also a page which contains general information about the
components of Xfce 4.6 and changes that are supposed to go into 4.6:

 [http://wiki.xfce.org/general_info_46](http://wiki.xfce.org/general_info_46)

Updated components:

 * Thunar
 * exo
 * libxfce4util
 * libxfcegui4
 * xfce-utils
 * xfce4-dev-tools
 * xfce4-panel
 * xfce4-session
 * xfdesktop
 * xfprint
 * xfwm4

Replaced components:

 * libxfce4mcs      => xfconf
 * xfce-mcs-manager => xfconf, xfce4-settings
 * xfce-mcs-plugins => xfce4-settings
 * xfce4-mixer      => xfce4-mixer (rewrite)
 * xfce4-appfinder  => xfce4-appfinder (rewrite)

New components:

 * libxfce4menu (used by xfdesktop and xfce4-appfinder)

Excerpt of new features:

 * While Xfce 4.4 shipped a centralized settings storage system with
   dynamically loaded plugins, 4.6 features a D-Bus based settings
   daemon (xfconfd). All settings dialogs are just standalone
   applications now which makes the whole platform more flexible. You
   can now much easier write a settings dialog and remove/add
   components from/to Xfce.

 * In addition to xfconf and the settings dialogs being ported to
   xfconf, there will also be tools addressed to users who would you
   like to have direct access to the settings. There is a shell
   application xfconf-query which allows to list/get/set properties
   and a graphical settings editor is in development and will most
   likely be part of 4.6 as well.

 * We have tried to make the keyboard shortcuts settings more
   transparent to the user. Shortcut themes have been completely
   dropped and there are dialogs now which help resolving conflicting
   shortcuts between xfce4-settings (command shortcuts) and xfwm4
   (window manager shortcuts).

 * The settings dialogs will be available as standalone apps but they
   will also support embedding into the main Xfce settings dialog
   which helps making the desktop less intrusive.

 * In 4.4 xfdesktop used a pseudo-fd.o-compliant menu system. In 4.6
   this is replaced by libxfce4menu which aims at implementing the
   fd.o menu spec. It's still in development but covers enough of the
   specification already to replace the old code.

 * The volume control (xfce4-mixer) has been replaced with a
   completely new mixer based on GStreamer 0.10. This removes the need
   to maintain support code for different sound architectures and also
   provides some new features.


Base dependencies
=================

Xfce 4.6 is going to depend on GTK+ 2.10 and GLib 2.12. There are some
optional features available with more recent versions like with the
tooltips API of GTK+ 2.12. Some of the (optional or not optional)
dependencies introduced by core components include:

 * gstreamer 0.10
 * gstreamer-plugins-base 0.10
 * libnotify >= 0.4.0
 * hal-storage >= 0.5.7
 * libstartup-notification-1.0 >= 0.5
 * libglade-2.0 >= 2.0.0
 * dbus-glib-1 >= 0.72
 * dbus-1 >= 1.0.0
 * libwnck-1.0 >= 2.12
 * cairo >= 1.0.0
 * xrandr >= 1.1.0

For a complete list, look here:

   [http://wiki.xfce.org/general_info_46#dependencies](http://wiki.xfce.org/general_info_46#dependencies)


Known Issues
============

As this is a development-release, we do not claim it is perfect. Here
is a list of issues we have already identified:

 * Some Xfce Menu items are unsorted.
 * xfdesktop and xfce4-menu-plugin can crash when installing new
   .desktop files or icons.
 * xfwm4 does not use the keyboard shortcuts configured in the settings dialog.
 * xfce4-settings-editor cannot be used to edit settings.
   It does show some of them though.
 * Due to a bug in xfce4-settings-editor using the wrong API, it depends
   on glib 2.14 instead of 2.12.
 * Workspaces settings dialog is missing the margins settings.
 * Workspaces settings dialog cannot set workspace names.
 * Icons for app launchers are not shown properly on the desktop.
 * "Help" buttons in settings dialogs aren't hooked up yet.


Downloading Xfce 4.6 ALPHA
==========================

Getting excited? You can download xfce 4.6 alpha from here:

   [http://www.xfce.org/download/#unstable](http://www.xfce.org/download/#unstable)

We hope you have a lot of fun trying out this new Xfce. If you find
any issues, don't hesitate to check out [http://bugzilla.xfce.org/](http://bugzilla.xfce.org/) and
look for the bug, or submit a new report if your issues are not
already mentioned.


Kind regards,

The Xfce development team

Ps.
You might need to be a little patient until the mirrors have synced.

---

### Post by Erik Trybom on 2008-09-15
Excellent news. Xfce is in my opinion a serious competitor to both Gnome and KDE, and not only because of its speed but because it's a very good desktop environment in its own right. Stable, clean and easy to configure. 

I don't see any amazing new features for the end user, but it seems like there are lots of improvements done under the hood. That's the way it should be too. I look forward to the final release of 4.6.

---

### Post by Naiki Muliaina on 2008-09-15
Very much looking forward to it here. I love XFCE even when my PC has a few gig of ram, i just like the desktop enviroment :)

---

### Post by mali2297 on 2008-09-15
Where does this *xfconf* store its settings? ...in separate xml and rc files like before or in a common *.xconf* file (like .gconf)?

I hope it allows editing by hand.

---

### Post by techmarks on 2008-09-15
Xfce has become my favourite desktop.

It's good to know it continues to improve.

---

### Post by danbuter on 2008-09-15
This is great news. xfce has become my desktop of choice.

---

### Post by Steveway on 2008-09-15
Great News. xfconf will bring us some great new posibilities, like beeing able to change the Desktop-background from another application.(Ristretto allready supports this through xfconf)
Thanks to all the great developers, I hope we get it in Intrepid even though it's still "alpha".

---

### Post by cardinals_fan on 2008-09-15
> **Steveway said:**
> Great News. xfconf will bring us some great new posibilities, like beeing able to change the Desktop-background from another application.(Ristretto allready supports this through xfconf)
Thanks to all the great developers, I hope we get it in Intrepid even though it's still "alpha".
The Xubuntu devs are going to include 4.4 but have 4.6 available in a PPA repo.

---

### Post by Steveway on 2008-09-16
> **cardinals_fan said:**
> The Xubuntu devs are going to include 4.4 but have 4.6 available in a PPA repo.

That's a good and wise decision. I'm gonna check it out soon.

---

### Post by mali2297 on 2008-10-15
The beta is out! See [http://www.xfce.org/about/news?id=16](http://www.xfce.org/about/news?id=16).

> 
A lot of bugs have been fixed in this release, a few highlights:
- Xfwm4 can now detect if a program is unresponsive. It will show a dialog to let the user kill it.
- Xfce4-session will start up significantly faster by using parallel startup.
- It is possible to configure the keyboard-layout.
- Toggling event-sounds with libcanberra + gtk 2.14 is now possible (meaning: you can turn them off).


Interesting, I never thought that they would implement event-sounds. Oh well, as long as I can turn them off.

---

### Post by SunnyRabbiera on 2008-10-15
So I guess this means XFCE will finally get a decent menu editor?

---

### Post by smartboyathome on 2008-10-16
By the way, you can test XFCE 4.6 using this ppa if you are on Intrepid:
[https://launchpad.net/~xubuntu-dev/+archive](https://launchpad.net/~xubuntu-dev/+archive)
I am probably going to try it, since they finally got a menu editor. :D

---

### Post by RiceMonster on 2008-10-16
Cool. Looking forward to trying this out

---

### Post by myusername on 2008-10-16
if they can give a decent menu editor (even openbox has this!) and panel transparency...xfce will be perfect im my opinion

---

### Post by smartboyathome on 2008-10-16
> **myusername said:**
> if they can give a decent menu editor (even openbox has this!) and panel transparency...xfce will be perfect im my opinion

It didn't give me the menu editor from the repo. The menu editor doesn't get installed. It also didn't allow me to set a GTK/icon theme. This was pretty much a deal breaker for me, so I went back to GNOME until the next update when I can actually use my themes.

---

### Post by cardinals_fan on 2008-10-16
> **myusername said:**
> if they can give a decent menu editor (even openbox has this!) and panel transparency...xfce will be perfect im my opinion
Xfce has always had a very good menu editor.  It just isn't implemented particularly well.  I think it has something to do with the tool for indexing the files in /usr/share/applications.  That's why opening the auto-generated menu in the 4.4 menu editor shows the links and a big blank "system" in the middle.  See [http://wiki.xfce.org/faq#menu](http://wiki.xfce.org/faq#menu)

---

### Post by psyBSD on 2008-10-17
> **SunnyRabbiera said:**
> So I guess this means XFCE will finally get a decent menu editor?

No, it means the crappy menu-editor is gone... it wont be replaced until 4.8. You'll have to do without with 4.6

---

### Post by psyBSD on 2008-10-17
> **mali2297 said:**
> The beta is out! See [http://www.xfce.org/about/news?id=16](http://www.xfce.org/about/news?id=16).



Interesting, I never thought that they would implement event-sounds. Oh well, as long as I can turn them off.

We haven't... gtk has implemented event-sounds. Xfce needs to be aware of that in order to tell Gtk to STFU ;)

---

### Post by SunnyRabbiera on 2008-10-17
> **psyBSD said:**
> No, it means the crappy menu-editor is gone... it wont be replaced until 4.8. You'll have to do without with 4.6

Dang, so you still have to edit the menu manually and the hard way...
That sucks, for new users I dont think XFCE is all that great because of its lack of a decent menu editor, the xfce menu has always been a weakpoint.

---

### Post by andrek on 2008-10-28
Uhm, where's that app for editing the menu? Which file has all the information about xfce's desktop menu?

---

