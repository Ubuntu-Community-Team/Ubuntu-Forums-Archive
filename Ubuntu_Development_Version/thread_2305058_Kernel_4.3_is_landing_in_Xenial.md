---
title: "Kernel 4.3 is landing in Xenial"
date: 2015-12-02
forum: Ubuntu Development Version
---

### Post by fthx on 2015-12-02
Well, I did not *notice* any regression.

---

### Post by slickymaster on 2015-12-02
Running smoothly over here```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Xenial Xerus (development branch)
Release:	16.04
Codename:	xenial
4.3.0-0-generic
```

---

### Post by sammiev on 2015-12-02
Been a smooth ride so far.

All is good.

---

### Post by MikeMecanic on 2015-12-02
Is Kernel 4.3 in today daily build or is it available only via Proposed?

Thanks for the update.

Edit: Not in Dec 2nd build but in proposed.

```
xenial3@hp:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Xenial Xerus (development branch)
Release:    16.04
Codename:    xenial
xenial3@hp:~$ grub-install --version
grub-install (GRUB) 2.02~beta2-32
xenial3@hp:~$ ubuntu-drivers list
intel-microcode
xenial3@hp:~$ ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free
xenial3@hp:~$ uname -r
4.3.0-0-generic
xenial3@hp:~$ exit

```

Have a bug with the icons:  There too big in the desktop and in Office.  **Try something that I never did in the pass, turn on Proposed before running Software Updater for the first time**.  
On reboot, icons were 10 times larger then usual.  I can reduce text size, launcher size but not the icons size?  Otherwise, I never seen an Ubuntu installer running that fast, ounce I set the password, it took about 2 minutes to complete the installation.

---

### Post by fthx on 2015-12-03
Nautilus 3.18 has landed in main repository. And it makes the icons really BIG (even the smaller size is not so small). In Gnome, I can change the icons size (desktop+windowed Nautilus) in Nautilus UI menu.

---

### Post by MikeMecanic on 2015-12-03
There is no place to reduce icons size in Nautilus 3.18.2. It wouldn't be a bad idea to introduce such setting. Iv'e got a perfect vision and things are always to big in a monitor: Launcher is set to 40 and text size to .75. 
All icons are affected plus the one in the desktop but I removed them (from post-installation). Not a big issue anyway and certainly not one to turn off Proposed or to go backward at Kernel 4.2...

---

### Post by fthx on 2015-12-03
There is a place to reduce icons size : grid icon > slider. I agree that there's for sure a size bug, though.
And Nautilus 3.18 is not in proposed but in main.

---

### Post by harry332 on 2015-12-03
Now also Linux 4.3.0-1.10 is in proposed.

---

### Post by flocculant on 2015-12-03
> **fthx said:**
> Nautilus 3.18 has landed in main repository. And it makes the icons really BIG (even the smaller size is not so small). In Gnome, I can change the icons size (desktop+windowed Nautilus) in Nautilus UI menu.

[https://bugs.launchpad.net/nautilus/+bug/1522316](https://bugs.launchpad.net/nautilus/+bug/1522316)

---

### Post by sammiev on 2015-12-03
> **flocculant said:**
> [https://bugs.launchpad.net/nautilus/+bug/1522316](https://bugs.launchpad.net/nautilus/+bug/1522316)

Looks good here.

---

### Post by flocculant on 2015-12-03
> **sammiev said:**
> Looks good here.

Looks good here too - I don't use Ubuntu :p

Just linking the bug ;)

---

### Post by zika on 2015-12-03
```
:~$ sudo apt-get dist-upgrade Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.4.0-0 linux-headers-4.4.0-0-lowlatency
  linux-image-4.4.0-0-lowlatency
The following packages will be upgraded:
  linux-headers-lowlatency linux-image-lowlatency linux-lowlatency
3 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 67,2 MB of archives.
After this operation, 290 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://ppa.launchpad.net/canonical-kernel-team/unstable/ubuntu devel/main amd64 linux-image-4.4.0-0-lowlatency amd64 4.4.0-0.1 [56,6 MB]
Get:2 http://ppa.launchpad.net/canonical-kernel-team/unstable/ubuntu devel/main amd64 linux-headers-4.4.0-0 all 4.4.0-0.1 [9783 kB]                                                                                                          
Get:3 http://ppa.launchpad.net/canonical-kernel-team/unstable/ubuntu devel/main amd64 linux-headers-4.4.0-0-lowlatency amd64 4.4.0-0.1 [762 kB]                                                                                              
Get:4 http://ppa.launchpad.net/canonical-kernel-team/unstable/ubuntu devel/main amd64 linux-lowlatency amd64 4.4.0.0.1 [1786 B]                                                                                                              
Get:5 http://ppa.launchpad.net/canonical-kernel-team/unstable/ubuntu devel/main amd64 linux-image-lowlatency amd64 4.4.0.0.1 [2494 B]                                                                                                        
Get:6 http://ppa.launchpad.net/canonical-kernel-team/unstable/ubuntu devel/main amd64 linux-headers-lowlatency amd64 4.4.0.0.1 [2484 B]                                                                                                      
Fetched 67,2 MB in 20s (3278 kB/s)
```

---

### Post by QDR06VV9 on 2015-12-03
Ah Ha.. Now I see why?!
> [COLOR=#000000][FONT=Ubuntu Mono]ppa.launchpad.net/canonical-kernel-team/unstable/ubuntu devel/main[/FONT][/COLOR] 
Now I have to play, Thanks zika;)

---

### Post by fjgaude on 2015-12-03
Kernel 4.3.0-1 upgraded in the normal update this morning. Working fine. Was using 4.3.0 because it was the only kernel that was working with my new Intel Z170 MB. Now looking for the release of 16.04 with 4.4 kernel! <smile>

And it seems this latest is supporting gedit and nautilus in their new gnome fittings.

---

### Post by MikeMecanic on 2015-12-03
> **fthx said:**
> There is a place to reduce icons size : grid icon > slider.

Things are back to normal now.  Thanks for the tip!
4.3.0-1-generic

---

### Post by P-I H on 2015-12-04
In Unity you are able to change icon size in Nautilus by holding the Ctrl key and use the mouse wheel to change the size.
[http://askubuntu.com/questions/477237/ubuntu-14-04-nautilus-icons-size](http://askubuntu.com/questions/477237/ubuntu-14-04-nautilus-icons-size)

---

### Post by MikeMecanic on 2015-12-04
> **P-I H said:**
> In Unity you are able to change icon size in Nautilus by holding the Ctrl key and use the mouse wheel to change the size.
[http://askubuntu.com/questions/477237/ubuntu-14-04-nautilus-icons-size](http://askubuntu.com/questions/477237/ubuntu-14-04-nautilus-icons-size)

Thanks for the tip: Works perfectly.

Regards,

---

### Post by Cavsfan on 2015-12-06
I didn't enable proposed but when the 4.3 kernel came through in regular updates my Xubuntu Xenial Xerus install was totally hosed it and that was with the 4.3.0-1-generic kernel.
The system would not even go full screen. I just let it sit and used Arch in the meantime.

Then the 4.3.0-2-generic kernel came through today but still the same thing no full screen system and a block a couple inches high at the bottom that was unusable.
But after purging compiz, nvidia-current (304.131 driver) and messing with it for a couple hours I got it right.

I applied a few tricks I've learned in this forum and that's what fixed it. I also learned something new that finally fixed the window manager. 
Everywhere you look it says to put in CCSM window decoration **/usr/bin/compiz** but that does not work and everything was still messed up.
I just looked around in /etc/bin and found compiz and also compiz-decorator so when I put **/usr/bin/compiz-decorator** in CCSM window decoration, BAM it worked a charm.
So, I finally do not have to try to get emerald installed to have a good window manager.

I even installed the 340.96 driver and thought this old card couldn't handle it but it works fine.

Regards :popcorn:

---

### Post by grahammechanical on 2015-12-06
I have 2 installs of Xenial. One which I uodate/upgrade every day is still on kernel 4.2 and Nautilus 3.14. The other Xenial I just updated for the first ime since I put in the install about 3 weeks ago and it is now on kernel 4.3 and Nautilus 3.18 with the massive icon sizes.

Kernel 4.3 is running fine on Nouveau. Although resizing a Libreoffice window goes a millimeter at a time & greys the window out. I have Nvida GT220 .

---

### Post by ventrical on 2015-12-07
I still get this little monster:

```

Errors were encountered while processing:
 /var/cache/apt/archives/libjpeg-progs_1%3a9a-2ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical-OptiPlex-755:~$ sudo -i dpkg --configure -a

```

but it runs after I use dpkg --configure -a

```

ventrical@ventrical-OptiPlex-755:~$ inxi -Fxz
System:    Host: ventrical-OptiPlex-755 Kernel: 4.3.0-2-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0
           Bios: American Megatrends v: V2.8 date: 07/17/2014
CPU:       Dual core Intel Pentium G3240 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12398
           clock speeds: max: 3100 MHz 1: 3100 MHz 2: 3100 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.17.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 11.0.6 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.3.0-2-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 80.0GB (13.2% used)
           ID-1: /dev/sda model: WDC_WD800HLFS size: 80.0GB
Partition: ID-1: / size: 39G used: 8.0G (22%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 2.10GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 207 Uptime: 0 min Memory: 528.8/7846.6MB
           Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.28 
ventrical@ventrical-OptiPlex-755:~$ 

```

btw .. this on xubuntu. Now for gnome.3

---

### Post by ventrical on 2015-12-07
On gnome-desktop you have to use the 'size' option to make the icons smaller because they are set big by default.

```

ventrical@ventrical-MS-7850:~$ uname -a
Linux ventrical-MS-7850 4.3.0-2-generic #11-Ubuntu SMP Fri Dec 4 20:37:48 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-MS-7850:~$ 


```

and this with proposed repos enabled.

---

### Post by flocculant on 2015-12-07
> **grahammechanical said:**
> ...

Kernel 4.3 is running fine on Nouveau. Although resizing a Libreoffice window goes a millimeter at a time & greys the window out. I have Nvida GT220 .

Same card, same driver, same kernel - slightly different issue.

Resizing a LO window - bit jerky, not greying out though. Obviously this is on Xubuntu.

---

### Post by ventrical on 2015-12-07
> **grahammechanical said:**
> I have 2 installs of Xenial. One which I uodate/upgrade every day is still on kernel 4.2 and Nautilus 3.14. The other Xenial I just updated for the first ime since I put in the install about 3 weeks ago and it is now on kernel 4.3 and Nautilus 3.18 with the massive icon sizes.

Kernel 4.3 is running fine on Nouveau. Although resizing a Libreoffice window goes a millimeter at a time & greys the window out. I have Nvida GT220 .

I cannot emulate this bug on Intel ..

```

ventrical@ventrical-MS-7850:~$ inxi -Fxz
System:    Host: ventrical-MS-7850 Kernel: 4.3.0-2-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Unity (Gtk 3.18.5-1ubuntu2) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0
           Bios: American Megatrends v: V2.8 date: 07/17/2014
CPU:       Dual core Intel Pentium G3240 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12398
           clock speeds: max: 3100 MHz 1: 3100 MHz 2: 3098 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.17.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 11.0.6 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.3.0-2-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (8.4% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 120.0GB temp: 0C
Partition: ID-1: / size: 54G used: 5.7G (12%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.15GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 204 Uptime: 4 min Memory: 620.1/7846.6MB
           Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.28 
ventrical@ventrical-MS-7850:~$ 

```


Regards..
Edit:

Also cannot emulate on this older machine.

```

ventrical@ventrical-MS-7850:~$ inxi -Fxz
System:    Host: ventrical-MS-7850 Kernel: 4.3.0-2-generic x86_64 (64 bit gcc: 5.2.1)
           Desktop: Unity (Gtk 3.18.5-1ubuntu2) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11981
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210] bus-ID: 01:00.0
           Display Server: X.Org 1.17.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVA8
           GLX Version: 3.0 Mesa 11.0.6 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.3.0-2-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (8.4% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 120.0GB
Partition: ID-1: / size: 54G used: 5.7G (12%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.15GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 32.0C mobo: 27.0C gpu: 31.0
           Fan Speeds (in rpm): cpu: 4245 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 216 Uptime: 2 min Memory: 595.1/2000.0MB
           Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.28 
ventrical@ventrical-MS-7850:~$ 

```

Regards..

---

### Post by ventrical on 2015-12-07
> **flocculant said:**
> Same card, same driver, same kernel - slightly different issue.

Resizing a LO window - bit jerky, not greying out though. Obviously this is on Xubuntu.

No jerky here .. nice a smooth (xubuntu).

---

### Post by ventrical on 2015-12-07
> **grahammechanical said:**
> 

Kernel 4.3 is running fine on Nouveau. Although resizing a Libreoffice window goes a millimeter at a time & greys the window out. I have Nvida GT220 .

@grammechanical

 I cannot emulate this behaviour.

```

ventrical@ventrical-MS-7850:~$ inxi -b
System:    Host: ventrical-MS-7850 Kernel: 4.3.0-2-generic x86_64 (64 bit)
           Desktop: Unity Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           Bios: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) speed: 2995 MHz (max)
Graphics:  Card: NVIDIA GT218 [GeForce 210]
           Display Server: X.Org 1.17.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVA8 GLX Version: 3.0 Mesa 11.0.6
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1
Drives:    HDD Total Size: 120.0GB (8.4% used)
Info:      Processes: 221 Uptime: 3 min Memory: 706.7/2000.0MB
           Client: Shell (bash) inxi: 2.2.28 
ventrical@ventrical-MS-7850:~$ 



```

---

### Post by grahammechanical on 2015-12-07
The effect is similar to doing a resize when running on llvmpipe. But it is Gallium 0.4. It might be an effect of my lack of RAM but the desktop is not affected and Firefox resizes as normal.

This is something to do with Libreoffice 5. Resizing a blank writer document is not so bad but try it with a document that has 814 pages as I am doing right now and you might as well go away for a meal. Libreoffice 5 takes a long time to load very large documents. Was not like this with Libreoffice 4.

```
graham@sdb1-xenial:~$ inxi -b
System:    Host: sdb1-xenial Kernel: 4.3.0-2-generic x86_64 (64 bit) Desktop: Unity Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5B-Deluxe v: Rev 1.xx Bios: American Megatrends v: 1004 date: 01/22/2007
CPU:       Dual core Intel Core2 6600 (-MCP-) speed: 2394 MHz (max)
Graphics:  Card: NVIDIA GT216 [GeForce GT 220]
           Display Server: X.Org 1.17.3 drivers: nouveau (unloaded: fbdev,vesa) Resolution: 1920x1080
           GLX Renderer: Gallium 0.4 on NVA5 GLX Version: 3.0 Mesa 11.0.6
Network:   Card-1: Marvell 88E8056 PCI-E Gigabit Ethernet Controller driver: sky2
           Card-2: Marvell 88E8001 Gigabit Ethernet Controller driver: skge
           Card-3: Realtek RTL8187 Wireless Adapter driver: rtl8187
Drives:    HDD Total Size: 750.1GB (11.2% used)
Info:      Processes: 216 Uptime: 1:07 Memory: 720.4/992.0MB Client: Shell (bash) inxi: 2.2.28 

```


Regards.

---

### Post by ventrical on 2015-12-07
> **grahammechanical said:**
> The effect is similar to doing a resize when running on llvmpipe. 


Regards.

This was the first thought that came to mind. I'll try it on another machine with less ram and bigger file.

Regards..

---

### Post by ventrical on 2015-12-07
> **grahammechanical said:**
> The effect is similar to doing a resize when running on llvmpipe. But it is Gallium 0.4. It might be an effect of my lack of RAM but the desktop is not affected and Firefox resizes as normal.

This is something to do with Libreoffice 5. Resizing a blank writer document is not so bad but try it with a document that has 814 pages as I am doing right now and you might as well go away for a meal. Libreoffice 5 takes a long time to load very large documents. Was not like this with Libreoffice 4.

```
graham@sdb1-xenial:~$ inxi -b
System:    Host: sdb1-xenial Kernel: 4.3.0-2-generic x86_64 (64 bit) Desktop: Unity Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5B-Deluxe v: Rev 1.xx Bios: American Megatrends v: 1004 date: 01/22/2007
CPU:       Dual core Intel Core2 6600 (-MCP-) speed: 2394 MHz (max)
Graphics:  Card: NVIDIA GT216 [GeForce GT 220]
           Display Server: X.Org 1.17.3 drivers: nouveau (unloaded: fbdev,vesa) Resolution: 1920x1080
           GLX Renderer: Gallium 0.4 on NVA5 GLX Version: 3.0 Mesa 11.0.6
Network:   Card-1: Marvell 88E8056 PCI-E Gigabit Ethernet Controller driver: sky2
           Card-2: Marvell 88E8001 Gigabit Ethernet Controller driver: skge
           Card-3: Realtek RTL8187 Wireless Adapter driver: rtl8187
Drives:    HDD Total Size: 750.1GB (11.2% used)
Info:      Processes: 216 Uptime: 1:07 Memory: 720.4/992.0MB Client: Shell (bash) inxi: 2.2.28 

```


Regards.

Can confirm Libre Office goes absolutely beserk while trying to load a 6MB PDF file, grey outs (in and out) chunky resizing and asks for password. Takes superlong timeto load on fast machine. Notice on much older machine.

```

ventrical@ventrical-MS-7850:~$ inxi -b
System:    Host: ventrical-MS-7850 Kernel: 4.3.0-2-generic x86_64 (64 bit)
           Desktop: Unity Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: P5LD2 v: Rev 1.xx
           Bios: American Megatrends v: 0901 date: 12/15/2005
CPU:       Dual core Intel Pentium D (-MCP-) speed: 3831 MHz (max)
Graphics:  Card: NVIDIA GF119 [GeForce GT 610]
           Display Server: X.Org 1.17.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9 GLX Version: 3.0 Mesa 11.0.6
Network:   Card: Marvell 88E8053 PCI-E Gigabit Ethernet Controller
           driver: sky2
Drives:    HDD Total Size: 120.0GB (8.4% used)
Info:      Processes: 202 Uptime: 13 min Memory: 965.1/2000.3MB
           Client: Shell (bash) inxi: 2.2.28 
ventrical@ventrical-MS-7850:~$ 

```

Also asks for password and will not cancel job.

---

### Post by Irihapeti on 2015-12-08
Up until now, Xenial has been almost boringly stable on my EeePC 900. However, kernel 4.3 has changed the situation.

I get what looks like some kind of overlay on most of the screen, though the bit that's still visible seems to appear normal. I can log in and do limited stuff by typing blind.

I was therefore able to get this:
```

System:    Host: ja-laptop Kernel: 4.3.0-2-generic i686 (32 bit)
           Desktop: Openbox 3.6.1 Distro: Ubuntu 16.04 xenial
Machine:   System: ASUSTeK product: 900 v: 0405
           Mobo: ASUSTeK model: 900 v: x.xx
           Bios: American Megatrends v: 1006 date: 03/03/2009
CPU:       Single core Intel Celeron M (-UP-) speed: 900 MHz (max)
Graphics:  Card: Intel Mobile 915GM/GMS/910GML Express Graphics Controller
           Display Server: X.Org 1.17.3 driver: intel
           Resolution: 1024x600@59.52hz
           GLX Renderer: Mesa DRI Intel 915GM x86/MMX/SSE2
           GLX Version: 1.4 Mesa 11.0.6
Network:   Card-1: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express)
           driver: ath5k
           Card-2: Qualcomm Atheros Attansic L2 Fast Ethernet driver: atl2
Drives:    HDD Total Size: 116.1GB (4.0% used)
Info:      Processes: 129 Uptime: 2 min Memory: 79.4/991.9MB
           Client: Shell (bash) inxi: 2.2.28 

```

Does this look like an existing bug, or should I report a new one?


I know the machine is a fair few years old now, but I don't want to throw it away just yet..... :(

[ATTACH=CONFIG]266057[/ATTACH]

---

### Post by ventrical on 2015-12-09
> **Irihapeti said:**
> Up until now, Xenial has been almost boringly stable on my EeePC 900. However, kernel 4.3 has changed the situation.


[ATTACH=CONFIG]266057[/ATTACH]

I have an earlier model (2007) that sudodus helped me put a lubuntu install of trusty on. I had to use the force pae option. Since it has been sitting there not doing much work I decided to upgrade (currently upgrading) it to xenial and see what happens with the kernel. It will also be a good test for an upgrade of this kind. I'll post results.
Edit:   I fubarred the install . (sh. tainted) etc .. verbose . Can't use recovery. Can't get to terminal. I should have 

```

apt-get update
apt-get upgrade

```

while in cli.. but no .. I got to use gnome terminal :(


Regards..

---

### Post by ventrical on 2015-12-09
@ Irihapeti

 I was able to get that kernel to work just fine in (lubuntu) live mode from daily xenial ISO with USB on my EeePC Series 701 but I can't install it because Ubiquity has 4.6 GB hdd limit and the ssd is surface mounted on that series.

Regards..

---

### Post by Irihapeti on 2015-12-09
Thanks. I have to go out now, but I might try a live version later and see what happens.

---

### Post by grahammechanical on 2015-12-09
I got fed up waiting for the 4.3 kernel even with proposed enabled so I ran dist-upgrade. On reboot I got low screen resolution and login bounce back. I was able to load the 4.2 kernel and change from Nvidia 304 to 340 driver and now I have 4.3 kernel on this install of Xenial. Nouveau works OK also.

It is strange how a video driver can cause login bounce back.

---

### Post by Irihapeti on 2015-12-10
Thanks to ventrical who suggested running a live version. I downloaded the Xubuntu daily and booted from that. No problems.

I'd love to know what the heck is causing the issue on the other version, as I'd prefer not to do a full reinstall.

---

### Post by ventrical on 2015-12-10
> **Irihapeti said:**
> Thanks to ventrical who suggested running a live version. I downloaded the Xubuntu daily and booted from that. No problems.

I'd love to know what the heck is causing the issue on the other version, as I'd prefer not to do a full reinstall.

I am still working on this.   I had noticed in the past that some intel drivers on certain machines have got blacklisted or obsoleted through update/upgrades. This is not always a kernel problem but a driver problem. Although it appears to work flawlessly in 'live' mode from USB boot, once it is installed it behaves differently. My opinion is that during update/upgrades the jockeying algorithms are not always choosing the correct drivers or replacing perfectly good ones to satisfy some other depend .

Regards..

---

### Post by ventrical on 2015-12-10
> **grahammechanical said:**
> I got fed up waiting for the 4.3 kernel even with proposed enabled so I ran dist-upgrade. On reboot I got low screen resolution and login bounce back. I was able to load the 4.2 kernel and change from Nvidia 304 to 340 driver and now I have 4.3 kernel on this install of Xenial. Nouveau works OK also.

It is strange how a video driver can cause login bounce back.

It is a non-verbose method of displaying that the driver is not be loaded or being loaded correctly. There seems to be a problem recently in this cycle where I have had to use:

```

sudo -H dpkg --configure -a

```

several times after an update/upgrade.  Update/upgrades appear to be installing but there are not installing and setting up completely and leaving broken depends. 

 In the hardware world video graphics adapters are always adding new features and so driver devs have to write in routines that works with newer hardware. Some times other segments of programs have to be re-written and the older hardware gets obsoleted because it cannot bind with a newer kernel at first run-up or to this effect but as you and I know .. it mostly gets ironed out eventually.

Regards..

---

### Post by ventrical on 2015-12-10
> **Irihapeti said:**
> Up until now, Xenial has been almost boringly stable on my EeePC 900. However, kernel 4.3 has changed the situation.

I get what looks like some kind of overlay on most of the screen, though the bit that's still visible seems to appear normal. I can log in and do limited stuff by typing blind.

I was therefore able to get this:
```

System:    Host: ja-laptop Kernel: 4.3.0-2-generic i686 (32 bit)
           Desktop: Openbox 3.6.1 Distro: Ubuntu 16.04 xenial
Machine:   System: ASUSTeK product: 900 v: 0405
           Mobo: ASUSTeK model: 900 v: x.xx
           Bios: American Megatrends v: 1006 date: 03/03/2009
CPU:       Single core Intel Celeron M (-UP-) speed: 900 MHz (max)
Graphics:  Card: Intel Mobile 915GM/GMS/910GML Express Graphics Controller
           Display Server: X.Org 1.17.3 driver: intel
           Resolution: 1024x600@59.52hz
           GLX Renderer: Mesa DRI Intel 915GM x86/MMX/SSE2
           GLX Version: 1.4 Mesa 11.0.6
Network:   Card-1: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express)
           driver: ath5k
           Card-2: Qualcomm Atheros Attansic L2 Fast Ethernet driver: atl2
Drives:    HDD Total Size: 116.1GB (4.0% used)
Info:      Processes: 129 Uptime: 2 min Memory: 79.4/991.9MB
           Client: Shell (bash) inxi: 2.2.28 

```

Does this look like an existing bug, or should I report a new one?


I know the machine is a fair few years old now, but I don't want to throw it away just yet..... :(

[ATTACH=CONFIG]266057[/ATTACH]

I was able to emulate this bug on my machine using the 4.3.x.x kernel but I do not think it is kernel bug. It is video modeset bug. So I am now going to try to re-install same lubuntu issue using nomodeset and see if that corrects.

---

### Post by ventrical on 2015-12-10
> **Irihapeti said:**
> Thanks to ventrical who suggested running a live version. I downloaded the Xubuntu daily and booted from that. No problems.

I'd love to know what the heck is causing the issue on the other version, as I'd prefer not to do a full reinstall.

nomodeset was the solution but I am assuming it can be fixed in recovery mode somehow.

```

ventrical@ventrical-701:~$ inxi -Fxz
System:    Host: ventrical-701 Kernel: 4.3.0-2-generic i686 (32 bit gcc: 5.2.1)
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 16.04 xenial
Machine:   System: ASUSTeK product: 701 v: x.x
           Mobo: ASUSTeK model: 701 v: x.xx
           Bios: American Megatrends v: 0401 date: 10/17/2007
CPU:       Single core Intel Celeron M (-UP-) cache: 512 KB
           flags: (pae sse sse2) bmips: 1260 speed: 630 MHz (max)
Graphics:  Card: Intel Mobile 915GM/GMS/910GML Express Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.17.3 drivers: fbdev,intel (unloaded: vesa)
           Resolution: 640x480@73.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
           GLX Version: 3.0 Mesa 11.0.6 Direct Rendering: Yes
Audio:     Card Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.3.0-2-generic
Network:   Card-1: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express)
           driver: ath5k bus-ID: 01:00.0
           IF: wlp1s0 state: down mac: <filter>
           Card-2: Qualcomm Atheros Attansic L2 Fast Ethernet
           driver: atl2 v: 2.2.3 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 4.0GB (75.1% used)
           ID-1: /dev/sda model: SILICONMOTION_SM size: 4.0GB temp: 0C
Partition: ID-1: / size: 3.2G used: 2.4G (80%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 0.53GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 50.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 1390
Info:      Processes: 136 Uptime: 2 min Memory: 125.2/485.4MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.3.421) inxi: 2.2.28 
ventrical@ventrical-701:~$ 


```

edit:

Notice the llvmpipe in video driver script. so the previous driver has been replaced.. probably this due to compositor development.

regards..

---

### Post by zika on 2015-12-10
If nomodeset is a solution then recovery mode is not needed. Simple edit of boot line in grub live...
Also, I suspect that all that could be solved via tty reached by using```
systemd.unit=multi-user.target
```in kernel boot line so that GUI does not try to start, instead of going to recovery mode, which might, at the end be the same thing... ;)

---

### Post by ventrical on 2015-12-10
How to edit in nomodeset into grub.

[http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

---

### Post by ventrical on 2015-12-10
> **zika said:**
> If nomodeset is a solution then recovery mode is not needed. Simple edit of boot line in grub live...
Also, I suspect that all that could be seolved via tty reached by using```
systemd.unit=multi-user.target
```in kernel boot line so that GUI does not try start, instead of going to recovery mode, which might, at the end be the same thing... ;)

Thnx ! :)

---

### Post by Irihapeti on 2015-12-10
Thanks. I'm able to get to a working desktop.

Only thing is, the resolution is wrong, displaying at 600*800 instead of 600*1024.

How do I reset that (permanently) using the command line? The last time I did that was when xorg.conf was a thing and I know it's different nowadays.

Yes, I've tried Googling, but there's just so much out-of-date junk out there, it's frustrating.

---

### Post by ventrical on 2015-12-10
@Irihapeti
What is results of :

```

xrandr -q

```

ie;

```

Screen 0: minimum 320 x 200, current 1440 x 900, maximum 32767 x 32767
VGA1 connected primary 1440x900+0+0 (normal left inverted right x axis y axis) 410mm x 256mm
   1440x900       59.9*+   75.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
ventrical@ventrical-MS-7798:~$ 



```

as per...

[http://askubuntu.com/questions/561820/setting-best-display-mode-as-default](http://askubuntu.com/questions/561820/setting-best-display-mode-as-default)

---

### Post by Irihapeti on 2015-12-10
Logged in after booting with nomodeset, I see:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600       75.00* 
```

... which doesn't look very useful.

I could probably manage to get the non-nomodeset output, if it's going to help.

---

### Post by Irihapeti on 2015-12-10
Here's the output without nomodeset:

```

Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x600      59.52*+
   800x600       60.32    56.25  
   640x480       59.94  
VGA1 unknown connection (normal left inverted right x axis y axis)
   1360x768      59.80  
   1152x864      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480       59.94 +
   640x480       59.94 +
   1024x768      59.94  
   800x600       59.94  

```

---

### Post by ventrical on 2015-12-10
Sounds about right.

---

### Post by Cavsfan on 2015-12-14
> **grahammechanical said:**
> I got fed up waiting for the 4.3 kernel even with proposed enabled so I ran dist-upgrade. On reboot I got low screen resolution and login bounce back. I was able to load the 4.2 kernel and change from Nvidia 304 to 340 driver and now I have 4.3 kernel on this install of Xenial. Nouveau works OK also.

It is strange how a video driver can cause login bounce back.

I had sort of the same thing happen to me: low resolution and only when I went from nvidia 304 to 340 driver did it fix itself. Since I seen it "should" work with my card and no problems yet with the video.

Didn't really have any login bounce back.

I was wondering if today's update to the 4.3 kernel helped anyone?

---

### Post by Irihapeti on 2015-12-14
> **Cavsfan said:**
> ...I was wondering if today's update to the 4.3 kernel helped anyone?

Unfortunately, it didn't make any difference here. :(

Is there a bug report for the Intel graphics problem?

---

### Post by QDR06VV9 on 2015-12-14
> **Irihapeti said:**
> Unfortunately, it didn't make any difference here. :(

Is there a bug report for the Intel graphics problem?
Hi Irihapeti Acer 5750 Laptop with Intel Graphics 3000 series With 1074 Mem...
No issue's here..
I am beginning to think that older hardware and graphic chips are not loved anymore:( at least with the newer kernels.(4. and up)
Kind Regards

---

### Post by Cavsfan on 2015-12-14
As you can see from my signature I have a system purchased in 2009. :p

Absolutely no problems here after I did what I posted in post [#18]("http://ubuntuforums.org/showthread.php?t=2305058&page=2&p=13402719#post13402719") of this thread.

---

### Post by QDR06VV9 on 2015-12-14
Well all along I thought we were talking about the
> [COLOR=#000000]*Is there a bug report for the Intel graphics problem?*[/COLOR]
:p
Hey there Cavsfan..

---

### Post by Irihapeti on 2015-12-14
> **runrickus said:**
> Hi Irihapeti Acer 5750 Laptop with Intel Graphics 3000 series With 1074 Mem...
No issue's here..
I am beginning to think that older hardware and graphic chips are not loved anymore:( at least with the newer kernels.(4. and up)
Kind Regards

In my case, it's not that the Intel graphics chip has been abandoned. If I fire up a daily live USB, the thing works absolutely fine. But when I install to disk (external drive), Bad Things happen and I get the error shown in my first post in this thread.

We just need to get the configuration on the live USB to be installed to disk, without alteration. That ought to be possible, somehow.

Or at least, that's what my granny brain thinks. :)

---

### Post by QDR06VV9 on 2015-12-14
> **Irihapeti said:**
> In my case, it's not that the Intel graphics chip has been abandoned. If I fire up a daily live USB, the thing works absolutely fine. But when I install to disk (external drive), Bad Things happen and I get the error shown in my first post in this thread.

**We just need to get the configuration on the live USB to be installed to disk**, without alteration. That ought to be possible, somehow.

Or at least, that's what my granny brain thinks. :)
We will see what we can up with, But yes it dose sound like a doable task..
I also have an Old Shuttle BareBones box with a Nvidia 7500 with 512 ram and Athlon 3000+ with 2 Gigs System Ram and anything with the 4.0 kernels will not work
on this little box..
I remember ventrical saying something along the lines of composting still being worked on.
With the hardware i have to test with, Video chips with less than 800MB for ram is lacking.
So i guess we wait to see:D 
Kind Regards
**EDIT: have you tried this yet..**
```
[FONT=monospace]xset dpms force off[/FONT]
```

---

### Post by Irihapeti on 2015-12-14
> **runrickus said:**
> 
**EDIT: have you tried this yet..**
```
[FONT=monospace]xset dpms force off[/FONT]
```

When do I do this? Part of the grub command line?

(Sorry if that sounds rather a basic /silly question - I haven't done much testing lately.)


Incidentally, if I boot using the last 4.2 kernel (which I left installed), the video is fine. That's with everything else being the latest.

---

### Post by QDR06VV9 on 2015-12-15
> **Irihapeti said:**
> When do I do this? Part of the grub command line?

We can just make a Script and a cron job
```


#!/bin/bash
export DISPLAY=:0.0


if [ $# -eq 0 ]; then
  echo usage: $(basename $0) "on|off|status"
  exit 1
fi


if [ $1 = "off" ]; then
  echo -en "Turning monitor off..."
  xset dpms force off
  echo -en "done.\nCheck:"
  xset -q|grep "Monitor is"
elif [ $1 = "on" ]; then
  echo -en "Turning monitor on..."
  xset dpms force on
  echo -en "done.\nCheck:"
  xset -q|grep "Monitor is"
elif [ $1 = "status" ]; then
  xset -q|sed -ne 's/^[ ]*Monitor is //p'
else
  echo usage: $(basename $0) "on|off|status"
fi

```
The credit gose to Rinzwind from Ask Ubuntu [http://askubuntu.com/questions/61291/how-to-permanently-disable-monitor-power-saver-using-the-command-line](http://askubuntu.com/questions/61291/how-to-permanently-disable-monitor-power-saver-using-the-command-line)
Save this script in something like /usr/bin, give it a name (like switch_dpms) and make it executable with chmod 664 /usr/bin/switch_dpm.


Now all you need to do is add it to a cron job. So open your crontab file with:
```
crontab -e
```
and add this at the bottom:
```
@reboot /usr/bin/switch_dpms off

```
Every reboot it will turn dpms to off and you can also turn it on from commandline by doing** "/usr/bin/switch_dpms on" **or check its status with "**/usr/bin/switch_dpms status"**.
> (Sorry if that sounds rather a basic /silly question - I haven't done much testing lately.)
Don't be silly you are Family Here!!:D
> Incidentally, if I boot using the last 4.2 kernel (which I left installed), the video is fine. That's with everything else being the latest.
This is what this is supposed to do..
**Bare in mind I have not had to use this myself..**

Fingers Crossed

---

### Post by zika on 2015-12-15
Using xset is restricted to having X running... Isn't it?
In the very thread You gave there are better solutions offered...
Not to mention some other... At least simpler, aside everything else...

---

### Post by QDR06VV9 on 2015-12-15
> **zika said:**
> Using xset is restricted to having X running... Isn't it?
In the very thread You gave there are better solutions offered...
Not to mention some other... At least simpler, aside everything else...
You Read my mind:D
Like this one might be the best just to test..
This will work. Open terminal in the etc/xdg/autostart directory. Issue this command:
```
sudo gedit nodpms.desktop
```
Hit enter, you will have to input your password. Gedit will open, copy and pasted the following code in and then save.
```
[Desktop Entry]Type=Application
Exec=xset -dpms
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=nodpms
Name=nodpms
Comment[en_US]=
Comment=
```
Issue this in the still open terminal:
```
sudo gedit noscreenblank.desktop
```
> Exec=xset s offHidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=noscreenblank
Name=noscreenblank
Comment[en_US]=
Comment=
Close the terminal. Open the file browser and navigate to the etc/xdg/autostart directory. Ensure that the files, nodpms.desktop and noscreenblank.desktop are there. If so, close everything and then reboot.


After reboot you can run an xset q command in terminal and see that dpms and screen blanking are turned off.

---

### Post by ventrical on 2015-12-15
> **runrickus said:**
> Hi Irihapeti Acer 5750 Laptop with Intel Graphics 3000 series With 1074 Mem...
No issue's here..
I am beginning to think that older hardware and graphic chips are not loved anymore:( at least with the newer kernels.(4. and up)
Kind Regards

My two opinions is that there is a kernel binding problem with fresh install. This would be either with apt or ubiquity and (2.) that the jockeying routine is defaulting to llvmpipe or (bad)modeset which has something to do with the original sub_routines during install.  Yes .. duiring LIVE  USB it runs perfect , but upon hard install it reverts to scrappy. This is systemic across all variants and has been doing this the past 4 or 5 cycles. It is random and intermittent .  Why ? 

Regards..

---

### Post by Irihapeti on 2015-12-15
> **runrickus said:**
> You Read my mind:D
Like this one might be the best just to test..
This will work. Open terminal in the etc/xdg/autostart directory. Issue this command:
```
sudo gedit nodpms.desktop
```
Hit enter, you will have to input your password. Gedit will open, copy and pasted the following code in and then save.
```
[Desktop Entry]Type=Application
Exec=xset -dpms
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=nodpms
Name=nodpms
Comment[en_US]=
Comment=
```
Issue this in the still open terminal:
```
sudo gedit noscreenblank.desktop
```

Close the terminal. Open the file browser and navigate to the etc/xdg/autostart directory. Ensure that the files, nodpms.desktop and noscreenblank.desktop are there. If so, close everything and then reboot.


After reboot you can run an xset q command in terminal and see that dpms and screen blanking are turned off.

This seems to work in a Xubuntu install. Thanks.

I'd like to get it working in Openbox, which is my preferred DE/WM on the EeePC nowadays. Any ideas?

Personally, I'd prefer a script to be run before login. No idea where to put it, though. The one that runrickus posted earlier (from AskUbuntu) seems unnecessarily complicated - not sure whether I really need to be able to turn it on/off.

---

### Post by Irihapeti on 2015-12-18
Further update: I am able to avoid the problem by removing the line 
```
gfxmode $linux_gfx_mode
```
from grub

Now to figure out how to stop grub from including that line by default when it updates.

---

### Post by zika on 2015-12-19
> **Irihapeti said:**
> Further update: I am able to avoid the problem by removing the line 
```
gfxmode $linux_gfx_mode
```
from grub

Now to figure out how to stop grub from including that line by default when it updates.Change  /etc/grub.d/10_linux, $gfxpayload_dynamic(="1").

---

### Post by Irihapeti on 2015-12-19
> **zika said:**
> Change  /etc/grub.d/10_linux, $gfxpayload_dynamic(="1").

Thanks! Now I'm back in business.

---

### Post by Cavsfan on 2015-12-20
> **Irihapeti said:**
> Further update: I am able to avoid the problem by removing the line 
```
gfxmode $linux_gfx_mode
```
from grub

Now to figure out how to stop grub from including that line by default when it updates.

Here's one solution that will work forever, unless you remove a partition or add one.

[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Here is the contents of my custom grub file and I haven't had a problem with it in 6 years. 
Grub doesn't actually see past the 4th partition on your drive, it always gets the sdxy lines wrong on the 5th and subsequent partitions whether the 5th one is on the 1st extended partition or not.

```
#!/bin/sh
echo 1>&2 "Adding Arch Linux, Xubuntu Xenial Xerus 16.04 (devel) and Windows 10"
exec tail -n +4 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Arch Linux" {
    set root=(hd0,3)
        linux /boot/vmlinuz-linux root=/dev/sda3 rw quiet
        initrd /boot/initramfs-linux.img
}
menuentry "Arch Linux (Recovery Mode)" {
    set root=(hd0,3)
        linux /boot/vmlinuz-linux root=/dev/sda3 rw single
        initrd /boot/initramfs-linux.img
}
menuentry "Xubuntu Xenial Xerus 16.04 (devel)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}
menuentry "Xubuntu Xenial Xerus 16.04 (devel) (Recovery Mode)" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro recovery nomodeset
        initrd /initrd.img
}
menuentry "Windows 10" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1CFC7A8DFC7A60C6
    chainloader +1
}

```

Ranch Hand taught me this. 

Cheers

---

### Post by Irihapeti on 2015-12-20
@Cavsfan:

Thanks, I'd wondered about that as an option. Glad to know that it works.

---

### Post by Cavsfan on 2015-12-21
You're welcome! I didn't notice that Zika had already supplied a solution.

I've got my controlling grub on Arch and you can only change the font colors on the menu (mine is normal cyan and red highlight).
But, in Ubuntu you can set another item **color_normal** which is that which displays at the top above and below the menu.

On arch the **color_normal** is white but that's fine with me.

[[img]http://www.zimagez.com/miniature/20151027143535.jpg[/img]](http://www.zimagez.com/zimage/20151027143535.php)

I believe this started with Jaunty Jackalope 9.04 and I've used it ever since without one fail.

I did have an upstart option for Xenial but since the option to do anything but logout is grayed out, I deleted that and stick with systemd.

---

### Post by Irihapeti on 2015-12-21
I've experienced a kernel upgrade since I applied zika's solution and the fix has held, so I think I'll leave well enough alone.

I suppose I should report a bug. I noticed a similar bug from a couple of years back, but that one lapsed because of additional information not being provided.

---

### Post by QDR06VV9 on 2015-12-21
> **Irihapeti said:**
> I've experienced a kernel upgrade since I applied zika's solution and the fix has held, so I think I'll leave well enough alone.

I suppose I should report a bug. I noticed a similar bug from a couple of years back, but that one lapsed because of additional information not being provided.
Thanks for the update Irihapeti, These things can make a difference. Oh and thanks to zika as well;)

---

### Post by Cavsfan on 2015-12-22
> **runrickus said:**
> Thanks for the update Irihapeti, These things can make a difference. Oh and thanks to zika as well;)

Guess I've been demoted to chopped liver eh? :lolflag: :lolflag: :lolflag: 

[IMG]http://images.sodahead.com/polls/003817681/294721039_p_rodney_dangerfield_12_xlarge.jpeg[/IMG]

---

### Post by Irihapeti on 2015-12-22
Well, thanks to Cavsfan also for suggesting an alternative, which I might use on another Grub install. It saves having to keep up with which kernel version is currently installed on which system. :confused:

---

### Post by QDR06VV9 on 2015-12-22
> **Irihapeti said:**
> _**Well, thanks to Cavsfan also for suggesting an alternative, which I might use on another Grub install.**_ It saves having to keep up with which kernel version is currently installed on which system. :confused:
Well I guess if we have to..Good Job Cavsfan:KS

---

### Post by Irihapeti on 2015-12-22
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1528708](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1528708), in case anyone is interested.

Thanks to all for having averted another disaster chez Irihapeti. :D

(A disaster is having to abandon the Ubuntu family on one of my devices, or, worse yet, throw said device into the bin... :( )

---

### Post by Cavsfan on 2015-12-23
> **Irihapeti said:**
> Well, thanks to Cavsfan also for suggesting an alternative, which I might use on another Grub install. It saves having to keep up with which kernel version is currently installed on which system. :confused:

> **runrickus said:**
> Well I guess if we have to..Good Job Cavsfan:KS

Thanks! Yes, customizing the grub makes it much simpler, it just boots into the most current kernel and that's it's it.

Keeping one grub in control of all of the systems on one machine makes things much easier.
There is a way to do that mentioned in section 1.8 of the wiki and you install the ones you don't want to control your grub in the PBR (e.g. sda4) instead of the MBR (e.g. sda).

Cheers!:KS

---

### Post by Irihapeti on 2015-12-23
Only thing is, whether a given drive is /dev/sdc or /dev/sdd depends on how many are plugged in, so I need to use UUIDs.

I know there's a way of doing it - just trying to figure it out, in between other pre-Christmas things. :)

---

### Post by Cavsfan on 2015-12-23
> **Irihapeti said:**
> Only thing is, whether a given drive is /dev/sdc or /dev/sdd depends on how many are plugged in, so I need to use UUIDs.

I know there's a way of doing it - just trying to figure it out, in between other pre-Christmas things. :)

You don't need to use UUIDs with this method. It will still find other drives if you set it up that way in the **06_custom** file.

I have only one drive so I can't say I've done it but I have perfect confidence that it will work with just **_sdxy_** and **_hdn,n_** and no UUIDs.
Like this 2 per Ubuntu, Mint and a few other systems that use grub:
```
menuentry "Name of system blah, blah, blah" {
    set root=([COLOR=#ff0000]hd0,5[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=#ff0000]sda5[/COLOR] ro quiet splash
        initrd /initrd.img
}
menuentry "Name of system blah, blah, blah (Recovery Mode)" {
    set root=(hd[COLOR=#ff0000]0,5[/COLOR])
        linux /vmlinuz root=/dev/[COLOR=#ff0000]sda5[/COLOR] ro recovery nomodeset
        initrd /initrd.img
}
```

Arch is a little different just in the boot lines:
```
menuentry "Arch Linux" {
    set root=(hd[COLOR="#FF0000"]0,3[/COLOR])
        linux [COLOR="#FF0000"]/boot/vmlinuz-linux[/COLOR] root=/dev/[COLOR="#FF0000"]sda3[/COLOR] rw quiet
        initrd [COLOR="#FF0000"]/boot/initramfs-linux[/COLOR].img
}
menuentry "Arch Linux (Recovery Mode)" {
    set root=(hd[COLOR="#FF0000"]0,3[/COLOR])
        linux [COLOR="#FF0000"]/boot/vmlinuz-linux[/COLOR] root=/dev/[COLOR="#FF0000"]sda3[/COLOR] rw single
        initrd [COLOR="#FF0000"]/boot/initramfs-linux[/COLOR].img
}
```

---

### Post by Irihapeti on 2015-12-24
I've ended up doing this, modified from something I found on an Arch Linux forum:

```

menuentry "Xubuntu Xenial Xerus 16.04 (devel) on SD card" {
    set root_uuid=<UUID of partition>
    search --no-floppy --fs-uuid $root_uuid --set=root
        linux /vmlinuz root=UUID=$root_uuid ro quiet splash
        initrd /initrd.img
}

menuentry "Xubuntu Xenial Xerus 16.04 (devel) on HDD" {
    set root_uuid=<UUID of partition>
    search --no-floppy --fs-uuid $root_uuid --set=root
        linux /vmlinuz root=UUID=$root_uuid ro quiet splash
        initrd /initrd.img
}

```

Seems to work, regardless of whether I have one or both of the devices plugged in.

---

