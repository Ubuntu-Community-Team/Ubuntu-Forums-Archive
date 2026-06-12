---
title: "Ubuntu 20.10 is the Groovy Gorilla"
date: 2020-04-24
forum: Ubuntu Development Version
---

### Post by dino99 on 2020-04-24
Next U+1 version is named :P

[https://www.omgubuntu.co.uk/2020/04/ubuntu-20-10-codename-groovy-gorilla](https://www.omgubuntu.co.uk/2020/04/ubuntu-20-10-codename-groovy-gorilla)
[https://discourse.ubuntu.com/t/groovy-gorilla-release-schedule/15531](https://discourse.ubuntu.com/t/groovy-gorilla-release-schedule/15531)

---

### Post by slickymaster on 2020-04-24
*Thread moved to **Ubuntu Development Version**.*

---

### Post by fooman on 2020-04-25
Far out name man, I dig it! :cool:

---

### Post by IanW on 2020-04-27
Richard Stallman was hoping for "Groovy GNU" ;)

---

### Post by kostkon on 2020-04-27
A great ape at last!

---

### Post by corradoventu on 2020-04-29
Repositories are open:
```
corrado@corrado-p3-ff-0324:~$ inxi -SCGx
System:
  Host: corrado-p3-ff-0324 Kernel: 5.4.0-28-generic x86_64 bits: 64 
  compiler: gcc v: 9.3.0 Desktop: Gnome 3.36.1 
  Distro: Ubuntu 20.10 (Groovy Gorilla) 
CPU:
  Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP 
  arch: Kaby Lake rev: 9 L2 cache: 3072 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 31199 
  Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
Graphics:
  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa Intel HD Graphics 630 (KBL GT2) v: 4.6 Mesa 20.0.4 
  direct render: Yes 
corrado@corrado-p3-ff-0324:~$ 
```

---

### Post by P-I H on 2020-04-30
Changed /etc/apt/sources.list and upgraded.
```
p-i@pi-MS-7A34:~$ inxi -SCGx
System:    Host: pi-MS-7A34 Kernel: 5.4.0-28-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
           Desktop: Gnome 3.36.1 Distro: Ubuntu 20.10 (Groovy Gorilla) 
CPU:       Topology: Quad Core model: AMD Ryzen 3 1200 bits: 64 type: MCP arch: Zen rev: 1 
           L2 cache: 2048 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm bogomips: 28798 
           Speed: 1380 MHz min/max: 1550/3600 MHz Core speeds (MHz): 1: 1376 2: 1377 3: 1377 4: 1378 
Graphics:  Device-1: AMD Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] vendor: Micro-Star MSI 
           driver: amdgpu v: kernel bus ID: 21:00.0 
           Display: wayland server: X.Org 1.20.8 driver: amdgpu resolution: 2560x1440~60Hz 
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 DRM 3.35.0 5.4.0-28-generic LLVM 9.0.1) 
           v: 4.6 Mesa 20.0.4 direct render: Yes 
p-i@pi-MS-7A34:~$ 

```

---

### Post by corradoventu on 2020-05-03
Installed from 1st available ISO Ubuntu 20.10 "Groovy Gorilla" - Alpha amd64 (20200430)
```
corrado@corrado-p3-gorilla:~$ inxi -SCGx
System:    Host: corrado-p3-gorilla Kernel: 5.4.0-26-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
           Desktop: Gnome 3.36.1 Distro: Ubuntu 20.10 (Groovy Gorilla) 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake rev: 9 
           L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31199 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
Graphics:  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel bus ID: 00:02.0 
           Device-2: ARC USB 2.0 Camera type: USB driver: uvcvideo bus ID: 1-2:2 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa Intel HD Graphics 630 (KBL GT2) v: 4.6 Mesa 20.0.4 direct render: Yes 
corrado@corrado-p3-gorilla:~$ 
```
Wallpaper: [https://d24qi7hsckwe9l.cloudfront.net/img/original/_dennis_stogsdill.jpg](https://d24qi7hsckwe9l.cloudfront.net/img/original/_dennis_stogsdill.jpg)

---

### Post by P-I H on 2020-10-02
Installed the beta release. Worked fine.
```
p-i@pi-MS-7A34:~$ inxi -Fz
System:    Kernel: 5.8.0-20-generic x86_64 bits: 64 Desktop: N/A Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:   Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: <filter> 
           UEFI: American Megatrends v: 1.H0 date: 05/02/2018 
CPU:       Info: Quad Core model: AMD Ryzen 3 1200 bits: 64 type: MCP L2 cache: 2048 KiB 
           Speed: 1378 MHz min/max: 1550/3600 MHz Core speeds (MHz): 1: 1378 2: 1377 3: 1377 4: 1378 
Graphics:  Device-1: NVIDIA GK106 [GeForce GTX 660] driver: nvidia v: 450.66 
           Display: x11 server: X.Org 1.20.8 driver: nvidia unloaded: fbdev,modesetting,nouveau,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: GeForce GTX 660/PCIe/SSE2 v: 4.6.0 NVIDIA 450.66 
Audio:     Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
           Device-2: NVIDIA GK106 HDMI Audio driver: snd_hda_intel 
           Device-3: AMD Family 17h HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.8.0-20-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp30s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 454.60 GiB used: 39.72 GiB (8.7%) 
           ID-1: /dev/sda vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
           ID-2: /dev/sdb vendor: Samsung model: SSD 830 Series size: 119.24 GiB 
           ID-3: /dev/sdc vendor: Kingston model: SV300S37A120G size: 111.79 GiB 
Partition: ID-1: / size: 109.04 GiB used: 39.67 GiB (36.4%) fs: ext4 dev: /dev/sdc2 
Swap:      ID-1: swap-1 type: file size: 2.00 GiB used: 22.7 MiB (1.1%) file: /swapfile 
Sensors:   System Temperatures: cpu: 28.0 C mobo: 30.0 C gpu: nvidia temp: 32 C 
           Fan Speeds (RPM): fan-1: 0 fan-2: 802 fan-3: 788 fan-4: 0 fan-5: 666 fan-6: 756 gpu: nvidia 
           fan: 30% 
Info:      Processes: 341 Uptime: 4h 53m Memory: 15.65 GiB used: 2.76 GiB (17.6%) Shell: Bash 
           inxi: 3.1.06 
p-i@pi-MS-7A34:~$ 

```

---

### Post by zebra2 on 2020-10-02
I've been running the dev version since Karmic and the thing that impresses me is the temperatures. I used to buy cooling pads to keep my legs from getting cooked from putting my laptop on my lap. My lenovo laptops running 20.10 stays at a cool 32C.  Power usage is 6W on power 4W on battery and half power. Of course a lot of this has to do with modern solid state integrated architecture but Gorilla is smooth as silk on all three of my laptops. They all run 24/7 and are barely a bleep on the electric bill. Thats what impresses me from a technical standpoint. So far as usability goes I'm using Gorilla Wayland and it is absolutely the finest most beautiful and smooth system I have used, period. Can't wait until the next evolution starts. What I have now will be hard to beat.

---

