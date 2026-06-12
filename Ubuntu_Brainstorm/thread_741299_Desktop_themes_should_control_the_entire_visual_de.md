---
title: "Desktop themes should control the entire visual design"
date: 2008-03-31
forum: Ubuntu Brainstorm
---

### Post by Mr. Picklesworth on 2008-03-31
At present, the appearance of one's desktop is selected in two places:
-Theme for controls / icons / window borders
-Desktop effects

At first glance, one may think "these have no relation to each other; why complicate things?"; after all, Wallpaper and Interface also affect desktop appearance.

What concerns me here, however, is how effects from the window decorator have a very real impact on the feel of the desktop as determined by that first theme selection. For example, my current desktop has no window borders; just a title bar. Without compositing, that theme is unbearable because one cannot differentiate between windows at a glance. However, if I turn on even Metacity's compositing system, the added shadows make it not only work but work *well*.

One other thing to note is that the Appearance capplet is obviously designed to affect the entire visual style; it could all be a single Theme selection, but that would be entirely pointless since we would just end up with today's Appearance preferences inside a Customize button. (Bringing back horrible memories of Redmond's Control Panel).
The simplest fix here is that perhaps themes could suggest desktop effects settings as they do background images. That would have to be applied upstream, since we wouldn't want to complicate GNOME's themes. Problem: GNOME does not have a desktop effects selection on its own.
Perhaps a fix would be for themes to suggest *gconf keys*, for example /desktop/gnome/applications/window_manager/current = /usr/bin/metacity, and /apps/metacity/general/compositing_manager = True...

Of course, the problem of people all having different software available still pops in. Maybe an even more vague thing, where the theme simply says "Use compositing for best results!" and the configuration software sorts out what to do. (Shouldn't the themes be drawing these window shadows themselves anyway?)

---

### Post by xelapond on 2008-04-07
I think this kind of goes against Linux's tendency to make you do everything yourself:)  It could work, but some of us want total customization, and also, how would it know?

---

