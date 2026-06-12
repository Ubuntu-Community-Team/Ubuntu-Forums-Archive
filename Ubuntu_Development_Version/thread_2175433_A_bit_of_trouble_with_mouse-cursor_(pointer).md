---
title: "A bit of trouble with mouse-cursor (pointer)"
date: 2013-09-19
forum: Ubuntu Development Version
---

### Post by zika on 2013-09-19
I have properly visible mouse-cursor (pointer) in GnomeShell (up-to-date from all PPAs for GS), Enlightenment... But I do not have visible mouse-cursor (pointer) in Unity, Fallback, Cinnamon (while it was installed), etc...
Any idea where to look? Mouse is working and I can see its effect on menus once I get to them „in the dark“...

---

### Post by QDR06VV9 on 2013-09-19
> **zika said:**
> I have properly visible mouse-cursor (pointer) in GnomeShell (up-to-date from all PPAs for GS), Enlightenment... But I do not have visible mouse-cursor (pointer) in Unity, Fallback, Cinnamon (while it was installed), etc...
Any idea where to look? Mouse is working and I can see its effect on menus once I get to them „in the dark“...

Are you running 32 bit OS?
That crops up once in a while for me also but only on my 32 bit installs.
But if I move mouse around a bit it reappears..

---

### Post by zika on 2013-09-19
> **runrickus said:**
> Are you running 32 bit OS?
That crops up once in a while for me also but only on my 32 bit installs.
But if I move mouse around a bit it reappears..
64-bit.
I wish this were as simple as moving the mose... I've tried that, more times than You could imagine...

---

### Post by mc4man on 2013-09-21
Happens here on occasion in a ubuntu(unity) session though a simple ctrl+alt+delete enter > log out/in usually resolves

---

### Post by zika on 2013-09-21
> **mc4man said:**
> Happens here on occasion in a ubuntu(unity) session though a simple ctrl+alt+delete enter > log out/in usually resolvesYes, You are right that as soon as I either log-out or do Ctrl-Alt-Del>Enter pointer returns but I do have little use of that since I'm on the road to GDM login screen at that moment... The moment I get (again) in Unity, pointer is gone... I can hardly call that „resolution“... ;)

---

### Post by zika on 2013-10-21
Solved via:
/org/gnome/settings-daemon/plugins/cursor->false
Update&#8321;: But it works now, even if not applied... It is OK now...

---

### Post by cariboo on 2013-10-21
Seeing as this thread is marked as solved, I'll close it now.

---

### Post by zika on 2013-10-21
> **cariboo907 said:**
> Seeing as this thread is marked as solved, I'll close it now.OK... Thank You.

---

