---
title: "Problem with external monitor"
date: 2012-06-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by thotz on 2012-06-20
Hello,

I'm testing Ubuntu 12.10 and I have a problem with my Sony Notebook and my external monitor. I was able to set the resolution of my external monitor in Alpha 1 but now testing with yesterday's image i only can choose "1024x768".

I have a second generation Intel i3 processor with the HD 3000 Graphics. In Ubuntu 12.04 LTS everything works fine.

Can you please help me?

// EDIT: It's more the problem that I can't choose the correct resolution!

---

### Post by jerrylamos on 2012-06-20
> **thotz said:**
> Hello,

I'm testing Ubuntu 12.10 and I have a problem with my Sony Notebook and my external monitor. I was able to set the resolution of my external monitor in Alpha 1 but now testing with yesterday's image i only can choose "1024x768".

I have a second generation Intel i3 processor with the HD 3000 Graphics. In Ubuntu 12.04 LTS everything works fine.

Can you please help me?

// EDIT: It's more the problem that I can't choose the correct resolution!I was struggling with the same problem for days.  For detail see launchpad bug #1007588 which was fixed yesterday 19 June.  It's an Acer Aspire 5253 wide screen notebook with an external monitor.  I haven't checked with today's updates yet....

Jerry

---

### Post by thotz on 2012-06-21
Thank you for your reply. With today's updates it's still not fixed so I have to use the xandr command.

---

### Post by thotz on 2012-06-23
Works now!

---

### Post by jerrylamos on 2012-06-23
Besides the widescreen notebook with computer external monitor, I've a netbook with a TV monitor.  System Settings > Displays calls it "unkown" and will only list resolutions 1024x768 and 800x600.

Found a how to for setting resolution on the TV:
#!/bin/bash
echo "http://askubuntu.com/questions/63863/unknown-monitor-intel-driver-want-to-set-vga-resolution-to-widescreen-tv/154818#154818"
xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1366x768_60.00
xrandr --output VGA1 --mode 1366x768_60.00

Now it works, good sharp display, however on logout/login reboot restart etc. I have to re-issue the exec again.  Did a search on Ask Ubuntu seems out of date, there is no folder /etc/gdm on 12.10 for example.

Jerry

---

### Post by jerrylamos on 2012-06-26
Some progress with the following /etc/X11/xorg.conf:

```

Section "Monitor"
    Identifier      "External DVI"
    Modeline        "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
EndSection
Section "Device"
    Identifier      "Intel Corporation N10 Family Integrated Graphics Controller"
    Driver          "Intel"
    Option          "Monitor-DVI-0" "External DVI"
EndSection
Section "Screen"
    Identifier      "Primary Screen"
    Device          "Intel Corporation N10 Family Integrated Graphics Controller"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1366x768" "1024x768" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Primary Screen"
EndSection
```
The device came from lspci | grep VGA
The driver was a guess
System Settings, Display is still screwed up but I'm  at least running.
Jerry
BTW did a chmod 777 on /etc/X11/xorg.conf

---

### Post by leitz010 on 2012-07-13
I currently am having the same problems with an external monitor hooked up to my dell mini 9, so if anyone has any ideas beyond inputting the code at every reboot that would be great.

---

### Post by jerrylamos on 2012-07-13
> **leitz010 said:**
> I currently am having the same problems with an external monitor hooked up to my dell mini 9, so if anyone has any ideas beyond inputting the code at every reboot that would be great.

The xorg.conf code gets copied in once and doesn't have to be repeated.

I also use a ~/.xprofile like so:

```
#!/bin/bash
xrandr --newmode "1366x768_60.00"   85.25  1366 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 "1366x768_60.00"
xrandr --output VGA1 --mode "1366x768_60.00"
```

Between the xorg.conf copied in once, and the .xprofile created once most of the time it comes up O.K. with no additonal keystrokes.  If it doesn't then I have to kick start it with the exec in the previous exec with xrandr.

Now I do turn off the laptop display using system settings > display which usually has the "unknown" monitor screwed up and may or may not show 1366x768 choice.

Anyway, with the .xprofile and the xorg.conf it comes up right mostly and I have the xrandr exec as backup.

Now I do see I must have done:

sudo chmod 755 .xprofile

somewhere along the line I'm not sure if that's needed.

Jerry

---

