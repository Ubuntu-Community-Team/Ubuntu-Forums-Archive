---
title: "Arrow keys won't work in VMWare while installing MS-DOS"
date: 2009-01-14
forum: Virtualisation
---

### Post by Flareside on 2009-01-14
I am trying to install MS-DOS 6.22 onto a virtual machine using VMWare 6.5. I have attached a screen shot of where I am. I need to select the second option, but my arrow keys don't work. All my other keys work though. My arrow keys also don't work in the bios settings of any of my virtual machines.

---

### Post by lensman3 on 2009-01-14
The VMWare Client requires you to set up the keyboard.  You have to map the key-presses through X11.  None of the extended keys are mapped including the keypad and the arrow key pad.  

I have the same problem and will have to fix it too.  Sorry I haven't looked far enough to see how to do that yet.  I image that VMWare.com has the files/howto on how to fix it.  The free 1.xxx version worked fine.  Once I moved to 2.xxx, it broke.

Can anybody help this person!  Sorry I can't be more helpful.

---

### Post by supertux on 2009-01-15
Try adding:

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

to ~/.vmware/config

---

### Post by Flareside on 2009-01-15
> **supertux said:**
> Try adding:

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

to ~/.vmware/config

Thanks, that worked perfectly

---

### Post by mie on 2009-01-21
for fixing the "Print Screen" key, which is mapped to the "Del" key, add this to your vmware config file (tested for /etc/vmware/config):

xkeymap.keycode.107 = 0x137 # Print Scrn

see:
[http://www.vmware.com/support/ws5/doc/ws_devices_keymap_linux_longer.html](http://www.vmware.com/support/ws5/doc/ws_devices_keymap_linux_longer.html)
[http://www.vmware.com/support/ws5/doc/ws_devices_keymap_vscan.html](http://www.vmware.com/support/ws5/doc/ws_devices_keymap_vscan.html)

---

### Post by yulian on 2009-02-19
To fix this, you need to run the following command from terminal:

echo 'xkeymap.nokeycodeMap = true' > ~/.vmware/config

and if VMware Player/Server/Workstation was running, just restart it.

Yulian

---

### Post by coolmig on 2009-03-02
> **supertux said:**
> Try adding:

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

to ~/.vmware/config

Thanks again, that worked perfectly to navigate inside the BIOS menu of a Virtual Machine on VMware Server 2. You saved the day!

---

### Post by kell05 on 2009-03-02
mnmnsjdfnajksdfnhsjkdfnha

---

