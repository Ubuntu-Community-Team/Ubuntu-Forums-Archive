---
title: "Upgrade from 12o4"
date: 2014-03-29
forum: Ubuntu Development Version
---

### Post by ibjsb4 on 2014-03-29
P4@1.6; w/512 ram running 32bit 12o4 ubuntu with very little on it (753 packages installed).  Installed packages:

fallback -no-recommends
lightdm
synaptic
nautilus
ff and chrome
leafpad

Me wonders if this will survive the jump to 14o4, any thoughts?

---

### Post by grahammechanical on 2014-03-29
I would remove anything that is not default and I include proprietary video drivers. Remove Fallback. It no longer exists. Once the upgrade is complete and the system is not broken, you can then install a proprietary video driver if you need to and also gnome-session-flashback. Notice the new name? You will then get two additional options on the login screen: Gnome Flashback (Compiz) and Gnome Flashback (Metacity). They both give something like Fallback but one runs on Compiz and can be modified using Compiz Configuration Settings Manager (CCSM). But be careful. Adjusting settings in CCSM also changes things in Unity.

The other session runs on Metacity. Which may prove more acceptable on a machine with 512MB RAM. There will only be one workspace. But a right click on the icon on the bottom panel will open a dialog where we increase the number of workspaces.

LightDm is still with 14.04 and so is Nautilus and Firefox but I would uninstall Chrome and re-install it. Likewise, with Leafpad. Switch to default themes and icon sets. Keep it as default as possible.

Ubuntu 14.04 comes with Browser (Ubuntu web browser). It is a migrant from the Ubuntu mobile platform. Use the mouse with swipe gestures. It does not compare with firefox but It may be using less memory. I have found 14.04 to be using less memory than 12.04. Again, it is an effect from the phone development work.

Edit: I have just done some unscientific measurements using system load indicator on my machine with 1GB RAM. Flashback (Metacity) has base RAM usage of 424MB going to 480MB with Firefox and down to 464MB with Browser and back up to 540MB with Chromium. Memory usage increases a bit more with pages loaded. So, on your machine expect some lag.

Regards

---

### Post by ibjsb4 on 2014-03-29
I went with the upgrade and now running 14o4 (flashback).  It did not install Unity or Gnome-shell, but my package count is now 1020.  And I did take a performance hit which will probably be the deal breaker on this box.

Edit
Think I'll give openbox a test drive.

---

### Post by ibjsb4 on 2014-03-29
Well I was just asking too much for it to run a gnome session so I wiped it and installed 14o4 with [lubuntu-core]("http://packages.ubuntu.com/trusty/lubuntu-core") (without recommended packages).  Nice start, got a single panel desktop to start with :)

Firefox runs good, but sucks up all the resources, so I guess its a trade off.

---

### Post by kansasnoob on 2014-03-29
QupZilla runs a bit lighter than Firefox for me :D

---

### Post by vasa1 on 2014-03-29
> **kansasnoob said:**
> QupZilla runs a bit lighter than Firefox for me :D
ibjsb4 and kansasnoob, can we talk about lighter browsers in a new thread? I would like people's opinions on Xombrero ([Unit193's ppa @ Launchpad]("https://launchpad.net/~unit193/+archive/xombrero")). Xombrero has a smaller installed size (546 v/s 7224) and doesn't need **qt**; it's still **gtk2**.

@ibjsb4, have you tried just Openbox and **no** desktop environment? I started a [thread here]("http://ubuntuforums.org/showthread.php?t=2173126") and I've been using pure Openbox (no DE) for most of 13.10. (But it's a bit lonely ;) )

---

### Post by ibjsb4 on 2014-03-30
@kansasnoob, I will be content with ff; chrome runs a little faster and uses less resources.


@vasa1, Ob and no-desktop?  Never tried it, but looks promising.  I quickly read your thread and I must say that it doesn't look easy to customize.  I'm a fan of dconf-tools (i know gnome only) for color themes and other changes.  Looks like Ob relies on the command line.


Synaptic will not launch from menu, but will launch from terminal.  My /usr/share/applications/synaptic:


```
[Desktop Entry]
Name=Synaptic Package Manager
GenericName=Package Manager
Comment=Install, remove and upgrade software packages
[COLOR=#ff0000]Exec=synaptic-pkexec  ##is this correct?[/COLOR]
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;Settings;
NotShowIn=KDE;
X-Ubuntu-Gettext-Domain=synaptic

```

---

### Post by vasa1 on 2014-03-30
> **ibjsb4 said:**
> ...
@vasa1, Ob and no-desktop?  Never tried it, but looks promising.  I quickly read your thread and I must say that it doesn't look easy to customize.  I'm a fan of dconf-tools (i know gnome only) for color themes and other changes.  Looks like Ob relies on the command line.


Synaptic will not launch from menu, but will launch from terminal.  My /usr/share/applications/synaptic:


```
[Desktop Entry]
Name=Synaptic Package Manager
GenericName=Package Manager
Comment=Install, remove and upgrade software packages
[COLOR=#ff0000]Exec=synaptic-pkexec  ##is this correct?[/COLOR]
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;Settings;
NotShowIn=KDE;
X-Ubuntu-Gettext-Domain=synaptic

```
Yes, it wasn't easy at first. I had to ask around quite a bit. (Stinkeye helped me a lot but now he's left :( .)

Re. Synaptic, I don't have it installed anymore but I think I made a .desktop file in ~/.local/share/applications like this:
```
[Desktop Entry]
Name=Software & Updates
#GenericName=Software & Updates
#Keywords=Drivers;Repositories;Repository;PPA;
Exec=gksudo software-properties-gtk
Icon=software-properties
Type=Application

```

So the Exec=line would have **gksudo synaptic** instead of **gksudo software-properties-gtk**. I've been followed this whole pkexec business from a distance. It seems quite complex and not yet "settled" (to me).

Re. themes and icons, there are a couple of files that need to be edited; at least that's how I did it. We don't really need the command line for that. Any editor would do.

---

### Post by ibjsb4 on 2014-03-30
```
[Desktop Entry]
Name=Synaptic Package Manager
GenericName=Package Manager
Comment=Install, remove and upgrade software packages
[COLOR=#ff0000]#Exec=synaptic-pkexec[/COLOR]
[COLOR=#ff0000]Exec=gksudo synaptic[/COLOR]
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;Settings;
NotShowIn=KDE;
X-Ubuntu-Gettext-Domain=synaptic

```

And its fixed, go figure :)

---

### Post by sudodus on 2014-03-30
> **vasa1 said:**
> ibjsb4 and kansasnoob, can we talk about lighter browsers in a new thread? I would like people's opinions on Xombrero ([Unit193's ppa @ Launchpad]("https://launchpad.net/~unit193/+archive/xombrero")). Xombrero has a smaller installed size (546 v/s 7224) and doesn't need **qt**; it's still **gtk2**.

@ibjsb4, have you tried just Openbox and **no** desktop environment? I started a [thread here]("http://ubuntuforums.org/showthread.php?t=2173126") and I've been using pure Openbox (no DE) for most of 13.10. (But it's a bit lonely ;) )

I can add ***Midori*** as a light browser candidate.

-o-

And maybe you would like to test a convenient way to install Lubuntu Core Trusty. Try the debian based installer ***9w*** and install it by expanding a compressed image file. See these links (posts #88, 89 and the following in the Ubuntu Forum thread

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

You can download 9w installers from this link where you can find iso files with a single image file (to use with a CD drive) and a multi-installer iso file (to use with a DVD or USB drive).

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

---

### Post by ibjsb4 on 2014-03-31
> **vasa1 said:**
> @ibjsb4, have you tried just Openbox and **no** desktop environment? I started a [thread here]("http://ubuntuforums.org/showthread.php?t=2173126") and I've been using pure Openbox (no DE) for most of 13.10. (But it's a bit lonely ;) )

Thanks to all for the input.  I'm marking this thread solved (Lubuntu is working fine) and moving on to play a bit with OpenBox.

---

