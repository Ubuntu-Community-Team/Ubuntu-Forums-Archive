---
title: "Chromium has broken click event"
date: 2019-05-30
forum: Ubuntu Development Version
---

### Post by dino99 on 2019-05-30
Looks like these changes have broben click event:

From [https://www.accuradio.com](https://www.accuradio.com) , select a music category, then click on the thumb you want loading : nothing happen. Was working with the previous chromium versions.

 chromium-browser (74.0.3729.169-0ubuntu2) eoan; urgency=medium

  * debian/patches/revert-gn-4960.patch: added
  * debian/patches/revert-gn-4980.patch: added

 -- Olivier Tilloy <hidden@xxxxx.com>  Wed, 22 May 2019 10:12:13 +0200

Error:
chromium-browser.desktop[1683]: [1:1:0530/080533.763426:ERROR:render_media_log.cc(27)] MediaEvent: MEDIA_ERROR_LOG_ENTRY {"error":"MediaSource endOfStream before demuxer initialization completes (before HAVE_METADATA) is treated as an error. This may also occur as consequence of other MediaSource errors before HAVE_METADATA."}

---

### Post by P-I H on 2019-05-30
Working OK on my system
[COLOR=#5F6368][FONT=Roboto]Chromium Version 74.0.3729.169

[/FONT][/COLOR]```
p-i@pi-MS-7A34:~$ sudo inxi -F -m
System:    Host: pi-MS-7A34 Kernel: 5.0.0-15-generic x86_64 bits: 64 Desktop: Gnome 3.32.2 Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:   Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: H216518909 UEFI: American Megatrends 
           v: 1.H0 date: 05/02/2018 
Memory:    RAM: total: 15.67 GiB used: 4.51 GiB (28.7%) 
           Array-1: capacity: 256 GiB note: check slots: 4 EC: None 
           Device-1: DIMM 0 size: No Module Installed 
           Device-2: DIMM 1 size: 8 GiB speed: 3200 MT/s 
           Device-3: DIMM 0 size: No Module Installed 
           Device-4: DIMM 1 size: 8 GiB speed: 3200 MT/s 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1377 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1374 2: 1377 3: 1373 4: 1374 5: 1377 6: 1377 7: 1377 
           8: 1377 9: 1377 10: 1377 11: 1375 12: 1377 13: 1377 14: 1374 15: 1377 16: 1376 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] driver: amdgpu 
           v: kernel 
           Display: server: X.Org 1.20.4 driver: amdgpu tty: N/A 
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 DRM 3.27.0 5.0.0-15-generic LLVM 8.0.0) v: 4.5 Mesa 19.0.5 
Audio:     Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
           Device-2: AMD Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590] driver: snd_hda_intel 
           Device-3: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Device-4: Logitech Webcam C250 type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server: ALSA v: k5.0.0-15-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp30s0 state: up speed: 1000 Mbps duplex: full mac: 4c:cc:6a:f4:2d:5e 
Drives:    Local Storage: total: 689.34 GiB used: 190.49 GiB (27.6%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 960 EVO 250GB size: 232.89 GiB 
           ID-2: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
           ID-3: /dev/sdb vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
Partition: ID-1: / size: 218.57 GiB used: 56.29 GiB (25.8%) fs: ext4 dev: /dev/sdb2 
Sensors:   System Temperatures: cpu: 38.0 C mobo: 38.0 C gpu: amdgpu temp: 35 C 
           Fan Speeds (RPM): fan-1: 510 fan-2: 686 fan-3: 847 fan-4: 0 fan-5: 649 fan-6: 0 gpu: amdgpu fan: 1205 
Info:      Processes: 394 Uptime: 7h 14m Shell: bash inxi: 3.0.34 
p-i@pi-MS-7A34:~$ 

```

[COLOR=#5F6368][FONT=Roboto]
[/FONT][/COLOR]

---

### Post by dino99 on 2019-05-30
hm ;) does gtkorphan list some packages on your system ? (mine is often cleaned, and i does not remember which ones have been purged recently)

---

### Post by P-I H on 2019-05-30
I normally don' use that application, but installed and run.
There are a lot of packages listed.

---

### Post by dino99 on 2019-05-31
Good news, got a systemd update and with the next cold boot click event is now working as expected :p

Thanks P-IH for your feedback ):P

---

