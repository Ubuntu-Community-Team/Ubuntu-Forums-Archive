---
title: "[SOLVED] Keyboard keys don't work in virtual machine"
date: 2008-11-02
forum: Virtualisation
---

### Post by RSF5 on 2008-11-02
Okay I have 8.10 Ubuntu running vmware player to use a vista vm

But when I'm in the vm the arrow keys on the keyboard and the delete key do not work.

I've been searching for a solution or explanation for this for hours..:(

---

### Post by RSF5 on 2008-11-02
Morning bump. Trying vmware workstation now.

---

### Post by RSF5 on 2008-11-02
SOLVED! Thank god, this was driving me bats**t insane.

Add the following code to the end of the file /etc/vmware/config

```
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
```

That'll remap the keys to the right places in the virtual machine

---

### Post by pertheusual on 2008-11-03
Thank you! I had this same problem.
This has been bugging me for a few days now.

-Per

---

### Post by chriv on 2009-01-11
This has been a problem for me ever since I went from VMware Workstation 6 to 6.5.

This was a HUGE annoyance because I very seldomly use the mouse.  I've been using predominately keyboard only controls for Windows every Since Windows 386 (2.0).  Hitting the down arrow and having the Start menu open was a major pain in the ****.

This remapping appears to have completely resolved the issue I was having.

THANK-YOU!!!!

---

### Post by mie on 2009-01-21
for fixing the "Print Screen" key, which is mapped to the "Del" key, add this to your vmware config file (tested for /etc/vmware/config):

xkeymap.keycode.107 = 0x137 # Print Scrn

see:
[http://www.vmware.com/support/ws5/doc/ws_devices_keymap_linux_longer.html](http://www.vmware.com/support/ws5/doc/ws_devices_keymap_linux_longer.html)
[http://www.vmware.com/support/ws5/doc/ws_devices_keymap_vscan.html](http://www.vmware.com/support/ws5/doc/ws_devices_keymap_vscan.html)

---

### Post by rimbaud on 2009-03-12
VMware don't really seem to care very much about Linux support as a host.  I left message about this and USB support in VMPlayer 2.5 on their forums and no reply.

---

### Post by clyrrad on 2010-07-03
Thank-you very much for this - I added the key-mappings and volia it worked like a charm.  This was driving me bonkers!  Thanks again! :D

---

