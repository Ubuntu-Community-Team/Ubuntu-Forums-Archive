---
title: "Graphic tablet won't work even with wizardpen drivers"
date: 2014-06-15
forum: Ubuntu Studio
---

### Post by jonas-h331 on 2014-06-15
Hello,
I own Genius PenSketch M912A graphics tablet. (website: [http://www.geniusnet.com/Genius/wSite/ct?xItem=53291&ctNode=174](http://www.geniusnet.com/Genius/wSite/ct?xItem=53291&ctNode=174))
When I first connected it to my computer, it acted only as a touchpad - I could only navigate the mouse with it by hovering the pen over the sensitive part of tablet (that's how it should work), but I can't click, it stops working when I touch the tablet with the pen and the mouse doesn't work at all. The tablet itself is working (tested on windows PC).

After seeing that it is not working, I decided to install drivers - I found wizardpen drivers - [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) - and installed them as described. 
I get the output, that the drivers were installed properly. Tablet still doesn't work. That means I had to edit the "[COLOR=#333333][FONT=Ubuntu]70-wizardpen.conf[/FONT][/COLOR]" file.

I edited it as in the guide, now it looks like this:
> Section "InputClass"   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-Genius_PenSketch_M912-event-mouse"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-Genius_PenSketch_M912-mouse"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection

And that is as far as I got.
Tablet still works the same as at the start, so it doesn't.
I'm not a really good Ubuntu user, so I might have done something wrong and I want to find what, because I don't want to use the tablet in windows.
Thanks for help. Maybe I didn't give you all the information you need, just tell me what and I will give you the information. And I'm also sorry for my not-so-good English.

---

### Post by CrocoDuck on 2014-06-15
Hi! Not that expert of graphic tabs (I have an old one I cannot figure out how to make it work... but since I am not in the graphic-thing I don't even try that hard). Can you give the output of this commands?

```

uname -a

```

```

lsusb

```

---

### Post by jonas-h331 on 2014-06-16
Thanks for replying,

uname -a output:
> Linux jonda-Lenovo-G770 3.13.0-29-lowlatency #53-Ubuntu SMP PREEMPT Wed Jun 4 21:27:51 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

lsusb output:
> 
Bus 002 Device 004: ID 064e:a222 Suyin Corp. 
Bus 002 Device 008: ID 0458:5015 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 003: ID 04b4:0060 Cypress Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


when I connected the tablet to another usb port:
> 
Bus 002 Device 009: ID 0458:5015 KYE Systems Corp. (Mouse Systems)

This one changed, just thought it might be helpful.

---

### Post by CrocoDuck on 2014-06-16
Let's have a look at xorg logs:

```

cat /var/log/Xorg.0.log | grep wizardpen

```

```

cat /var/log/Xorg.0.log | grep ABI

```

---

### Post by jonas-h331 on 2014-06-16
The first one ([COLOR=#000000][FONT=Ubuntu Mono]cat /var/log/Xorg.0.log | grep wizardpen[/FONT][/COLOR]) haven't outputed anything.
The output of the second one:
> 
[    28.451] (II) Module ABI versions:[    29.199]     ABI class: X.Org Server Extension, version 8.0
[    29.252]     ABI class: X.Org Video Driver, version 15.0
[    29.252]     ABI class: X.Org Video Driver, version 15.0
[    29.317]     ABI class: X.Org Video Driver, version 15.0
[    29.317]     ABI class: X.Org Video Driver, version 15.0
[    29.317]     ABI class: X.Org Video Driver, version 15.0
[    29.317]     ABI class: X.Org Video Driver, version 15.0
[    29.318]     ABI class: X.Org Video Driver, version 15.0
[    29.318]     ABI class: X.Org Video Driver, version 15.0
[    29.318]     ABI class: X.Org Video Driver, version 15.0
[    29.318]     ABI class: X.Org Video Driver, version 15.0
[    29.319]     ABI class: X.Org Video Driver, version 15.0
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
[    29.325]     ABI class: X.Org Video Driver, version 15.0
[    29.327]     ABI class: X.Org Video Driver, version 15.0
[    29.357]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.458]     ABI class: X.Org XInput driver, version 20.0
[    29.467]     ABI class: X.Org XInput driver, version 20.0


Though, there's a log about the tablet (if it helps):

> [   972.973] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/mouse2)[   972.973] (II) No input driver specified, ignoring this device.
[   972.973] (II) This device may have been added with another device file.
[   972.973] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/event14)
[   972.973] (**) Genius PenSketch M912: Applying InputClass "evdev pointer catchall"
[   972.973] (**) Genius PenSketch M912: Applying InputClass "evdev keyboard catchall"
[   972.973] (**) Genius PenSketch M912: Applying InputClass "evdev tablet catchall"
[   972.973] (II) Using input driver 'evdev' for 'Genius PenSketch M912'
[   972.973] (**) Genius PenSketch M912: always reports core events
[   972.973] (**) evdev: Genius PenSketch M912: Device: "/dev/input/event14"
[   972.973] (--) evdev: Genius PenSketch M912: Vendor 0x458 Product 0x5015
[   972.973] (--) evdev: Genius PenSketch M912: Found 10 mouse buttons
[   972.973] (--) evdev: Genius PenSketch M912: Found scroll wheel(s)
[   972.973] (--) evdev: Genius PenSketch M912: Found relative axes
[   972.973] (--) evdev: Genius PenSketch M912: Found x and y relative axes
[   972.973] (--) evdev: Genius PenSketch M912: Found absolute axes
[   972.973] (--) evdev: Genius PenSketch M912: Found x and y absolute axes
[   972.973] (--) evdev: Genius PenSketch M912: Found absolute tablet.
[   972.973] (--) evdev: Genius PenSketch M912: Found keys
[   972.973] (II) evdev: Genius PenSketch M912: Configuring as tablet
[   972.973] (II) evdev: Genius PenSketch M912: Configuring as keyboard
[   972.973] (II) evdev: Genius PenSketch M912: Adding scrollwheel support
[   972.973] (**) evdev: Genius PenSketch M912: YAxisMapping: buttons 4 and 5
[   972.974] (**) evdev: Genius PenSketch M912: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   972.974] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input15/event14"
[   972.974] (II) XINPUT: Adding extended input device "Genius PenSketch M912" (type: KEYBOARD, id 16)
[   972.974] (**) Option "xkb_rules" "evdev"
[   972.974] (**) Option "xkb_model" "pc105"
[   972.974] (**) Option "xkb_layout" "cz"
[   972.974] (WW) evdev: Genius PenSketch M912: touchpads, tablets and touchscreens ignore relative axes.
[   972.974] (II) evdev: Genius PenSketch M912: initialized for absolute axes.
[   972.974] (**) Genius PenSketch M912: (accel) keeping acceleration scheme 1
[   972.974] (**) Genius PenSketch M912: (accel) acceleration profile 0
[   972.974] (**) Genius PenSketch M912: (accel) acceleration factor: 2.000
[   972.974] (**) Genius PenSketch M912: (accel) acceleration threshold: 4
[   972.998] reporting 9 6 10 77
[   973.100] reporting 9 6 10 77
[   973.252] reporting 9 6 10 77
[   973.393] reporting 9 6 10 77
[   973.478] reporting 9 6 10 77
[   983.169] (II) config/udev: removing device Genius PenSketch M912
[   983.182] (II) evdev: Genius PenSketch M912: Close
[   983.182] (II) UnloadModule: "evdev"
[   984.724] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/mouse2)
[   984.724] (II) No input driver specified, ignoring this device.
[   984.724] (II) This device may have been added with another device file.
[   984.725] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/event14)
[   984.725] (**) Genius PenSketch M912: Applying InputClass "evdev pointer catchall"
[   984.725] (**) Genius PenSketch M912: Applying InputClass "evdev keyboard catchall"
[   984.725] (**) Genius PenSketch M912: Applying InputClass "evdev tablet catchall"
[   984.725] (II) Using input driver 'evdev' for 'Genius PenSketch M912'
[   984.725] (**) Genius PenSketch M912: always reports core events
[   984.725] (**) evdev: Genius PenSketch M912: Device: "/dev/input/event14"
[   984.725] (--) evdev: Genius PenSketch M912: Vendor 0x458 Product 0x5015
[   984.725] (--) evdev: Genius PenSketch M912: Found 10 mouse buttons
[   984.725] (--) evdev: Genius PenSketch M912: Found scroll wheel(s)
[   984.725] (--) evdev: Genius PenSketch M912: Found relative axes
[   984.725] (--) evdev: Genius PenSketch M912: Found x and y relative axes
[   984.725] (--) evdev: Genius PenSketch M912: Found absolute axes
[   984.725] (--) evdev: Genius PenSketch M912: Found x and y absolute axes
[   984.725] (--) evdev: Genius PenSketch M912: Found absolute tablet.
[   984.725] (--) evdev: Genius PenSketch M912: Found keys
[   984.725] (II) evdev: Genius PenSketch M912: Configuring as tablet
[   984.725] (II) evdev: Genius PenSketch M912: Configuring as keyboard
[   984.725] (II) evdev: Genius PenSketch M912: Adding scrollwheel support
[   984.725] (**) evdev: Genius PenSketch M912: YAxisMapping: buttons 4 and 5
[   984.725] (**) evdev: Genius PenSketch M912: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   984.725] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input16/event14"
[   984.725] (II) XINPUT: Adding extended input device "Genius PenSketch M912" (type: KEYBOARD, id 16)
[   984.725] (**) Option "xkb_rules" "evdev"
[   984.725] (**) Option "xkb_model" "pc105"
[   984.726] (**) Option "xkb_layout" "cz"
[   984.726] (WW) evdev: Genius PenSketch M912: touchpads, tablets and touchscreens ignore relative axes.
[   984.726] (II) evdev: Genius PenSketch M912: initialized for absolute axes.
[   984.727] (**) Genius PenSketch M912: (accel) keeping acceleration scheme 1
[   984.727] (**) Genius PenSketch M912: (accel) acceleration profile 0
[   984.727] (**) Genius PenSketch M912: (accel) acceleration factor: 2.000
[   984.727] (**) Genius PenSketch M912: (accel) acceleration threshold: 4
[   984.730] reporting 9 6 10 77
[   984.840] reporting 9 6 10 77
[   984.993] reporting 9 6 10 77
[   985.135] reporting 9 6 10 77
[   985.210] reporting 9 6 10 77
[   990.332] (II) config/udev: removing device Genius PenSketch M912
[   990.346] (II) evdev: Genius PenSketch M912: Close
[   990.346] (II) UnloadModule: "evdev"
[   991.761] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/mouse2)
[   991.761] (II) No input driver specified, ignoring this device.
[   991.761] (II) This device may have been added with another device file.
[   991.763] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/event14)
[   991.763] (**) Genius PenSketch M912: Applying InputClass "evdev pointer catchall"
[   991.763] (**) Genius PenSketch M912: Applying InputClass "evdev keyboard catchall"
[   991.763] (**) Genius PenSketch M912: Applying InputClass "evdev tablet catchall"
[   991.763] (II) Using input driver 'evdev' for 'Genius PenSketch M912'
[   991.763] (**) Genius PenSketch M912: always reports core events
[   991.763] (**) evdev: Genius PenSketch M912: Device: "/dev/input/event14"
[   991.763] (--) evdev: Genius PenSketch M912: Vendor 0x458 Product 0x5015
[   991.763] (--) evdev: Genius PenSketch M912: Found 10 mouse buttons
[   991.763] (--) evdev: Genius PenSketch M912: Found scroll wheel(s)
[   991.763] (--) evdev: Genius PenSketch M912: Found relative axes
[   991.763] (--) evdev: Genius PenSketch M912: Found x and y relative axes
[   991.763] (--) evdev: Genius PenSketch M912: Found absolute axes
[   991.763] (--) evdev: Genius PenSketch M912: Found x and y absolute axes
[   991.763] (--) evdev: Genius PenSketch M912: Found absolute tablet.
[   991.763] (--) evdev: Genius PenSketch M912: Found keys
[   991.763] (II) evdev: Genius PenSketch M912: Configuring as tablet
[   991.763] (II) evdev: Genius PenSketch M912: Configuring as keyboard
[   991.763] (II) evdev: Genius PenSketch M912: Adding scrollwheel support
[   991.763] (**) evdev: Genius PenSketch M912: YAxisMapping: buttons 4 and 5
[   991.763] (**) evdev: Genius PenSketch M912: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   991.763] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/usb3/3-1/3-1:1.0/input/input17/event14"
[   991.763] (II) XINPUT: Adding extended input device "Genius PenSketch M912" (type: KEYBOARD, id 16)
[   991.763] (**) Option "xkb_rules" "evdev"
[   991.763] (**) Option "xkb_model" "pc105"
[   991.763] (**) Option "xkb_layout" "cz"
[   991.763] (WW) evdev: Genius PenSketch M912: touchpads, tablets and touchscreens ignore relative axes.
[   991.763] (II) evdev: Genius PenSketch M912: initialized for absolute axes.
[   991.764] (**) Genius PenSketch M912: (accel) keeping acceleration scheme 1
[   991.764] (**) Genius PenSketch M912: (accel) acceleration profile 0
[   991.764] (**) Genius PenSketch M912: (accel) acceleration factor: 2.000
[   991.764] (**) Genius PenSketch M912: (accel) acceleration threshold: 4
[   991.768] reporting 9 6 10 77
[   991.894] reporting 9 6 10 77
[   992.075] reporting 9 6 10 77
[   992.231] reporting 9 6 10 77
[   992.334] reporting 9 6 10 77
[  1012.318] reporting 9 6 10 77
[  1013.662] reporting 9 6 10 77
[  1013.713] reporting 9 6 10 77
[  1022.324] reporting 9 6 10 77
[  1022.348] reporting 9 6 10 77
[  1022.499] reporting 9 6 10 77
[  1213.817] (II) config/udev: removing device Genius PenSketch M912
[  1213.832] (II) evdev: Genius PenSketch M912: Close
[  1213.832] (II) UnloadModule: "evdev"
[  1215.370] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/mouse2)
[  1215.370] (II) No input driver specified, ignoring this device.
[  1215.370] (II) This device may have been added with another device file.
[  1215.371] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/event14)
[  1215.371] (**) Genius PenSketch M912: Applying InputClass "evdev pointer catchall"
[  1215.371] (**) Genius PenSketch M912: Applying InputClass "evdev keyboard catchall"
[  1215.371] (**) Genius PenSketch M912: Applying InputClass "evdev tablet catchall"
[  1215.371] (II) Using input driver 'evdev' for 'Genius PenSketch M912'
[  1215.371] (**) Genius PenSketch M912: always reports core events
[  1215.371] (**) evdev: Genius PenSketch M912: Device: "/dev/input/event14"
[  1215.371] (--) evdev: Genius PenSketch M912: Vendor 0x458 Product 0x5015
[  1215.371] (--) evdev: Genius PenSketch M912: Found 10 mouse buttons
[  1215.371] (--) evdev: Genius PenSketch M912: Found scroll wheel(s)
[  1215.371] (--) evdev: Genius PenSketch M912: Found relative axes
[  1215.371] (--) evdev: Genius PenSketch M912: Found x and y relative axes
[  1215.371] (--) evdev: Genius PenSketch M912: Found absolute axes
[  1215.371] (--) evdev: Genius PenSketch M912: Found x and y absolute axes
[  1215.371] (--) evdev: Genius PenSketch M912: Found absolute tablet.
[  1215.371] (--) evdev: Genius PenSketch M912: Found keys
[  1215.371] (II) evdev: Genius PenSketch M912: Configuring as tablet
[  1215.371] (II) evdev: Genius PenSketch M912: Configuring as keyboard
[  1215.371] (II) evdev: Genius PenSketch M912: Adding scrollwheel support
[  1215.371] (**) evdev: Genius PenSketch M912: YAxisMapping: buttons 4 and 5
[  1215.371] (**) evdev: Genius PenSketch M912: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1215.371] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input18/event14"
[  1215.371] (II) XINPUT: Adding extended input device "Genius PenSketch M912" (type: KEYBOARD, id 16)
[  1215.371] (**) Option "xkb_rules" "evdev"
[  1215.371] (**) Option "xkb_model" "pc105"
[  1215.371] (**) Option "xkb_layout" "cz"
[  1215.371] (WW) evdev: Genius PenSketch M912: touchpads, tablets and touchscreens ignore relative axes.
[  1215.372] (II) evdev: Genius PenSketch M912: initialized for absolute axes.
[  1215.372] (**) Genius PenSketch M912: (accel) keeping acceleration scheme 1
[  1215.372] (**) Genius PenSketch M912: (accel) acceleration profile 0
[  1215.372] (**) Genius PenSketch M912: (accel) acceleration factor: 2.000
[  1215.372] (**) Genius PenSketch M912: (accel) acceleration threshold: 4
[  1215.374] reporting 9 6 10 77
[  1215.477] reporting 9 6 10 77
[  1215.620] reporting 9 6 10 77
[  1215.742] reporting 9 6 10 77
[  1215.856] reporting 9 6 10 77
[  1233.015] (II) config/udev: removing device Genius PenSketch M912
[  1233.020] (II) evdev: Genius PenSketch M912: Close
[  1233.020] (II) UnloadModule: "evdev"
[  1234.068] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/mouse2)
[  1234.068] (II) No input driver specified, ignoring this device.
[  1234.068] (II) This device may have been added with another device file.
[  1234.070] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/event14)
[  1234.070] (**) Genius PenSketch M912: Applying InputClass "evdev pointer catchall"
[  1234.070] (**) Genius PenSketch M912: Applying InputClass "evdev keyboard catchall"
[  1234.070] (**) Genius PenSketch M912: Applying InputClass "evdev tablet catchall"
[  1234.070] (II) Using input driver 'evdev' for 'Genius PenSketch M912'
[  1234.070] (**) Genius PenSketch M912: always reports core events
[  1234.070] (**) evdev: Genius PenSketch M912: Device: "/dev/input/event14"
[  1234.070] (--) evdev: Genius PenSketch M912: Vendor 0x458 Product 0x5015
[  1234.070] (--) evdev: Genius PenSketch M912: Found 10 mouse buttons
[  1234.070] (--) evdev: Genius PenSketch M912: Found scroll wheel(s)
[  1234.071] (--) evdev: Genius PenSketch M912: Found relative axes
[  1234.071] (--) evdev: Genius PenSketch M912: Found x and y relative axes
[  1234.071] (--) evdev: Genius PenSketch M912: Found absolute axes
[  1234.071] (--) evdev: Genius PenSketch M912: Found x and y absolute axes
[  1234.071] (--) evdev: Genius PenSketch M912: Found absolute tablet.
[  1234.071] (--) evdev: Genius PenSketch M912: Found keys
[  1234.071] (II) evdev: Genius PenSketch M912: Configuring as tablet
[  1234.071] (II) evdev: Genius PenSketch M912: Configuring as keyboard
[  1234.071] (II) evdev: Genius PenSketch M912: Adding scrollwheel support
[  1234.071] (**) evdev: Genius PenSketch M912: YAxisMapping: buttons 4 and 5
[  1234.071] (**) evdev: Genius PenSketch M912: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1234.071] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input19/event14"
[  1234.071] (II) XINPUT: Adding extended input device "Genius PenSketch M912" (type: KEYBOARD, id 16)
[  1234.071] (**) Option "xkb_rules" "evdev"
[  1234.071] (**) Option "xkb_model" "pc105"
[  1234.071] (**) Option "xkb_layout" "cz"
[  1234.071] (WW) evdev: Genius PenSketch M912: touchpads, tablets and touchscreens ignore relative axes.
[  1234.072] (II) evdev: Genius PenSketch M912: initialized for absolute axes.
[  1234.072] (**) Genius PenSketch M912: (accel) keeping acceleration scheme 1
[  1234.072] (**) Genius PenSketch M912: (accel) acceleration profile 0
[  1234.072] (**) Genius PenSketch M912: (accel) acceleration factor: 2.000
[  1234.072] (**) Genius PenSketch M912: (accel) acceleration threshold: 4
[  1234.075] reporting 9 6 10 77
[  1234.182] reporting 9 6 10 77
[  1234.325] reporting 9 6 10 77
[  1234.437] reporting 9 6 10 77
[  1234.545] reporting 9 6 10 77
[  1258.952] reporting 9 6 10 77
[  1260.704] reporting 9 6 10 77
[  1265.900] reporting 9 6 10 77
[  1271.160] (II) config/udev: removing device Genius PenSketch M912
[  1271.171] (II) evdev: Genius PenSketch M912: Close
[  1271.171] (II) UnloadModule: "evdev"
[  1273.224] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/mouse2)
[  1273.224] (II) No input driver specified, ignoring this device.
[  1273.224] (II) This device may have been added with another device file.
[  1273.228] (II) config/udev: Adding input device Genius PenSketch M912 (/dev/input/event14)
[  1273.228] (**) Genius PenSketch M912: Applying InputClass "evdev pointer catchall"
[  1273.228] (**) Genius PenSketch M912: Applying InputClass "evdev keyboard catchall"
[  1273.228] (**) Genius PenSketch M912: Applying InputClass "evdev tablet catchall"
[  1273.228] (II) Using input driver 'evdev' for 'Genius PenSketch M912'
[  1273.228] (**) Genius PenSketch M912: always reports core events
[  1273.228] (**) evdev: Genius PenSketch M912: Device: "/dev/input/event14"
[  1273.228] (--) evdev: Genius PenSketch M912: Vendor 0x458 Product 0x5015
[  1273.228] (--) evdev: Genius PenSketch M912: Found 10 mouse buttons
[  1273.228] (--) evdev: Genius PenSketch M912: Found scroll wheel(s)
[  1273.228] (--) evdev: Genius PenSketch M912: Found relative axes
[  1273.228] (--) evdev: Genius PenSketch M912: Found x and y relative axes
[  1273.228] (--) evdev: Genius PenSketch M912: Found absolute axes
[  1273.228] (--) evdev: Genius PenSketch M912: Found x and y absolute axes
[  1273.228] (--) evdev: Genius PenSketch M912: Found absolute tablet.
[  1273.228] (--) evdev: Genius PenSketch M912: Found keys
[  1273.228] (II) evdev: Genius PenSketch M912: Configuring as tablet
[  1273.228] (II) evdev: Genius PenSketch M912: Configuring as keyboard
[  1273.228] (II) evdev: Genius PenSketch M912: Adding scrollwheel support
[  1273.228] (**) evdev: Genius PenSketch M912: YAxisMapping: buttons 4 and 5
[  1273.228] (**) evdev: Genius PenSketch M912: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1273.228] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input20/event14"
[  1273.228] (II) XINPUT: Adding extended input device "Genius PenSketch M912" (type: KEYBOARD, id 16)
[  1273.228] (**) Option "xkb_rules" "evdev"
[  1273.228] (**) Option "xkb_model" "pc105"
[  1273.228] (**) Option "xkb_layout" "cz"
[  1273.228] (WW) evdev: Genius PenSketch M912: touchpads, tablets and touchscreens ignore relative axes.
[  1273.228] (II) evdev: Genius PenSketch M912: initialized for absolute axes.
[  1273.229] (**) Genius PenSketch M912: (accel) keeping acceleration scheme 1
[  1273.229] (**) Genius PenSketch M912: (accel) acceleration profile 0
[  1273.229] (**) Genius PenSketch M912: (accel) acceleration factor: 2.000
[  1273.229] (**) Genius PenSketch M912: (accel) acceleration threshold: 4


---

### Post by CrocoDuck on 2014-06-16
Uhm... I suspect you may be facing this bug or one closely related: [https://bugs.launchpad.net/wizardpen/+bug/1029951](https://bugs.launchpad.net/wizardpen/+bug/1029951) . At post #5 is suggested a workaround. You could try to uninstall the drivers and then compiling them from source with the proper headers as suggested. Can't find the same errors though. This is making me thinking:

```

[   972.973] (II) config/udev: Adding input device Genius PenSketch  M912 (/dev/input/mouse2)[   972.973] (II) No input driver specified,  ignoring this device.

```

---

### Post by jonas-h331 on 2014-06-16
So I deleted all the driver files and tried installing again, now reading everything carefully. It got stuck, when I did the make command here is the error:

> make  all-recursivemake[1]: Entering directory `/home/jonda/xorg-input-wizardpen-0.8.0'
Making all in src
make[2]: Entering directory `/home/jonda/xorg-input-wizardpen-0.8.0/src'
/bin/bash ../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -pthread -fvisibility=hidden -I/usr/include/pixman-1 -I/usr/include/mirclient -I/usr/include/libdrm -I/usr/include/mircommon -I/usr/include/xorg -I/usr/include/X11/dri    -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c -o wizardpen.lo wizardpen.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -pthread -fvisibility=hidden -I/usr/include/pixman-1 -I/usr/include/mirclient -I/usr/include/libdrm -I/usr/include/mircommon -I/usr/include/xorg -I/usr/include/X11/dri -I../src -MT wizardpen.lo -MD -MP -MF .deps/wizardpen.Tpo -c wizardpen.c  -fPIC -DPIC -o .libs/wizardpen.o
In file included from wizardpen.c:77:0:
wizardpen.h:134:1: warning: parameter names (without types) in function declaration [enabled by default]
 static void CloseProc (LocalDevicePtr);
 ^
wizardpen.h:138:54: error: unknown type name 'IDevPtr'
 static InputInfoPtr WizardPenPreInit(InputDriverPtr, IDevPtr , int);
                                                      ^
wizardpen.h:141:5: warning: parameter names (without types) in function declaration [enabled by default]
     static void USBReadInput (LocalDevicePtr);
     ^
wizardpen.h:142:5: warning: parameter names (without types) in function declaration [enabled by default]
     static Bool USBQueryHardware (LocalDevicePtr);
     ^
wizardpen.h:144:55: error: expected ')' before 'int'
     static Bool WizardPenAutoDevProbe(LocalDevicePtr, int);
                                                       ^
wizardpen.c:98:5: error: 'WizardPenPreInit' undeclared here (not in a function)
     WizardPenPreInit,
     ^
wizardpen.c:200:23: error: unknown type name 'LocalDevicePtr'
 WizardPenAutoDevProbe(LocalDevicePtr local, int verb)
                       ^
wizardpen.c:301:38: error: unknown type name 'IDevPtr'
 WizardPenPreInit(InputDriverPtr drv, IDevPtr dev, int flags)
                                      ^
wizardpen.c: In function 'DeviceOn':
wizardpen.c:602:5: error: unknown type name 'LocalDevicePtr'
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
     ^
wizardpen.c:602:29: error: 'LocalDevicePtr' undeclared (first use in this function)
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
                             ^
wizardpen.c:602:29: note: each undeclared identifier is reported only once for each function it appears in
wizardpen.c:602:45: error: expected ',' or ';' before 'dev'
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
                                             ^
wizardpen.c:603:60: error: invalid type argument of '->' (have 'int')
     WizardPenPrivatePtr priv = (WizardPenPrivatePtr) (local->private);
                                                            ^
wizardpen.c:605:51: error: invalid type argument of '->' (have 'int')
     xf86MsgVerb(X_INFO, 4, "%s Device On\n", local->name);
                                                   ^
wizardpen.c:607:10: error: invalid type argument of '->' (have 'int')
     local->fd = xf86OpenSerial(local->options);
          ^
wizardpen.c:607:37: error: invalid type argument of '->' (have 'int')
     local->fd = xf86OpenSerial(local->options);
                                     ^
wizardpen.c:608:14: error: invalid type argument of '->' (have 'int')
     if (local->fd == -1)
              ^
wizardpen.c:610:74: error: invalid type argument of '->' (have 'int')
         xf86Msg(X_WARNING, "%s: cannot open input device %s: %s\n", local->name, xf86FindOptionValue(local->options, "Device"), strerror(errno));
                                                                          ^
wizardpen.c:610:107: error: invalid type argument of '->' (have 'int')
         xf86Msg(X_WARNING, "%s: cannot open input device %s: %s\n", local->name, xf86FindOptionValue(local->options, "Device"), strerror(errno));
                                                                                                           ^
wizardpen.c:614:18: error: invalid type argument of '->' (have 'int')
             local->fd = xf86OpenSerial(local->options);
                  ^
wizardpen.c:614:45: error: invalid type argument of '->' (have 'int')
             local->fd = xf86OpenSerial(local->options);
                                             ^
wizardpen.c:615:18: error: invalid type argument of '->' (have 'int')
         if (local->fd == -1)
                  ^
wizardpen.c:623:37: error: invalid type argument of '->' (have 'int')
         priv->buffer = XisbNew(local->fd, 200);
                                     ^
wizardpen.c:626:34: error: invalid type argument of '->' (have 'int')
             xf86CloseSerial(local->fd);
                                  ^
wizardpen.c:627:18: error: invalid type argument of '->' (have 'int')
             local->fd = -1;
                  ^
wizardpen.c:636:25: error: invalid type argument of '->' (have 'int')
     xf86FlushInput(local->fd);
                         ^
wizardpen.c:637:5: warning: passing argument 1 of 'xf86AddEnabledDevice' makes pointer from integer without a cast [enabled by default]
     xf86AddEnabledDevice (local);
     ^
In file included from wizardpen.c:58:0:
/usr/include/xorg/xf86Xinput.h:171:23: note: expected 'InputInfoPtr' but argument is of type 'int'
 extern _X_EXPORT void xf86AddEnabledDevice(InputInfoPtr pInfo);
                       ^
wizardpen.c: In function 'DeviceOff':
wizardpen.c:645:5: error: unknown type name 'LocalDevicePtr'
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
     ^
wizardpen.c:645:29: error: 'LocalDevicePtr' undeclared (first use in this function)
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
                             ^
wizardpen.c:645:45: error: expected ',' or ';' before 'dev'
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
                                             ^
wizardpen.c:646:60: error: invalid type argument of '->' (have 'int')
     WizardPenPrivatePtr priv = (WizardPenPrivatePtr) (local->private);
                                                            ^
wizardpen.c:648:52: error: invalid type argument of '->' (have 'int')
     xf86MsgVerb(X_INFO, 4, "%s Device Off\n", local->name);
                                                    ^
wizardpen.c:650:14: error: invalid type argument of '->' (have 'int')
     if (local->fd != -1)
              ^
wizardpen.c:652:35: error: invalid type argument of '->' (have 'int')
         RemoveEnabledDevice (local->fd);
                                   ^
wizardpen.c:658:30: error: invalid type argument of '->' (have 'int')
         xf86CloseSerial(local->fd);
                              ^
wizardpen.c:662:5: warning: passing argument 1 of 'xf86RemoveEnabledDevice' makes pointer from integer without a cast [enabled by default]
     xf86RemoveEnabledDevice (local);
     ^
In file included from wizardpen.c:58:0:
/usr/include/xorg/xf86Xinput.h:172:23: note: expected 'InputInfoPtr' but argument is of type 'int'
 extern _X_EXPORT void xf86RemoveEnabledDevice(InputInfoPtr pInfo);
                       ^
wizardpen.c: In function 'DeviceClose':
wizardpen.c:670:5: error: unknown type name 'LocalDevicePtr'
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
     ^
wizardpen.c:670:29: error: 'LocalDevicePtr' undeclared (first use in this function)
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
                             ^
wizardpen.c:670:45: error: expected ',' or ';' before 'dev'
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
                                             ^
wizardpen.c:672:54: error: invalid type argument of '->' (have 'int')
     xf86MsgVerb(X_INFO, 4, "%s Device Close\n", local->name);
                                                      ^
wizardpen.c: In function 'ControlProc':
wizardpen.c:680:5: error: unknown type name 'LocalDevicePtr'
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
     ^
wizardpen.c:680:29: error: 'LocalDevicePtr' undeclared (first use in this function)
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
                             ^
wizardpen.c:680:45: error: expected ',' or ';' before 'dev'
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
                                             ^
wizardpen.c:682:54: error: invalid type argument of '->' (have 'int')
     xf86MsgVerb(X_INFO, 4, "%s Control Proc\n", local->name);
                                                      ^
wizardpen.c: In function 'DeviceInit':
wizardpen.c:689:5: error: unknown type name 'LocalDevicePtr'
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
     ^
wizardpen.c:689:29: error: 'LocalDevicePtr' undeclared (first use in this function)
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
                             ^
wizardpen.c:689:45: error: expected ',' or ';' before 'dev'
     LocalDevicePtr local = (LocalDevicePtr) dev->public.devicePrivate;
                                             ^
wizardpen.c:690:60: error: invalid type argument of '->' (have 'int')
     WizardPenPrivatePtr priv = (WizardPenPrivatePtr) (local->private);
                                                            ^
wizardpen.c:695:46: error: invalid type argument of '->' (have 'int')
     xf86MsgVerb(X_INFO, 4, "%s Init\n", local->name);
                                              ^
wizardpen.c:711:83: error: invalid type argument of '->' (have 'int')
         xf86Msg(X_ERROR, "%s: unable to allocate ButtonClassDeviceStruct\n", local->name);
                                                                                   ^
wizardpen.c:717:82: error: invalid type argument of '->' (have 'int')
         xf86Msg(X_ERROR, "%s: unable to allocate FocusClassDeviceStruct\n", local->name);
                                                                                  ^
wizardpen.c:722:68: error: invalid type argument of '->' (have 'int')
         xf86Msg(X_ERROR, "%s: unable to init ptr feedback\n", local->name);
                                                                    ^
wizardpen.c:735:14: error: invalid type argument of '->' (have 'int')
         local->history_size,
              ^
wizardpen.c:738:85: error: invalid type argument of '->' (have 'int')
         xf86Msg(X_ERROR, "%s: unable to allocate ValuatorClassDeviceStruct\n", local->name);
                                                                                     ^
wizardpen.c:767:17: error: too few arguments to function 'InitValuatorAxisStruct'
                 1000);      /* max_res */
                 ^
In file included from wizardpen.c:59:0:
/usr/include/xorg/exevents.h:58:23: note: declared here
 extern _X_EXPORT Bool InitValuatorAxisStruct(DeviceIntPtr /* dev */ ,
                       ^
wizardpen.c:777:17: error: too few arguments to function 'InitValuatorAxisStruct'
                 1000);      /* max_res */
                 ^
In file included from wizardpen.c:59:0:
/usr/include/xorg/exevents.h:58:23: note: declared here
 extern _X_EXPORT Bool InitValuatorAxisStruct(DeviceIntPtr /* dev */ ,
                       ^
wizardpen.c:787:17: error: too few arguments to function 'InitValuatorAxisStruct'
                 1000);      /* max_res */
                 ^
In file included from wizardpen.c:59:0:
/usr/include/xorg/exevents.h:58:23: note: declared here
 extern _X_EXPORT Bool InitValuatorAxisStruct(DeviceIntPtr /* dev */ ,
                       ^
wizardpen.c:799:86: error: invalid type argument of '->' (have 'int')
         xf86Msg(X_ERROR, "%s: unable to allocate ProximityClassDeviceStruct\n", local->name);
                                                                                      ^
wizardpen.c:803:5: warning: passing argument 1 of 'xf86MotionHistoryAllocate' makes pointer from integer without a cast [enabled by default]
     xf86MotionHistoryAllocate (local);
     ^
In file included from wizardpen.c:58:0:
/usr/include/xorg/xf86Xinput.h:187:23: note: expected 'InputInfoPtr' but argument is of type 'int'
 extern _X_EXPORT void xf86MotionHistoryAllocate(InputInfoPtr pInfo);
                       ^
wizardpen.c:821:48: error: invalid type argument of '->' (have 'int')
     xf86Msg(X_INFO, "%s Increment: %d\n", local->name, priv->increment);
                                                ^
wizardpen.c: At top level:
wizardpen.c:829:15: error: unknown type name 'LocalDevicePtr'
 USBReadInput (LocalDevicePtr local)
               ^
wizardpen.c:1234:12: error: unknown type name 'LocalDevicePtr'
 CloseProc (LocalDevicePtr local)
            ^
wizardpen.c:1284:19: error: unknown type name 'LocalDevicePtr'
 USBQueryHardware (LocalDevicePtr local)
                   ^
make[2]: *** [wizardpen.lo] Error 1
make[2]: Leaving directory `/home/jonda/xorg-input-wizardpen-0.8.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jonda/xorg-input-wizardpen-0.8.0'
make: *** [all] Error 2


Any ideas what I should do? Maybe try different versions of wizardpen drivers?

---

### Post by CrocoDuck on 2014-06-16
Hi, sorry for the late reply. Seems that you are just missing some package dependencies. Here it is a little tricky. You have to carefully read the error message, from the beggining to the end, end try to guess what package install to guarantee the missing files to be in your system. Basically, use google, search the error and see what happens. This ones, for example, could be useful:

```

xorg-dev xserver-xorg-dev xserver-xorg-input-synaptics xserver-xorg-input-synaptics-dev

```

Have a try installing them. Then, try to make again. I am sorry, but I don't have an Ubuntu machine ready to try to compile the software, so I cannot test the dependencies for you (maybe I should not state this on a Ubuntu forum... but I switched to ArchBang... :-\").

---

### Post by jonas-h331 on 2014-06-16
So... thanks for the tip for searching for the missing files.
Anyway, I played around a bit with different versions and 0.8.1 (latest one) seems to work just fine. I installed it rebooted computer and the tablet is still not working.
So the driver should be installed properly, I guess I'll try to play around withe the 70-wizardpen.conf, because my tablet is not on the list of tablets that work right after installing the wizardpen driver.
Thanks for all your help and I'll say how it goes.
(your little secret is safe with me :) )

Edit: No matter what I do with the 70-wizardpen.conf or 52-tablet.conf it is still not working. I really don't knwo what could I do.

---

### Post by CrocoDuck on 2014-06-18
> **jonas-h331 said:**
> Edit: No matter what I do with the 70-wizardpen.conf or 52-tablet.conf it is still not working. I really don't knwo what could I do.

:sad:... So, I think that the only choice is to try to compile from source (you will just have to install some package and make will go smooth) and see what happens. Also, you may contact the developers. [Here]("https://launchpad.net/wizardpen") you should find how.

---

