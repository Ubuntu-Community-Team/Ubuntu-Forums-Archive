---
title: "Two Notification Applets?"
date: 2010-05-22
forum: The Cafe
---

### Post by emanuel.b on 2010-05-22
This is one of the first things I noticed when upgrading to 10.04. There are two notification applets now. The native GNOME applet by Red Hat, and a new one by Canonical. It seems like they're made it to hold all their custom items. On my computer, all the notification icons appear on the Canonical one, but only the network icon appears on the other. What gives!? I'd like only one applet, thank you. Either they should move all the notification icons to the new one, or switch back to the old one. Is anyone else on the same page here?

(I know this seems pointless, but it just bugs the heck out of me.)

---

### Post by ingvildr on 2010-05-22
They are planning on removing the old notification area in the next release i think, just left both there for the moment while they modify existing apps to use the new one.

---

### Post by emanuel.b on 2010-05-22
> **ingvildr said:**
> They are planning on removing the old notification area in the next release i think, just left both there for the moment while they modify existing apps to use the new one.
I certainly hope so. I guess the folks at Canonical are trying to give Ubuntu it's own sense of originality.

---

### Post by pelle.k on 2010-05-23
> **emanuel.b said:**
> This is one of the first things I noticed when upgrading to 10.04. There are two notification applets now. The native GNOME applet by Red Hat, and a new one by Canonical. It seems like they're made it to hold all their custom items. On my computer, all the notification icons appear on the Canonical one, but only the network icon appears on the other. What gives!? I'd like only one applet, thank you. Either they should move all the notification icons to the new one, or switch back to the old one. Is anyone else on the same page here?

(I know this seems pointless, but it just bugs the heck out of me.)

I'll tell you what bugs the heck out of me; the fact that the original notification area uses much less padding to other icons than the new indicator-applet does.
Also, why did they port the rhythmbox notification icon to indicator applet? You can't click the icon to iconify/deiconify it (with a single click) anymore.

It seems to me we need both. Why not keep *real* applets (that have no real main window) in the indicator-applet, and use the old notification area for appz that want to iconify (or minimize to tray as they say). That way, you can single click them to bring them out of/ in to the tray, while keeping a dropdown menu (using right clicking) for menu access.

Do you see the difference here, and how that might be an advantage to using only indicator-applet? So in my mind, porting everything to indicator-applet is a fail.

---

