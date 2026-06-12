---
title: "Resolution problem with AMP and HTPC"
date: 2015-09-01
forum: Ubuntu/Debian BASED
---

### Post by alex_p2 on 2015-09-01
Hi,

I'm actually using KODIBuntu on my HTPC which is working fine.
Sadly, I've got a problem which I'm not able to fix by myself.
My HTPC is connected to my AMP (Denon AVR-1912). My TV (Samsung Smart TV) is also connected to the AVR.

When I turn on everything with my remote, everything works fine.
If I add a timer for my PVR in the future, the HTPC turns on by RTC and record the timer. Now to my problem:

If a record is running and just the HTPC is turned on and I turn on my AVR and the TV, I don't get a picture.
It seems, that the AVR/HTPC handshake (concerning the resolution) is not working.

As far as I remember, KODIBuntu is using Lightdm as default.
Could please someone help me? I also tried a solution with udevadm monitor, which was not working. In addition I also tried a grub parameter with EDID, which is also not working.

Might this is helping. This is the output from udevadm monitor when the AMP turns on:

```

[COLOR=#333333][FONT=Consolas]root@kodi:~# udevadm monitor[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]monitor will print the received events for:[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]UDEV - the event which udev sends out after rule processing[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]KERNEL - the kernel uevent[/FONT][/COLOR]

[COLOR=#333333][FONT=Consolas]KERNEL[1011.301987] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]UDEV  [1011.302552] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]KERNEL[1011.329056] add      /devices/platform/HDMI-A-2 (platform)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]UDEV  [1011.329346] add      /devices/platform/HDMI-A-2 (platform)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]KERNEL[1011.330344] remove   /devices/platform/HDMI-A-2 (platform)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]UDEV  [1011.330470] remove   /devices/platform/HDMI-A-2 (platform)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]KERNEL[1011.393123] add      /devices/platform/HDMI-A-2 (platform)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]KERNEL[1011.393188] remove   /devices/platform/HDMI-A-2 (platform)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]UDEV  [1011.393301] add      /devices/platform/HDMI-A-2 (platform)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]UDEV  [1011.393730] remove   /devices/platform/HDMI-A-2 (platform)[/FONT][/COLOR]

[COLOR=#333333][FONT=Consolas]Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]VGA1 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]HDMI1 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]HDMI2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1920x1080      60.0*+   50.0     59.9     30.0     25.0     24.0     30.0     24.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1920x1080i     60.1     50.0     60.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1680x1050      59.9[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   2880x576       50.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1600x900       60.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   2880x480       60.0     59.9[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1280x1024      75.0     60.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1440x900       59.9[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1366x768       59.8[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1280x800       59.9[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1152x864       75.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1280x720       60.0     50.0     59.9[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1440x576       50.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1440x576i      50.1[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1024x768       75.1     70.1     60.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1440x480       60.0     59.9[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   1440x480i      60.1     60.1[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   832x624        74.6[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   800x600        72.2     75.0     60.3[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   720x576        50.0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   720x480        60.0     59.9[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   640x480        75.0     72.8     66.7     60.0     59.9[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]   720x400        70.1[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]VIRTUAL1 disconnected (normal left inverted right x axis y axis)[/FONT][/COLOR]

```

I would really appreciate if someone could finally help me to solve this problem.
Thanks in advance.

---

### Post by howefield on 2015-09-01
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by alex_p2 on 2015-09-07
No one? :(

---

