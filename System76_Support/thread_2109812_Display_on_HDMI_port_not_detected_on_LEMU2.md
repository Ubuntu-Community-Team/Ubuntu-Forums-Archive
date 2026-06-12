---
title: "Display on HDMI port not detected on LEMU2"
date: 2013-01-28
forum: System76 Support
---

### Post by distroslut on 2013-01-28
This morning I found that my Lemur U2 running Ubuntu 12.10,with Kubuntu (package version 4:4.9.4-0ubuntu0.1) installed over the top, does not detect my Dell 1920x1200 external display which is connected to the HDMI port.

I have tried using a few different HDMI cables, a DVI cable with a DVI-HDMI adapter, and a different (but identical) monitor. No luck.

Below is the output of a few commands...

uname -a
Linux chandrasekhar 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 295mm x 166mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200      60.0*+
   1920x1080      60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1680x945       60.0  
   1400x1050      74.9     60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1280x768       74.9     59.9  
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     60.0  
   720x400        70.1

FTR, VGA out appears to be functioning normally.

Is there any other information that would be useful to post?

Thanks.

---

### Post by isantop on 2013-01-28
> **distroslut said:**
> This morning I found that my Lemur U2 running Ubuntu 12.10,with Kubuntu (package version 4:4.9.4-0ubuntu0.1) installed over the top, does not detect my Dell 1920x1200 external display which is connected to the HDMI port.

I have tried using a few different HDMI cables, a DVI cable with a DVI-HDMI adapter, and a different (but identical) monitor. No luck.

Below is the output of a few commands...

uname -a
Linux chandrasekhar 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 295mm x 166mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 519mm x 324mm
   1920x1200      60.0*+
   1920x1080      60.0  
   1600x1200      60.0  
   1680x1050      60.0  
   1680x945       60.0  
   1400x1050      74.9     60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1280x768       74.9     59.9  
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     60.0  
   720x400        70.1

FTR, VGA out appears to be functioning normally.

Is there any other information that would be useful to post?

Thanks.

How are you enabling the monitor? It's normal for it not to automatically come on.

---

### Post by distroslut on 2013-01-28
> How are you enabling the monitor? It's normal for it not to automatically come on.

If I plug in the HDMI cable when I'm already logged into KDE, a dialog box pops up asking if I want to launch the "Configure Display" dialog. From this dialog I enable the HDMI output at the resolution and orientation I want and hit "Apply"...

ftp.ssec.wisc.edu:/pub/incoming/Configure_Display.png

If the HDMI cable is already connected when I log in, I launch the same "Configure Display" dialog using the KDE panel "Resize and Rotate" widget.

Ordinarily, along with "LVDS1" and "VGA1", "HDMI1" would appear as an option in the "Configure Display" dialog (albeit disbled) if the cable was connected. I would then select the resolution I wanted and hit "Apply". A countdown dialog would then appear asking if wanted to keep the new settings.

---

### Post by distroslut on 2013-01-28
An update to the previous post... I took the LemU2 home and connected it to a different (1680x1050) Dell monitor. This time I was successful. A screenie of the configure dialog showing the HDMI entry can be found at...

ftp.ssec.wisc.edu:/pub/incoming/Configure_Display_2.png

I'm not quite ready to call this one resolved, I've got a few things to check out first. Stay tuned.

---

### Post by distroslut on 2013-01-29
Display on original Dell monitor using HDMI now functioning normally. I wish I had some idea what caused the original problem. Oh well.

---

