---
title: "how to fix nvidia/plymouth fails on release candidate"
date: 2017-10-13
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-10-13
We have been having lots of problems with RC and beta etc on PCs with nVidia.

Here is what I did as workaround/fix. I downgraded my nVidia card (changed it) to see if there was hardware problem.

1.Start the PC that has just had the daily/current hard installed.
2. Hold down the shift key while booting.
2.(a) Wait for Grub screen.
2.(b) Choose <advanced options> THEN
2.(c) Choose Recovery option.
3.Wait till all verbose code runs.
4 .Click "resume". Don't do anything!
5. Wait for reboot. It may boot into weird gdm resolution with no gdm Cog-Wheel.
6.Enter password and it should load up ubuntu on xorg. (it did on mine because old nVidia does not support wayland)
7. There might be fuzzy resolution. Don't worry about it.
8. Restart from panel.
9. Go through normal boot and it should boot up to gdm screen with proper resolution.
10. Log on and you will have proper resolution of gnome desktop.

You will notice that it loaded with the old vesa driver which is just  too awesome!:)

my old nVidia card on gnome3 with xorg.

```

ventrical@ventrical-Precision-WorkStation-T3400:~$ inxi -Fxz
System:    Host: ventrical-Precision-WorkStation-T3400 Kernel: 4.13.0-15-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.1 (Gtk 3.22.21-0ubuntu1)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop System: Dell product: Precision WorkStation T3400 serial: N/A
           Mobo: Dell model: 0TP412 serial: N/A
           BIOS: Dell v: A03 date: 01/31/2008
CPU:       Quad core Intel Core2 Quad Q6600 (-MCP-) 
           arch: Conroe rev.11 cache: 4096 KB
           flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 19153
           clock speeds: max: 2394 MHz 1: 2394 MHz 2: 2394 MHz 3: 2394 MHz
           4: 2394 MHz
Graphics:  Card: NVIDIA G98 [GeForce 8400 GS Rev. 2] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.3 )
           drivers: vesa (unloaded: modesetting,fbdev) FAILED: nouveau
           Resolution: 1440x900@59.89hz
           OpenGL: renderer: NV98 version: 3.3 Mesa 17.2.2 Direct Render: Yes
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-15-generic
Network:   Card: Broadcom Limited NetXtreme BCM5754 Gigabit Ethernet PCIE
           driver: tg3 v: 3.137 bus-ID: 04:00.0
           IF: enp4s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 160.0GB (3.6% used)
           ID-1: /dev/sda model: ST3160815AS size: 160.0GB temp: 33C
Partition: ID-1: / size: 146G used: 5.5G (4%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 37.0C mobo: N/A gpu: 35.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 218 Uptime: 14 min Memory: 1374.0/3881.8MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.37 
ventrical@ventrical-Precision-WorkStation-T3400:~$ 

```

Will switch back to late model nVidia card after I give this old dinosaur a run ;)

regards..

---

### Post by ventrical on 2017-10-14
Update: This method eventually failed after hard reboot. It went back to the plymouth/freeze so I installed lightdm. Works from there.


Regards..

---

### Post by ventrical on 2017-10-14
Ok.. so after I install lightdm  nouveau all of a sudden kicks in. Look at my first post on this. gdm3 is mangling  up the jockeying process.

```

Graphics:  Card: NVIDIA G98 [GeForce 8400 GS Rev. 2] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.5 )
           drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1440x900@59.89hz
           OpenGL: renderer: NV98 version: 3.3 Mesa 17.2.2 Direct Render: Yes

```

this should be impossible on this old nvidia card.

Regards..

---

### Post by amano on 2017-10-14
I can get into GDM sometimes (on every 5th reboot or so).

Those are my specs then (I have an older nvidia card/chip as well):


```

System:    Host: amano-desktop Kernel: 4.13.0-16-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.1 (Gtk 3.22.21-0ubuntu1)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: ASRock model: AMCP7A-ION serial: N/A
           BIOS: American Megatrends v: P1.60 date: 08/26/2009
CPU:       Dual core Intel Atom 330 (-HT-MCP-) 
           arch: Bonnell rev.2 cache: 512 KB
           flags: (lm nx sse sse2 sse3 ssse3) bmips: 6399
           clock speeds: max: 1599 MHz 1: 1599 MHz 2: 1599 MHz 3: 1599 MHz
           4: 1599 MHz
Graphics:  Card: NVIDIA ION VGA bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.5 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: NVAC version: 3.3 Mesa 17.2.2 Direct Render: Yes
Audio:     Card NVIDIA MCP79 High Def. Audio
           driver: snd_hda_intel bus-ID: 00:08.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-16-generic
Network:   Card: NVIDIA MCP79 Ethernet
           driver: forcedeth port: d080 bus-ID: 00:0a.0
           IF: enp0s10 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 320.1GB (47.3% used)
           ID-1: /dev/sda model: ST9320325AS size: 320.1GB temp: 46C
Partition: ID-1: / size: 21G used: 14G (69%) fs: ext4 dev: /dev/sda5
           ID-2: swap-1 size: 1.03GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 77.0C mobo: N/A gpu: 81.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 227 Uptime: 39 min Memory: 1605.8/3256.5MB
           Init: systemd runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (bash 4.4.121) inxi: 2.3.3

```

```

amano@amano-desktop:~$ echo $DESKTOP_SESSION
ubuntu

```

My ION is nvidia 9400M based. So like yours probably from the same "generation 9" gpus-

---

### Post by ventrical on 2017-10-14
> **amano said:**
> I can get into GDM sometimes (on every 5th reboot or so).

Those are my specs then (I have an older nvidia card/chip as well):


```

System:    Host: amano-desktop Kernel: 4.13.0-16-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.1 (Gtk 3.22.21-0ubuntu1)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: ASRock model: AMCP7A-ION serial: N/A
           BIOS: American Megatrends v: P1.60 date: 08/26/2009
CPU:       Dual core Intel Atom 330 (-HT-MCP-) 
           arch: Bonnell rev.2 cache: 512 KB
           flags: (lm nx sse sse2 sse3 ssse3) bmips: 6399
           clock speeds: max: 1599 MHz 1: 1599 MHz 2: 1599 MHz 3: 1599 MHz
           4: 1599 MHz
Graphics:  Card: NVIDIA ION VGA bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.5 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: NVAC version: 3.3 Mesa 17.2.2 Direct Render: Yes
Audio:     Card NVIDIA MCP79 High Def. Audio
           driver: snd_hda_intel bus-ID: 00:08.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-16-generic
Network:   Card: NVIDIA MCP79 Ethernet
           driver: forcedeth port: d080 bus-ID: 00:0a.0
           IF: enp0s10 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 320.1GB (47.3% used)
           ID-1: /dev/sda model: ST9320325AS size: 320.1GB temp: 46C
Partition: ID-1: / size: 21G used: 14G (69%) fs: ext4 dev: /dev/sda5
           ID-2: swap-1 size: 1.03GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 77.0C mobo: N/A gpu: 81.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 227 Uptime: 39 min Memory: 1605.8/3256.5MB
           Init: systemd runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (bash 4.4.121) inxi: 2.3.3

```

```

amano@amano-desktop:~$ echo $DESKTOP_SESSION
ubuntu

```

My ION is nvidia 9400M based. So like yours probably from the same "generation 9" gpus-

Ahh .. thanks.  I see you are using the proprietary driver.

Regards..

---

### Post by amano on 2017-10-15
Ventrical, the proprietary driver is disabled in update-manager. 

Nvidia 340 shouldn't support wayland at all (just nvidia 384 can do that) and as you can see I am on the Ubuntu session that uses Wayland. So I am guessing that I am on Nouveau, despite what inxi says (we hit another bug?).

If I explicitely enable the proprietary driver “Ubuntu“ and “Gnome“ are not listed in the GDM cog anymore. So it makes a difference.

---

### Post by ventrical on 2017-10-15
> **amano said:**
> Ventrical, the proprietary driver is disabled in update-manager. 

Nvidia 340 shouldn't support wayland at all (just nvidia 384 can do that) and as you can see I am on the Ubuntu session that uses Wayland. So I am guessing that I am on Nouveau, despite what inxi says (we hit another bug?).

If I explicitly enable the proprietary driver “Ubuntu“ and “Gnome“ are not listed in the GDM cog anymore. So it makes a difference.

I will swap in my other nVida adapter and install the nVidia driver to see if I can emulate. We had some really huge breakage during 12.04 dev and in between up to 14.04 with unity on nVidia right up to the end of the cycle. Between 14.04 and 16.04 I started to see that ubuntu was working better  exclusively on Intel graphics based machines.

If we can't trust basic reporting tools like inxi then , yes, those are some serious bugs.

---

### Post by ventrical on 2017-10-15
> **ventrical said:**
> I will swap in my other nVida adapter and install the nVidia driver to see if I can emulate. We had some really huge breakage during 12.04 dev and in between up to 14.04 with unity on nVidia right up to the end of the cycle. Between 14.04 and 16.04 I started to see that ubuntu was working better  exclusively on Intel graphics based machines.

If we can't trust basic reporting tools like inxi then , yes, those are some serious bugs.

OK.. swapped in my other nVidia card:

```

Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: x11 (X.Org 1.19.5 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1440x900@59.89hz
           OpenGL: renderer: GeForce GT 610/PCIe/SSE2
           version: 4.5.0 NVIDIA 384.90 Direct Render: Yes

```

install 384 driver

will not work  with walyand

Regards..

---

### Post by amano on 2017-10-16
That makes the difference: nvidia 340 does't support Wayland. Since it doesn't try to bring up Wayland for that reason and just uses x, it doesn't freeze.

Nvidia 384 is Wayland capable, so tries to bring up Wayland and hits the bug.

Mesa is Wayland capable and thus hits the bug as well.

---

### Post by ventrical on 2017-10-16
Earlier on in the cycles .. just a couple weeks back, I had it working in gdm3 with nouveau and  an update just killed it. I'm trying to keep my installs  as bare metal as possible with no addons or tweaks because there are just so many apps in the universe that can break it (gnome3). I like the themes and concepts and all but it's just so fragile and touchy. Not too may probs with Intel/wayland. I'm getting very wary of nVidia cards new and old. They are beginning to be a real pain.

Regards..

---

