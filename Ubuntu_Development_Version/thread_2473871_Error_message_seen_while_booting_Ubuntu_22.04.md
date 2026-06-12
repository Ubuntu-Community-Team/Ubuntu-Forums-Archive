---
title: "Error message seen while booting Ubuntu 22.04"
date: 2022-04-16
forum: Ubuntu Development Version
---

### Post by mdintisar on 2022-04-16
Previously on Ubuntu 21.10 the following error message was hidden.

```
DMAR: [Firmware Bug]: No firmware reserved region can cover this RMRR [0x0000000079800000-0x000000007bffffff], contact BIOS vendor for fixes
```

I have used Debian 11 and the same message is shown.

But Arch and Manjaro like Ubuntu 21.10 doesn't show this error message.

I want to hide this error message. Is there any way to do it in Ubuntu 22.04 LTS?

Also I see this error message while booting :   ```
Bluetooth: hci0: unexpected event for opcode 0xfc2f
``` but I find no problem with my Bluetooth. Is it a problem?


My inxi: 


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
    volts: 16.6 min: 14.8 model: SMP DELL VN3N047 serial: <filter> status: Full
CPU:
  Info: dual core model: Intel Core i7-6500U bits: 64 type: MT MCP
    arch: Skylake rev: 3 cache: L1: 128 KiB L2: 512 KiB L3: 4 MiB
  Speed (MHz): avg: 3038 high: 3078 min/max: 400/3100 cores: 1: 3006
    2: 3027 3: 3078 4: 3043 bogomips: 20799
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
    bus-ID: 1-5:3 chip-ID: 0c45:6712
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
    bus-ID: 1-8:5 chip-ID: 8087:07dc
  Report: hciconfig ID: hci0 rfk-id: 0 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 931.51 GiB used: 406.29 GiB (43.6%)
  ID-1: /dev/sda vendor: Seagate model: ST1000LM024 HN-M101MBB
    size: 931.51 GiB speed: 6.0 Gb/s serial: <filter>
Partition:
  ID-1: / size: 168.24 GiB used: 26.75 GiB (15.9%) fs: ext4 dev: /dev/sda8
  ID-2: /boot/efi size: 96 MiB used: 44.8 MiB (46.7%) fs: vfat
    dev: /dev/sda2
Swap:
  ID-1: swap-1 type: partition size: 8 GiB used: 0 KiB (0.0%) priority: -2
    dev: /dev/sda9
Sensors:
  System Temperatures: cpu: 42.0 C pch: 37.5 C mobo: 38.0 C sodimm: SODIMM C
    gpu: radeon temp: 41.0 C
  Fan Speeds (RPM): cpu: 0
Info:
  Processes: 244 Uptime: 1h 52m Memory: 7.66 GiB used: 2.18 GiB (28.4%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: 11.2.0 alt: 11
  Packages: 2522 apt: 2497 flatpak: 12 snap: 13 Shell: fish v: 3.3.1
  running-in: gnome-terminal inxi: 3.3.13



```

---

### Post by Claus7 on 2022-04-19
Hello,

just check these links if they are helpful:
askubuntu.com/questions/1331090/dmar-firmware-bug-broken-bios
askubuntu.com/questions/1179883/how-to-solve-256966901-bluetooth-hclo-unexpected-event-for-opcode-0xfc2f-mes

If they pose no problem, I would not tamper with them. 

Regards!

---

### Post by mdintisar on 2022-04-19
Thanks for the links.

My bluetooth error is no longer shown but the method described in the 1st link didn't work for me.

I don't understand why the error is shown in Ubuntu 22.04 and not shown in Ubuntu 21.10.

---

### Post by Claus7 on 2022-04-20
Hello,

> **mdintisar said:**
> ...

I don't understand why the error is shown in Ubuntu 22.04 and not shown in Ubuntu 21.10.

I face a similar problem with a new line appearing during boot (after that line just the clean line of disk size appears) of ubuntu 22.04 and just ignore it. I do not know either. I suppose that new kernels have different features that make these messages appear. If they are harmless they are just ignored.

Regards!

---

### Post by mdintisar on 2022-04-20
I guess I will have to live with that for now.

---

