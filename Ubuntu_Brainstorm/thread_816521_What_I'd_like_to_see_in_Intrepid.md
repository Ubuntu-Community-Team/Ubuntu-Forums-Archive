---
title: "What I'd like to see in Intrepid"
date: 2008-06-02
forum: Ubuntu Brainstorm
---

### Post by AdrianStrays on 2008-06-02
I don't know if there is a place for ideas, so I'll just post here.  One of the things that excited me about Ubuntu was multiple desktops.  The idea that on one desktop I could have a set of certain icons with a unique background that was different than another one.  I was depressed to find that this wasn't the actual case. I think the workspace idea is good, but isn't fully fleshed out and I'd love to see it "completed".  I think those are the kinds of innovative features that set an OS apart, and end up being the standard in future versions of all OS's.

---

### Post by smartboyathome on 2008-06-02
This would take too much memory and CPU, as it would have to store each desktop in memory and fetch it when you switch. It would also cause a noticable delay when changing desktops.

---

### Post by Neon Lights on 2008-06-02
This is something being worked upon. ;]

---

### Post by james09173 on 2008-06-03
I had a Windows program that gave me a real 6-sided Cube desktop and I could pick a different desktop background for each one. So that, at least, should be doable in Compiz down the road if it's not already. 

As for each desktop having its own set of icons, that's a different story. Haven't seen anything do that, but it would be an interesting feature.

---

### Post by irrdev on 2008-06-03
> **james09173 said:**
> I had a Windows program that gave me a real 6-sided Cube desktop and I could pick a different desktop background for each one. So that, at least, should be doable in Compiz down the road if it's not already. 

...

KDE allows for you to associate different desktop backgrounds with different desktops. The downside is that Kwin doesn't support the above-mentioned "cube" effect. You might want to still check it out though. ;)

---

### Post by smartboyathome on 2008-06-03
> **james09173 said:**
> I had a Windows program that gave me a real 6-sided Cube desktop and I could pick a different desktop background for each one. So that, at least, should be doable in Compiz down the road if it's not already.

It already is with a patch to Nautilus.

---

### Post by AdrianStrays on 2008-06-04
A background and some short cuts don't seem like they would take up too much.  Either way, the feature could be flipped off.

---

### Post by smartboyathome on 2008-06-04
> **AdrianStrays said:**
> A background and some short cuts don't seem like they would take up too much.  Either way, the feature could be flipped off.

They wouldn't be shortcuts. While the background wouldn't be hard, the icons would. You would have to have 1 instance of nautilus open per desktop, and when you get up to 4, that can mean tons of memory and cpu.

---

### Post by tom56 on 2008-06-07
> **smartboyathome said:**
> They wouldn't be shortcuts. While the background wouldn't be hard, the icons would. You would have to have 1 instance of nautilus open per desktop, and when you get up to 4, that can mean tons of memory and cpu.

It needn't work like that, though it would be difficult to implement. What you'd likely do is add a new line (Desktop) to whatever.desktop like in the example below, and then nautilus only displays it depending on which desktop you are looking at.
```
[Desktop Entry]
Encoding=UTF-8
Name=Pidgin Internet Messenger
GenericName=Internet Messenger
Comment=Send instant messages over multiple protocols
Exec=pidgin
Icon=pidgin
StartupNotify=true
Terminal=false
Type=Application
Categories=Network;InstantMessaging;
X-Ubuntu-Gettext-Domain=pidgin
**Desktop=1**
*or maybe*
**Desktop=2**
*or even*
**Desktop=all**
```

The desktop background idea is being worked on already I believe.

---

### Post by smartboyathome on 2008-06-07
That could work. Though that would mean you would need Nautilus to hide everything that initially goes onto the desktop and replace it with a desktop file (not that hard, really).

---

