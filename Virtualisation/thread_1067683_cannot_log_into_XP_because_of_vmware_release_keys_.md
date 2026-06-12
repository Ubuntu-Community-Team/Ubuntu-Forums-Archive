---
title: "cannot log into XP because of vmware release keys conflict"
date: 2009-02-12
forum: Virtualisation
---

### Post by ddtpoison on 2009-02-12
Good day,

Bit of an embarrassing situation i find myself in.
Always used vmware server in linux, and always installed standard XP on it, teh standard way, sometimes with password and sometimes without.

But now i installed vmware server 2 at the office (for work reasons) in Ubuntu 8.10. Created a new virtual XP installation.......but the windows in the office uses the whole login to domain thing, and here is my issue:

In windows in order to login after bootup i must fist press "ctrl+alt+del" to have the login fields displayed, but for vmware pressing "ctrl+alt" releases the mouse from the console window which basically ruins your ability to log in to windows....

Anybody know a workaround or key-binding-changes one can do to solve this?
Like i said its rather embarrassing!  :D

Any help will be greatly appreciated.
Thank you.

---

### Post by dcstar on 2009-02-15
> **ddtpoison said:**
> Good day,

Bit of an embarrassing situation i find myself in.
Always used vmware server in linux, and always installed standard XP on it, teh standard way, sometimes with password and sometimes without.

But now i installed vmware server 2 at the office (for work reasons) in Ubuntu 8.10. Created a new virtual XP installation.......but the windows in the office uses the whole login to domain thing, and here is my issue:

In windows in order to login after bootup i must fist press "ctrl+alt+del" to have the login fields displayed, but for vmware pressing "ctrl+alt" releases the mouse from the console window which basically ruins your ability to log in to windows....

Anybody know a workaround or key-binding-changes one can do to solve this?
Like i said its rather embarrassing!  :D

Any help will be greatly appreciated.
Thank you.

In VMware console (1.0.8, cannot remember where it is in 2.0): VM-Send Ctrl+Alt+Del

---

### Post by ddtpoison on 2009-02-16
Thank you. Will try it. :)

---

### Post by veloce on 2009-02-16
> **ddtpoison said:**
> Thank you. Will try it. :)

Also try:

Ctl+Alt+Enter
Ctl+Alt+. (the "." on the numerical keypad)

These are required for vmware 2 as it doesn't have the menu option anymore.

---

### Post by ddtpoison on 2009-02-19
Thank you.
I next have time to work on my vmware this weekend. Once tested i will report on my findings. :)

---

### Post by popq on 2009-02-20
Solution found at [http://communities.vmware.com/thread/177133](http://communities.vmware.com/thread/177133)

In short:

Add:

xkeymap.keycode.108 = 0x138 # Alt_R
xkeymap.keycode.106 = 0x135 # KP_Divide
xkeymap.keycode.104 = 0x11c # KP_Enter
xkeymap.keycode.111 = 0x148 # Up
xkeymap.keycode.116 = 0x150 # Down
xkeymap.keycode.113 = 0x14b # Left
xkeymap.keycode.114 = 0x14d # Right
xkeymap.keycode.105 = 0x11d # Control_R
xkeymap.keycode.118 = 0x152 # Insert
xkeymap.keycode.119 = 0x153 # Delete
xkeymap.keycode.110 = 0x147 # Home
xkeymap.keycode.115 = 0x14f # End
xkeymap.keycode.112 = 0x149 # Prior
xkeymap.keycode.117 = 0x151 # Next
xkeymap.keycode.78 = 0x46 # Scroll_Lock
xkeymap.keycode.127 = 0x100 # Pause
xkeymap.keycode.133 = 0x15b # Meta_L
xkeymap.keycode.134 = 0x15c # Meta_R
xkeymap.keycode.135 = 0x15d # Menu
xkeymap.keycode.107 = 0x54 # PrintScr

to /etc/vmware/config.

---

### Post by dcstar on 2009-02-21
> **veloce said:**
> Also try:

Ctl+Alt+Enter
Ctl+Alt+. (the "." on the numerical keypad)

These are required for vmware 2 as it doesn't have the menu option anymore.

Yet another reason I'm glad I went back to 1.0.8.........

---

