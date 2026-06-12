---
title: "New theme for nautilus and gedit doesn't work without root"
date: 2016-10-10
forum: Ubuntu Development Version
---

### Post by straightedge89 on 2016-10-10
I just upgraded and I saw that the new theme for nautilus and gedit (for example), the one with the big action bar on the very top besides the windows control icons it's not working the proper way.

[IMG]http://i.imgur.com/qjJheY3.png[/IMG]

I tried to change the theme to the default one but it's the same.

[IMG]http://i.imgur.com/bqoKtnl.png[/IMG]

So I gave up. Then by accident I used gksudo nautilus and I found that in root (i tried sudo too) it's working fine.

[IMG]http://i.imgur.com/EYttXGJ.png[/IMG]

[IMG]http://i.imgur.com/wrXGXLV.png[/IMG]

---

### Post by dino99 on 2016-10-10
Ubuntu only support adwaita as official theme; goto the tweak tool to switch. The other themes are supported by the community.

---

### Post by straightedge89 on 2016-10-10
Yeah but it's not a theme problem because with radiance or ambiance it's the same.

---

### Post by mc4man on 2016-10-10
Your upper pics (the default in non gnome sessions) have a titlebar & headerbar used like a toolbar. This is done via a patch in nautilus & I'd assume the method used doesn't/can't extend to a root nautilus window. 
So in that case you just get a header bar which is the gnome (gnome-shell) default.

So not a bug & nothing to be done other than 
1. use a gnome session like gnome-shell
2. rebuild nautilus & exclude the patch which may or may not have other consequences in an ubuntu session.

---

### Post by straightedge89 on 2016-10-11
But I did nothing to change it's behaviour, I just upgraded to 16.10. Every pic I found online of Nautilus 3.20 on Ubuntu are like the second set (the one with root) so I think that the headerbar/bar merge is default.
I tryed gedit too and it's the same thing so I think that it's something with gtk 3.0+ applications.
I'm using standard Ubuntu with Unity.

---

### Post by mc4man on 2016-10-11
> **straightedge89 said:**
> But I did nothing to change it's behaviour, I just upgraded to 16.10. Every pic I found online of Nautilus 3.20 on Ubuntu are like the second set (the one with root) so I think that the headerbar/bar merge is default.
I tryed gedit too and it's the same thing so I think that it's something with gtk 3.0+ applications.
I'm using standard Ubuntu with Unity.

As I said - nautilus is patched in Ubuntu to  use a titlebar & headerbar (toolbar) in non gnome sessions. What you see online is what's used in a gnome session.
A root nautilus window is not covered by the patch.

---

