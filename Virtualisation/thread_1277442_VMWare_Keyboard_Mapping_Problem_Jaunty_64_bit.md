---
title: "VMWare Keyboard Mapping Problem Jaunty 64 bit"
date: 2009-09-28
forum: Virtualisation
---

### Post by dlobo on 2009-09-28
Dear All,

I have the recurring keyboard problem that most of us have had at one point or another when running VMWare in Ubuntu. The arrow keys and some other keys do not work.
These are my specs:
Host OS: Jaunty 64 bit.
Guest: Win XP 32 bit.
VMWare Server 2.0.1

I have fixed this successfully on 32-bit in the past, but I am struggling with Jaunty 64-bit.
I have tried the various solutions I have seen posted in different forums:
xkeymap.usekeycodeMap = true 
This did not have any effect.

I also tried the re-mapping of different keys.
To find out the right mapping I ran a xkeymod -pk first. Then based on that output I created the following entries in the /etc/vmware/config:
xkeymap.keysym.ISO_Level3_Shift = 0xfe03 # ISO_Level3_Shift
xkeymap.keycode.64  = 0xffe9 # ALT_L
xkeymap.keycode.106 = 0xffaf # KP_Divide
xkeymap.keycode.104 = 0xff8d # KP_Enter
xkeymap.keycode.111 = 0xff52 # Up
xkeymap.keycode.116 = 0xff54 # Down
xkeymap.keycode.113 = 0xff51 # Left
xkeymap.keycode.114 = 0xff53 # Right
xkeymap.keycode.105 = 0xffe4 # Control_R
xkeymap.keycode.118 = 0xff63 # Insert
xkeymap.keycode.119 = 0xffff # Delete
xkeymap.keycode.110 = 0xff50 # Home
xkeymap.keycode.115 = 0xff57 # End
xkeymap.keycode.112 = 0xff55 # Prior
xkeymap.keycode.117 = 0xff56 # Next
xkeymap.keycode.78  = 0xff14 # Scroll_Lock
xkeymap.keycode.127 = 0×ff13 # Pause
xkeymap.keycode.133 = 0xffeb # Super_L
xkeymap.keycode.134 = 0xffec # Super_R
xkeymap.keycode.135 = 0xff67 # Menu

This one had a funny side effect. The moment I use the up or down arrows it changes the behaviour of my mouse within my guest OS. The left button starts behaving like the right button. For example when I click on "My Computer", I get the same result as if I were doing right click.

I am at wit's end with this one, so if any of you Ubuntu fellows have any suggestions as to how to go around this I will greatly appreaciate.

Thanks a lot in advance
Respectfully

dmlobo

---

### Post by dlobo on 2009-09-30
Problem solved.
The keymap I provided was wrong. The one below (which you can find in many listed solutions worked this time.
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

It did not work before, Every time I would use an arrow key I would get a vmware error message saying that the key had a non-integer value assigned to it. That's when I started trying different things.
After some other changes and things getting worse, I finally decided to run vmware-config.pl again and everything is working just fine now.

Thanks a lot
Respectfully

dmlobo

---

### Post by Deadpan110 on 2009-10-03
Thankyou - Copy and pasting the keymaps into /etc/vmware/config and then running vmware-config.pl worked for me!

```
# Copy and paste the above keymaps into the config
sudo gedit /etc/vmware/config

# I am not sure if running vmware-config.pl is needed
# or maybe just restarting vmware - but I did it anyway

# vmware-config.pl complains about modules already on the system

# The following VMware kernel modules have been found on your system that were 
# not installed by the VMware Installer.  Please remove them then run this 
# installer again.

sudo rm -Rv /lib/modules/2.6.28-15-generic/misc/vm*
sudo vmware-config.pl
```


I found this before I even saw any other solutions on the web.

---

