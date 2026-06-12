---
title: "Keyboard arrow keys not working"
date: 2009-03-19
forum: Virtualisation
---

### Post by AnimalMagic on 2009-03-19
I have a Dell USB keyboard model L100 which Ubuntu decides is a generic 105 key keyboard. In 8.04 it works as expected, both in host and guest, but in 8.10 the independent arrow keys (up, down, left and right, separate from the num keypad) do not work at all in the guest (I've tried WinXp and Ubuntu 8.10).

All keys work as expected in the host.

Is there some setting which could get them working again?

---

### Post by AnimalMagic on 2009-03-20
Can't beleive I'm the only one experiencing this...? :-(

---

### Post by AnimalMagic on 2009-03-20
And I'm not. I found a solution...

/etc/vmware/config needs the following added:

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

---

### Post by Pcniatic on 2009-03-23
Thank you AnimalMagic, i did have the same problem and your solution worked great.

I have a Dell 640m with Windows XP Professional as guest.

---

