---
title: "Ubuntu virtualbox, black screen with mate desktop, resolution going off screen."
date: 2022-06-15
forum: Virtualisation
---

### Post by c0d3dsk1lls on 2022-06-15
I have been using linux for a while, so im pretty good with figuring things out, however this one has got me stumped.

So, first i stalled ubuntu through virtualbox, and it worked, however whenever i go to set the screen resolution, anything past 1360x768 goes right off the screen making it impossible to use properly. I messed it up so bad that i actually had to reinstall ubuntu  because the apply button was completly off screen, and i could not change resolution back, so i reinstalled ubunto and it worked fine. then i installed ubuntu-mate-desktop, , it did its thing, and it worked. but when i tried to log in i tried to set resolution again, and same issue, i messed it up so bad that i had to reinstall ubuntu, however, in my second attempt, and every attempt after that, everything works up until the point where i install mate desktop, and when i log into mate session, its nothing but a black screen, im able to login to gdm but cannot login to mate, ive messed with this for hours, trying to reinstall, changing names of install, changing video settings everything, I cannot seem to no matter what i do, install mate desktop, however the first time i installed it, it worked.. So i dont know what settings its keeping or whatever, but some help would rlly be great.

also, pretty much every linux distro i install on virtualbox, the resolutions all go off screen, except for kali linux, this works fine... it makes no sense to me.

whats really got me annoyed is, why did mate work the first time i tried it, but then no time after that?

no offence ubuntu, but i absolutly hate the gnome desktop. its garbage.
Xfce or mate is my fav.

PS i got it to work on vmware

---

### Post by ajgreeny on 2022-06-15
Do you have the correct Guest-Additions installed in your Vbox VM which will normally be needed to run a fullscreen resolution VM?

The guest additions MUST BE exactly the same version as your virtualbox version for it to work properly, and it was in my opinion  much better to use vbox direct from the Oracle repos than the version in the Ubuntu repos, though I've now moved to KVM/QEMU whic is much faster and smother than vbox. It only runs on a Linux host and I'm not sure if that is your situation.

If you want the Mate DE it would be much better to install Ubuntu-Mate direct, not just add the Mate DE to Ubuntu.

Also tell us what hardware you have with the output of ***inxi -Fzx*** or use the newer ßystem info script from [https://ubuntuforums.org/showthread.php?t=2475932](https://ubuntuforums.org/showthread.php?t=2475932)

---

### Post by c0d3dsk1lls on 2022-06-15
> **ajgreeny said:**
> Do you have the correct Guest-Additions installed in your Vbox VM which will normally be needed to run a fullscreen resolution VM?

The guest additions MUST BE exactly the same version as your virtualbox version for it to work properly, and it was in my opinion  much better to use vbox direct from the Oracle repos than the version in the Ubuntu repos, though I've now moved to KVM/QEMU whic is much faster and smother than vbox. It only runs on a Linux host and I'm not sure if that is your situation.

If you want the Mate DE it would be much better to install Ubuntu-Mate direct, not just add the Mate DE to Ubuntu.

Also tell us what hardware you have with the output of ***inxi -Fzx*** or use the newer ßystem info script from [https://ubuntuforums.org/showthread.php?t=2475932](https://ubuntuforums.org/showthread.php?t=2475932)

```
System:
  Kernel: 5.15.0-37-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: MATE 1.26.0 Distro: Ubuntu 22.04 LTS (Jammy Jellyfish)
Machine:
  Type: Vmware System: VMware product: VMware Virtual Platform v: N/A
    serial: <superuser required>
  Mobo: Intel model: 440BX Desktop Reference Platform
    serial: <superuser required> BIOS: Phoenix v: 6.00 date: 11/12/2020
CPU:
  Info: 4x 1-core model: Intel Core i9-10900X bits: 64 type: SMP
    arch: Cascade Lake rev: 7 cache: L1: 4x 64 KiB (256 KiB)
    L2: 4x 1024 KiB (4 MiB) L3: 4x 19.2 MiB (77 MiB)
  Speed (MHz): avg: 3696 min/max: N/A cores: 1: 3696 2: 3696 3: 3696
    4: 3696 bogomips: 29568
  Flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3
Graphics:
  Device-1: VMware SVGA II Adapter driver: vmwgfx v: 2.19.0.0 bus-ID: 00:0f.0
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: vmware
    unloaded: fbdev,modesetting,vesa gpu: vmwgfx resolution: 1280x1024~60Hz
  OpenGL: renderer: SVGA3D; build: RELEASE; LLVM; v: 4.1 Mesa 22.0.1
    direct render: Yes
Audio:
  Device-1: Ensoniq ES1371/ES1373 / Creative Labs CT2518 driver: snd_ens1371
    v: kernel bus-ID: 02:02.0
  Sound Server-1: ALSA v: k5.15.0-37-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel 82371AB/EB/MB PIIX4 ACPI vendor: VMware Virtual Machine
    type: network bridge driver: N/A port: N/A bus-ID: 00:07.3
  Device-2: Intel 82545EM Gigabit Ethernet
    vendor: VMware PRO/1000 MT Single Port driver: e1000 v: kernel port: 2000
    bus-ID: 02:01.0
  IF: ens33 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:
  Local Storage: total: 30 GiB used: 11.19 GiB (37.3%)
  ID-1: /dev/sda vendor: VMware model: Virtual S size: 30 GiB
Partition:
  ID-1: / size: 28.87 GiB used: 11.18 GiB (38.7%) fs: ext4 dev: /dev/sda3
  ID-2: /boot/efi size: 512 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/sda2
Swap:
  ID-1: swap-1 type: file size: 1.37 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  Message: No sensor data found. Is lm-sensors configured?
Info:
  Processes: 309 Uptime: 6m Memory: 3.8 GiB used: 1.2 GiB (31.6%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.2.0 Packages: 2281 Shell: Bash
  v: 5.1.16 inxi: 3.3.13


```

I just decided to use vmware instead, it seems to work better anyway, gives me more vram.

---

