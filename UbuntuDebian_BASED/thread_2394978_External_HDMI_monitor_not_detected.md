---
title: "External HDMI monitor not detected"
date: 2018-06-24
forum: Ubuntu/Debian BASED
---

### Post by Avoozl on 2018-06-24
I have an Envy 14 laptop on which I am running Crunchbang++ (basically debian 9). I cannot get the external monitor (TV) to be detected through the HDMI port. I know that the monitor, port, and cable are all working as I had this monitor working with Windows 10 on this computer. As far as I can tell this laptop has two graphics cards, integrated graphics and also an AMD Mobility Radeon 5000 series card. I know very little about hardware.

Xrandr does not detect any HDMI device. I get LVDS-1 connected and VGA-1 disconnected.

The monitor also "comes on" (though the screen stays black) while the computer is booting but once the OS is fully loaded the external monitor says "no video signal detected."

Does anyone have any ideas of what I might be able to do to get the external monitor working? Thank you.

---

### Post by Avoozl on 2018-06-24
Here is the output of inxi -F:

System:    Host: northwarden Kernel: 4.9.0-6-amd64 x86_64 (64 bit) Desktop: Openbox 3.6.1
           Distro: Debian GNU/Linux 9 (stretch)
Machine:   Device: laptop System: Hewlett-Packard product: HP ENVY NOTEBOOK PC v: 057E120011243E10001620000
           Mobo: Hewlett-Packard model: 1436 v: 59.23 BIOS: Hewlett-Packard v: F.23 date: 11/11/2010
Battery    BAT0: charge: 21.2 Wh 77.9% condition: 27.3/27.3 Wh (100%)
CPU:       Dual core Intel Core i5 M 480 (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 2667 MHz 1: 1733 MHz 2: 1199 MHz 3: 1199 MHz 4: 1199 MHz
Graphics:  Card-1: Intel Core Processor Integrated Graphics Controller
           Card-2: Advanced Micro Devices [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
           Display Server: X.Org 1.19.2 drivers: modesetting,ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1366x768@59.64hz
           GLX Renderer: Mesa DRI Intel Ironlake Mobile GLX Version: 2.1 Mesa 13.0.6
Audio:     Card-1 Intel 5 Series/3400 Series High Definition Audio driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series]
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.9.0-6-amd64
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp2s0 state: down mac: 64:31:50:6b:4e:67
           Card-2: Intel Centrino Advanced-N 6200 driver: iwlwifi
           IF: wlp3s0 state: up mac: 58:94:6b:b1:de:e8
Drives:    HDD Total Size: 500.1GB (3.9% used)
           ID-1: /dev/sda model: ST9500420AS size: 500.1GB
Partition: ID-1: / size: 452G used: 13G (3%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 6.23GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
Sensors:   System Temperatures: cpu: 46.0C mobo: N/A gpu: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 178 Uptime: 1:43 Memory: 784.2/5769.2MB Client: Shell (bash) inxi: 2.3.5

---

### Post by Avoozl on 2018-06-25
Okay well, I sort of figured it out.  The integrated card can't access the HDMI port, so a sort of workaround is to have the integrated card process both monitors and simply pass one of them to the discrete card for display.

```
xrandr --listproviders
```
WIll report the integrated card as 0 and the discrete card as 1.  Then I can run:
```
xrandr --setprovideroutputsource 1 0
```
to allow the HDMI port to be recognized by the integrated card.  Then I used normal xrandr commands to enable the newly-recognized HDMI-1-0 device.

I have a new problem (sound through HDMI) but that will be another thread.  I was going to just delete this thread but I couldn't figure out how.

---

