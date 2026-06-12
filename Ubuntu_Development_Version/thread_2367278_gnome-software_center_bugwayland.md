---
title: "gnome-software center bug/wayland"
date: 2017-07-28
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-07-28
gnome-software center will open blank. Then you have to close it. when you open it again it will populate with apps.on wayland



[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1707164](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1707164)

---

### Post by sudodus on 2017-07-28
It works for me (installed Artful on Wayland, updated & upgraded today), but it is slow until it is populated. What happens if you wait a minute?

---

### Post by rrnbtter on 2017-07-28
Greetings,
It works perfect for me. Considering the reported issues with the "greeter", you many want to log out and then back into Wayland. I doubt that Wayland is the problem with any of the reported issues. More likely the hodge podge patchwork that Canonical has going on right now. I got a luckybackup update last night but lucky doesn't work any better because rsync that it is the frontend for can't access root under Wayland. This in spite of the fact that rsync being a server backup doesn't normally need sudo to get root.

---

### Post by ventrical on 2017-07-28
> **sudodus said:**
> It works for me (installed Artful on Wayland, updated & upgraded today), but it is slow until it is populated. What happens if you wait a minute?

2 minutes. Thats a bug  because if I close it right away and then re-open it,  it starts right up.

---

### Post by ventrical on 2017-07-28
> **rrnbtter said:**
> Greetings,
It works perfect for me. Considering the reported issues with the "greeter", you many want to log out and then back into Wayland. 

Over and over again.
Still same behaviour.


```


ventrical@ventrical-MS-7850:~$ inxi -Fxz
System:    Host: ventrical-MS-7850 Kernel: 4.11.0-10-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.3 (Gtk 3.22.17-0ubuntu1)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0
           BIOS: American Megatrends v: V2.8 date: 07/17/2014
CPU:       Dual core Intel Pentium G3240 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12400
           clock speeds: max: 3100 MHz 1: 3092 MHz 2: 3100 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.3) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: Mesa DRI Intel Haswell Desktop
           version: 4.5 Mesa 17.1.2 Direct Render: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Card-3 Logitech Webcam C210 driver: USB Audio usb-ID: 003-002
           Sound: Advanced Linux Sound Architecture v: k4.11.0-10-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (11.1% used)
           ID-1: /dev/sda model: KINGSTON_SV300S3 size: 120.0GB
Partition: ID-1: / size: 52G used: 9.6G (20%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 3.21GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 223 Uptime: 4:32 Memory: 1393.1/3812.4MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.25 
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by sudodus on 2017-07-28
> **ventrical said:**
> 

```

Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.3) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: Mesa DRI Intel Haswell Desktop
           version: 4.5 Mesa 17.1.2 Direct Render: Yes

```

Could it be a problem because of the graphics? What happens if you try in a computer with another kind of graphics hardware (not Intel, or at least not Intel Xeon integrated graphics)?

---

### Post by ventrical on 2017-07-28
> **sudodus said:**
> Could it be a problem because of the graphics? What happens if you try in a computer with another kind of graphics hardware (not Intel, or at least not Intel Xeon integrated graphics)?

Yes will try another box .

---

### Post by ventrical on 2017-07-28
45 seconds on nVidia box

---

### Post by sudodus on 2017-07-28
> **ventrical said:**
> 45 seconds on nVidia box

Is it populated after 45 seconds?

---

### Post by ventrical on 2017-07-28
> **sudodus said:**
> Is it populated after 45 seconds?

yes. it starts slow .. looks broken at first .. but then starts to populate.

---

### Post by sudodus on 2017-07-28
That's how it works for me too.

---

### Post by ventrical on 2017-07-28
It's busted on nvidia too because if you click the app on , shut if off and then real fast click it back on it populates in 5 seconds so there is serious bug with this.

---

### Post by sudodus on 2017-07-28
I see. I will mark 'affects me too'.

---

### Post by ventrical on 2017-07-28
> **sudodus said:**
> I see. I will mark 'affects me too'.

+1 :)

---

