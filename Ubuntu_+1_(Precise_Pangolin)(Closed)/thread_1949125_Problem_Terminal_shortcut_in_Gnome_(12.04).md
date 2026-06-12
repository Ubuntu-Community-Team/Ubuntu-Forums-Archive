---
title: "Problem: Terminal shortcut in Gnome (12.04)"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dingd0ng on 2012-03-29
Hi Everyone,

I'm sort of new here and thought maybe this community could help me figure this minor inconvenience out.

I upgraded to 12.04 from 11.10 and love what I see. The *only* problem I'm having is when I log into Gnome shell, my Terminal shortcut, CTRL+ALT+T, doesn't work. It's there in my keyboard>shortcuts list, and it works fine when I log into Unity, but alas not in Gnome.

Any leads as to what I should look into? I'm sort of a beginner.


p.s. I love Ubuntu!

---

### Post by thaelim on 2012-03-30
This bug seems to have been around for quite a while, and none of the common workarounds have fixed it for me. One suggestion is to take a look at a program called AutoKey - it allows you to create keyboard shortcuts totally independent of the desktop environment.

---

### Post by mc4man on 2012-03-30
Pretty simple- 
Open system settings > keyboard > Shortcuts > Custom Shortcuts
Click on the + and add a new one named Terminal with a command of 
gnome-terminal
Click on the 'disabled' and set binding to Ctrl+Alt+t - there will be a pop up as in screen. Click on 'reassign'

---

### Post by philinux on 2012-03-30
An even better keyboard shortcut for terminal, for me anyways, is to use the unused menu key.

The one between the right side win key and Ctrl

---

### Post by Robert Lock on 2012-04-14
Thanks mc4man!  The custom terminal shortcut works!  Now if I could get the minimize window option (Alt+F9) working.... do you have any suggestions?

---

### Post by mc4man on 2012-04-14
Just put up some new 32 & 64 bit installs so checked in Unity
The shortcut was Ctrl+Alt+0 which did nothing
Changed to Alt+F9 & that worked in unity

Installing & trying in Gs - no go

Did get it to work this way
Either in dconf-editor - see screen
or from terminal
```
gsettings set org.gnome.desktop.wm.keybindings minimize "['<Alt>+F9']"
```

---

