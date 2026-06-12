---
title: "Remove Ubuntu One from context menu?"
date: 2010-05-23
forum: Ubuntu One (CLOSED)
---

### Post by Vincent Vermeulen on 2010-05-23
Is there any way to remove the "Syncronize on Ubuntu One" item from the Nautilus context menu?

I don't think I can just remove the package ubuntuone-client-gnome, as it also provides a tray applet (or is that depricated for Lucid?):
> Description: Ubuntu One client GNOME integration
 Ubuntu One is a suite of on-line services. This package contains the tray
 applet and Nautilus extension, providing integration with the GNOME desktop.I just don't like my Nautilus context menu to get too full :)

---

### Post by blucht on 2010-07-25
I know this is thread is a little old, but it's still the first Google hit for removing the Ubuntu One contextual menu item so I figure it might be worth a little resurrection. I was clued into the solution by [this]("http://techienotes.info/2009/12/30/how-i-removed-an-annoying-nautilus-context-menu-item/") post. In short, I moved the file 
```
/usr/lib/nautilus/extensions-2.0/libnautilus-ubuntuone.so
``` and, after a quick ```
# killall nautilus
``` the Send to Ubuntu One menu item no longer appears. As a disclaimer, I have no idea how this will break/be broken by future updates to Nautilus or Ubuntu One.

---

