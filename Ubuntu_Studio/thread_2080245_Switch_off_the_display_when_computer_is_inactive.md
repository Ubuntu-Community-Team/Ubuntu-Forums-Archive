---
title: "Switch off the display when computer is inactive"
date: 2012-11-03
forum: Ubuntu Studio
---

### Post by ZoxX on 2012-11-03
I have Ubuntu Studio 12.10. I don't want to switch off my monitor ever. My 27" monitor is of new generation, it has a sensor to go to sleep mode whenever the user is not sitting in front of it. I can easily turn off the sensor if I want to watch movie from the distance.

In Power Manager I have the following settings:
On AC [Actions] Put the computer to sleep when inactive for: Never
On AC [Monitor] Put display to sleep when computer...: Never
Switch off display when computer is inactive for: Never

In Screensaver Preferences:
[Display Modes] Disable Screen Saver
[Advanced] All disabled

However, when computer is inactive for some 10 minutes the display switches off, and I must move a mouse to switch it on.
Is there something I missed?

---

### Post by jejeman on 2012-11-03
Goes blank or off?
Kill the screensaver deamon. See if it helps.

---

### Post by ZoxX on 2012-11-03
> **jejeman said:**
> Goes blank or off?
Kill the screensaver deamon. See if it helps.

It goes blank after 30 seconds if I'm not in front of it. I would say it goes off after 10 minutes and on again if I move mouse.
I would call it "off" because if I listen a music via monitors build-in speakers audio mutes too.
It doesn't look like screensaver. I removed Screensaver from Session and Startup [Application Autostart] at the beginning, I will remove Power Manager to see if it helps.
The list of my sessions:
xfwm4
Thunar
xfce4-panel
Xfsettings
xfdesktop
Power Manager
/usr/lib/qjackctl/qjackctl.real

---

### Post by ZoxX on 2012-11-03
I disabled Power Manager, restarted the computer, and it didn't help.

---

### Post by ZoxX on 2012-11-11
Solved:
Add the following lines to the "Server Flags" section in /etc/X11/xorg.conf:

Section "ServerFlags"
Option "DontZap" "False"
# Following is to disble Energy Star
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
Option "dpms" "false"
EndSection

---

