---
title: "Ubuntu 25.04 Proud Penguin?"
date: 2024-10-12
forum: Ubuntu Development Version
---

### Post by corradoventu on 2024-10-12
[https://discourse.ubuntu.com/t/pp-release-notes/48687](https://discourse.ubuntu.com/t/pp-release-notes/48687)

---

### Post by krzysztofdenir on 2024-10-12
Ubuntu 25.04 codename will be [COLOR=#333333][FONT=&quot]Perceptive Panda[/FONT][/COLOR]

---

### Post by corradoventu on 2024-10-17
[https://launchpad.net/ubuntu/plucky](https://launchpad.net/ubuntu/plucky)
[https://discourse.ubuntu.com/t/plucky-puffin-release-schedule/36461](https://discourse.ubuntu.com/t/plucky-puffin-release-schedule/36461)

---

### Post by kamennedev on 2024-10-17
Dang.

I was holding my breath for Perpendicular Pterosaur.

---

### Post by corradoventu on 2024-10-18
Repository are open:```
corrado@corrado-n5-plucky:~$ inxi -Fxc
System:
  Host: corrado-n5-plucky Kernel: 6.11.0-8-generic arch: x86_64 bits: 64
    compiler: gcc v: 14.2.0
  Desktop: GNOME v: 47.0 Distro: Ubuntu 25.04 (Plucky Puffin)
Machine:
  Type: Laptop System: Dell product: Inspiron 3793 v: N/A
    serial: <superuser required>
  Mobo: Dell model: 0C1PF2 v: A00 serial: <superuser required> UEFI: Dell
    v: 1.30.0 date: 03/07/2024
Battery:
  ID-1: BAT0 charge: 21.5 Wh (63.6%) condition: 33.8/42.0 Wh (80.4%)
    volts: 11.5 min: 11.4 model: SWD-ATL3.618 DELL WJPC403 status: discharging
CPU:
  Info: quad core model: Intel Core i5-1035G1 bits: 64 type: MT MCP
    arch: Ice Lake rev: 5 cache: L1: 320 KiB L2: 2 MiB L3: 6 MiB
  Speed (MHz): avg: 622 high: 1000 min/max: 400/1000 cores: 1: 400 2: 978
    3: 400 4: 1000 5: 1000 6: 400 7: 400 8: 400 bogomips: 19046
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Iris Plus Graphics G1 vendor: Dell driver: i915 v: kernel
    arch: Gen-11 bus-ID: 00:02.0
  Device-2: Realtek Integrated_Webcam_HD driver: uvcvideo type: USB
    bus-ID: 1-6:3
  Display: wayland server: X.Org v: 24.1.2 with: Xwayland v: 24.1.2
    compositor: gnome-shell driver: dri: iris gpu: i915
    resolution: 1920x1080~60Hz
  API: EGL v: 1.5 drivers: iris,swrast platforms:
    active: gbm,wayland,x11,surfaceless,device inactive: N/A
  API: OpenGL v: 4.6 compat-v: 4.5 vendor: intel mesa v: 24.2.3-1ubuntu1
    glx-v: 1.4 direct-render: yes renderer: Mesa Intel UHD Graphics (ICL GT1)
Audio:
  Device-1: Intel Ice Lake-LP Smart Sound Audio vendor: Dell
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3
  API: ALSA v: k6.11.0-8-generic status: kernel-api
  Server-1: PipeWire v: 1.2.4 status: active
Network:
  Device-1: Realtek RTL810xE PCI Express Fast Ethernet vendor: Dell
    driver: r8169 v: kernel port: 3000 bus-ID: 01:00.0
  IF: enp1s0 state: up speed: 100 Mbps duplex: full mac: 98:e7:43:59:19:19
  Device-2: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
    vendor: Dell driver: ath10k_pci v: kernel bus-ID: 02:00.0
  IF: wlp2s0 state: down mac: d8:12:65:b8:21:b9
Bluetooth:
  Device-1: Qualcomm Atheros driver: btusb v: 0.8 type: USB bus-ID: 1-10:4
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: D8:12:65:B8:21:BA
    bt-v: 4.2 lmp-v: 8
Drives:
  Local Storage: total: 942.7 GiB used: 12.77 GiB (1.4%)
  ID-1: /dev/nvme0n1 vendor: Toshiba model: KBG40ZNS512G NVMe KIOXIA 512GB
    size: 476.94 GiB temp: 36.9 C
  ID-2: /dev/sda vendor: Crucial model: CT500MX500SSD1 size: 465.76 GiB
Partition:
  ID-1: / size: 39.08 GiB used: 12.7 GiB (32.5%) fs: ext4 dev: /dev/nvme0n1p5
  ID-2: /boot/efi size: 246 MiB used: 65.8 MiB (26.8%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 4 GiB used: 0 KiB (0.0%) file: /swap.img
Sensors:
  System Temperatures: cpu: 53.0 C mobo: 38.0 C
  Fan Speeds (rpm): cpu: 0
Info:
  Memory: total: 16 GiB note: est. available: 14.89 GiB used: 2.54 GiB (17.1%)
  Processes: 276 Uptime: 38m Init: systemd target: graphical (5)
  Packages: 1946 Compilers: N/A Shell: Bash v: 5.2.32 inxi: 3.3.35
corrado@corrado-n5-plucky:~$ 

```

---

### Post by 1fallen on 2024-10-18
From here [https://discourse.ubuntu.com/t/plucky-puffin-release-notes/48687](https://discourse.ubuntu.com/t/plucky-puffin-release-notes/48687), and this is just a heads up for ZFS users:

General

[list]
    
[*]The Live Session of the new Ubuntu Desktop installer is not localized. It is still possible to perform a non-English installation using the new installer, but internet access at install time is required to download the language packs. (LP: #2013329)
    
[*]ZFS with Encryption on Ubuntu 24.10 will fail to activate the cryptoswap partition. This affects both new installs and upgrades. We expect to address this post-release with an archive update.
    
[*]Some particular hardware (e.g. Thinkpad x201) might have issues (general freeze, desktop-security-center not launching), when booted without nomodeset (Safe graphics). Follow these steps if you encounter such an issue:
[/list]

---

### Post by chrismine on 2024-10-21
Please post the upgrade command - the one's I tried working previously don't. Thank you kindly.

---

### Post by corradoventu on 2024-10-22
```
sudo gted /etc/apt/sources.list.d/ubuntu.sources
``` and change "oracular" to "plucky"
```
sudo gted /etc/lsb-release
sudo gted /etc/os-release
```
and change accordingly
```
sudo apt uodate && sudo apt upgrade
```
```
reboot
```

---

### Post by chrismine on 2024-10-22
Thank you kindly.

---

