---
title: "Can't find wayland on Ubuntu 22.04"
date: 2022-04-16
forum: Ubuntu Development Version
---

### Post by mdintisar on 2022-04-16
I have installed Ubuntu 22.04 and upgraded it to the latest. 

I am logged into the x11 instead of Wayland. Do I need to install anything?? 

```
System:  Kernel: 5.15.0-25-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: GNOME 42.0 tk: GTK 3.24.33 wm: gnome-shell dm: GDM3
    Distro: Ubuntu 22.04 (Jammy Jellyfish)
Machine:
  Type: Laptop System: Dell product: Inspiron 5459 v: N/A
    serial: <superuser required> Chassis: type: 10 serial: <superuser required>
  Mobo: Dell model: 0F1J0W v: A00 serial: <superuser required> UEFI: Dell
    v: 1.9.0 date: 09/07/2020
Battery:
  ID-1: BAT0 charge: 29.0 Wh (100.0%) condition: 29.0/32.6 Wh (89.2%)
    volts: 16.6 min: 14.8 model: SMP DELL VN3N047 serial: <filter> status: Full
CPU:
  Info: dual core model: Intel Core i7-6500U bits: 64 type: MT MCP
    arch: Skylake rev: 3 cache: L1: 128 KiB L2: 512 KiB L3: 4 MiB
  Speed (MHz): avg: 2956 high: 3039 min/max: 400/3100 cores: 1: 3028
    2: 3039 3: 2759 4: 2998 bogomips: 20799
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Skylake GT2 [HD Graphics 520] vendor: Dell driver: i915
    v: kernel ports: active: eDP-1 empty: HDMI-A-1 bus-ID: 00:02.0
    chip-ID: 8086:1916
  Device-2: AMD Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330 M430 Radeon
    520 Mobile]
    vendor: Dell driver: radeon v: kernel pcie: speed: 2.5 GT/s lanes: 4
    bus-ID: 01:00.0 chip-ID: 1002:6660
  Device-3: Microdia Integrated Webcam HD type: USB driver: uvcvideo
    bus-ID: 1-5:4 chip-ID: 0c45:6712
  Display: x11 server: X.Org v: 1.21.1.3 compositor: gnome-shell driver: X:
    loaded: ati,modesetting,radeon unloaded: fbdev,vesa gpu: i915
    display-ID: :1 screens: 1
  Screen-1: 0 s-res: 1366x768 s-dpi: 96
  Monitor-1: eDP-1 model: Chi Mei Innolux res: 1366x768 dpi: 112
    diag: 354mm (13.9")
  OpenGL: renderer: Mesa Intel HD Graphics 520 (SKL GT2) v: 4.6 Mesa 22.0.1
    direct render: Yes
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio vendor: Dell
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3 chip-ID: 8086:9d70
  Sound Server-1: ALSA v: k5.15.0-25-generic running: yes
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
  Report: hciconfig ID: hci0 rfk-id: 0 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 931.51 GiB used: 192.2 GiB (20.6%)
  ID-1: /dev/sda vendor: Seagate model: ST1000LM024 HN-M101MBB
    size: 931.51 GiB speed: 6.0 Gb/s serial: <filter>
Partition:
  ID-1: / size: 168.24 GiB used: 14.77 GiB (8.8%) fs: ext4 dev: /dev/sda8
  ID-2: /boot/efi size: 96 MiB used: 44.8 MiB (46.7%) fs: vfat
    dev: /dev/sda2
Swap:
  ID-1: swap-1 type: partition size: 8 GiB used: 1000 KiB (0.0%) priority: -2
    dev: /dev/sda9
Sensors:
  System Temperatures: cpu: 55.0 C pch: 48.5 C mobo: 47.0 C sodimm: SODIMM C
    gpu: radeon temp: 53.0 C
  Fan Speeds (RPM): cpu: 0
Info:
  Processes: 251 Uptime: 1h 36m Memory: 7.66 GiB used: 2.19 GiB (28.6%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: N/A Packages: 2270
  apt: 2249 flatpak: 8 snap: 13 Shell: Bash v: 5.1.16
  running-in: gnome-terminal inxi: 3.3.13



```

This is my inxi output.

---

### Post by deadflowr on 2022-04-16
Is there no option for it when you login?

When you login, after you select the user to login (when the password field shows), there should be an icon in the bottom right corner area of the screen.

---

### Post by mdintisar on 2022-04-16
There is supposed to be a option. But there is no option. 

If I use > XDG_SESSION_TYPE=wayland dbus-run-session gnome-session

I am looged into wayland. Otherwise not able to log in and I see no option in the gdm. 

I have also enabled wayland in gdm config. But still not solved.

---

### Post by grahammechanical on 2022-04-16
For clarification.

Ubuntu 20.04 defaults to X-server with Wayland as a login option (Ubuntu on Wayland). Ubuntu 22.04 defaults to Wayland with X-Server as a login option (Ubuntu on X-Server).

Regards

---

### Post by mdintisar on 2022-04-16
I am aware that Ubuntu 22.04 defaults to wayland. But I am not being able to log in to wayland. I see no option to change between wayland or xorg in the gdm menu.

---

### Post by grahammechanical on 2022-04-16
I have just logged in to 22.04 and the option to login on X-Server is gone. There is no option to login to Wayland. System Settings>About says: Windowing System - X11. I am about to update/upgrade this installation to see if the situation changes.

Regards

Edit: Today's update did not correct this. On 22.04 /etc/gdm3/custom.conf still has this entry

> # Uncomment the line below to force the login screen to use Xorg
#WaylandEnable=false

So, I have no idea as to why or how 220.04 is default to xorg.

---

### Post by deadflowr on 2022-04-16
Found this: [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969243]("https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969243")

---

### Post by mdintisar on 2022-04-16
> **grahammechanical said:**
> I have just logged in to 22.04 and the option to login on X-Server is gone. There is no option to login to Wayland. System Settings>About says: Windowing System - X11. I am about to update/upgrade this installation to see if the situation changes.

Regards

Edit: Today's update did not correct this. On 22.04 /etc/gdm3/custom.conf still has this entry



So, I have no idea as to why or how 220.04 is default to xorg.

This is exactly the problem I am having.

---

### Post by mdintisar on 2022-04-16
:KS
> As a workaround, you can edit /lib/udev/rules.d/61-gdm.rules and comment out or remove these lines:#
```
# Check if suspend/resume services necessary for working wayland support is available
TEST{0711}!="/usr/bin/nvidia-sleep.sh", GOTO="gdm_disable_wayland"
TEST{0711}!="/usr/lib/systemd/system-sleep/nvidia", GOTO="gdm_disable_wayland"
IMPORT{program}="/bin/sh -c \"sed -e 's/: /=/g' -e 's/\([^[:upper:]]\)\([[:upper:]]\)/\1_\2/g' -e 's/[[:lower:]]/\U&/g' -e 's/^/NVIDIA_/' /proc/driver/nvidia/params\""
ENV{NVIDIA_PRESERVE_VIDEO_MEMORY_ALLOCATIONS}!="1", GOTO="gdm_disable_wayland"
IMPORT{program}="/bin/sh -c 'echo NVIDIA_HIBERNATE=`systemctl is-enabled nvidia-hibernate`'"
ENV{NVIDIA_HIBERNATE}!="enabled", GOTO="gdm_disable_wayland"
IMPORT{program}="/bin/sh -c 'echo NVIDIA_RESUME=`systemctl is-enabled nvidia-resume`'"
ENV{NVIDIA_RESUME}!="enabled", GOTO="gdm_disable_wayland"
IMPORT{program}="/bin/sh -c 'echo NVIDIA_SUSPEND=`systemctl is-enabled nvidia-suspend`'"

ENV{NVIDIA_SUSPEND}!="enabled", GOTO="gdm_disable_wayland"
```

This solved my gdm session login defaults. 

I am able to login to wayland after the edit and a reboot.

---

### Post by DuckHook on 2022-04-16
> **deadflowr said:**
> Found this: [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969243]("https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969243")
Thanks deadflowr. This solved my problem. I've subscribed to the bug and can hopefully update this thread when the bug gets squashed.

---

### Post by grahammechanical on 2022-04-16
The bug report claims that this bug is Nvidia specific but there is one report that it exists on Intel graphic card. I can confirm this as I have Intel UHD Graphics (CML, GT2)

Regards

---

### Post by DuckHook on 2022-04-16
It's stated further down that the bug is not just nVidia but rather an unintended result of trying to handle nVidia problems. However, it effects everyone. My system is AMD graphics, so it's universal.

It's weird that bugs of this magnitude are still cropping up so close to the end of beta stage, but I guess that's why Jammy status is still "development".

---

### Post by #&amp;thj^% on 2022-04-16
> **DuckHook said:**
> It's stated further down that the bug is not just nVidia but rather an unintended result of trying to handle nVidia problems. However, it effects everyone. My system is AMD graphics, so it's universal.

It's weird that bugs of this magnitude are still cropping up so close to the end of beta stage, but I guess that's why Jammy status is still "development".
Yep, that's where the blood comes from in bleeding edge. :)

---

### Post by exploder on 2022-04-17
Wayland has not worked with my supported RX 560 for about two days now...

Edit: Gave the workaround a try and wayland is back to working!

---

### Post by grahammechanical on 2022-04-17
As a work around the work around works, apparently. But a work around should not be necessary in an LTS version. The developers have until 21st April. I wonder if they will squash this bug temporarily by building the work around into 22.04. In theory 22.04 development version without the work around should not get a Wayland option or by default unless the bug is well and truly fixed and an update/upgrade applies it. So, I will see.

Regards

---

### Post by exploder on 2022-04-17
@ grahammechanical

i agree with you 100%! Wayland by default is a feature in this LTS release. It is unusual for a bug like this to pop up this close to the final release. On the good side, at least X11 was there to fall back to, affected systems did still run. Also, the cause of the issue has been found. The patch that was released should have been tested better.

---

### Post by DuckHook on 2022-04-17
The devs are doing the best they can. If you subscribe to [the bug report]("https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969243"), the dev it has been assigned to has this to say:
> Yes, this bug disabled Wayland for everyone. So we don't need more reports confirming that it affects your Intel or AMD system. The bugfix is waiting for someone from the Ubuntu Release Team to accept it but it's a holiday weekend so it may take until tomorrow.
It will be fixed before April 21st.

It is also worth noting that there is nothing magical about an LTS release. If previous experience is anything to go by, Jammy will be full of bugs until its first point release (in Oct or thereabouts). An LTS is not initially more stable. It just has a longer shelf life so that it *eventually* gets more stable. But no LTS has ever started out that way and I don't think Jammy will either. Let's set our expectations accordingly and we won't be disappointed.

---

### Post by DuckHook on 2022-04-18
gdm3 has been patched, so Wayland should be available again to those of us who don't use nVidia graphics.

[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969243/comments/31](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969243/comments/31)

I'm afraid it's a mixed blessing: while Intel and AMD graphics can use Wayland again, nVidia users will still have to wait&#8212;hopefully not for too long.

---

### Post by DuckHook on 2022-04-18
Those with nVidia graphics still waiting for a fix may wish to follow the following bug report: [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1968929](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1968929)

---

