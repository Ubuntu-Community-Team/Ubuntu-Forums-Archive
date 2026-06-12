---
title: "Fixing Overscan Problem FINALLY"
date: 2017-04-03
forum: Ubuntu, Linux and OS Chat
---

### Post by markackerman8@gmail.com on 2017-04-03
What Worked!!!!

In Terminal
     xrandr --newmode "1800x1012_60.00" 151.42 1800 1912 2104 2408 1012 1013 1016 1048 -HSync +Vsync
     xrandr --addmode HDMI1 "1800x1012_60.00"
     xrandr --output HDMI1 --mode "1800x1012_60.00"
           &#8227; In My case replace HDMI1 witjh HDMI-1-1

Yes it is an inexpensive UltraHD Screen/TV
and my computer specs are:
HP Omen 15-5220ca, M2D10UA#ABL, 
&#8227; Intel® Core i7-4720HQ CPU, Quad Core @ 2.60GHz ×  8 Threads,   
&#8227; GeForce GTX 960M,   
&#8227; PCIe 512GB SSD - SSE2 (M.2),   
&#8227; 15.6 GB RAM
&#8227; NVIDIA 375.39 Driver

FINALLY!  
I hope it helps others, Mark :P

--------------------------------------------------------------------------------
What Did NotWORK! so many things
-of course no TV setting and/
- of course no NVidia setting options

• xrand r--verbose    or
• xrandr --current
&#8728; eDP-1-1 connected (normal)
&#8227; scaling mode: Full aspect 
&#8728; HDMI-1-1 connected 1920x1080+0+0 (0x73) normal (normal) 708mm x 398mm
&#8728; HDMI-1-1 connected primary 1920x1080+0+0 708mm x 398mm
• Try
&#8728; xrandr --output HDMI-1-1 --scale 0.95x0.95    ....  Nope
&#8728; xrandr --output eDP-1-1 --scale 0.95x0.95              Nope
&#8728; xrandr --output HDMI-1-1 --fb 1920x1080 --transform 1,0,-20,0,1,-10,0,0,1
&#8728; xrandr --output LVDS1 --off --output HDMI-1-1 --set audio force-dvi
• xrandr --output eDP-1-1 --off --output HDMI-1-1 --set audio force-dvi
&#8728; xrandr --size 1680x1050
• xrandr --size 1870x1030
&#8728; sudo dpkg-reconfigure xserver-xorg

and A Lot more other attempts too!

---

### Post by QIII on 2017-04-03
It might be more helpful if you said what the original problem was.

Since this is an answer looking for a question, it does not fit in the general support sections of the Forums.

---

### Post by markackerman8@gmail.com on 2017-04-05
The problem is in the title.

Overscan is a new term for many new TV's that trim off the edges for "WHATEVER" reason, apparently because of older tube TV's.  And most (of the new TVs) have an option to turn "Overscan" OFF.  But many (often cheaper ones) do not.

So when you plug in athese TVs all 4 edges are slightly cut off often cutting into or elliminating tabs/panels.

p.s. if anyone knows an "EASY" GUI fix for making this permanent ... please tell me ... I haVE YET TO FIND ONE!

Silly but for others ... in Arandr you can go into Layout/Save As .... and it will save a script that you can click on top re-activate the custom option and apply it, ...
a pain, but works eliminating at least the need for the 3 commands that one needed initially.

Hoping to help other, Mark ):P

---

### Post by markackerman8@gmail.com on 2017-04-06
To Make work at boot - So many things did NOT work as it is a second monitor (TV from a laptop)

What DID work


Step 1: Take those 3 commands, save in a set-screen.sh somewhere in your home directory. For example, mine would be in /home/serg/bin/set-screen.sh and that's how it would look like:

#!/bin/sh
sleep 15
xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
xrandr --addmode DVI-I-1 1368x768_60.00
xrandr --output DVI-I-1 --mode  1368x768_60.00
Step 2: do in terminal chmod 755 set-screen.sh.

Step 3: Open the Startup Applications and add full path to your file as one of the startup commands.
/home/YOU/path_to_set-screen.sh

Fewwww WORKS!

---

