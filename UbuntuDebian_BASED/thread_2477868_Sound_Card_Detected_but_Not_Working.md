---
title: "Sound Card Detected but Not Working"
date: 2022-08-09
forum: Ubuntu/Debian BASED
---

### Post by Fuzzy-Mark on 2022-08-09
I just got a new desktop computer to use for a DAW. It's a used SuperLogics SL-4U-AH370A-wb running LM 20.3 with a new Digigram VX882e sound card.

It looks like it doesn't have a driver but it's supposed to work out of  the box with ALSA. I checked the Driver Manager and it says no drivers  are needed. I've gone through several threads and removed and  re-installed ALSA base and pulseaudio but still not working. Only option  in Sound Preferences is Dummy Output.

I contacted Digigram and they said there were some files missing from the newer kernels but haven't been able to get back with me after a month.
 
What was the last kernel version before the ALSA files were removed?

Thanks.
```
ocean@SuperLogics:~$ inxi -Axxx
Audio:
  Device-1: PLX PCI9056 32-bit 66MHz PCI <-> IOBus Bridge vendor: Digigram 
  driver: N/A bus ID: 02:04.0 chip ID: 10b5:9056 
  Sound Server: ALSA v: k5.4.0-122-generic
```

```

ocean@SuperLogics:~$ aplay -l
aplay: device_list:276: no soundcards found...
```

```

ocean@SuperLogics:~$  inxi -FAxz
System:
  Kernel: 5.4.0-122-generic x86_64 bits: 64 compiler: gcc v: 9.4.0 
  Desktop: MATE 1.26.0 Distro: Linux Mint 20.3 Una base: Ubuntu 20.04 focal 
Machine:
  Type: Desktop Mobo: ASRock model: H370 Pro4 serial: <filter> 
  UEFI [Legacy]: American Megatrends v: P1.00 date: 02/09/2018 
CPU:
  Topology: 6-Core model: Intel Core i5-8600K bits: 64 type: MCP 
  arch: Kaby Lake rev: A L2 cache: 9216 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 43200 
  Speed: 4250 MHz min/max: 800/4300 MHz Core speeds (MHz): 1: 4250 2: 3896 
  3: 3585 4: 4216 5: 4235 6: 4227 
Graphics:
  Device-1: Intel UHD Graphics 630 vendor: ASRock driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.13 driver: modesetting 
  unloaded: fbdev,vesa resolution: 1360x768~60Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2) v: 4.6 Mesa 21.2.6 
  direct render: Yes 
Audio:
  Device-1: PLX PCI9056 32-bit 66MHz PCI <-> IOBus Bridge vendor: Digigram 
  driver: N/A bus ID: 02:04.0 
  Sound Server: ALSA v: k5.4.0-122-generic 
Network:
  Device-1: Intel Ethernet I219-V vendor: ASRock driver: e1000e v: 3.2.6-k 
  port: efa0 bus ID: 00:1f.6 
  IF: eno1 state: up speed: 100 Mbps duplex: full mac: <filter> 
  Device-2: Intel 82574L Gigabit Network driver: e1000e v: 3.2.6-k 
  port: 7000 bus ID: 04:00.0 
  IF: enp4s0 state: down mac: <filter> 
  Device-3: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 6000 bus ID: 07:00.0 
  IF: enp7s0 state: down mac: <filter> 
  Device-4: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 5000 bus ID: 08:00.0 
  IF: enp8s0 state: down mac: <filter> 
  Device-5: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 4000 bus ID: 09:00.0 
  IF: enp9s0 state: down mac: <filter> 
  Device-6: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: 3000 bus ID: 0a:00.0 
  IF-ID-1: enp10s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 7.73 TiB used: 14.12 GiB (0.2%) 
  ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 960 EVO 500GB 
  size: 465.76 GiB 
  ID-2: /dev/sda vendor: HGST (Hitachi) model: HUH728080ALE600 
  size: 7.28 TiB 
Partition:
  ID-1: / size: 456.88 GiB used: 14.12 GiB (3.1%) fs: ext4 
  dev: /dev/nvme0n1p5 
Sensors:
  System Temperatures: cpu: 52.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 214 Uptime: 12m Memory: 31.04 GiB used: 1.29 GiB (4.2%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.4.0 Shell: bash v: 5.0.17 
  inxi: 3.0.38 

```

---

### Post by howefield on 2022-08-09
Thread moved to the "*Ubuntu/Debian BASED*" sub forum.

---

### Post by Fuzzy-Mark on 2022-08-24
I think I figured this out thanks to help from a member on another forum and another thread.

I had to do all of the following to get it to work:
```
 sudo apt install alsa-tools 
```
```
 sudo apt install alsa-firmware-loaders 
```

I downloaded the ALSA firmware from [https://www.alsa-project.org/files/pub/firmware/alsa-firmware-1.2.4.tar.bz2](https://www.alsa-project.org/files/pub/firmware/alsa-firmware-1.2.4.tar.bz2) and extracted to my home folder, then:

```
 sudo apt install build-essential 
```
Change directory to extracted folder:
```
 cd ~/(name of extracted folder) 
``` mine was called "alsa-firmware-1.2.4"
```
 ./configure 
```
```
 make 
```
```
 sudo make install 
```
```
 sudo modprobe snd-pcxhr 
```

Then rebooted and it works.

I followed this thread for the ALSA firmware install [https://askubuntu.com/questions/493122/digigram-vx222hr-not-detected](https://askubuntu.com/questions/493122/digigram-vx222hr-not-detected)

---

