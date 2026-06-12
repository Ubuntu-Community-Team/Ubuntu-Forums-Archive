---
title: "Setting external monitor resolution (Starling Netbook)"
date: 2009-08-22
forum: System76 Support
---

### Post by JeffV on 2009-08-22
I noticed this thread ( [http://ubuntuforums.org/showthread.php?t=1171109](http://ubuntuforums.org/showthread.php?t=1171109) ), it was mentioned the Starling hardware specs indicate supporting resolutions up to 2048×1536 on an external monitor and that it's been tested up to 1900x1200 on a 26" KDS Widescreen LCD.

So how exactly do you set this resolution?  I have two different LCD monitors I tried setting up as external monitors.  In both cases, the highest resolution that is listed as available is 1024x768.  This is using the Preferences->Display settings.  Is there something special you have to do to get larger resolution options?

---

### Post by drewbenn on 2009-08-22
Did you turn off the Mirror Screens option?  If you leave it on, I think you're limited to the LCD's available resolutions.

---

### Post by JeffV on 2009-08-22
Yes, I made sure Mirror Screens was unchecked.

---

### Post by thomasaaron on 2009-08-24
If the monitor's actual resolution isn't offered, it could be that Ubuntu isn't correctly reading the specs of your monitor -- or that your monitor isn't correctly reporting them.

What is the make and model of your monitor?

---

### Post by jbelmonte on 2009-08-24
I don't have a Starling (yet), but I have noticed limited resolution choices if my monitor is not connected and turned on when I boot up under Ubuntu. Could this be the reason you are not seeing the expected resolutions?

---

### Post by JeffV on 2009-08-24
I've tried this on two different monitors:

ViewSonic VX724 (17 inch LCD)
Acer AL2216W (22 inch widescreen LCD).

I also tried booting with them connected and it made no difference.  It's definitely getting at least some info from the monitors because it correctly identifies them by name (i.e. ViewSonic 17").  But I'll only get 5 resolutions to choose from, 1024x768 being the highest.

So is it supposed to just automatically populate the list with all the supported resolutions for that monitor?

---

### Post by JeffV on 2009-08-24
Actually...nevermind.  I just figured it out!

In the xorg.conf file, there was a setting of

SubSection "Display"
    Virtual 1280x768
EndSubSection

I commented this out and it worked.  So I guess this setting was limiting the selection of resolutions available.

---

### Post by thomasaaron on 2009-08-25
Nice job, JeffV. You da' man.

---

### Post by atmiller65 on 2009-09-19
Can you explain in a little more detail how you resolved it? I have the same problem with my Zareason netbook and the people at Zareason are, after six days, still at a loss as to how to fix it.

---

### Post by JeffV on 2009-09-20
^^ Sure:

I just opened the xorg.conf file in the text editor:  
**sudo gedit /etc/X11/xorg.conf**

In my case, there were 3 lines in the file:
[I]SubSection "Display"
Virtual 1280x768
EndSubSection[/I]

Either delete the 3 lines, or comment them out with a # in front of each line.

Save the file and reboot.  Next time you select resolutions, a complete list of supported resolutions should be there.  Also, I noticed that when selecting an external monitor to be used at the same time as the internal one, it will define a new virtual resolution to support it and insert the correct lines back into the xorg.conf file automatically.  Once there, you don't want to mess with it anymore and everything should just work.

---

