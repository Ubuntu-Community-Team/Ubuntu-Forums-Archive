---
title: "27/8 Update"
date: 2019-08-28
forum: Ubuntu Development Version
---

### Post by P-I H on 2019-08-28
Updated on bare metal.
Went OK.
p-i@pi-MS-7A34:~$ inxi -F
```
System:    Host: pi-MS-7A34 Kernel: 5.2.0-13-generic x86_64 bits: 64 Desktop: Gnome 3.33.91 Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:   Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: <root required> 
           UEFI: American Megatrends v: 1.H0 date: 05/02/2018 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1374 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1375 2: 1372 3: 1377 4: 1380 5: 1377 6: 1376 7: 1376 
           8: 1376 9: 1377 10: 1375 11: 1375 12: 1378 13: 1376 14: 1375 15: 1378 16: 1377 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] driver: amdgpu 
           v: kernel 
           Display: x11 server: X.Org 1.20.5 driver: amdgpu tty: N/A 
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 DRM 3.32.0 5.2.0-13-generic LLVM 8.0.1) v: 4.5 Mesa 19.1.4 
Audio:     Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
           Device-2: AMD Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590] driver: snd_hda_intel 
           Device-3: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Device-4: Logitech Webcam C250 type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server: ALSA v: k5.2.0-13-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp30s0 state: up speed: 1000 Mbps duplex: 
Drives:    Local Storage: total: 903.59 GiB used: 71.24 GiB (7.9%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SA1000M8480G size: 447.13 GiB 
           ID-2: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
           ID-3: /dev/sdb vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
Partition: ID-1: / size: 437.68 GiB used: 71.23 GiB (16.3%) fs: ext4 dev: /dev/dm-3 
           ID-2: swap-1 size: 980.0 MiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-4 
Sensors:   System Temperatures: cpu: 34.0 C mobo: 34.0 C gpu: amdgpu temp: 28 C 
           Fan Speeds (RPM): fan-1: 507 fan-2: 624 fan-3: 858 fan-4: 0 fan-5: 664 fan-6: 0 gpu: amdgpu fan: 1147 
Info:      Processes: 370 Uptime: 16m Memory: 15.67 GiB used: 1.67 GiB (10.7%) Shell: bash inxi: 3.0.36 
p-i@pi-MS-7A34:~$ 

```
Lost the Suspend Button extension.
Freon isn't working as expected. Don't update "values" and isn't clickable.

---

### Post by PaulW2U on 2019-08-28
Apart from a temporary login error that I've posted about elsewhere yesterday's updates are less problematic than I first thought. All I've lost are the Suspend Button, Window List and Dash to Dock extensions. So patiently awaiting for them to be updated by the respective authors.

I've re-enabled the Ubuntu Dock and noticed that mounted drives and the Rubbish Bin (Trash Can) now appear below the application icons as per the attached screenshot. Suits me as I seem to be one of the few that don't like desktop icons. ;)

---

### Post by oldfred on 2019-08-28
Last few days I have been trying to update my ISO from daily-live and it was always the 19th. Only because you posted I then checked the zsync link & web site to see if they went back to different site by date.

My normal update using daily live, which is only the 19th of Aug.
```
zsync [http://cdimage.ubuntu.com/ubuntu/daily-live/current/eoan-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/ubuntu/daily-live/current/eoan-desktop-amd64.iso.zsync)

```
This then updated my ISO.
```
zsync http://cdimage.ubuntu.com/ubuntu/daily-live/20190828/eoan-desktop-amd64.iso.zsync
Read eoan-desktop-amd64.iso. Target 77.8% complete.      ********************
downloading from http://cdimage.ubuntu.com/ubuntu/daily-live/20190828/eoan-desktop-amd64.iso:
#################### 100.0% 12774.1 kBps DONE     

verifying download...checksum matches OK
used 1725190144 local, fetched 493454243

```

---

### Post by PaulW2U on 2019-08-28
> **oldfred said:**
> Last few days I have been trying to update my ISO from daily-live and it was always the 19th.
There was a problem with the new version of LibreOffice that was trying to pull in dependencies that were not in 'main' so the builds failed. This didn't affect the flavours just Ubuntu itself which first failed on 22nd August. Once the problem was fixed building the daily ISO was again possible.

It seems that the "current" link on cdimage.ubuntu.com is still not updating for Ubuntu though which I understand does not necessarily indicate that automatic testing of the ISO has failed.

---

### Post by MyMurry on 2019-08-30
> **PaulW2U said:**
> All I've lost are the Suspend Button, 

If you press long on the shutdown button it change to suspend:

---

### Post by PaulW2U on 2019-08-30
> **MyMurry said:**
> If you press long on the shutdown button it change to suspend:
Thanks, I think that is something I knew but had long forgotten.

Most of the extensions I have installed add “nice to have” features but just add to the problems each cycle when many of them break before they are updated for the new GNOME release. Extension now removed.

---

