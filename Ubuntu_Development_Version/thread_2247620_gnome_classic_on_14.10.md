---
title: "gnome classic on 14.10"
date: 2014-10-09
forum: Ubuntu Development Version
---

### Post by RoadRunnr on 2014-10-09
Hi,

Just installed a new 14.10 test VM with server installation and then added the gnome-desktop task. The login screen lets me choose between GNOME and GNOME Classic session. However, both are exactly the same. How do I get the normal GNOME Classic session back?

Andreas

---

### Post by slickymaster on 2014-10-09
Press Ctrl+Alt+T to open the terminal and run the following commands:```
sudo apt-get update
sudo apt-get install gnome-session-fallback
```Or open the Ubuntu Software Centre and search for &#8220;gnome-session-flashback".

Once installed, log out the current session. When you&#8217;re in log-in screen, click the logo icon and select log in to Gnome Flashback (Compiz) or Gnome Flashback (Metacity).

---

### Post by grahammechanical on 2014-10-09
Please explain what you mean by "normal Gnome Classic."

The Gnome developers stopped work on Gnome 2 panel years ago, which people now refer to as "classic." The Gnome 3 desktop gives us the Gnome 3 shell. It is possible to install a shell extension that resembles the look of Gnome 2 panel but it is still obvious that you are using Gnome 3 shell with an expanding menu system.

What was called Gnome classic in 12.04 is gone from 14.04 and onwards. But we do have gnome-session-flashback. It give us two extra options at login. Gnome Flashback (Compiz) and Gnome flashback (metacity). Both have a similar look to what you might be thinking of as "Gnome Classic."

For something much closer to Gnome 2 panel have a look at Ubuntu Mate. It is based upon 14.10 code and not yet a flavour of Ubuntu. But the developers have applied for approved flavour status.

[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

Regards.

---

### Post by kansasnoob on 2014-10-13
I just noticed this in Ubuntu GNOME Utopic so I asked at Ubuntu GNOME QA (and cc;ed the lead dev):

[https://lists.launchpad.net/ubuntugnome-qa/msg00578.html](https://lists.launchpad.net/ubuntugnome-qa/msg00578.html)

> **Utopic Classic session looks just like 'gnome-shell' session**

I don't typically use the Classic session so I hadn't paid any attention until now but it appears that no extensions are activated as they should be when selecting the Classic session at login, so it looks identical to the default 'gnome-shell' session. Come to think of it though, in Trusty I believe the Classic session used the 'clearlooks-phenix' theme, but in Utopic it's using 'adwaita' just like the default session.


Could you try logging into a Classic session and see what happens on your end? I've made very, very few changes post-install, certainly nothing that should break the Classic session. I'll be glad to open a new bug report if you'd like. 

---

### Post by kansasnoob on 2014-10-14
I need to steal some white-board space :biggrin:

```
lance@lance-desktop:~$ echo $DESKTOP_SESSION
gnome-classic
lance@lance-desktop:~$ gnome-shell --mode=classic --replace
libGL error: Version 4 or later of flush extension not found
libGL error: failed to load driver: i915
Gjs-Message: JS LOG: No permission to trigger offline updates: Polkit.Error: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: Action org.freedesktop.packagekit.trigger-offline-update is not registered
Gjs-Message: JS LOG: GNOME Shell started at Tue Oct 14 2014 06:26:28 GMT-0500 (CDT)
Gjs-Message: JS LOG: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name :1.127 was not provided by any .service files


```

---

### Post by kansasnoob on 2014-10-14
There is now a bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1381297](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1381297)

---

### Post by VinDSL on 2014-10-15
Added a 'me too'...  ;)

---

