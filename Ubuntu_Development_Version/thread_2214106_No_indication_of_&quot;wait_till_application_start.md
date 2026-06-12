---
title: "No indication of &quot;wait till application starts&quot; (no hourglass or rolling circle)"
date: 2014-03-30
forum: Ubuntu Development Version
---

### Post by GeorgeVita on 2014-03-30
Now running "current" **lubuntu** daily .iso, when I clicked at "Web Browser" launch icon to start browsing **there is NO indication that the application execution began** and the user must wait (ex. hourglass, rolling circle, change in color of the icon). This is a little bit confusing ...

The same happens if you are using a time consuming command as "Search for a file" (Menu > Accessories > File Manager > Tools > Find Files).
The only indicator is the "HD working" LED!

Is there any "application startup indicator enable" somewhere to preference settings? If no, do we have a bug report already?

---

### Post by bapoumba on 2014-03-30
I have the same behavior, if that can help. Just supposed it was by design.. I think I read something about that somewhere, I'll try to see if I can find it again.
Edit : not the one I was thinking of, but close enough [http://forum.lxde.org/viewtopic.php?f=8&t=36351](http://forum.lxde.org/viewtopic.php?f=8&t=36351)
Edit nb2 : when Chrome waits for a page to load, here on the forums for ex, the cursor does change to a spinning circle. What I read was it was left to applications to use it or not.

---

### Post by GeorgeVita on 2014-03-30
> **bapoumba said:**
> I have the same behavior, if that can help. Just supposed it was by design.. I think I read something about that somewhere, I'll try to see if I can find it again.
Edit : not the one I was thinking of, but close enough [http://forum.lxde.org/viewtopic.php?f=8&t=36351](http://forum.lxde.org/viewtopic.php?f=8&t=36351)
Edit nb2 : when Chrome waits for a page to load, here on the forums for ex, the cursor does change to a spinning circle. What I read was it was left to applications to use it or not.


Thanks for the link, actually I have the same configuration with Rex (mod @ lxde forum) who mentions it as [a minor problem]("http://forum.lxde.org/viewtopic.php?f=8&t=36351#p48417").

In my EeePC, first firefox run appear after 6-7 seconds of "no indication". Possibly a faster PC minimizes the time lug, but "[Lubuntu has very low hardware requirements]("http://lubuntu.net/")" and main target could be XP-PCs.

I tried to find other ideas but I got dissapointed as there is no "single trim" to get it.
Now I am trying to find an existing bug report, otherwise will make one after final release.

---

### Post by bapoumba on 2014-03-30
Now there is something I have been looking at, is try to set the StartupNotify=true, but have not found where it is.. I have no .desktop file in my /home.
```
grep -H -r "StartupNotify" /home/bapoumba_lxde/
```
Returns only Chromium cached files from this thread or my searches..

---

### Post by GeorgeVita on 2014-03-30
> **GeorgeVita said:**
> ...The same happens if you are using a time consuming command as "Search for a file" (Menu > Accessories > File Manager > Tools > Find Files).
The only indicator is the "HD working" LED! ...

> **bapoumba said:**
> ...  I have been looking ... I have no .desktop file in my /home.

Try the "typical file search" as a "typical" (not technical) user will do.
The "HD working" LED or the "HD head movement sound" will be your assistant...

---

### Post by bapoumba on 2014-03-30
> **GeorgeVita said:**
> Try the "typical file search" as a "typical" (not technical) user will do.
The "HD working" LED or the "HD head movement sound" will be your assistant...
When I search for .desktop in my /home with PCManFM 1.2.0, I have a spinning wheel. Looks like I cannot take a screenshot, as even with a timed screenshot, the cursor turns to the regular arrow when the screen is captured.. You'll have to take my word for it :)

---

### Post by GeorgeVita on 2014-03-30
Thanks for declaring, this helps me to try it more!
About ".desktop", using terminal:
```
sudo find / -name firefox.desktop
```
I found it but it was already set: StartupNotify=true
(file: /usr/share/applications/firefox.desktop)

Now running Lubuntu 13.10, I'll try also using latest daily .iso.

---

### Post by bapoumba on 2014-03-30
> **GeorgeVita said:**
> Thanks for declaring, this helps me to try it more!
About ".desktop", using terminal:
```
sudo find / -name firefox.desktop
```
I found it but it was already set: StartupNotify=true
(file: /usr/share/applications/firefox.desktop)

Now running Lubuntu 13.10, I'll try also using latest daily .iso.

/o\ Why was I stuck on the idea this was going to be a /home file ?
Same here for /usr/share/applications/firefox.desktop BTW.

---

### Post by mc4man on 2014-03-30
I don't use lubuntu so more of an aside regarding "StartupNotify=true" in a .desktop
That may not be enough, at least in recent history,  to cause 'cursor spin' while an app is opening.
An example would be Ubuntu/compiz where it wasn't always happening which lead to this bug
[https://bugs.launchpad.net/compiz/+bug/1179155](https://bugs.launchpad.net/compiz/+bug/1179155)

In the case of compiz they did decide to fix thru [rev. 3696]("http://bazaar.launchpad.net/~compiz-team/compiz/0.9.10/revision/3696") so probably lubuntu would need to address specifically like ubuntu/compiz did.

(myself revert 3696 for the compiz I use here as it has some unintended effects & with newish hardware nothing takes more than 1 sec. or so to open at worst...

---

### Post by GeorgeVita on 2014-03-31
> **mc4man said:**
> ...  regarding "StartupNotify=true" in a .desktop
That may not be enough, ...
Also we found that this parameter is already set to "true", but also setting to "false" makes no difference! Possibly, as LXDE is minimal, it does not check this flag.

Trying to identify the reason for the long start time of firefox, I got better times (aprox 4 sec.) after reseting firefox (no addons, no home page, etc.).
This reveal another problem existing in Lubuntu 13.10 but not in Ubuntu:
```
(process:2366): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkRange::activate-slider' of type `gboolean' from rc file value "((GString*) 0xaf0ecd40)" of type `GString'
```

In any case, it is not a solution to trim every launcher for "slow startup" applications (ex. firefox with add-ons).
At this time it seems that we have to live without "application startup notification" in Lubuntu.

---

