---
title: "Focal Fossa toolchain uploaded"
date: 2019-10-18
forum: Ubuntu Development Version
---

### Post by harry332 on 2019-10-18
Just find out that the Focal Fossa toolchain is uploaded.
So my etc/apt/sources.list has now focal in all its links.
And they work.

---

### Post by kansasnoob on 2019-10-18
Awesome. That was FAST!

---

### Post by uRock on 2019-10-18
I think I may jump on this train with my laptop.

---

### Post by harry332 on 2019-10-18
Base-files already in the repository:

[https://launchpad.net/ubuntu/+source/base-files/11ubuntu1](https://launchpad.net/ubuntu/+source/base-files/11ubuntu1)

---

### Post by P-I H on 2019-10-19
Installed 19.10 in Boxes and used the "sudo sed -i" method to upgrade to focal.
Got the first update today.
```
p-i@pi-Standard:~$ inxi -Fz
System:
  Host: pi-Standard Kernel: 5.3.0-18-generic x86_64 bits: 64 
  Desktop: Gnome 3.34.1 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:
  Type: Kvm System: QEMU product: Standard PC (Q35 + ICH9, 2009) 
  v: pc-q35-4.1 serial: <filter> 
  Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS 
  v: rel-1.12.1-0-ga5cab58e9a3f-prebuilt.qemu.org date: 04/01/2014 
CPU:
  Topology: 16-Core (2-Die) model: AMD Ryzen 7 1700 bits: 64 type: MCP MCM 
  L2 cache: 8192 KiB 
  Speed: 3750 MHz min/max: N/A Core speeds (MHz): 1: 3750 2: 3750 3: 3750 
  4: 3750 5: 3750 6: 3750 7: 3750 8: 3750 9: 3750 10: 3750 11: 3750 12: 3750 
  13: 3750 14: 3750 15: 3750 16: 3750 
Graphics:
  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel 
  Display: x11 server: X.Org 1.20.5 driver: qxl resolution: 1811x1027~60Hz 
  OpenGL: renderer: llvmpipe (LLVM 9.0 128 bits) v: 3.3 Mesa 19.2.1 
Audio:
  Device-1: Intel 82801FB/FBM/FR/FW/FRW High Definition Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k5.3.0-18-generic 
Network:
  Device-1: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter 
  driver: 8139cp 
  IF: ens1 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 38.11 GiB used: 5.03 GiB (13.2%) 
  ID-1: /dev/sda vendor: QEMU model: HARDDISK size: 38.11 GiB 
Partition:
  ID-1: / size: 36.30 GiB used: 5.03 GiB (13.9%) fs: ext4 dev: /dev/dm-0 
  ID-2: swap-1 size: 976.0 MiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-1 
Sensors:
  Message: No sensors data was found. Is sensors configured? 
Info:
  Processes: 314 Uptime: 10m Memory: 3.82 GiB used: 1.28 GiB (33.6%) 
  Shell: bash inxi: 3.0.36 
p-i@pi-Standard:~$ 

```

---

### Post by corradoventu on 2019-10-19
Installed from ISO Ubuntu 20.04 LTS "Focal Fossa" - Alpha amd64 (20191019)

---

### Post by oldfred on 2019-10-19
I installed 19.10 from daily download on Tuesday before release on Thursday.
Renamed the daily ISO to release and did zsync:
fred@Bionic-Z170N:~/ISO$ zsync [http://releases.ubuntu.com/eoan/ubuntu-19.10-desktop-amd64.iso.zsync](http://releases.ubuntu.com/eoan/ubuntu-19.10-desktop-amd64.iso.zsync)
Read ubuntu-19.10-desktop-amd64.iso. Target 91.7% complete. 

Then renamed 19.10 ISO to daily focal ISO and zsycned so only about 1% added over release so far:

fred@Bionic-Z170N:~/ISO$ zsync [http://cdimage.ubuntu.com/daily-live/20191019/focal-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/20191019/focal-desktop-amd64.iso.zsync)
Read focal-desktop-amd64.iso. Target 98.9% complete.      
downloading from [http://cdimage.ubuntu.com/daily-live/20191019/focal-desktop-amd64.iso:](http://cdimage.ubuntu.com/daily-live/20191019/focal-desktop-amd64.iso:)
#################### 100.0% 3487.2 kBps DONE     

verifying download...checksum matches OK
used 2436005888 local, fetched 27980878

---

### Post by Frogs Hair on 2019-10-19
Upgraded sources via the sed command and received updates.

```
Distributor ID:    Ubuntu
Description:    Ubuntu Focal Fossa (development branch)
Release:    20.04
Codename:    focal

```

---

