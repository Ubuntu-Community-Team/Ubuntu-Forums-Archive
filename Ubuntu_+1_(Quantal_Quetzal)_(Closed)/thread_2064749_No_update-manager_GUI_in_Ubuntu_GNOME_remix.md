---
title: "No update-manager GUI in Ubuntu GNOME remix?"
date: 2012-09-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-09-30
I've never followed Gnome dev enough to know what a "virgin" gnome version 3 default DE should have installed by default so excuse my dumb question :)

I've been playing with Jeremy Bicha's Ubuntu GNOME Remix quite a bit the past few days and I'm really impressed, but I notice there is no GUI for 'update-manager' installed by default. Is that an intentional move by Gnome?

It's not a big deal, just something I'm curious about.

---

### Post by Harry33 on 2012-09-30
Update Manager was originally written for Ubuntu, now it is a part of Debian.
Starting from Ubuntu 12.10 (QQ), the Update Manager is called
the Software Updater.
[https://launchpad.net/update-manager](https://launchpad.net/update-manager)

So, I think it was an intentional move.

---

### Post by mc4man on 2012-09-30
It's got an app named Software, open it & in the app menu select 'check for updates'

---

### Post by kansasnoob on 2012-09-30
I knew about the name change but the package name is still 'update-manager' AFAIK. I've particularly been testing classic (no effects) and the Software Updater GUI is just not there in System > Admin by default.

But I'd previously installed synaptic (just because it simplifies parsing package names, etc) so I installed 'update-manager' and then Software Updater appears in the menu:

> Start-Date: 2012-09-29  11:40:17
Commandline: /usr/sbin/synaptic
Install: update-manager:i386 (0.174.1), update-notifier:i386 (0.122, automatic), ubuntu-release-upgrader-gtk:i386 (0.181, automatic)
End-Date: 2012-09-29  11:40:29


---

### Post by kansasnoob on 2012-09-30
> **mc4man said:**
> It's got an app named Software, open it & in the app menu select 'check for updates'

Aha, so Gnome made their software manager work for both installing and updating software, eh :confused:

---

### Post by kansasnoob on 2012-09-30
OK, in gnome shell you can display "check for updates" like this:

[ATTACH]224886[/ATTACH]

But in classic there appears to be no way other than installing the package 'update-manager':

[ATTACH]224887[/ATTACH]

That's easy enough :D

---

### Post by Kirk M on 2012-09-30
> **mc4man said:**
> It's got an app named Software, open it & in the app menu select 'check for updates'

Ah, that covers my next question about the Ubuntu Gnome Remix then. Users are going to have to get used to to right-clicking on the application icon in the "panel" for access to what used to be in the application menu bar. No big deal really, it just takes some getting used to.

Now, is it me or did previous versions of Gnome 3/gnome-shell not have a right-clickable application icon in the panel? It's been awhile since I last used gnome-shell.

---

### Post by kansasnoob on 2012-09-30
> **Kirk M said:**
> Ah, that covers my next question about the Ubuntu Gnome Remix then. Users are going to have to get used to to right-clicking on the application icon in the "panel" for access to what used to be in the application menu bar. No big deal really, it just takes some getting used to.

Now, is it me or did previous versions of Gnome 3/gnome-shell not have a right-clickable application icon in the panel? It's been awhile since I last used gnome-shell.

I hadn't thought about right-clicking the displayed app in 'gnome-panel' but knowing that eliminates the need to install 'update-manager' :)

---

