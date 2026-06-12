---
title: "Pop!_os not sleeping, running hot, random resets"
date: 2023-08-24
forum: Ubuntu/Debian BASED
---

### Post by ross02012 on 2023-08-24
I have an older XPS 15 (9550) that dual boots pop os and Windows 10. Pop os has been running great since installed about a year ago, until recently.

Now the fan runs constantly, it won't sleep through timeout or closing the lid like it used to, and it resets randomly sometimes. All this happened after installing gnome boxes where I have a Windows 11 VM. To be clear, this is still happening with the VM shut down and boxes closed, but I didn't know if it would change a setting somewhere.

I've included the output of inxi -Fxxz

inxi -Fxxz
System:
  Kernel: 6.4.6-76060406-generic x86_64 bits: 64 compiler: N/A
    Desktop: GNOME 42.5 tk: GTK 3.24.33 wm: gnome-shell dm: GDM3
    Distro: Pop!_OS 22.04 LTS base: Ubuntu 22.04 LTS Jammy
Machine:
  Type: Laptop System: Dell product: XPS 15 7590 v: N/A
    serial: <superuser required> Chassis: type: 10 serial: <superuser required>
  Mobo: Dell model: 0VYV0G v: A00 serial: <superuser required> UEFI: Dell
    v: 1.23.0 date: 07/18/2023
Battery:
  ID-1: BAT0 charge: 38.6 Wh (46.5%) condition: 83.0/97.0 Wh (85.6%)
    volts: 11.1 min: 11.4 model: LGC-LGC3.67 DELL T453X serial: <filter>
    status: Discharging
CPU:
  Info: 6-core model: Intel Core i7-9750H bits: 64 type: MT MCP
    arch: Coffee Lake rev: A cache: L1: 384 KiB L2: 1.5 MiB L3: 12 MiB
  Speed (MHz): avg: 2600 min/max: 800/2600 cores: 1: 2600 2: 2600 3: 2600
    4: 2600 5: 2600 6: 2600 7: 2600 8: 2600 9: 2600 10: 2600 11: 2600 12: 2600
    bogomips: 62399
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel CoffeeLake-H GT2 [UHD Graphics 630] vendor: Dell
    driver: i915 v: kernel ports: active: eDP-1 empty: DP-1,DP-2,DP-3
    bus-ID: 00:02.0 chip-ID: 8086:3e9b
  Device-2: NVIDIA TU117M [GeForce GTX 1650 Mobile / Max-Q] vendor: Dell
    driver: N/A pcie: speed: 8 GT/s lanes: 16 bus-ID: 01:00.0
    chip-ID: 10de:1f91
  Device-3: Microdia Integrated_Webcam_HD type: USB driver: uvcvideo
    bus-ID: 1-12:4 chip-ID: 0c45:6723
  Display: x11 server: X.Org v: 1.21.1.4 compositor: gnome-shell driver: X:
    loaded: modesetting unloaded: fbdev,vesa gpu: i915 display-ID: :1
    screens: 1
  Screen-1: 0 s-res: 3840x2160 s-dpi: 96
  Monitor-1: eDP-1 model: Sharp res: 3840x2160 dpi: 284 diag: 395mm (15.5")
  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2)
    v: 4.6 Mesa 23.1.3-1pop0~1689084530~22.04~0618746 direct render: Yes
Audio:
  Device-1: Intel Cannon Lake PCH cAVS vendor: Dell driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3 chip-ID: 8086:a348
  Sound Server-1: ALSA v: k6.4.6-76060406-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: no
  Sound Server-3: PipeWire v: 0.3.74 running: yes
Network:
  Device-1: Intel Wi-Fi 6 AX200 vendor: Rivet Networks Killer™
    driver: iwlwifi v: kernel pcie: speed: 5 GT/s lanes: 1 bus-ID: 3b:00.0
    chip-ID: 8086:2723
  IF: wlp59s0 state: up mac: <filter>
Bluetooth:
  Device-1: Intel AX200 Bluetooth type: USB driver: btusb v: 0.8
    bus-ID: 1-4:2 chip-ID: 8087:0029
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.2 sub-v: 20ce
Drives:
  Local Storage: total: 953.87 GiB used: 277.79 GiB (29.1%)
  ID-1: /dev/nvme0n1 vendor: Toshiba model: KXG60ZNV1T02 NVMe 1024GB
    size: 953.87 GiB speed: 31.6 Gb/s lanes: 4 serial: <filter> temp: 40.9 C
Partition:
  ID-1: / size: 474.24 GiB used: 277.52 GiB (58.5%) fs: ext4
    dev: /dev/nvme0n1p9
  ID-2: /boot/efi size: 1021 MiB used: 282.4 MiB (27.7%) fs: vfat
    dev: /dev/nvme0n1p4
Swap:
  ID-1: swap-1 type: zram size: 16 GiB used: 0 KiB (0.0%) priority: 1000
    dev: /dev/zram0
Sensors:
  System Temperatures: cpu: 58.0 C pch: 51.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 359 Uptime: 2m Memory: 30.98 GiB used: 5.38 GiB (17.4%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: 11.4.0 alt: 11/12
  Packages: 2306 note: see --pkg apt: 2280 flatpak: 26 Shell: Bash v: 5.1.16
  running-in: gnome-terminal inxi: 3.3.13

---

