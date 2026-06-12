---
title: "Lost the option to change window focus on mouse over"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by chmac on 2012-04-01
After the recent batch of updates (I'm only able to download updates once a week or so), a couple of things changed in my desktop setup. I've reset most of them, but I'm struggling to find one.

I had a setting (I think it was in ccsm > Unity) so when the mouse moved over a window, that window took the focus. I can't find the option any more, I'm not sure if it moved, or if it has disappeared, or I'm looking in the wrong place.

How do I re-enable this setting?

---

### Post by mc4man on 2012-04-01
visually can be set in dconf-editor (install dconf-tools

Found at location in screen, likely the 'mouse' option, click in box to expose dropdown

from cli (setting to 'mouse'

```
gsettings set org.gnome.desktop.wm.preferences focus-mode mouse
```

available values for gsettings
```
$ gsettings range  org.gnome.desktop.wm.preferences focus-mode 
enum
'click'
'sloppy'
'mouse'
```

---

### Post by chmac on 2012-04-01
Outstanding, you sir (or mam) are a gentleman (or woman) and a scholar! I thank you kindly. :-)

---

### Post by mc4man on 2012-04-01
just to note-(here) it doesn't seem the 'mouse' mode works quite as intended ?, leaving a window doesn't return focus to the Desktop if going to the Desktop

---

### Post by chmac on 2012-04-01
As far as I remember, it didn't previously select the desktop when leaving a window, if another window wasn't behind. It seems to be working as it as before, about which I am personally delighted. It's ultra helpful to be able to type in one window while another window is on top of it... :-)

---

