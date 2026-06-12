---
title: "libreoffice window cannot be focused when maximised"
date: 2024-04-12
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2024-04-12
After recent updates to mutter and/or gnome-shell, libreoffice window cannot be focused when maximised whenever there is a window of another app in the same workspace.
I can select text with the mouse, but cannot click anything and cannot type.
If I click the window at a place that covers another app (such as Files), the other app becomes focused and rised up.

Only workaround is close all non-libreoffice window at the same workspace.

Is this a known issue? or should it be reported as a new mutter bug?

---

### Post by corradoventu on 2024-04-12
I'm unable to reproduce problem on my Ubuntu 24.04 installed from Beta ISO. Session Wayland Intel UHD Graphics 730

---

### Post by Wise Ferret on 2024-04-12
Thank you. My session is nvidia-driver-550 + X11.

---

### Post by #&amp;thj^% on 2024-04-12
Hi Wise Ferret, this has been a problem with Gnome for a few years Hit and Miss.
Anyway have you tried, While Calc is your current program, use [Alt + Space] to force the window to maximize again, or resize to wherever you want it.

```
 inxi -G | grep -e Display -e Device-1 -e v
  Device-1: NVIDIA GA107BM [GeForce RTX 3050 Ti Mobile] driver: nvidia
    v: 550.67
  Device-2: AMD Cezanne [Radeon Vega Series / Radeon Mobile Series]
    driver: amdgpu v: kernel
  Device-3: Bison Integrated Camera driver: uvcvideo type: USB
  Display: wayland server: X.org v: 1.21.1.12 with: Xwayland v: 21.1.99
    compositor: kwin_wayland driver: X: loaded: modesetting,nvidia dri: radeonsi
    gpu: nvidia,amdgpu resolution: 1829x1029
  API: EGL v: 1.5 drivers: nvidia,radeonsi,swrast
    platforms: gbm,wayland,x11,surfaceless,device
  API: OpenGL v: 4.6.0 compat-v: 4.5 vendor: amd mesa v: 24.0.5-arch1.2
  API: Vulkan v: 1.3.279 drivers: nvidia,radv surfaces: xcb,xlib,wayland

```

---

### Post by #&amp;thj^% on 2024-04-12
> **1fallen said:**
> Hi Wise Ferret, this has been a problem with Gnome for a few years Hit and Miss.
Anyway have you tried, While Calc is your current program, use [Alt + Space] to force the window to maximize again, or resize to wherever you want it.

Screenshots added to help.

---

### Post by Wise Ferret on 2024-04-12
Thank you, alt+space is a workaround.
Now I see the problem is more complicated then I thought. It seems the latest updates added a new monitor called "unknown", even though I have only one monitor, and it moves the libreoffice window there on startup!
This is what I see on xrandr -q:```
~$ xrandr -q
Screen 0: minimum 8 x 8, current 7680 x 2160, maximum 32767 x 32767
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 600mm x 340mm
   3840x2160     60.00*+  30.00  
   2560x1440     59.95  
   1920x1080     60.00    59.94  
   1600x900      60.00  
   1280x1024     60.02  
   1280x800      59.81  
   1280x720      60.00    59.94  
   1152x864      59.96  
   1024x768      60.00  
   800x600       60.32  
   720x480       59.94  
   640x480       59.94    59.93  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
None-1-1 connected (normal left inverted right x axis y axis)
   3840x2160     60.00 +
```

As you see, I there is a screen named "None-1-1" connected besides my proper screen.
When I tried removing it, I got: ```
~$ xrandr --output None-1-1 --off
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Serial number of failed request:  45
  Current serial number in output stream:  47
```

 And this is what I have is /sys/class/drm: ```
ls /sys/class/drm
card0            card1       card1-DP-2      card1-HDMI-A-2  version
card0-Unknown-1  card1-DP-1  card1-HDMI-A-1  renderD128
```

How can I get rid of the newly-added, non-existent monitor?

---

### Post by jbicha on 2024-04-12
Personally I find that there are some odd bugs when Ubuntu's tiling extension is turned on. You can turn it off in the Settings app > Ubuntu Desktop > Enhanced Tiling has its own off switch.

---

### Post by Wise Ferret on 2024-04-13
> **jbicha said:**
> Personally I find that there are some odd bugs when Ubuntu's tiling extension is turned on. You can turn it off in the Settings app > Ubuntu Desktop > Enhanced Tiling has its own off switch.
Thank you, this seems to help out. Before I disabled this extension, I couldn't even grab libreoffice window borders with the mouse in order to resize it, and now it works. It also stopped playing weird games with the focus.
That's a shame, because the tiling extension's functionality is very useful to me.

---

