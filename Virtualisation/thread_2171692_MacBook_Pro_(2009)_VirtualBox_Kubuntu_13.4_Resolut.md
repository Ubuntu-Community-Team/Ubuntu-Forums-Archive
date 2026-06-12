---
title: "MacBook Pro (2009) VirtualBox Kubuntu 13.4 Resolution"
date: 2013-09-01
forum: Virtualisation
---

### Post by Kenner58 on 2013-09-01
- 2009 MacBook Pro with OS X 10.6.8 
- VirtualBox 4.2.2 
- Kubuntu 13.4 + VBoxLinuxAdditions installed from Linux Format DVD LXF172

PROBLEM 1: Resolution 1280x800 not available in Kubuntu Display Configuration

Followed instructions in [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) to add and select the required resolution.

1) Checked existing resolutions: $ xrandr
2) Found required modeline:      $ gtf 1280 800 60.0
3) Created a new mode:           $ xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809  831 -hsync +vsync
4) Added new mode to display:  $ xrandr --addmode VBOX0 1280x800_60.00
5) Selected the new mode:       $ xrandr  --output VBOX0 --mode 1280x800_60.00

But I couldn't make these changes persistent in any of the four ways suggested. E.g. the ".xprofile" and "xorg.conf" files mentioned don't exist.

SOLUTION 1: Added the following lines to my user profile ( ~/.profile ) to make the changes persistent

xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809  831 -hsync +vsync
xrandr --addmode VBOX0 1280x800_60.00
xrandr  --output VBOX0 --mode 1280x800_60.00

PROBLEM 2: How to make these changes persistent for all users?

Any suggestions?

Cheers

---

