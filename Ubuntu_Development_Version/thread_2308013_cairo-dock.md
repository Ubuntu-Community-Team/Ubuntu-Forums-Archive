---
title: "cairo-dock"
date: 2015-12-30
forum: Ubuntu Development Version
---

### Post by valereguerin on 2015-12-30
Hello community,

When i click on : quick directory  in cairo, the list of directory open but i can't do anything sometimes the machine freeze just possible ctrl+alt+backspace killing xserveur !

AND i put the monitor applet on the desk but i can't move it, click right or left on....nothing happen....SORRY IT 'S MONITOR SCREENLET APPLET ! not Cairo
 

System:    Host: Sniper-one Kernel: 4.3.0-5-generic x86_64 (64 bit) Desktop: Gnome 3.18.2
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award v: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 930 (-HT-MCP-) speed: 2798 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
           Display Server: X.Org 1.17.3 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.6.2) GLX Version: 3.0 Mesa 11.0.8

---

### Post by valereguerin on 2015-12-30
hello,

when i right click on cairo icon choose cairo-dock and quick masking, maybe it do maybe not has it want !:p

---

### Post by cariboo on 2015-12-30
merged two threads on the same subject.

---

### Post by ventrical on 2015-12-31
> **valereguerin said:**
> Hello community,

When i click on : quick directory  in cairo, the list of directory open but i can't do anything sometimes the machine freeze just possible ctrl+alt+backspace killing xserveur !

AND i put the monitor applet on the desk but i can't move it, click right or left on....nothing happen....
 

System:    Host: Sniper-one Kernel: 4.3.0-5-generic x86_64 (64 bit) Desktop: Gnome 3.18.2
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award v: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 930 (-HT-MCP-) speed: 2798 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
           Display Server: X.Org 1.17.3 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.6.2) GLX Version: 3.0 Mesa 11.0.8


"> DRM 2.43.0, LLVM 3.6.2) GLX Version: 3.0 Mesa 11.0.8

Something does not look right with this driver. If cario-dock is running on llvmpipe then it is sure to have performance problems. My experience with cario-dock and aTI cards has always presented an eventual unstable desktop.

Regards..

edit:

Run,

```

lspci

```

 in terminal and post results.

[http://www.glx-dock.org/](http://www.glx-dock.org/)

---

### Post by valereguerin on 2016-01-06
```
freeman@Sniper-one:~$ lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:10.0 PIC: Intel Corporation 7500/5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 13)
00:10.1 PIC: Intel Corporation 7500/5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 13)
00:11.0 PIC: Intel Corporation 7500/5520/5500 Physical and Link Layer Registers Port 1 (rev 13)
00:11.1 PIC: Intel Corporation 7500/5520/5500 Routing & Protocol Layer Register Port 1 (rev 13)
00:13.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 13)
00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:15.0 PIC: Intel Corporation 7500/5520/5500/X58 Trusted Execution Technology Registers (rev 13)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation SATA Controller [RAID mode]
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 SATA controller: Marvell Technology Group Ltd. Device 9182 (rev 10)
02:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series]
05:00.0 Audio device: Creative Labs EMU20k2 [X-Fi Titanium Series] (rev 03)
06:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
06:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
07:00.0 Power PC: Freescale Semiconductor Inc MPC8308 (rev 10)
08:00.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
3f:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
3f:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
3f:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
3f:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
3f:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
3f:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
3f:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
3f:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
3f:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
3f:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
3f:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
3f:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
3f:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
3f:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
3f:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
3f:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
3f:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
3f:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
3f:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)
```

```
freeman@Sniper-one:~$ inxi -b
System:    Host: Sniper-one Kernel: 4.3.0-5-generic x86_64 (64 bit)
           Desktop: Gnome 3.18.2 Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award v: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 930 (-HT-MCP-) speed: 2797 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
           Display Server: X.Org 1.17.3 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.6.2)
           GLX Version: 3.0 Mesa 11.0.8
Network:   Card: D-Link System DGE-528T Gigabit Ethernet Adapter
           driver: r8169
Drives:    HDD Total Size: 5847.3GB (23.4% used)
Info:      Processes: 356 Uptime: 22:03 Memory: 2526.8/7853.2MB
           Client: Shell (bash) inxi: 2.2.28
```

---

### Post by ventrical on 2016-01-06
```

           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.6.2)
      
``` 

Ok.. not necessarily I am correct on this one. Could be somthing else. I could test on my ATi card.

[https://www.phoronix.com/scan.php?page=news_item&px=LLVM-3.6.2-Released](https://www.phoronix.com/scan.php?page=news_item&px=LLVM-3.6.2-Released)

Keep updating.

Do you have ppas installed?

---

### Post by valereguerin on 2016-01-06
just now i'm installed the develop version unstable 3.4.1 for test it

```
freeman@Sniper-one:~$ inxi -b
System:    Host: Sniper-one Kernel: 4.3.0-5-generic x86_64 (64 bit) Desktop: Gnome 3.18.2
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award v: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 930 (-HT-MCP-) speed: 2798 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
           Display Server: X.Org 1.17.3 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.6.2) GLX Version: 3.0 Mesa 11.0.8

```

it's better but slow (but no crash)
i have installed llvm 3.6, after update full-upgrade and reboot it's the same thing

>                                                    [                                                      [IMG]http://ubuntuforums.org/customavatars/avatar77104_73.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=77104")                                                                                     [**[COLOR=#990303][B]cariboo**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=77104")      
                         [IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]                                                                    Caffeine Fueled                                                                   [IMG]http://ubuntuforums.org/images/rank_uf_admin_2013-07.png[/IMG]                                                                                                                                                                                            
                                      
             
                                                                                                       
DistroUbuntu Development Release

                                                           
                      
                                               **Re: cairo-dock**

                                                                                  [INDENT]                     merged two threads on the same subject.                 [/INDENT]
            
                         


sorry but i don't know how put it together:(:(:confused::confused: i post rarely on forums just when i can't find solutions...

always problem with "navigateur de fichier" ....

---

### Post by MikeMecanic on 2016-02-15
Was using Simple Dock last week and I didn't get any issues (GDM3).  Try it, maybe you’ll get better results.
Plus, Simple Dock is an easy app. that moves the original launcher on the left side to the bottom of the screen.  You must restart to enable Simple Dock . Unfortunately, I don’t know about Cairo.


[https://github.com/optimisme/gnome-shell-simple-dock](https://github.com/optimisme/gnome-shell-simple-dock)

---

### Post by valereguerin on 2016-02-28
Thanks for help

yes thanks ! but i love cairo-dock no need everything else (unity....., or another...)

i will try to discover where the probleme is...

Have a good day  Mike.

---

### Post by valereguerin on 2016-03-11
update & upgrade, and development version of cairo-dock
Now everything works fine

Just monitor don't want to move (it is in the middle of my screen! ) but it's not Cairo it's screenlet applet !

---

