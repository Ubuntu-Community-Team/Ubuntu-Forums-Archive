---
title: "Webcam constantly on"
date: 2021-05-13
forum: Security
---

### Post by ricardo-pedri on 2021-05-13
So, I'm thinking there might be an unauthorized script turning on my webcam.




I already put a tape on it, just in case, but I am want to check this through.


How can I see what process is behind this? I tried "ps -ef" but I couldn't find anything.
I also ran chkrootkit and clamav and nothing was found.

---

### Post by ajgreeny on 2021-05-13
Laptop or desktop?  Tell us more about the hardware with output from command ```
inxi -Fzx
```

Is this a separate webcam or built in to the screen?

laptops usually have a Function key + (F1-12) set as a toggle for the webcam; have you looked for that?

---

### Post by ricardo-pedri on 2021-05-17
> **ajgreeny said:**
> Laptop or desktop?  Tell us more about the hardware with output from command ```
inxi -Fzx
```

Is this a separate webcam or built in to the screen?

laptops usually have a Function key + (F1-12) set as a toggle for the webcam; have you looked for that?

It's a built-in cam. I am not using the laptop keyboards, but an addon keyboard instead.
These are the system details:

```
System:
  Kernel: 5.4.0-72-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Xfce 4.14.2 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: ASUSTeK product: VivoBook 15_ASUS Laptop X540UAR 
  v: 1.0 serial: <filter> 
  Mobo: ASUSTeK model: X540UAR v: 1.0 serial: <filter> 
  UEFI [Legacy]: American Megatrends v: X540UAR.305 date: 06/21/2019 
Battery:
  ID-1: BAT0 charge: 27.4 Wh condition: 30.2/33.2 Wh (91%) 
  model: ASUSTeK ASUS Battery status: Discharging 
CPU:
  Topology: Dual Core model: Intel Core i3-8130U bits: 64 type: MT MCP 
  arch: Kaby Lake rev: A L2 cache: 4096 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 17599 
  Speed: 800 MHz min/max: 400/3400 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
Graphics:
  Device-1: Intel UHD Graphics 620 vendor: ASUSTeK driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 620 (KBL GT2) v: 4.6 Mesa 20.2.6 
  direct render: Yes 
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio vendor: ASUSTeK 
  driver: snd_hda_intel v: kernel bus ID: 00:1f.3 
  Sound Server: ALSA v: k5.4.0-72-generic 
Network:
  Device-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter 
  vendor: Lite-On driver: ath9k v: kernel port: f040 bus ID: 02:00.0 
  IF: wlp2s0 state: up mac: <filter> 
Drives:
  Local Storage: total: 238.47 GiB used: 168.18 GiB (70.5%) 
  ID-1: /dev/sda vendor: SanDisk model: SD9SB8W256G1002 size: 238.47 GiB 
  temp: 31 C 
Partition:
  ID-1: / size: 177.17 GiB used: 165.90 GiB (93.6%) fs: ext4 dev: /dev/sda6 
  ID-2: swap-1 size: 4.86 GiB used: 2.28 GiB (47.0%) fs: swap dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 37.0 C mobo: N/A 
  Fan Speeds (RPM): cpu: 1900 
Info:
  Processes: 253 Uptime: 1d 6h 26m Memory: 3.73 GiB used: 2.60 GiB (69.8%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38 


```

---

