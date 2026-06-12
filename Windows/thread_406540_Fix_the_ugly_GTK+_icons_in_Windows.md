---
title: "Fix the ugly GTK+ icons in Windows"
date: 2007-04-11
forum: Windows
---

### Post by detyabozhye on 2007-04-11
OK, so I got some people to start using Gaim^W Pidgin on Windows, and using the GTK-Wimp theme it looks fine, but when using the open/save file dialog or just using the menus, the stock GTK+ icons are just ugly.

I tried searching all over the Internet on how to change them in Windows. Then I decided to try by myself since I didn't find anything. I copied the Tango icon theme from Ubuntu to C:\Program Files\Common Files\GTK\2.0\share\icons\ and adding the line gtk-icon-theme-name = "Tango" to the gtkrc file in C:\Program Files\Common Files\GTK\2.0\etc\gtk-2.0\ (twice, first time I crashed Windows somehow and the changes didn't get saved) and it worked!

What I'm wondering is why hasn't anyone said anything about this yet anywhere? Lots of Windoze users use GTK apps, haven't they noticed the ugly icons yet?

---

### Post by sloggerkhan on 2007-04-11
most windows icons are ugly. Plus windows users have an atitude of "what can you expect from something free?" (Answering themselves with a rhetorical "very little.")

---

### Post by detyabozhye on 2007-04-11
True, but won't they care to see that it doens't have to be ugly?

---

### Post by sloggerkhan on 2007-04-11
You have a point. If open source apps were always pretty, it might help change such perceptions.

---

