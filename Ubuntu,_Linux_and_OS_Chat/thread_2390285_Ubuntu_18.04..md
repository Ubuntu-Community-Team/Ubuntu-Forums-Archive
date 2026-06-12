---
title: "Ubuntu 18.04."
date: 2018-04-27
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2018-04-27
Hello All,

I just installed ***Ubuntu 18.04***  and the install went without problems.

I like the ***Gnome Desktop*** and have no problems navigating through it.

The only problem I seem to be having is ***FF 59.0.2*** crashes a lot. ***Yeah I know what's new***.

Ran the ***Spectre / Melt Down Check*** and shows ***No Vulnerability*** on all ***Variants***.

I like it. :cool:  ):P


My Frankenstein Build.

```
thomas@ASUS-M4A785-M:~$ inxi -Fxz
System:    Host: ASUS-M4A785-M Kernel: 4.15.0-20-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.1 (Gtk 3.22.30-1ubuntu1) Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: M4A785-M v: Rev X.0x serial: N/A
           BIOS: American Megatrends v: 1006 date: 08/18/2010
CPU:       Triple core AMD Phenom 8650 (-MCP-) arch: K10 rev.3 cache: 1536 KB
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 13861
           clock speeds: max: 2300 MHz 1: 1150 MHz 2: 1150 MHz 3: 2300 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RS880 [Radeon HD 4200] bus-ID: 01:05.0
           Display Server: x11 (X.Org 1.19.6 ) driver: radeon Resolution: 1280x720@60.00hz
           OpenGL: renderer: AMD RS880 (DRM 2.50.0 / 4.15.0-20-generic, LLVM 6.0.0)
           version: 3.3 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]
           driver: snd_hda_intel bus-ID: 01:05.1
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel bus-ID: 00:14.2
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e800 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 20.0GB (26.5% used)
           ID-1: /dev/sda model: ST320014A size: 20.0GB
Partition: ID-1: / size: 19G used: 5.0G (29%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: 38.0C
           Fan Speeds (in rpm): cpu: 2528 sys-1: 1859
Info:      Processes: 184 Uptime: 1:01 Memory: 945.7/3692.7MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.191) inxi: 2.3.56 
thomas@ASUS-M4A785-M:~$ 

```

---

### Post by sudodus on 2018-04-27
Congratulations :-)

Try the community flavours of 18.04 LTS too (at least, you can try them live from USB without installing).

I think you will find some nice surprises :-)

---

### Post by PaulW2U on 2018-04-27
> **poorguy said:**
> I just installed ***Ubuntu 18.04***  and the install went without problems.

I like the ***Gnome Desktop*** and have no problems navigating through it.

The only problem I seem to be having is ***FF 59.0.2*** crashes a lot.

Hello poorguy, thanks for the PM. I've just installed Xubuntu 18.04 after an upgrade from 16.04 wasn't 100% successful.  :(

I have Ubuntu 18.04 on another PC and that's working well too. No problems here with Firefox on either Ubuntu or Xubuntu.

---

### Post by i7Fd-2sCB1 on 2018-04-27
> **poorguy said:**
> Hello All,

I just installed ***Ubuntu 18.04***  and the install went without problems.

I like the ***Gnome Desktop*** and have no problems navigating through it.

The only problem I seem to be having is ***FF 59.0.2*** crashes a lot. ***Yeah I know what's new***.

Ran the ***Spectre / Melt Down Check*** and shows ***No Vulnerability*** on all ***Variants***.

I like it. :cool:  ):P


My Frankenstein Build.

```
thomas@ASUS-M4A785-M:~$ inxi -Fxz
System:    Host: ASUS-M4A785-M Kernel: 4.15.0-20-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.28.1 (Gtk 3.22.30-1ubuntu1) Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: M4A785-M v: Rev X.0x serial: N/A
           BIOS: American Megatrends v: 1006 date: 08/18/2010
CPU:       Triple core AMD Phenom 8650 (-MCP-) arch: K10 rev.3 cache: 1536 KB
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 13861
           clock speeds: max: 2300 MHz 1: 1150 MHz 2: 1150 MHz 3: 2300 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RS880 [Radeon HD 4200] bus-ID: 01:05.0
           Display Server: x11 (X.Org 1.19.6 ) driver: radeon Resolution: 1280x720@60.00hz
           OpenGL: renderer: AMD RS880 (DRM 2.50.0 / 4.15.0-20-generic, LLVM 6.0.0)
           version: 3.3 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]
           driver: snd_hda_intel bus-ID: 01:05.1
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel bus-ID: 00:14.2
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e800 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 20.0GB (26.5% used)
           ID-1: /dev/sda model: ST320014A size: 20.0GB
Partition: ID-1: / size: 19G used: 5.0G (29%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: 38.0C
           Fan Speeds (in rpm): cpu: 2528 sys-1: 1859
Info:      Processes: 184 Uptime: 1:01 Memory: 945.7/3692.7MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.191) inxi: 2.3.56 
thomas@ASUS-M4A785-M:~$ 

```

I haven't used Ubuntu for years since it adopted Unity but have since then this year gone back to it from using Arch Linux originally. As with Firefox I've experienced no crashes on the Ubuntu 18.04 LTS version, could it be hardware issue or drivers?

---

### Post by poorguy on 2018-04-27
> **sudodus said:**
> Congratulations :-)

Try the community flavours of 18.04 LTS too (at least, you can try them live from USB without installing).

I think you will find some nice surprises :-)
At the risk of sounding stupid ***(one thing I do well)*** by community flavors are you referring to ***Lubuntu / Xubuntu*** etc.

[I][B]

@centralpython[/B][/I] 
It could very well be a hardware issue as this ***Frankenstein Build ***is from ***2010*** and I just through it together out of spare parts to install and try out [I][B]Ubuntu 18.04.

[/B][/I] Perfect example of spare parts look at the ***hard drive*** it's a  ***20 GB 5400 RPM***  ***unopened new old stock*** I had acquired throughout the years figured what the hell I'll use it.

Anyway I installed ***Chromium*** and no more browser crashes so I happy. 

The ***Ubuntu Developers*** did an excellent job with*** Bionic Beaver***.

This is my second new final release since using Linux and this time [I][B]I'm very impressed.


[/B][/I]poorguy ;)

---

### Post by Autodave on 2018-04-27
Installed Xubuntu on an older machine and it is running just fine.  Getting ready to do the 6 machines now. Yehaw.

---

### Post by sudodus on 2018-04-27
> **poorguy said:**
> by community flavors are you referring to ***Lubuntu / Xubuntu*** etc.


Yes :-)

You find them all in convenient way via [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by poorguy on 2018-04-27
> **sudodus said:**
> Yes :-)

You find them all in convenient way via [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
Hey sudodus,


Thanks for the link.

I kinda figured that's what you meant.


I just noticed that the installer no longer creates a swap partion.

If a user only has 4.0 GB of memory is a swap partion still needed.

I wonder why no swap partion anymore.


Thanks

---

### Post by &amp;KyT$0P# on 2018-04-27
> **poorguy said:**
> I just noticed that the installer no longer creates a swap partion.

If a user only has 4.0 GB of memory is a swap partion still needed.

I wonder why no swap partion anymore.
It instead creates a swapfile.  Check [FONT=Courier New]/etc/fstab[/FONT] to find where your swapfile is located.

---

### Post by poorguy on 2018-04-28
> **halogen2 said:**
> It instead creates a swapfile.  Check [FONT=Courier New]/etc/fstab[/FONT] to find where your swapfile is located.
Hello halogen2,

Interesting why it does it that way.

I went ahead and did a reinstall and this time minimum instead of the full cause I don't use a lot of the software that comes with a full install. 

I partitioned the drive the manual way and created a 2.0 GB swap partition since I only have a 20 GB hard drive.


Live and learn. ;)

---

### Post by deadflowr on 2018-04-28
About swap change:
[http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html?utm_source=omgubuntu]("http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html?utm_source=omgubuntu")
fwiw

---

### Post by poorguy on 2018-04-28
Hello deadflowr,

Interesting read and something I didn't know.

Well I'll keep my existing set up since I already have it installed and it is working.

I wished I had known about this before installing.

I always seem to be learning something new about Linux all of the time.


Thanks.

---

### Post by sudodus on 2018-04-28
> **poorguy said:**
> I always seem to be learning something new about Linux all of the time.

We all do :-)

---

### Post by poorguy on 2018-04-28
I've just installed ***Xubuntu 18.04*** on the desktop below and everything works 100% OOTB. :cool:

```

thomas@Dell-OptiPlex-380:~$ inxi -Fxz
System:    Host: Dell-OptiPlex-380 Kernel: 4.15.0-20-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Xfce 4.12.3 (Gtk 2.24.31) Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop System: Dell product: OptiPlex 380 serial: N/A
           Mobo: Dell model: 0HN7XN v: A01 serial: N/A BIOS: Dell v: A02 date: 08/27/2010
CPU:       Dual core Intel Core2 Duo E7500 (-MCP-) arch: Penryn rev.10 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11704
           clock speeds: max: 2933 MHz 1: 1596 MHz 2: 1595 MHz
Graphics:  Card: Intel 4 Series Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1280x720@60.00hz
           OpenGL: renderer: Mesa DRI Intel G41 version: 2.1 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Broadcom Limited NetLink BCM57780 Gigabit Ethernet PCIe driver: tg3 v: 3.137 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (5.6% used)
           ID-1: /dev/sda model: Hitachi_HTS54161 size: 120.0GB
Partition: ID-1: / size: 110G used: 6.3G (6%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 41.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 151 Uptime: 36 min Memory: 653.4/3844.4MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 
thomas@Dell-OptiPlex-380:~$ 

```

---

### Post by poorguy on 2018-05-01
> **sudodus said:**
> Congratulations :-)

Try the community flavours of 18.04 LTS too (at least, you can try them live from USB without installing).

I think you will find some nice surprises :-)
Hey sudodus,


The ***"community flavours of 18.04 LTS" ***are excellent. [IMG]https://ubuntuforums.org/images/icons/icon14.png[/IMG]

---

### Post by poorguy on 2018-05-20
I installed ***Lubuntu 18.04 (64bit)*** on this old ***Dell Optiplex 320 / Pentium D 950 Processor, 3.40 GHz and only 2.0 GB DDR2 Memory ***and this old relic runs great.

For some reason the ***Bios*** won't support no more than ***2.0GB Memory ***and*** Dell*** won't write a ***bios*** that would correct this problem.[I][B] OH Well!

[/B][/I]I just did it because I got bored. :cool:

```
Dell-OptiPlex-320:~$ inxi -Fxz
System:    Host: Dell-OptiPlex-320 Kernel: 4.15.0-20-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop System: Dell product: OptiPlex 320 serial: N/A
           Mobo: Dell model: 0TY915 serial: N/A BIOS: Dell v: 1.1.12 date: 06/17/2007
CPU:       Dual core Intel Pentium D (-MCP-) arch: Netburst Prescott rev.4 cache: 2048 KB
           flags: (lm nx sse sse2 sse3 vmx) bmips: 13599
           clock speeds: max: 3400 MHz 1: 2400 MHz 2: 3400 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RC410 [Radeon Xpress 200/1100] bus-ID: 01:05.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1280x720@60.00hz
           OpenGL: renderer: ATI RC410 version: 2.1 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA) driver: snd_hda_intel bus-ID: 00:14.2
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Broadcom Limited BCM4401-B0 100Base-TX driver: b44 v: 2.0 bus-ID: 02:09.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 40.0GB (13.7% used)
           ID-1: /dev/sda model: WDC_WD400JB size: 40.0GB
Partition: ID-1: / size: 37G used: 5.2G (15%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 137 Uptime: 53 min Memory: 781.3/1959.1MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 
Dell-OptiPlex-320:~$ 
```

---

