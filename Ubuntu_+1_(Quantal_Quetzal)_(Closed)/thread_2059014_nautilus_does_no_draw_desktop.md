---
title: "nautilus does no draw desktop"
date: 2012-09-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by funicorn on 2012-09-17
I upgraded from 12.04 to 12.10 and found something wrong with 'Desktop' , by which I mean what is shown when all windows are minimized. And I found

1. 'Desktop' does NOT response to mouse right-click.
2.  Desktop icons are gone too. 
3. In addition, when all windows are minimized, pressing 'super' cannot popup unity dash  

I checked in gconf-editor that bool value of key 'apps/nautilus/preference' 'show desktop' is unchecked (which was sure checked before upgrade). So I rechecked 
it and re-login, however 'Desktop' is still malfunctioning. Then I checked in gonf-editor and found that key value was unchecked again.

Hence I think there's something wrong with nautilus drawing desktop feature or something wrong with gnome conf framework.

Anyone else encountered similar problem and any suggestion to fix it ?

---

### Post by mc4man on 2012-09-17
Most settings are in dconf so open dconf-editor & as in screen
If need be toggle the setting till fixed

---

### Post by funicorn on 2012-09-17
thank you very much ! I checked in dconf-editor and found the key 'show desktop' is already checked, but the key 'show desktop icon' is not. Hence I checked it and everything goes right.

---

### Post by jbicha on 2012-09-17
Just curious, do you have ubuntu-settings installed?

---

### Post by funicorn on 2012-09-18
At first I do not, then I googled and had it installed. But Desktop works until I set  'show dekstop icon' true in gsettings. what is ubuntu-settings?

---

### Post by jbicha on 2012-09-18
ubuntu-settings is a new package containing most of the gsettings overrides the Ubuntu developers added to GNOME packages. By putting them in a separate package, it makes it easier to merge GNOME packages with Debian (one less Ubuntu-specific change) and it makes it easier for derivatives like the Ubuntu GNOME Remix to clearly see what's been changed and either copy those changes or override them if they wish.

If you have ubuntu-desktop installed, you should have ubuntu-settings installed (you may need to do a dist-upgrade). ubuntu-settings tells Nautilus to draw the desktop by default.

---

### Post by mc4man on 2012-09-18
At this point I think the ubuntu-settings.overrides ect. seems to be working well, haven't tried an upgrade yet though.

One thing to keep in mind is that dconf-editor won't always  show the results of these settings/overrides unless they were also user set.

So in this example nautilus should be managing the Desktop even if dconf-editor shows it disabled.

For upgraders with an existing ~/.config/dconf/user file it all should probably be ok though there may be some room for misbehavior of sorts

---

### Post by sacridex on 2012-09-18
Thank the heavens, I was almost going insane. ;)
No Desktop, weird fonts, drove me crazy. ^^
But for some reasons ubuntu-settings was uninstalled, reinstalled it, and now its fine!

---

### Post by Yougo on 2012-09-30
Thanks a bunch! somehow ubuntu-settings wasn't installed on my machine either.

:-k it does raise a question though: 

Apparently, Unity expects *something* to draw the desktop, so the desktop can be focused on. 

without Nautilus drawing the desktop + everything minimized, i noticed Unity having very much trouble to decide what to focus, eating my cpu.


see bug: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1059226](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1059226)

---

