---
title: "Changing screen resolution on TV via HDMI"
date: 2010-05-08
forum: Server Platforms
---

### Post by Zeophlite on 2010-05-08
I've just finished installing Ubuntu Server 10.4 onto my ASRock ION330.  I don't have a spare monitor lying around, so I've plugged my TV into my machince via HDMI.  This works, but the text is tiny.  There are too many rows and columns of characters (or equivalently, the font is too small).  When I try changing the TV resolution to a smaller size, it just cuts out the rest of the text.  So from the command line, how do I make the text bigger?

---

### Post by P4man on 2010-05-08
Try running ```
xrandr
```. It will spit out the supported resolutions.
Then try changing it with something like this:

```
xrandr --output LVDS --mode 1024x768
```

(may need to change LVDS for VGA or HDMI or default or whatever xrandr calls your tv).

---

### Post by Zeophlite on 2010-05-08
I tried xranr, but got
```

The program 'xrandr' is currently not installed. You can install it by typing:
sudo apt-get install x11-xserver-utils

```
Doing so gets:
```

E: Couldn't find package x11-xserver-utils

```

Forgive me, but my machine is plugged directly into the TV, so is my understanding is that that wouldn't be under X server type stuff.  I'm quite a newbie at all this.

Just so you know, I changed /etc/apt/sources.lst by un#ing the
```

deb cdrom:[[Ubuntu-Server 10.04 LTS...

```
line so that I could get ethtool
```

sudo apt-get update
sudo apt-get install ethtool

```
Actually turns out I didn't need ethtool.

---

### Post by P4man on 2010-05-08
You are forgiven because you are correct :D

Try this then:

```
sudo hwinfo --framebuffer | grep Mode     
```

that will list all (vesa?) modes supported. You can pass those to your kernel as boot option. Try it first by manually changing in grub (in grub menu, press E to edit)  

Find the line that looks like

linux /boot/vmlinuz-2.6.31-14-generic root=UUID=376bb7b9-cd0b-4f2f-a610-82a2207d81de ro single splash 

add at the end

linux /boot/vmlinuz-2.6.31-14-generic root=UUID=376bb7b9-cd0b-4f2f-a610-82a2207d81de ro single splash **vga=0x0317**

replace the code with the resolution you want to use and that is supported by both your tv and the videocard.

---

### Post by Zeophlite on 2010-05-08
I forgot to mention this beforehand, but thank you for your quick response.

```

**sudo hwinfo --framebuffer | grep Mode**
sudo: hwinfo: command not found
**hwinfo**
The program 'hwinfo' is currently not installed.  You can install it by typing:
sudo apt-get install hwinfo
**sudo apt-get install hwinfo**
Reading package lists... Done
Building dependancy tree
Reading state information... Done
E: Couldn't find package hwinfo

```

Any other suggestions?

> **P4man said:**
> 
Try it first by manually changing in grub (in grub menu, press E to edit)  


How do I get to grub menu?  I've only got a command line interface.


Thank you again

---

### Post by P4man on 2010-05-08
? Is the machine not connected to the internet?
rather strange. Anyway, if you dont have hwinfo, here is a list with all modes:
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

Pick one you think will work

To add that to grub:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

On lucid its a bit different, you may have to hold down the shift key right after the bios to see the grub boot menu.

---

### Post by Zeophlite on 2010-05-08
I added it to grub, but it didn't have any effect.  But in grub the TV registers 1920x1080 resolution, but the text size is large enough to be visible.  Can I change the font size somehow?

---

### Post by cariboo on 2010-05-09
Can't you just ssh into the server and do what you need there? My server sits on a shelf with only a power cord, network cable and usb connection for the ups, I do all administration remotely.

---

### Post by Zeophlite on 2010-05-09
I can now, this was posted before I got the network and ssh working, so I needed to use the TV.  I'd still like to know how in case I ever want to use it from the TV.

---

