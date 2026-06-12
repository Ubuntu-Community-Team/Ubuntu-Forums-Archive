---
title: "If your PC older than 15 years old what Linux distro are you using?"
date: 2022-10-27
forum: Ubuntu, Linux and OS Chat
---

### Post by f23948 on 2022-10-27
I'm using Linux Mint Xfce edition on my 10 years old PC. I'm planning to use Linux Mint cinnamon debian 32 bit edition if my PC pasts 15 year old.
Please post it here

---

### Post by ne29914 on 2022-10-27
HP/Compaq 6910p, 2007. 4 GB, 250 GB SSD.
Lubuntu 22.04 LTS. Very fast and reliable.

---

### Post by ajgreeny on 2022-10-27
There is no 32bit Mint anymore so your hope to use that will fail, I think.
You may have to move to something else, eg Debian to get a 32bit OS.

Whoops!
I've just noticed you said LMDE. Is that still available as a 32bit system?

---

### Post by f23948 on 2022-10-27
> **ajgreeny said:**
> There is no 32bit Mint anymore so your hope to use that will fail, I think.
You may have to move to something else, eg Debian to get a 32bit OS.

Whoops!
I've just noticed you said LMDE. Is that still available as a 32bit system?

32 bit based on Debian is still available
https://linuxmint.com/edition.php?id=297

---

### Post by guiverc on 2022-10-27
I use a number of devices that are >15 years, though not very often.

I have a IBM Thinkpad t43 (2005) that still runs Ubuntu 18.04 LTS  (a Lubuntu install, with Xubuntu/Xfce added), having felt no need to re-install and replace the OS yet  (*it'll move to Debian when I do*).

I have other pentium M devices I also use on occasion too (ibm r50p, t42p.., even asus eepc) used for other purposes & they all run Debian (*old-old-stable if I recall correctly; they performed better on the older kernels*). 

The PC I'm typing this on is a 2008 dell; so I guess it's approaching 15 years - but not yet.

---

### Post by poorguy on 2022-10-30
My 15 year old curb find runs Ubuntu 22.04.1 just fine.

```
ubuntu@ubuntu:~$ inxi -Fxz
System:
  Kernel: 5.15.0-52-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: GNOME 42.4 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: HP-Pavilion product: GN556AA-ABA a6200n v: N/A
    serial: <superuser required>
  Mobo: ECS model: Nettle2 v: 1.0 serial: <superuser required>
    BIOS: Phoenix v: 5.12 date: 06/11/2007
CPU:
  Info: dual core model: AMD Athlon 64 X2 5600+ bits: 64 type: MCP
    arch: K8 rev.F+ rev: 3 cache: L1: 256 KiB L2: 2 MiB
  Speed (MHz): avg: 1000 min/max: 1000/2800 cores: 1: 1000 2: 1000
    bogomips: 11251
  Flags: ht lm nx pae sse sse2 sse3 svm
Graphics:
  Device-1: NVIDIA GT218 [GeForce 8400 GS Rev. 3] vendor: ASUSTeK
    driver: nouveau v: kernel bus-ID: 02:00.0
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: nouveau resolution: 1024x768~75Hz
  OpenGL: renderer: NVA8 v: 3.3 Mesa 22.0.5 direct render: Yes
Audio:
  Device-1: NVIDIA MCP61 High Definition Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 00:05.0
  Device-2: NVIDIA High Definition Audio vendor: ASUSTeK
    driver: snd_hda_intel v: kernel bus-ID: 02:00.1
  Sound Server-1: ALSA v: k5.15.0-52-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: NVIDIA MCP61 Ethernet vendor: Hewlett-Packard
    type: network bridge driver: forcedeth v: kernel port: ec00 bus-ID: 00:07.0
  IF: enp0s7 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:
  Local Storage: total: 76.69 GiB used: 10.82 GiB (14.1%)
  ID-1: /dev/sda vendor: Hitachi model: HDS721680PLAT80 size: 76.69 GiB
Partition:
  ID-1: / size: 74.44 GiB used: 10.81 GiB (14.5%) fs: ext4 dev: /dev/sda3
  ID-2: /boot/efi size: 512 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/sda2
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 40.0 C mobo: N/A gpu: nouveau temp: 49.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 201 Uptime: 9m Memory: 7.76 GiB used: 1.3 GiB (16.7%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.3.0 Packages: 1688 Shell: Bash
  v: 5.1.16 inxi: 3.3.13
ubuntu@ubuntu:~$ 


```

---

### Post by lammert-nijhof on 2022-10-30
My backup server is almost 20 years, it consists of the left-overs from a 2003 HP d530 SFF with a defect power-supply and its parts have been moved to a Compaq EVO tower with a Win 98SE activation sticker.  It has a Pentium 4 HT (1C2T; 3.0GHz) with 1.5GB DDR (400MHz) and 1.21TB in 4 HDDs (250+320GB; IDE; 3.5" and 320+320GB; SATA-1; 2.5").  I needed a reliable 32-bits version of OpenZFS 2.1.4, so I moved to FreeBSD 13.1.  I use OpenZFS too on my Ubuntu 22.04 LTS desktop.  It is in use since June 2019 for 1 to 2 hours per week to receive the ZFS incremental backup (send | ssh receive).  All storage on both sides and the transfers are lz4 compressed.

---

### Post by maketopsite on 2022-11-11
Debian 32 bit, openSUSE Tumbleweed 32 bit.

---

### Post by poorguy on 2022-11-17
12 year old Dell Optiplex 380 runs Ubuntu 20.04.5 LTS like a top not sluggish at all.

```
[nelson@Dell-OptiPlex-380:~$ inxi -Fxz
System:    Kernel: 5.15.0-53-generic x86_64 bits: 64 compiler: N/A Desktop: Gnome 3.36.9 
           Distro: Ubuntu 20.04.5 LTS (Focal Fossa) 
Machine:   Type: Desktop System: Dell product: OptiPlex 380 v: N/A serial: <filter> 
           Mobo: Dell model: 0HN7XN v: A01 serial: <filter> BIOS: Dell v: A02 date: 08/27/2010 
CPU:       Topology: Dual Core model: Intel Core2 Duo E7500 bits: 64 type: MCP arch: Penryn rev: A 
           L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 ssse3 vmx bogomips: 11703 
           Speed: 1812 MHz min/max: 1600/2933 MHz Core speeds (MHz): 1: 1857 2: 1857 
Graphics:  Device-1: Intel 4 Series Integrated Graphics vendor: Dell driver: i915 v: kernel 
           bus ID: 00:02.0 
           Display: wayland server: X.Org 1.20.13 driver: i915 resolution: 1024x768~75Hz 
           OpenGL: renderer: Mesa DRI Intel G41 (ELK) v: 2.1 Mesa 21.2.6 direct render: Yes 
Audio:     Device-1: Intel NM10/ICH7 Family High Definition Audio vendor: Dell driver: snd_hda_intel 
           v: kernel bus ID: 00:1b.0 
           Sound Server: ALSA v: k5.15.0-53-generic 
Network:   Device-1: Broadcom and subsidiaries NetLink BCM57780 Gigabit Ethernet PCIe vendor: Dell 
           driver: tg3 v: kernel port: ece0 bus ID: 02:00.0 
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 149.05 GiB used: 13.12 GiB (8.8%) 
           ID-1: /dev/sda vendor: Fujitsu model: MHW2160BH PL size: 149.05 GiB 
Partition: ID-1: / size: 145.16 GiB used: 13.12 GiB (9.0%) fs: ext4 dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 41.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 183 Uptime: 14m Memory: 3.73 GiB used: 1.37 GiB (36.6%) Init: systemd 
           runlevel: 5 Compilers: gcc: 9.4.0 Shell: bash v: 5.0.17 inxi: 3.0.38 
nelson@Dell-OptiPlex-380:~$ 

```

---

### Post by sudodus on 2022-11-17
Have a look at this link: [Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by TheFu on 2022-11-17
15 yrs ago, I was running SuSE-something after running Mandrake.
20 yrs ago, I was running a RedHat Desktop.
25 yrs ago, I was running Slackware. Still have the CD somewhere here.  Slackware was the "easy" distro.  Have a relative that still uses slackware and I installed it about 5 yrs ago just to see what had changed.  It is a bit easier, but still asks lots of questions.

Ran Gentoo for a few months just before Redhat Desktop.  In theory, Gentoo should have been faster, but it wasn't. That convinced me that marketing lies still existed.

---

### Post by exploder on 2022-11-17
I installed Mint Cinnamon edition on an old PC a couple of days ago. I built it out of odds and ends parts but in a really sharp NZXT case. I cheated a little though, overclocked it to 4.1 GHz, overclocked the DDR 3 RAM too! It was too slow before the overclock, it's not slow now and it runs ice cold! I won the silicone lottery with this chip! I originally wanted Ubuntu 22.04 but the NVIDIA GT 1030 graphics just refused to work with it. Mint just worked, every single thing works perfectly! I have a new computer in the room, Ryzen 5600 system I built a few months ago, it runs Ubuntu. I would challenge anyone to guess which is faster by simply using each of them. The older system feels faster even though it really is not.

It is possible to keep a computer in service for 15 years. I had a core 2 duo system running Ubuntu 20.04, it's 14 years old and as far as I know still working. I donated that computer to a friend that gives computers to needy children and the elderly. Linux shines on older hardware! The FX series computer I built turned out awesome! Total parts cost $200.00 and people think it cost a fortune! I fix and sell computers on the side and that system serves as a good example for people on a tight budget. I little elbow grease and a few dollars can go a long way and save a lot of money!

Just a disclaimer, do not overclock a system unless you know what you are doing!

---

### Post by poorguy on 2022-11-17
> **sudodus said:**
> Have a look at this link: [Old hardware brought back to life]("https://ubuntuforums.org/showthread.php?t=2130640")

I have learned so much from that link.

---

### Post by agentl074 on 2022-11-21
Not 15+, but for my wife's 2011 laptop, Linux Mint 20.3 (which is Ubuntu based) works great! For new machines, the advances of regular Ubuntu are a bit nicer, however.

---

### Post by Frogs Hair on 2022-11-21
Took all the spare 10 to 12 year old parts around the basement and built a Ubuntu Budgie 22.04 box. Biostar MB, Athlon IIx4 , 8 Gb of memory, and 2Gb Nvidia card. I suspect it will be around for a while. My HP [8460P ]("https://support.hp.com/us-en/product/hp-elitebook-8460p-notebook-pc/5056942/product-info")runs Solus Plasma.

---

