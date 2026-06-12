---
title: "BGH Positivo AT 300 Auto Sleep When Working"
date: 2019-03-13
forum: Ubuntu/Debian BASED
---

### Post by ragallo on 2019-03-13
Hi everyone,

I was using Lubuntu 18.04 but the bluetooth doesn't work well, either the USB, so I try others flavors of Linux:
[LIST]
[*]Ubuntu 18.04 
[*]Bodhi Linux 5.0 
[*]Peppermint 9 
[/LIST]
 
With this last tree i have the same problem. The PC go to sleep, and dont mater if I'm working or not. 

Here is a video of the problem:
[https://youtu.be/1gQTZQU-oAE](https://youtu.be/1gQTZQU-oAE)

Here is the PC especifications: 
[https://store.bgh.com.ar/notebook-pos](https://store.bgh.com.ar/notebook-pos)... 

I leave some information of the PC

```
**inxi -Fz**
System:    Host: ragallo-Serie-AT300 Kernel: 4.15.0-43-generic x86_64 bits: 64
           Desktop: N/A Distro: Peppermint Nine
Machine:   Device: laptop System: POSITIVO BGH product: Serie AT300 v: Tablet serial: N/A
           Mobo: POSITIVO BGH model: Serie AT300 v: tablet serial: N/A
           UEFI: POSITIVO BGH v: CHT14BP.09.BGHV01XY2 date: 09/28/2017
CPU:       Quad core Intel Atom x5-Z8350 (-MCP-) cache: 1024 KB
           clock speeds: max: 1920 MHz 1: 757 MHz 2: 787 MHz 3: 575 MHz 4: 815 MHz
Graphics:  Card: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.01hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics (Cherrytrail)
           version: 4.5 Mesa 18.0.5
Audio:     Card-1 Intel HDMI/DP LPE Audio driver: HdmiLpeAudio
           Card-2 bytcht-es8316 driver: bytcht-es8316
           Sound: Advanced Linux Sound Architecture v: k4.15.0-43-generic
Network:   Card: Failed to Detect Network Card!
Drives:    HDD Total Size: NA (-)
           ID-1: /dev/mmcblk0 model: N/A size: 31.3GB
Partition: ID-1: / size: 29G used: 5.4G (21%) fs: ext4 dev: /dev/mmcblk0p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 44.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 250 Uptime: 2:38 Memory: 644.4/1795.4MB
           Client: Shell (bash) inxi: 2.3.56 
```

```
**xset -q**
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  20
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
```

I try 
```
xset -dpms
```

I also try
```
sudo killall xfce4-power-manager
```

and still doing the same

Can someone help me with this?

---

### Post by howefield on 2019-03-13
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by felipemaranda on 2019-06-10
Hi!

The first thing I suggest to you, is update the kernel to a newer one. The Cherry Trail Atom got lots of improvements in newer kernels. You can easily do that with Ukuu in any Ubuntu based distros ([https://teejeetech.in/ukuu/](https://teejeetech.in/ukuu/)).

---

