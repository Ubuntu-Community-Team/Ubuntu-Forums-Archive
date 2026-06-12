---
title: "How to change Ubuntu 11.10 Login Screen resolution in VMWare Fusion."
date: 2011-12-10
forum: Virtualisation
---

### Post by AKYJedi on 2011-12-10
I have a TOSHIBA 32TL515U 3D LED TV as my computer monitor as I work in Ubuntu 11.10 virtual machine (VM) using VMWare Fusion (Mac).

Ubuntu 11.10 has no problem in displaying 1920 x 1080 screen resolution after logging into Ubuntu 3D desktop (though display monitor is shown as "unknown").  My question however is "**How do I change the screen resolution for Ubuntu 11.10 login screen?**"  The login screen is shown at a lower resolution than the desktop screen (after login).

_VM Graphics Card is:_

*lspci | grep VGA*
**00:0f.0 VGA compatible controller: VMware SVGA II Adapter**

_Content of /etc/X11/xorg.conf:_ 

Section "Monitor"
   Identifier   "TOSHIBA 32TL515U 3D LED TV"
   Vendorname   "TOSHIBA"
   Modelname   "TOSHIBA 32TL515U LED TV Panel 1920x1080"
   Horizsync   31.5-50.0
   Vertrefresh   56.0 - 65.0
   modeline  "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
   Gamma   1.0
EndSection

_Running the command "*xrandr*" yields the following:_

[COLOR="Red"]xrandr: Failed to get size of gamma for output default[/COLOR]
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 5120 x 3200
default connected 1920x1080+0+0 0mm x 0mm
   1024x768       60.0      0.0  
   800x600        60.0     56.0      0.0  
   640x480        60.0      0.0  
   320x240         0.0  
   400x300         0.0  
   512x384         0.0  
   1152x864        0.0  
   1280x960        0.0  
   1400x1050       0.0  
   1600x1200       0.0  
   1920x1440       0.0  
   2048x1536       0.0  
   2560x1920       0.0  
   854x480         0.0  
   1280x720        0.0  
   1366x768        0.0  
   1920x1080       0.0* 
   1280x800        0.0  
   1440x900        0.0  
   1680x1050       0.0  
   1920x1200       0.0  
   2560x1600       0.0  
   720x480         0.0  
   720x576         0.0  
   320x200         0.0  
   640x400         0.0  
   800x480         0.0  
   1280x768        0.0  
   1280x1024       0.0  
   5120x3200       0.0  

Also, **VMware Tools** for this Ubuntu 11.10 VM has been installed successfully.

Thanks for any help offered to get my Ubuntu 11.10 Login screen to display in 1920 x 1080 resolution. :)

---

### Post by creiss on 2011-12-12
I am having the exact same problem. My login screen is rubbish (like 800x600). Once logged in its all cheerio!

I did switch from freeware drivers to fglrx for a moment (reboot), changed my mind and deinstalled. Then the problems occured.
 (But only with login screen, kernel boot and X is fine)

---

### Post by duckwhistle on 2012-04-08
Try adding the red subsection to your /etc/X11/xorg.conf file. Put the desired resolution first that should be the default.

```
Section "Screen"
    Identifier  "..."
    Device      "..."
    Monitor     "..."
    DefaultDepth    24

    [...]

[COLOR="Red"]    SubSection "Display"
        Depth       24
        Modes       "1280x1024" "1280x960" "1024x768" "800x600"
    EndSubSection[/COLOR]
EndSection
```

---

