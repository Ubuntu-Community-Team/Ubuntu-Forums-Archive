---
title: "How to get pdigin into message tray 12.10?"
date: 2012-09-29
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ELD on 2012-09-29
Is there a way to get pidgin to show up in the message tray in 12.10? Doesn't work currently.

---

### Post by ELD on 2012-10-03
BUMP - No one using Pidgin?

---

### Post by pressureman on 2012-10-03
In Pidgin, Tools > Preferences > Interface; set "Show system tray icon" to "Always".

---

### Post by ELD on 2012-10-03
System tray != Message tray icon.

Setting it to always gives Pidigin it's own icon which you then have to whitelist.

---

### Post by thotz on 2012-10-03
Same problem here, yes there a pidgin users :)

---

### Post by ELD on 2012-10-03
So you haven't figured out how to get it to work? Has anyone done a bug report against message indicator or shall i?

Edit > I did the bug report [https://bugs.launchpad.net/indicator-messages/+bug/1060878](https://bugs.launchpad.net/indicator-messages/+bug/1060878)

---

### Post by pressureman on 2012-10-03
Well maybe if you clarified what desktop environment you're using...

Works fine for me in Gnome Shell.

---

### Post by ELD on 2012-10-03
> **pressureman said:**
> Well maybe if you clarified what desktop environment you're using...

Works fine for me in Gnome Shell.

If i was using anything other than Unity i would have put it and i wouldn't use the "Ubuntu" tag...

---

### Post by Aenima99x on 2012-10-03
I've managed to get Pidgin to show in the messaging menu, but it's not fully integrated. It will launch Pidgin from the menu, but it doesn't show any status. You can add it to the messaging menu through dconf editor. It's under com/canonical/indicator/messages. Just add in pidgin.desktop the entries.
Also, there is already a bug report open for pidgin and the other main messaging indicators here - [https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/1040259](https://bugs.launchpad.net/ubuntu/+source/indicator-messages/+bug/1040259)

---

### Post by pressureman on 2012-10-03
> **ELD said:**
> If i was using anything other than Unity i would have put it and i wouldn't use the "Ubuntu" tag...

Ubuntu != Unity

Just because there is a Gnome respin now, doesn't mean all Gnome Shell users have suddenly flocked over to it. Some of us simply install Gnome Shell alongside Unity.

Anyway, best of luck solving your problem.

---

### Post by ELD on 2012-10-04
> **pressureman said:**
> Ubuntu != Unity

Just because there is a Gnome respin now, doesn't mean all Gnome Shell users have suddenly flocked over to it. Some of us simply install Gnome Shell alongside Unity.

Anyway, best of luck solving your problem.

There was no need to carry on this is nothing to do with my bug report.

FYI Ubuntu does = Unity as stock Ubuntu is Unity, all others have names, Kubuntu, Xubuntu etc.

As pointed out earlier this is a known issue and part of a bigger bug report, marking as solved since it has someone assigned.

---

### Post by Elfy on 2012-10-04
Closed.

---

