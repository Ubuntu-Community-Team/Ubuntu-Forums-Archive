---
title: "nvidia drivers and prime/bumblebee unusable in 16.04"
date: 2016-04-15
forum: Ubuntu Development Version
---

### Post by Pjem on 2016-04-15
Hi everyone,
I just installed the release candidate for 16.04, and I cannot use the nvidia drivers in any way.

I have a dell XPS with the usual Intel + nvidia card setup (a 640M).

I have tried the following, and between any tentative I issued an apt-get remove --purge nvidia* bumblebee* primus*, just in case.

- Install nvidia-prime, install either nvidia-current or one of the numbered drivers (tried 304, 340, 361), reboot. X crashes and I have to log on tty2 and remove all the thingies
- Install bumblebee, install nvidia-current (or 340, 361). Reboot goes fine. But if I try optirun glxinfo X crashes

I also tried to remove the nouveau driver completely in case the two were fighting, and repeated the two things above no effect.

Here's the end of my xorg log after the nvidia-prime disaster.

```

[   263.884] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   263.884] (==) modeset(G0): DPI set to (96, 96)
[   263.884] (II) Loading sub module "fb"
[   263.884] (II) LoadModule: "fb"
[   263.884] (II) Loading /usr/lib/xorg/modules/libfb.so
[   263.884] (II) Module fb: vendor="X.Org Foundation"
[   263.884]     compiled for 1.18.3, module version = 1.0.0
[   263.884]     ABI class: X.Org ANSI C Emulation, version 0.4
[   263.884] (II) Loading sub module "shadow"
[   263.884] (II) LoadModule: "shadow"
[   263.884] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   263.885] (II) Module shadow: vendor="X.Org Foundation"
[   263.885]     compiled for 1.18.3, module version = 1.1.0
[   263.885]     ABI class: X.Org ANSI C Emulation, version 0.4
[   263.885] (--) Depth 24 pixmap format is 32 bpp
[   263.885] (==) modeset(G0): Backing store enabled
[   263.885] (==) modeset(G0): Silken mouse enabled
[   263.885] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   263.885] (==) modeset(G0): DPMS enabled
[   263.885] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[   263.885] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[   264.170] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[   264.170] (II) NVIDIA:     access.
[   264.213] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[   264.214] (II) NVIDIA(0): Setting mode "NULL"
[   264.223] (==) NVIDIA(0): Disabling shared memory pixmaps
[   264.223] (==) NVIDIA(0): Backing store enabled
[   264.223] (==) NVIDIA(0): Silken mouse enabled
[   264.223] (==) NVIDIA(0): DPMS enabled
[   264.223] (II) Loading sub module "x11glvnd"
[   264.223] (II) LoadModule: "x11glvnd"
[   264.224] (WW) Warning, couldn't open module x11glvnd
[   264.224] (II) UnloadModule: "x11glvnd"
[   264.224] (II) Unloading x11glvnd
[   264.224] (II) x11glvnd Loading
[   264.224] (II) Loading sub module "dri2"
[   264.224] (II) LoadModule: "dri2"
[   264.224] (II) Module "dri2" already built-in
[   264.224] (II) NVIDIA(0): [DRI2] Setup complete
[   264.224] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[   264.224] (--) RandR disabled
[   264.230] (II) SELinux: Disabled on system
[   264.231] (II) Initializing extension GLX
[   264.231] (II) Indirect GLX disabled.
[   264.233] (II) modeset(G0): Damage tracking initialized
[   264.293] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   264.293] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   264.293] (II) LoadModule: "evdev"
[   264.294] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   264.294] (II) Module evdev: vendor="X.Org Foundation"
[   264.294]     compiled for 1.18.1, module version = 2.10.1
[   264.294]     Module class: X.Org XInput Driver
[   264.294]     ABI class: X.Org XInput driver, version 22.1
[   264.295] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 31 paused 0
[   264.295] (II) Using input driver 'evdev' for 'Power Button'
[   264.295] (**) Power Button: always reports core events
[   264.295] (**) evdev: Power Button: Device: "/dev/input/event2"
[   264.295] (--) evdev: Power Button: Vendor 0 Product 0x1
[   264.295] (--) evdev: Power Button: Found keys
[   264.295] (II) evdev: Power Button: Configuring as keyboard
[   264.295] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   264.295] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   264.295] (**) Option "xkb_rules" "evdev"
[   264.295] (**) Option "xkb_layout" "us,it"
[   264.295] (**) Option "xkb_variant" ","
[   264.322] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   264.322] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   264.323] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 32 paused 0
[   264.323] (II) Using input driver 'evdev' for 'Video Bus'
[   264.323] (**) Video Bus: always reports core events
[   264.323] (**) evdev: Video Bus: Device: "/dev/input/event5"
[   264.323] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   264.323] (--) evdev: Video Bus: Found keys
[   264.323] (II) evdev: Video Bus: Configuring as keyboard
[   264.323] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7/event5"
[   264.323] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   264.323] (**) Option "xkb_rules" "evdev"
[   264.323] (**) Option "xkb_layout" "us,it"
[   264.323] (**) Option "xkb_variant" ","
[   264.324] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   264.324] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   264.324] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 33 paused 0
[   264.324] (II) Using input driver 'evdev' for 'Power Button'
[   264.324] (**) Power Button: always reports core events
[   264.324] (**) evdev: Power Button: Device: "/dev/input/event0"
[   264.324] (--) evdev: Power Button: Vendor 0 Product 0x1
[   264.324] (--) evdev: Power Button: Found keys
[   264.325] (II) evdev: Power Button: Configuring as keyboard
[   264.325] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[   264.325] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[   264.325] (**) Option "xkb_rules" "evdev"
[   264.325] (**) Option "xkb_layout" "us,it"
[   264.325] (**) Option "xkb_variant" ","
[   264.325] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[   264.325] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   264.326] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 34 paused 0
[   264.326] (II) Using input driver 'evdev' for 'Video Bus'
[   264.326] (**) Video Bus: always reports core events
[   264.326] (**) evdev: Video Bus: Device: "/dev/input/event4"
[   264.326] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   264.326] (--) evdev: Video Bus: Found keys
[   264.326] (II) evdev: Video Bus: Configuring as keyboard
[   264.326] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:38/LNXVIDEO:00/input/input6/event4"
[   264.326] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 9)
[   264.326] (**) Option "xkb_rules" "evdev"
[   264.326] (**) Option "xkb_layout" "us,it"
[   264.326] (**) Option "xkb_variant" ","
[   264.327] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[   264.327] (II) No input driver specified, ignoring this device.
[   264.327] (II) This device may have been added with another device file.
[   264.327] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[   264.327] (II) No input driver specified, ignoring this device.
[   264.327] (II) This device may have been added with another device file.
[   264.328] (II) config/udev: Adding input device Laptop_Integrated_Webcam_1.3M (/dev/input/event8)
[   264.328] (**) Laptop_Integrated_Webcam_1.3M: Applying InputClass "evdev keyboard catchall"
[   264.329] (II) systemd-logind: got fd for /dev/input/event8 13:72 fd 35 paused 0
[   264.329] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_1.3M'
[   264.329] (**) Laptop_Integrated_Webcam_1.3M: always reports core events
[   264.329] (**) evdev: Laptop_Integrated_Webcam_1.3M: Device: "/dev/input/event8"
[   264.329] (--) evdev: Laptop_Integrated_Webcam_1.3M: Vendor 0xc45 Product 0x646b
[   264.329] (--) evdev: Laptop_Integrated_Webcam_1.3M: Found keys
[   264.329] (II) evdev: Laptop_Integrated_Webcam_1.3M: Configuring as keyboard
[   264.329] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input9/event8"
[   264.329] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_1.3M" (type: KEYBOARD, id 10)
[   264.329] (**) Option "xkb_rules" "evdev"
[   264.329] (**) Option "xkb_layout" "us,it"
[   264.329] (**) Option "xkb_variant" ","
[   264.329] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[   264.329] (II) No input driver specified, ignoring this device.
[   264.329] (II) This device may have been added with another device file.
[   264.330] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event10)
[   264.330] (II) No input driver specified, ignoring this device.
[   264.330] (II) This device may have been added with another device file.
[   264.330] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event11)
[   264.330] (II) No input driver specified, ignoring this device.
[   264.330] (II) This device may have been added with another device file.
[   264.330] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[   264.330] (II) No input driver specified, ignoring this device.
[   264.330] (II) This device may have been added with another device file.
[   264.331] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   264.331] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   264.331] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 36 paused 0
[   264.331] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   264.331] (**) AT Translated Set 2 keyboard: always reports core events
[   264.331] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   264.331] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   264.331] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   264.331] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   264.332] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   264.332] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[   264.332] (**) Option "xkb_rules" "evdev"
[   264.332] (**) Option "xkb_layout" "us,it"
[   264.332] (**) Option "xkb_variant" ","
[   264.332] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[   264.332] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   264.332] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchscreen catchall"
[   264.332] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   264.332] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   264.332] (II) LoadModule: "synaptics"
[   264.332] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   264.333] (II) Module synaptics: vendor="X.Org Foundation"
[   264.333]     compiled for 1.18.1, module version = 1.8.2
[   264.333]     Module class: X.Org XInput Driver
[   264.333]     ABI class: X.Org XInput driver, version 22.1
[   264.333] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 37 paused 0
[   264.333] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   264.333] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   264.333] (**) Option "Device" "/dev/input/event6"
[   264.372] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[   264.372] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1264 - 5678 (res 46)
[   264.372] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1174 - 4680 (res 51)
[   264.372] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   264.372] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   264.372] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[   264.372] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   264.372] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[   264.372] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   264.372] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   264.372] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event6"
[   264.372] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[   264.372] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   264.372] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[   264.372] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[   264.372] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   264.372] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   264.372] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   264.372] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   264.373] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   264.373] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   264.373] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   264.376] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[ 264.376] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   264.377] (II) systemd-logind: got fd for /dev/input/event7 13:71 fd 38 paused 0
[   264.377] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[   264.377] (**) Dell WMI hotkeys: always reports core events
[   264.377] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event7"
[   264.377] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[   264.377] (--) evdev: Dell WMI hotkeys: Found keys
[   264.377] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[   264.377] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event7"
[   264.377] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)
[   264.377] (**) Option "xkb_rules" "evdev"
[   264.377] (**) Option "xkb_layout" "us,it"
[   264.377] (**) Option "xkb_variant" ","
[   265.988] (--) NVIDIA(GPU-0): DFP-0: disconnected
[   265.988] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[   265.988] (--) NVIDIA(GPU-0): DFP-0: 165.0 MHz maximum pixel clock
[   265.988] (--) NVIDIA(GPU-0): 
[   265.988] (--) NVIDIA(GPU-0): DFP-1: disconnected
[   265.988] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[   265.988] (--) NVIDIA(GPU-0): DFP-1: 960.0 MHz maximum pixel clock
[   265.988] (--) NVIDIA(GPU-0): 
[   266.478] (--) NVIDIA(GPU-0): DFP-0: disconnected
[   266.478] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[   266.478] (--) NVIDIA(GPU-0): DFP-0: 165.0 MHz maximum pixel clock
[   266.478] (--) NVIDIA(GPU-0): 
[   266.478] (--) NVIDIA(GPU-0): DFP-1: disconnected
[   266.478] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[   266.478] (--) NVIDIA(GPU-0): DFP-1: 960.0 MHz maximum pixel clock
[   266.478] (--) NVIDIA(GPU-0): 
[   266.893] (II) evdev: Dell WMI hotkeys: Close
[   266.893] (II) UnloadModule: "evdev"
[   266.893] (II) systemd-logind: releasing fd for 13:71
[   266.908] (II) UnloadModule: "synaptics"
[   266.908] (II) systemd-logind: releasing fd for 13:70
[   266.924] (II) evdev: AT Translated Set 2 keyboard: Close
[   266.924] (II) UnloadModule: "evdev"
[   266.924] (II) systemd-logind: releasing fd for 13:67
[   266.968] (II) evdev: Laptop_Integrated_Webcam_1.3M: Close
[   266.968] (II) UnloadModule: "evdev"
[   266.968] (II) systemd-logind: releasing fd for 13:72
[   266.980] (II) evdev: Video Bus: Close
[   266.980] (II) UnloadModule: "evdev"
[   266.980] (II) systemd-logind: releasing fd for 13:68
[   266.992] (II) evdev: Power Button: Close
[   266.992] (II) UnloadModule: "evdev"
[   266.992] (II) systemd-logind: releasing fd for 13:64
[   267.004] (II) evdev: Video Bus: Close
[   267.004] (II) UnloadModule: "evdev"
[   267.004] (II) systemd-logind: releasing fd for 13:69
[   267.020] (II) evdev: Power Button: Close
[   267.020] (II) UnloadModule: "evdev"
[   267.020] (II) systemd-logind: releasing fd for 13:66
[   267.106] (II) NVIDIA(GPU-0): Deleting GPU-0
[   267.150] (II) Server terminated successfully (0). Closing log file.


```


Am I doing something stupid? Am I forgetting something?

Thanks for any help



     Pj

---

### Post by Pjem on 2016-04-15
Let me also add the xorg.conf driver that the installation brewed in the case, as an example, of the nvidia-361 driver:

> 
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "None"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia-361"
    Driver "nvidia-361"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection


---

### Post by mc4man on 2016-04-15
Here on a skylake with 940m using nvidia-prime has proved almost impossible. Depending on which driver 1 of 3 possibilities - 
see here - [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516/comments/8](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516/comments/8)
So maybe read thru the report & some of the attached logs to compare to see if you're seeing the same.

(- the 358 drivers do work in a roundabout manner, if not still available in the ubuntu drivers ppa I've got them in another ppa for 'safe keeping'

---

### Post by Pjem on 2016-04-15
Ok, I can report that I managed to get this solved.

So for future reference, if people have a Dell XPS with nvidia 640M in ubuntu 16.04, the driver that works is nvidia-364

Just apt-get remove & purge every nvidia* bumblebee* and issue

apt-get install nvidia-364
reboot

I am able to use prime-select to switch between nvidia and intel

   Pj

---

### Post by stuardo on 2016-05-05
> **Pjem said:**
> 
apt-get install nvidia-364


Where did you got that? The only driver I found was 3.61.42

---

### Post by cariboo on 2016-05-05
Thread closed, as it has nothing to do with Yakkety. Please start a new thread in one of the other support forums.

---

