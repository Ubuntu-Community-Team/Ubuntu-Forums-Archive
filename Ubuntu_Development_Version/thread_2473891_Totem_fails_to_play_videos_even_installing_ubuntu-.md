---
title: "Totem fails to play videos even installing ubuntu-restricted extras"
date: 2022-04-17
forum: Ubuntu Development Version
---

### Post by mdintisar on 2022-04-17
Totem fails to play any video properly (tested mp4 and mkv formats). VLC and mpv is working properly. The problem is specific to Totem. I have installed ubuntu-restricted-extras but it didn't solve the problem.  When I try to play anything it shows like the following. 

[IMG]https://ibb.co/Twn039z[/IMG]
[https://ibb.co/Twn039z](https://ibb.co/Twn039z)

Also it shows the following if I run Totem in terminal and try to play video.

```
totemsys:1: Warning: g_param_values_cmp: assertion 'G_IS_VALUE (value1)' failed
Unsupported modifier, resource creation failed.
XXX: resource creation failed
Unsupported modifier, resource creation failed.
XXX: resource creation failed
Unsupported modifier, resource creation failed.
XXX: resource creation failed
Unsupported modifier, resource creation failed.
XXX: resource creation failed
Unsupported modifier, resource creation failed.
XXX: resource creation failed



```

Is there any solution?
[IMG]https://ibb.co/Twn039z[/IMG]
[IMG]https://ibb.co/Twn039z[/IMG]

---

### Post by ajgreeny on 2022-04-17
It's many years since I last used totem and gnome but I think it is possible that you may need to install the ***gstreamer-plugins-bad*** and ***gstreamer-plugins-ugly*** which in 20.04 are both *suggested* dependency packages of totem but not actual dependencies so unless you have manually added them they will not be installed.
Should you already have these installed I am afraid I can not suggest anything else; totem is now an application that I do not use.

---

### Post by mdintisar on 2022-04-17
They are already installed. The problem is not yet solved for me. I was hoping Ubuntu as it is shipping it in the ISO, Totem would be without any major bugs.

---

### Post by Claus7 on 2022-04-17
Hello,

I do not see the problem you are facing. Other than videos (a.k.a. totem) not respecting the theme, mkv files are working.

Regards!

---

### Post by DuckHook on 2022-04-17
I have experienced similar issues to those of mdintisar.

In my prior installations of Impish, Totem would run some media files but not others. I was never able to chase down where the problem was. Just like mdinstisar, VLC and MPV worked fine, but not Totem. I too had all of the restricted extras and gstreamer plugins installed in addition to a few other obscure codecs&#8212;in fact, everything I could think of.

I eventually gave up and just switched my default media app to VLC.

Oddly, installing the LXD container image versions of Totem got it working again. But firing up a container just to run Totem is overkill.

@mdintisar

[LIST=1]
[*]Which 'buntu flavour are you running?
[*]Wayland or X11? If you normally run only the one, try the other.
[*]What GPU and which driver?
[*]Have you tried uninstalling Totem, then reinstalling?
[*]Do you have any PPAs or 3rd party repos installed?
[/LIST]

---

### Post by mdintisar on 2022-04-17
```
System:  Kernel: 5.15.0-27-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: GNOME 42.0 tk: GTK 3.24.33 wm: gnome-shell dm: GDM3
    Distro: Ubuntu 22.04 (Jammy Jellyfish)
Machine:
  Type: Laptop System: Dell product: Inspiron 5459 v: N/A
    serial: <superuser required> Chassis: type: 10 serial: <superuser required>
  Mobo: Dell model: 0F1J0W v: A00 serial: <superuser required> UEFI: Dell
    v: 1.9.0 date: 09/07/2020
Battery:
  ID-1: BAT0 charge: 29.0 Wh (100.0%) condition: 29.0/32.6 Wh (89.2%)
    volts: 16.5 min: 14.8 model: SMP DELL VN3N047 serial: <filter> status: Full
CPU:
  Info: dual core model: Intel Core i7-6500U bits: 64 type: MT MCP
    arch: Skylake rev: 3 cache: L1: 128 KiB L2: 512 KiB L3: 4 MiB
  Speed (MHz): avg: 3041 high: 3077 min/max: 400/3100 cores: 1: 3077
    2: 3000 3: 3064 4: 3026 bogomips: 20799
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Skylake GT2 [HD Graphics 520] vendor: Dell driver: i915
    v: kernel ports: active: eDP-1 empty: HDMI-A-1 bus-ID: 00:02.0
    chip-ID: 8086:1916
  Device-2: AMD Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 M430 Radeon
    520 Mobile]
    vendor: Dell driver: radeon v: kernel pcie: speed: 8 GT/s lanes: 4
    bus-ID: 01:00.0 chip-ID: 1002:6660
  Device-3: Microdia Integrated Webcam HD type: USB driver: uvcvideo
    bus-ID: 1-5:4 chip-ID: 0c45:6712
  Display: wayland server: X.org v: 1.21.1.3 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: X: loaded: ati,modesetting,radeon
    unloaded: fbdev,vesa gpu: i915 display-ID: 0
  Monitor-1: eDP-1 model: Chi Mei Innolux res: 1366x768 dpi: 112
    diag: 354mm (13.9")
  OpenGL: renderer: Mesa Intel HD Graphics 520 (SKL GT2) v: 4.6 Mesa 22.0.1
    direct render: Yes
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio vendor: Dell
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3 chip-ID: 8086:9d70
  Sound Server-1: ALSA v: k5.15.0-27-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Wireless 3160 driver: iwlwifi v: kernel pcie:
    speed: 2.5 GT/s lanes: 1 bus-ID: 02:00.0 chip-ID: 8086:08b3
  IF: wlp2s0 state: up mac: <filter>
  Device-2: Realtek RTL810xE PCI Express Fast Ethernet vendor: Dell
    driver: r8169 v: kernel pcie: speed: 2.5 GT/s lanes: 1 port: d000
    bus-ID: 03:00.0 chip-ID: 10ec:8136
  IF: enp3s0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth wireless interface type: USB driver: btusb v: 0.8
    bus-ID: 1-8:6 chip-ID: 8087:07dc
  Report: hciconfig ID: hci0 rfk-id: 2 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 931.51 GiB used: 413.14 GiB (44.4%)
  ID-1: /dev/sda vendor: Seagate model: ST1000LM024 HN-M101MBB
    size: 931.51 GiB speed: 6.0 Gb/s serial: <filter>
Partition:
  ID-1: / size: 168.24 GiB used: 33.52 GiB (19.9%) fs: ext4 dev: /dev/sda8
  ID-2: /boot/efi size: 96 MiB used: 44.8 MiB (46.7%) fs: vfat
    dev: /dev/sda2
Swap:
  ID-1: swap-1 type: partition size: 8 GiB used: 75.8 MiB (0.9%) priority: -2
    dev: /dev/sda9
Sensors:
  System Temperatures: cpu: 42.0 C pch: 36.0 C mobo: 35.0 C sodimm: SODIMM C
    gpu: radeon temp: 39.0 C
  Fan Speeds (RPM): cpu: 0
Info:
  Processes: 317 Uptime: 19h 29m Memory: 7.66 GiB used: 3.11 GiB (40.7%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: 11.2.0 alt: 11
  Packages: 2534 apt: 2509 flatpak: 12 snap: 13 Shell: fish v: 3.3.1
  running-in: gnome-terminal inxi: 3.3.13



```

this is my setup

---

### Post by mdintisar on 2022-04-17
For me I found that I was using i965 vaapi driver and it caused the problem with Totem. I removed LIBVA_DRIVER_NAME=i965 from /etc/environment and now Totem works fine.

But now Kdenlive has stopped supporting VAAPI

---

### Post by mIk3_08 on 2022-04-18
> **mdintisar said:**
> Totem fails to play any video properly (tested mp4 and mkv formats). VLC and mpv is working properly. The problem is specific to Totem. I have installed ubuntu-restricted-extras but it didn't solve the problem.  When I try to play anything it shows like the following. 

[IMG]https://ibb.co/Twn039z[/IMG]
[https://ibb.co/Twn039z](https://ibb.co/Twn039z)

Also it shows the following if I run Totem in terminal and try to play video.

```
totemsys:1: Warning: g_param_values_cmp: assertion 'G_IS_VALUE (value1)' failed
Unsupported modifier, resource creation failed.
XXX: resource creation failed
Unsupported modifier, resource creation failed.
XXX: resource creation failed
Unsupported modifier, resource creation failed.
XXX: resource creation failed
Unsupported modifier, resource creation failed.
XXX: resource creation failed
Unsupported modifier, resource creation failed.
XXX: resource creation failed



```

Is there any solution?
[IMG]https://ibb.co/Twn039z[/IMG]
[IMG]https://ibb.co/Twn039z[/IMG]
I prefer to use the latest VLC than totem. It runs smoothly to my Linux Ubuntu Operating System and I haven't encountered any error/failure so far.  Regards and Cheers.

---

### Post by mdintisar on 2022-04-18
I installed nonfree vaapi drivers and both kdenlive and totem is working.

---

### Post by gleedadswell on 2022-05-09
I was having this problem as well.  Totem wasn't playing videos at all.  I tried Parole and it played audio only.  VLC worked.  As the OP says, installing 

intel-media-va-driver-non-free:i386

seems to fix the problem.

---

### Post by dieviv on 2022-12-22
VLC worked.ok. 1) control restric-ubuntu-extras.  2) verify menú preferences on VLC, output video x11, (ok for me).

---

