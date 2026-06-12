---
title: "No right-click-menu in the desktop (Unity)"
date: 2012-09-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-09-27
After update & upgrade today I noticed my right-click-menu in the desktop was gone. 

My workaround was to run Nautilus...

> $ nautilus &


...and my right-click-menu is back. But I have to do that every time I start a desktop session.

Regards,
Effenberg

---

### Post by jbicha on 2012-09-27
Do you have ubuntu-settings installed?
By the way, Ubuntu GNOME Remix does not have Nautilus handle the desktop by default.

---

### Post by effenberg0x0 on 2012-09-27
[QUOTE=jbicha;12265089]Do you have ubuntu-settings installed?


Hi, yes, it's installed:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-settings is already the newest version.
```

I'll wait for more updates, apparently no one else is reporting it. Maybe it's something I did here.

Regards,
Effenberg

---

### Post by mc4man on 2012-09-27
If it doesn't self heal then you can thru org.gnome.desktop.background > show-desktop-icons
(by default it's not enabled as the override should override
You can toggle it a time or two or three 
(again  - once toggled a bit if you reset key to 'default' you'll still get nautilus handling the desktop in an ubuntu session even though it's disabled in dconf

---

### Post by ventrical on 2012-09-27
> **effenberg0x0 said:**
> [QUOTE=jbicha;12265089]Do you have ubuntu-settings installed?


Hi, yes, it's installed:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-settings is already the newest version.
```I'll wait for more updates, apparently no one else is reporting it. Maybe it's something I did here.

Regards,
Effenberg

 I got it too - from todays updates. No right click menu!

---

### Post by effenberg0x0 on 2012-09-27
> **ventrical said:**
> [QUOTE=effenberg0x0;12265151]

 I got it too - from todays updates. No right click menu!

It's actually a relief to see it affects someone else. I've been switching between 4 maximized Tilda tabs all day long (1 local, 3 SSH), throwing commands like crazy to setup 3 remote servers from scratch to Xen + Ubuntu + Lamp + OpenSSH Key-based auth + VSFTPd + Postfix + Dovecot + Clamav + Squirrelmail + WordPress + WP Template + Customize WP Template + 4 VirtualHosts/Domains/Mail each + proprietary stuff + Snapshots + etc....... After many hours of that it's easy for me to make a mistake and run commands in the wrong tab/machine or add a wrong char or space to a command/wildcard and mess things up. Wouldn't be the first time I screw up.

Regards,
Effenberg

---

### Post by ventrical on 2012-09-27
Sorry I could not get back sooner. Just too dern busy.

---

### Post by Yougo on 2012-09-30
according to [this thread](http://ubuntuforums.org/showthread.php?t=2059014&highlight=unity+nautilus)

uninstalling and reinstalling unity-settings does the trick if it is installed but not working right

---

### Post by ventrical on 2012-09-30
> **Yougo said:**
> according to [this thread]("http://ubuntuforums.org/showthread.php?t=2059014&highlight=unity+nautilus")

uninstalling and reinstalling unity-settings does the trick if it is installed but not working right


Can't find unity-settings in the repos.

---

### Post by mc4man on 2012-09-30
ubuntu-setting

---

### Post by ventrical on 2012-09-30
> **mc4man said:**
> ubuntu-setting


+1 ;)

Even got my desktop back ! :)

---

### Post by VinDSL on 2012-10-01
> **effenberg0x0 said:**
> After update & upgrade today I noticed my right-click-menu in the desktop was gone. 

...and my right-click-menu is back. But I have to do that every time I start a desktop session.
Interesting!  

"right-click-menu in the desktop" hasn't worked for me, in some time -- probably 6 months, in "tester years".  ;)

Yes, ubu-setting was AWOL, so I went ahead and installed it.  Big mistake!  

Heh!  After I get done submitting this reply, I'm going to purge it.  Allow me to explain...

[LIST]
[*]I've grown to h-a-t-e Nautilus!  The only reason it's on my HDD is because 3.4.2 magically reappeared (like a virus) during an update, and I left it there (like a dummy)!


[*]The only time "right-click-menu in the desktop" works is when a Nautilus window is open. Close the window, and it goes away again.


[*]The big one... when a Nautilus window is open, and I open a file with root auth (for instance, to edit a file in /usr/share/) my friggin' desktop wallpaper is overwritten by the most hideous background Ubu ever published.  Looks like Haiti after a Cat 5 hurricane!


[*]When I say "overwritten" I mean it simply covers-up the original wallpaper.  The only way to get back to the original wall is to log out of the session, or reboot.


[*]When the session is closing down, and objects are slowly disappearing from the desktop, one-by-one, you can see the original wall sitting there, pouting in the background, just before the session stops.


[*]When I log into a new session, the original wallpaper returns... until I open a file "as root" in Nautilus.
[/LIST]

Anyway, thanks for bringing this to light.  Now, I know how to get rid of the problem...  LoL!  :D

---

### Post by philinux on 2012-10-01
Worky here but that's a clean install.

---

