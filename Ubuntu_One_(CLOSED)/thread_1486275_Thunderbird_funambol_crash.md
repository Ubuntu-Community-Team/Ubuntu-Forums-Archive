---
title: "Thunderbird funambol crash"
date: 2010-05-17
forum: Ubuntu One (CLOSED)
---

### Post by miguelastico on 2010-05-17
Hi, since a couple of hours ago I noticed that my thunderbird started crashing when starting.
After a couple of install, remove, change profile, restore profile and so on, I discovered that the funambol plugin is causing the problem

the error I got at startup was:
```
(crashreporter:2534): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
```

And it's just by chance that I tried disabling funambol.

Thunderbird starts correctly when I disable network, but if the network is on there is no way to make it start (if funambol is enabled)

I use funambol only for ubuntu one contacts

Do someone know if this is a known bug, and, if so, which is the solution?

Thanks

---

### Post by EmanresuusernamE on 2010-05-26
Seems to be a bug in Funambol as my Thunderbird is crashing on me when ever it attempts to sync.  This is the Windows Thunderbird too, so it seems to be scope wide so far.  Need a Mac user to confirm it now. :)

If I uninstall it and reinstall it, it will work for awhile, but then start to die horribly over and over again whenever the sync occurs.  Disable the sync at startup and see if that's why you can't load Thunderbird with Funambol enabled.

---

### Post by craig100 on 2010-06-20
I get this too. Using Lucid x64 and Thunderbird 3.0.4

---

