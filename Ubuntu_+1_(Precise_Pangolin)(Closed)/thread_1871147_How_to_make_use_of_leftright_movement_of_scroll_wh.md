---
title: "How to make use of left/right movement of scroll wheel on mouse"
date: 2011-10-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zika on 2011-10-28
As title suggests, I would like to use left/right movement of scroll wheel on my Logitech mouse...
Any ideas?

---

### Post by Harry33 on 2011-10-28
> **zika said:**
> As title suggests, I would like to use left/right movement of scroll wheel on my Logitech mouse...
Any ideas?

It should work automatically if you have input driver evdev installed.
No need to have /etc/X11/xorg.conf.

---

### Post by Bowmore on 2011-10-28
If it's about switching viewports that's achieved in ccsm Viewport switcher > Desktop-based Viewport Switching:

- Move Next = Button5
- Move Prev = Button4

---

### Post by Xgen on 2011-10-28
Quite easy to do...I have various commands keyed to my Logitech mouse, including starting programs. First, install xbindkeys and xautomation. Create a file called .xbindkeysrc and add to your home profile. Use my file as a template:

```

#@@@@@@@@@@@@@@@@@@ BUTTON ASSIGNMENTS @@@@@@@@@@@@@@@@@@@

# b:1	-	left mouse button
# b:2	-	wheel button
# b:3 	-	right mouse button
# b:4	-	mouse wheel up
# b:5	-	mouse wheel down
# b:6	-	mouse wheel left
# b:7	-	mouse wheel right
# b:8	-	back side button
# b:9	-	forward side button

#@@@@@@@@@@@@@@@@@@@ BUTTON MAPPING @@@@@@@@@@@@@@@@@@@@@@

# Exit Programs (Various Combinations)
"xte 'keydown Alt_L' 'key F4' 'keyup Alt_L' "
  b:2
"xte 'keydown Shift_L' 'keydown Control_L' 'key Q' 'keyup Shift_L' 'keyup Control_L' "
  b:2

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@

# Miscellaneous

#Shutdown
"sudo shutdown -h now" 
  Alt + Control + b:2
#Reboot
"sudo init 6" 
  Control + mod4 + b:2
"gnome-terminal"
  Control + b:2
"gksu gnome-terminal"
  Alt + b:2

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@

# Internet
"firefox -P firefox -no-remote"
  b:8
"/.media/Linshare/Internet/Browsers/nightly/firefox -P nightly -no-remote"
  Control + b:8

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@

# File Browsers
"nautilus /home/larry"
  b:9
"gksu nautilus"
  Control + b:9

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@

# History Back & Forward
"xte 'keydown Alt_L' 'key Left' 'keyup Alt_L' "
  b:6
"xte 'keydown Alt_L' 'key Right' 'keyup Alt_L' "
  b:7



```

To start automatically at boot, create a startup program in your Startup  Applications with the command xbindkeys.

Reboot or restart profile. Should work, unless I forgot a step :P

---

### Post by effenberg0x0 on 2011-10-28
I have used the buttons 6, 7, 8, 9,10 of my mouse directly in CCSM "Expo" / "Desktop Wall" plugins bindings and also the "Commands" plugin. Doing a cat in /etc/X11/xorg.conf you can see how xorg detects your mouse and buttons and play with it in compiz plugins bindings to reach the desired behavior. But, at any rate, it's a much less advanced method than the one proposed above.

---

### Post by lucazade on 2011-10-28
otherwise you can use xmodmap to map mouse buttons, I use it with a logitech performace mx mouse to get middle click on side buttons.

---

### Post by zika on 2011-10-28
It works, but I was wrong in the way I expected it to work. I'll explore given advices how to make it more usefull. Thank You all..

---

### Post by zika on 2011-10-29
> **Xgen said:**
> Quite easy to do...I have various commands keyed to my Logitech mouse, including starting programs. First, install xbindkeys and xautomation. Create a file called .xbindkeysrc and add to your home profile. Use my file as a template:

```

#@@@@@@@@@@@@@@@@@@ BUTTON ASSIGNMENTS @@@@@@@@@@@@@@@@@@@

# b:1    -    left mouse button
# b:2    -    wheel button
# b:3     -    right mouse button
# b:4    -    mouse wheel up
# b:5    -    mouse wheel down
# b:6    -    mouse wheel left
# b:7    -    mouse wheel right
# b:8    -    back side button
# b:9    -    forward side button

#@@@@@@@@@@@@@@@@@@@ BUTTON MAPPING @@@@@@@@@@@@@@@@@@@@@@

# Exit Programs (Various Combinations)
"xte 'keydown Alt_L' 'key F4' 'keyup Alt_L' "
  b:2
"xte 'keydown Shift_L' 'keydown Control_L' 'key Q' 'keyup Shift_L' 'keyup Control_L' "
  b:2

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@

# Miscellaneous

#Shutdown
"sudo shutdown -h now" 
  Alt + Control + b:2
#Reboot
"sudo init 6" 
  Control + mod4 + b:2
"gnome-terminal"
  Control + b:2
"gksu gnome-terminal"
  Alt + b:2

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@

# Internet
"firefox -P firefox -no-remote"
  b:8
"/.media/Linshare/Internet/Browsers/nightly/firefox -P nightly -no-remote"
  Control + b:8

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@

# File Browsers
"nautilus /home/larry"
  b:9
"gksu nautilus"
  Control + b:9

#@@@@@@@@@@@@@@@@@@@@@@@@@@@@

# History Back & Forward
"xte 'keydown Alt_L' 'key Left' 'keyup Alt_L' "
  b:6
"xte 'keydown Alt_L' 'key Right' 'keyup Alt_L' "
  b:7



```To start automatically at boot, create a startup program in your Startup  Applications with the command xbindkeys.

Reboot or restart profile. Should work, unless I forgot a step :P
Last section is just what I needed!
Thank You!
You, really, made me very happy... ;)

---

