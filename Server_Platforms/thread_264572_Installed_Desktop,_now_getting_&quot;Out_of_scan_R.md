---
title: "Installed Desktop, now getting &quot;Out of scan Range&quot; upon reboot"
date: 2006-09-24
forum: Server Platforms
---

### Post by KyferEz on 2006-09-24
I installed Ubuntu LAMP server. Then I installed the desktop. I had to reboot for some reason, and got this error.

I know when I get that message my monitor cannot display the resolution that was selected. The wierd thing is that my monitor does support all the resolutions I checked in the desktop setup program... Unless I accidently clicked one it couldn't.

Anyway, I had fortuantely installed SSH server, and have access to the pc that way. I don't want the desktop to start at bootup either. Could someone please tell me how to:
1) fix the resolution problem
2) Prevent the desktop from starting at bootup

Thank you very much,
KyferEz

---

### Post by bluefrog on 2006-09-25
fix your prblem.. don't know

prevent gdm from starting

sudo update-rc.d remove gdm

or something similar (man update-rc.d if I wrote something wrong)

James

---

### Post by KyferEz on 2006-09-25
James, Thanks!

For anyone who searches, I had to move "gdm" in front of the word "remove": 
sudo update-rc.d gdm remove

Now, I just need to fix the resolution problem and will be good.

KyferEz

---

### Post by KyferEz on 2006-09-27
BUMP

I still have the problem where I cannot see the desktop because of the resolution. How do I manually change the resolution from command line?

Thanks,
KyferEz

---

### Post by dallday on 2006-10-17
Had the same problem - seems that the monitor is not being detected correctly so uses a higher refresh rate than the monitor can support.

I did have a kubuntu setup using a different graphic card that had the monitor set correctly so copied in that monitor section to /etc/X11/xorg.conf

using 
gksudo gedit /etc/X11/xorg.conf

Section below - that seem to have sorted it and now it works correctly.

How you set that manually I don't know

David



Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Sony"
  modelname "Sony CPD-200ES"
  HorizSync 30.0-70.0
  VertRefresh 50.0-120.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  gamma 1.0
EndSection

---

### Post by dallday on 2006-10-17
and just to mention that if you cannot get desktop you can get to a terminal using ctrl + Alt and F1 ( F1 to F6 are terminal F7 is GUI Screen and F8 seems to be a log )

Login as your user and then use a text editor like nano (?)

use sudo to switch to root to update the file.

sudo nano /etc/X11/xorg.conf

---

