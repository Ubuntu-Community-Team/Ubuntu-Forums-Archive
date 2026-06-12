---
title: "Resolution not found in Display Menu"
date: 2017-09-04
forum: Virtualisation
---

### Post by poutrygiest on 2017-09-04
I am running Ubuntu 16.04 LTS in VMWare.

The Display menu does not have 1920x1080 as a resolution option, which is my monitors native resolution.

I can add it with:

sudo xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
sudo xrandr --addmode Virtual1 1920x1080_60.00

but upon restart the option disappears and it defaults to 800x600 which makes some menus impossible to navigate through.

How does Ubuntu allow a resolution option to persist through restart? Or running those commands at login as a workaround?

---

### Post by deadflowr on 2017-09-05
*Thread moved to **Virtualization ***

---

### Post by poutrygiest on 2017-09-05
@deadflowr

Is this related to an issue with VMWare?

I  would have thought that adding a resolution and ensuring it is defaulted  upon restart is irrelevant to it being in a virtual machine.

---

### Post by crjackson on 2018-03-01
I’m having the same problem w/same resolution needed. Can’t even get it to appear in the selection menu at all. I’ve applie the appropriate xrandr terminal commands also. The new mode line is added, but the selection is still missing and totally unavailable.

I’ll try again tomorrow.

```
sudo xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
sudo xrandr --addmode Virtual1 1920x1080_60.00
```

---

### Post by crjackson on 2018-03-11
I was able to resolve this particular issue by reinstalling vmware-tools using;

```
sudo apt-get install open-vm-tools-desktop
```
I&#8217;m still fighting to get a proper boot splash screen but I&#8217;m about to concede to failure.

I&#8217;m also thinking that 7.10 is so freaking buggy, I may go back to the latest LTS or just ditch Ubuntu and move to a new distro.

---

