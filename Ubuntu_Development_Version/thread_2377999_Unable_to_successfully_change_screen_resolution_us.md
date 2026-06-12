---
title: "Unable to successfully change screen resolution using ATI HD 6850 on a Dell u3011"
date: 2017-11-18
forum: Ubuntu Development Version
---

### Post by darran-kelinske on 2017-11-18
I am running the nightlies and am unable to change my screen resolution. It appears the screen gets updated, but only half the screen displays appropriate content. The other half displays squigglies and the terminal.

I am running an ATI HD 6850 on a Dell u3011. All of my packages are the latest from the repos.

Thank you!

Darran

---

### Post by darran-kelinske on 2017-12-13
This is what the screen looks like when I try to change the resolution:

[https://photos.app.goo.gl/zK9uez2nKMRPFKYr2](https://photos.app.goo.gl/zK9uez2nKMRPFKYr2)

[IMG]https://photos.app.goo.gl/zK9uez2nKMRPFKYr2[/IMG]

---

### Post by ventrical on 2017-12-15
> **darran-kelinske said:**
> This is what the screen looks like when I try to change the resolution:

[https://photos.app.goo.gl/zK9uez2nKMRPFKYr2](https://photos.app.goo.gl/zK9uez2nKMRPFKYr2)

[IMG]https://photos.app.goo.gl/zK9uez2nKMRPFKYr2[/IMG]


Have you tried an install with the nomodeset option? There have been problems with ATi graphics adapters and the drivers. Gnome3 (ubuntu-desktop default) has been a little more ATi friendly as of late.

Regards..

---

### Post by darran-kelinske on 2017-12-15
I set radeon.nomodeset=0 in grub and was able to change the resolution to 2560 x 1600, but now the screen always looks like the picture in that screenshot. It is like the terminal and the desktop are trying to be displayed at the same time with the terminal being displayed on top of the desktop.

---

### Post by ventrical on 2017-12-15
Could I please see you results of:

inxi -Fxz

> **darran-kelinske said:**
> I set radeon.nomodeset=0 in grub 

 I usually set nomodeset at beginning a fresh install so it doesn't lock weird graphical drivers in.

---

### Post by darran-kelinske on 2017-12-15
I went into terminal and did the following and now the desktop is displaying properly:

```
sudo apt-get purge ubuntu-desktop

sudo apt-get purge xorg

sudo apt-get install ubuntu-desktop
```

then updated and upgraded all packages and now my desktop is correctly displaying at 2560 x 1600 - i did lose the ubuntu dock on the left side though

One thing to note. The right side of the screen does not expand half-way to the left when a window edge is pushed next to it. The left side of the screen does function correctly. Automatically expanding the window halfway across the screen.

> **ventrical said:**
> Could I please see you results of:

inxi -Fxz


```
System:    Host: iloveyou Kernel: 4.14.0-11-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.2 (Gtk 3.22.26-2ubuntu1)
           Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: desktop Mobo: BIOSTAR model: A770E3 serial: N/A
           BIOS: American Megatrends v: 080014 date: 04/21/2010
CPU:       Hexa core AMD Phenom II X6 1090T (-MCP-) 
           arch: K10 rev.0 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 38402
           clock speeds: max: 3200 MHz 1: 2400 MHz 2: 2400 MHz 3: 2400 MHz
           4: 1600 MHz 5: 3200 MHz 6: 1600 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Barts XT [Radeon HD 6870]
           bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.5 )
           driver: FAILED: modesetting
           Resolution: 2560x1600@59.94hz, 1920x1200@59.88hz
           OpenGL: renderer: AMD BARTS (DRM 2.50.0 / 4.14.0-11-generic, LLVM 5.0.0)
           version: 3.3 Mesa 17.2.4 Direct Render: Yes
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Barts HDMI Audio [Radeon HD 6790/6850/6870 / 7720 OEM]
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Creative Labs EMU10k1 [Sound Blaster Live! Series]
           driver: snd_emu10k1 port: e800 bus-ID: 04:07.0
           Sound: Advanced Linux Sound Architecture v: k4.14.0-11-generic
Network:   Card-1: Qualcomm Atheros AR93xx Wireless Network Adapter
           driver: ath9k bus-ID: 02:00.0
           IF: wlp2s0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d800 bus-ID: 03:00.0
           IF: eth0 state: down mac: <filter>
Drives:    HDD Total Size: 1314.3GB (61.7% used)
           ID-1: /dev/sda model: SAMSUNG_HD103SJ size: 1000.2GB temp: 24C
           ID-2: /dev/sdb model: Corsair_CSSD size: 64.0GB temp: 0C
           ID-3: /dev/sdc model: CT250BX100SSD1 size: 250.1GB temp: 27C
Partition: ID-1: / size: 47G used: 40G (90%) fs: ext4 dev: /dev/dm-0
           ID-2: /boot size: 228M used: 139M (65%) fs: ext2 dev: /dev/sdb1
           ID-3: swap-1 size: 12.88GB used: 0.00GB (0%)
           fs: swap dev: /dev/dm-1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 65.0C mobo: N/A gpu: 65.5
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 264 Uptime: 19 min Memory: 3344.3/11882.7MB
           Init: systemd runlevel: 5 Gcc sys: 7.2.1
           Client: Shell (bash 4.4.121) inxi: 2.3.45
```

What does this mean?

```
"driver: FAILED: modesetting"
```

---

### Post by ventrical on 2017-12-15
The nomodeset will block the ati-driver - or it seems that this is what it is doing. You are also using LLVM (which is llvmpipe) and may not give you full graphical movement. You could try to remove nomodset and see if it will pick a non-llvmpipe driver. A lot of ATi graphical hardware has been obsoleted. Some will work well, some will jockey in a VESA driver which is not bad (except no wayland) and yet still , more so than not, it will choose an LLVM driver.

There are also a lot of Nvidia graphical adapter problems. IntelMobile and embeded intel drivers(nouveau) usually work best.

---

### Post by darran-kelinske on 2017-12-18
I don't know what happened, but after making that setting everything works :) I realized I had the hdmi and dvi plugged into the same monitor and ubuntu was seeing that as two separate displays.

---

### Post by darran-kelinske on 2017-12-22
What is weird is that each time I restart my computer the screen ends up looking like the screen in the screenshot, but once I turn my monitor on and back off again the screen will render correctly at 2560 x 1600.

---

### Post by standall on 2017-12-28
You can change the resolution through the terminal by the following.

You open the terminal and execute the command:

 xrand-q

You will be paid on results the screen resolution you can use. The picture below is the result of his machine and attached is the result of graphics applications for easier comparison.

For  example I want to change the resolution to 1024 × 768 then I will have  to choose 1 of 4 refresh rate (refresh rate) is 85, 75, 60 and 70.1. If I select a refresh rate is 60, I will have to execute the following command:

 sudo xrandr-s 1024 × 768-r 60

With this command the resolution of your screen will be switched to 1024 × 768 with refresh rate is 60.

---

