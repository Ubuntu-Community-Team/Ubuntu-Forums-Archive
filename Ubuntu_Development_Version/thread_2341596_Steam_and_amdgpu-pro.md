---
title: "Steam and amdgpu-pro"
date: 2016-10-29
forum: Ubuntu Development Version
---

### Post by P-I H on 2016-10-29
I got some problems with Steam and amdgpu-pro.
I used amdgpu-pro during testing of Yakkety Yak. That worked OK and I want to do this also on Zesty Zapus.
Now after installation of Ubuntu 16.04.1, installation of amdgpu-pro, upgrade to Ubuntu 16.10 and changed /etc/apt/sources.list, I have a working system.

```
p-i@pi-GA-990FXA-UD3-test:~$ inxi -F
System:    Host: pi-GA-990FXA-UD3-test Kernel: 4.8.0-26-generic x86_64 (64 bit)
           Desktop: Unity 7.5.0
           Distro: Ubuntu Zesty Zapus (development branch)
Machine:   Mobo: Gigabyte model: GA-990FXA-UD3 v: x.x
           BIOS: Award v: F5 date: 10/13/2011
CPU:       Quad core AMD FX-8120 Eight-Core (-HT-MCP-) cache: 8192 KB 
           clock speeds: max: 4000 MHz 1: 2300 MHz 2: 1400 MHz 3: 2300 MHz
           4: 2300 MHz 5: 2300 MHz 6: 2300 MHz 7: 1900 MHz 8: 2300 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tonga PRO [Radeon R9 285/380]
           Display Server: X.Org 1.18.4 driver: amdgpu
           Resolution: 1920x1200@59.95hz
           GLX Renderer: AMD Radeon R9 380 Series GLX Version: 4.5.13453 - CPC
Audio:     Card-1 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-2 Advanced Micro Devices [AMD/ATI] Tonga HDMI Audio [Radeon R9 285/380]
           driver: snd_hda_intel
           Card-3 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Card-4 Logitech Webcam C250 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.8.0-26-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           IF: enp6s0 state: up speed: 1000 Mbps duplex: full
           mac: 
Drives:    HDD Total Size: 480.1GB (5.6% used)
           ID-1: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-2: /dev/sdb model: OCZ size: 120.0GB
           ID-3: /dev/sdc model: KINGSTON_SV300S3 size: 120.0GB
Partition: ID-1: / size: 103G used: 18G (19%) fs: ext4 dev: /dev/sdb1
           ID-2: swap-1 size: 8.57GB used: 0.00GB (0%) fs: swap dev: /dev/sdb5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 41.0C mobo: 35.0C gpu: 53.0
           Fan Speeds (in rpm): cpu: 931 fan-2: 813 fan-3: 0 fan-4: 1439
Info:      Processes: 316 Uptime: 1:11 Memory: 1747.8/7964.4MB
           Client: Shell (bash) inxi: 2.3.1 
p-i@pi-GA-990FXA-UD3-test:~$ systemd-analyze
Startup finished in 5.225s (kernel) + 1.299s (userspace) = 6.524s
p-i@pi-GA-990FXA-UD3-test:~$
``` 
However start of some indicators take about 1.5 minutes. This is perhaps theme related.
```
okt 29 15:32:59 pi-GA-990FXA-UD3-test unity-panel-ser[2275]: track_menus: assertion 'IS_WINDOW_MENU(menus)' failed
okt 29 15:33:07 pi-GA-990FXA-UD3-test pulseaudio[2141]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
okt 29 15:33:07 pi-GA-990FXA-UD3-test pulseaudio[1273]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
okt 29 15:34:26 pi-GA-990FXA-UD3-test gnome-session-binary[2079]: WARNING: Application 'at-spi-dbus-bus.desktop' failed to register before timeout
okt 29 15:34:26 pi-GA-990FXA-UD3-test nautilus[2439]: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
okt 29 15:34:26 pi-GA-990FXA-UD3-test nautilus[2439]: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
okt 29 15:34:26 pi-GA-990FXA-UD3-test at-spi2-registr[2312]: Failed to register client: GDBus.Error:org.gnome.SessionManager.AlreadyRegistered: Unable to register client
okt 29 15:34:26 pi-GA-990FXA-UD3-test at-spi2-registr[2312]: Unable to register client with session manager
okt 29 15:34:26 pi-GA-990FXA-UD3-test indicator-appli[2452]: Unable to get watcher name 'org.kde.StatusNotifierWatcher'
okt 29 15:34:26 pi-GA-990FXA-UD3-test indicator-appli[2452]: Name Lost
okt 29 15:34:26 pi-GA-990FXA-UD3-test polkit-gnome-au[2444]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test polkit-gnome-au[2444]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:26 pi-GA-990FXA-UD3-test polkit-gnome-au[2444]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test polkit-gnome-au[2444]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:26 pi-GA-990FXA-UD3-test polkit-gnome-au[2444]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test polkit-gnome-au[2444]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:26 pi-GA-990FXA-UD3-test unity-fallback-[2446]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test unity-fallback-[2446]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:26 pi-GA-990FXA-UD3-test polkit-gnome-au[2444]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:26 pi-GA-990FXA-UD3-test polkit-gnome-au[2444]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:26 pi-GA-990FXA-UD3-test unity-fallback-[2446]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test unity-fallback-[2446]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:26 pi-GA-990FXA-UD3-test nm-applet[2443]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test nm-applet[2443]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:26 pi-GA-990FXA-UD3-test unity-fallback-[2446]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test unity-fallback-[2446]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:26 pi-GA-990FXA-UD3-test nm-applet[2443]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test nm-applet[2443]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:26 pi-GA-990FXA-UD3-test unity-fallback-[2446]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:26 pi-GA-990FXA-UD3-test unity-fallback-[2446]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:26 pi-GA-990FXA-UD3-test nm-applet[2443]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test nm-applet[2443]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:26 pi-GA-990FXA-UD3-test indicator-multi[2450]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test indicator-multi[2450]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:26 pi-GA-990FXA-UD3-test nm-applet[2443]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:26 pi-GA-990FXA-UD3-test nm-applet[2443]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:26 pi-GA-990FXA-UD3-test indicator-multi[2450]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test indicator-multi[2450]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:26 pi-GA-990FXA-UD3-test indicator-multi[2450]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test indicator-multi[2450]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:26 pi-GA-990FXA-UD3-test indicator-multi[2450]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:26 pi-GA-990FXA-UD3-test indicator-multi[2450]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:26 pi-GA-990FXA-UD3-test gnome-software[2445]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test gnome-software[2445]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:26 pi-GA-990FXA-UD3-test gnome-software[2445]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test gnome-software[2445]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:26 pi-GA-990FXA-UD3-test gnome-software[2445]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:26 pi-GA-990FXA-UD3-test gnome-software[2445]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:26 pi-GA-990FXA-UD3-test gnome-software[2445]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:26 pi-GA-990FXA-UD3-test gnome-software[2445]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:27 pi-GA-990FXA-UD3-test fwupd[2491]: Failed to coldplug: UEFI firmware updating not supported
okt 29 15:34:28 pi-GA-990FXA-UD3-test notify-osd[2514]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:28 pi-GA-990FXA-UD3-test notify-osd[2514]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:28 pi-GA-990FXA-UD3-test notify-osd[2514]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:28 pi-GA-990FXA-UD3-test notify-osd[2514]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:28 pi-GA-990FXA-UD3-test notify-osd[2514]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:28 pi-GA-990FXA-UD3-test notify-osd[2514]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:28 pi-GA-990FXA-UD3-test notify-osd[2514]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:28 pi-GA-990FXA-UD3-test notify-osd[2514]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:28 pi-GA-990FXA-UD3-test dropbox[2476]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:28 pi-GA-990FXA-UD3-test dropbox[2476]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:28 pi-GA-990FXA-UD3-test dropbox[2476]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:28 pi-GA-990FXA-UD3-test dropbox[2476]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:28 pi-GA-990FXA-UD3-test dropbox[2476]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:28 pi-GA-990FXA-UD3-test dropbox[2476]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:28 pi-GA-990FXA-UD3-test dropbox[2476]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:28 pi-GA-990FXA-UD3-test dropbox[2476]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal.[2598]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal.[2598]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal.[2598]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal.[2598]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal.[2598]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal.[2598]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal.[2598]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal.[2598]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:37 pi-GA-990FXA-UD3-test gnome-terminal-[2601]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:46 pi-GA-990FXA-UD3-test zeitgeist-datah[2646]: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
okt 29 15:34:54 pi-GA-990FXA-UD3-test gedit[2672]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:54 pi-GA-990FXA-UD3-test gedit[2672]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:54 pi-GA-990FXA-UD3-test gedit[2672]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:54 pi-GA-990FXA-UD3-test gedit[2672]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:54 pi-GA-990FXA-UD3-test gedit[2672]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:54 pi-GA-990FXA-UD3-test gedit[2672]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:54 pi-GA-990FXA-UD3-test gedit[2672]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:54 pi-GA-990FXA-UD3-test gedit[2672]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:56 pi-GA-990FXA-UD3-test zeitgeist-datah[2626]: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: 
okt 29 15:34:56 pi-GA-990FXA-UD3-test psensor[2682]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:34:56 pi-GA-990FXA-UD3-test psensor[2682]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:34:56 pi-GA-990FXA-UD3-test psensor[2682]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:34:56 pi-GA-990FXA-UD3-test psensor[2682]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:34:56 pi-GA-990FXA-UD3-test psensor[2682]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:34:56 pi-GA-990FXA-UD3-test psensor[2682]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:34:56 pi-GA-990FXA-UD3-test psensor[2682]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:34:56 pi-GA-990FXA-UD3-test psensor[2682]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:35:26 pi-GA-990FXA-UD3-test update-notifier[2698]: Theme parsing error: gtk-widgets.css:23:18: not a number
okt 29 15:35:26 pi-GA-990FXA-UD3-test update-notifier[2698]: Theme parsing error: gtk-widgets.css:23:18: Expected a string.
okt 29 15:35:26 pi-GA-990FXA-UD3-test update-notifier[2698]: Theme parsing error: gtk-widgets.css:832:10: not a number
okt 29 15:35:26 pi-GA-990FXA-UD3-test update-notifier[2698]: Theme parsing error: gtk-widgets.css:832:24: Using Pango syntax for the font: style property is deprecated; please use CSS syntax
okt 29 15:35:26 pi-GA-990FXA-UD3-test update-notifier[2698]: Theme parsing error: gtk-widgets.css:1985:14: not a number
okt 29 15:35:26 pi-GA-990FXA-UD3-test update-notifier[2698]: Theme parsing error: gtk-widgets.css:1985:14: Expected a string.
okt 29 15:35:26 pi-GA-990FXA-UD3-test update-notifier[2698]: Theme parsing error: nautilus.css:55:71: Using one color stop with linear-gradient() is deprecated.
okt 29 15:35:26 pi-GA-990FXA-UD3-test update-notifier[2698]: Theme parsing error: nautilus.css:56:71: Using one color stop with linear-gradient() is dep

```

---

### Post by P-I H on 2016-11-23
The indicator problem is fixed now.

---

