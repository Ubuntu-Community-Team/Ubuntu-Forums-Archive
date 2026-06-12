---
title: "How to change vmwareplayer/server hotkeys?"
date: 2008-10-21
forum: Virtualisation
---

### Post by saltydog on 2008-10-21
I am getting a problem in running my windows server VM appliance. When I get to the login screen, windows asks me to press Ctrl-Alt-Del to enter, but as the sequence Ctrl+Alt is the ungrabbing hotkey for vmware, I cannot reach the login. This happens either in vmware server or in vmware player.

---

### Post by GorArn on 2008-11-19
(Running vmware server 2.0 on Ubuntu 8.10)

Ctrl-Alt-PrtScr works. Some documentation of vmware suggests Ctrl-Alt-Insert as an alternative but that does not work for me.

There are two possible solutions suggested at

[http://communities.vmware.com/thread/177688](http://communities.vmware.com/thread/177688)

The "long" one worked for me, i.e. add the following lines to /etc/vmware/config

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

---

