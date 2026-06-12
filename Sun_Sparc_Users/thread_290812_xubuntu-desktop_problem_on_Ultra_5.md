---
title: "xubuntu-desktop problem on Ultra 5"
date: 2006-11-01
forum: Sun Sparc Users
---

### Post by trmentry on 2006-11-01
Hello,

I have an old Ultra 5 sitting here that I'm working on getting Ubuntu on.  I was able to get Ubuntu installed without issue in CLI mode (no DNS or LAMP).   I then wanted to get a GUI going and considering how old this thing is, I thought xubuntu would be fine.  So I did a 
apt-get install xubuntu-desktop

500+ packages later it was done.  

During the install of the packages it went asked about my screen resolutions.  So I chose a safe one of 1024x768 which I know my montior can handle.  The monitor is a new Compaq 17" FS7600 model.

After I rebooted the machine, the montior displays "Resolution out of sync" or some such.  IE - it can't display it.  However I know it can display 1024x768.  My issue is I can't figure out why the Ultra 5 is giving it such an odd resolution to bork it.  

Wehn Ubuntu installs its appears to be in a 1280x1024 resolution so I'm even more confused.

I've tried going in via the cd in rescue mode and editing the xorg.conf file and changing drivers to suncg6 and ati but still no joy.

Can someone please enlighten me as to what I'm doing wrong with this poor server?

TIA.


On a side note:  during the install of Ubuntu it asks what type of keyboard I have and Sun Type 5 isn't listed.  I chose Generic 104, is that ok or is there a better choice?

---

### Post by netztier on 2006-11-02
> **trmentry said:**
> Hello,

IOn a side note:  during the install of Ubuntu it asks what type of keyboard I have and Sun Type 5 isn't listed.  I chose Generic 104, is that ok or is there a better choice?

Paradoxical as it might seem, it still is correct. The 2.6.x series kernels have some internal mappings for the keycodes coming from the SUN keyboards, so yes, selecting a plain standard pc104/pc105 keyboard is *correct*!

Same is true for the configuration of X.org. Just don't select any of the sun keyboard options or you'll end up with garbled keys.

regards

Marc

---

### Post by netztier on 2006-11-02
> **trmentry said:**
> 
After I rebooted the machine, the montior displays "Resolution out of sync" or some such.  IE - it can't display it.  However I know it can display 1024x768.  My issue is I can't figure out why the Ultra 5 is giving it such an odd resolution to bork it.  


Hm, maybe it's just defaulting to too a high vertical refresh rate.

This should help: in your /etc/X11/xorg.conf, make sure that
in the "Monitor" section, there are settings for the ranges of HorizSync  (in kHz) and VertRefresh (in Hz) that match your monitor's specs. This should look somewhat like this:

```
Section "Monitor"
    Identifier      "Default Monitor"
    ...
    HorizSync       31-64
    VertRefresh     43-60
    ...
EndSection
```


> **trmentry said:**
> 
Wehn Ubuntu installs its appears to be in a 1280x1024 resolution so I'm even more confused.


A bit of text from [Gentoo's SPARC FAQ]("http://www.gentoo.org/doc/en/gentoo-sparc-faq.xml") might clarify things a bit:

```
[COLOR="Blue"]I have a CRT/LCD monitor attached to my SPARC that 
selects a resolution my monitor can't handle when the 
kernel boots. How do I get a visible and/or non-distorted 
display on my monitor?[/COLOR]

This problem is a result of the framebuffer support the 
Linux kernel loads at boot time, and the modelines 
available on SPARC systems. Here we will assume your 
monitor and video card will agree on a resolution of 
1024 by 768 at a refresh rate of 60 Hz. In OBP, you can 
set the resolution by adjusting the setting for 
output-device. To view the current setting, use the 
command: 

[COLOR="DarkGreen"]**Code Listing 2.1: View current settings**
 
ok printenv output-device

<output-device>        <screen>          <screen>[/COLOR] 

Now, to set this so it will start the display 
using the above mentioned resolution, we will 
use the setenv command as follows: 

[COLOR="DarkGreen"]**Code Listing 2.2: Setting display**
 
ok> setenv output-device screen:r1024x768x60
output-device =       screen:r1024x768x60[/COLOR] 

In order for this to take effect, you will need 
to reset the machine: 

[COLOR="DarkGreen"]**Code Listing 2.3: Resetting the machine** 
ok> reset[/COLOR] 

Additionally, for users using the onboard video 
card based on the ATI Mach64 chipset (Ultra 5/10 
and Blade 100/150), you will want to append the 
following to your kernel boot options: 

[COLOR="darkgreen"]**Code Listing 2.4: Appending a kernel boot option** 
video=atyfb:1024x768@[/COLOR]60
 

If you are booting from SILO, you can append the 
above string onto the end of a given boot image. 

```

I think you can skip the latest part with the kernel boot option.

> **trmentry said:**
> 
I've tried going in via the cd in rescue mode and editing the xorg.conf file and changing drivers to suncg6 and ati but still no joy.


If the machine does not hardlock but it's just the monitor going dark, you shouldn't have to boot rescue for that. Wait a little until you can assume that X has started and if it were visible the GDM login sceen would show up on screen, then hit **[FONT="Courier New"]Crtl-Alt-F1[/FONT]**. This will bring you back to a normal tty where you can login into text mode and edit xorg.conf from there. Afterwards, you can reboot the machine or switch back to X with **[FONT="Courier New"]Alt-F7[/FONT]** (yes, Alt-F7, not Ctrl-Alt-F7) and kill/restart X.org with Crtl-Alt-Backspace.

For an Ulta5, stick with the **ati** driver, it definitely is the one to use. Be aware though, that it probably won't be able to do 24bit colors at 1280x1024 because of video memory limitations. My Ultra 5 runs X.org in 16bit color mode perfectly at 1280x1024 at 60Hz, you'll need to change the DefaultDepth setting in xorg.conf's screen section.

I'll post my U5's xorg.conf within the next few days. The machine is powered-down and sitting in a corner...

regards

Marc

---

### Post by trmentry on 2006-11-02
Thank you for the info.  I had forgotten about the ctrl-alt-f1 to get back to cli.

Anyway... I logged on and checked my xorg.conf file and its Horizontal and Vertical values were correct.  I told it to use 16 bit mode at 1280x1024.

I type 'startx' at the prompt and this is what I get after the screen flickers.


```

Fatal server error:
xf06MapPciMem: Could not mmap PCI memory [base=0xe0008000, hostbase=ox300080000, size=2000] (Inappropriate ioctl for device)

XI0: fatal IO error 54 (Connection reset by peer) on X server ":0.0" after 0 requests *0 known processed) with 0 events remaining.

```


Here is a copy of my xorg.conf file.  

```

chris@dagobah:~$ more /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "ati"
        BusID           "PCI:1:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "115
2x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "115
2x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "115
2x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "115
2x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "115
2x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "115
2x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
```


Any ideas?  

Thanks again.

---

### Post by netztier on 2006-11-02
> **trmentry said:**
> Any ideas?

Hm. What does the output of /var/log/Xorg.0.log look like? Can you attach it to a posting, 
along with the outputs of lspci and dmesg (right after boot)?

regards

Marc

---

### Post by trmentry on 2006-11-02
> **netztier said:**
> Hm. What does the output of /var/log/Xorg.0.log look like? Can you attach it to a posting, 
along with the outputs of lspci and dmesg (right after boot)?




Sure thing.  

```

root@dagobah:~# dmesg
[    0.000000] PROMLIB: Sun IEEE Boot Prom 'OBP 3.11.12 1998/05/19 11:30'
[    0.000000] PROMLIB: Root node compatible: 
[    0.000000] Linux version 2.6.17-10-sparc64 (root@artigas) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 17:04:28 UTC 2006 (Ubuntu 2.6.17-10.33-sparc64)
[    0.000000] ARCH: SUN4U
[    0.000000] Ethernet address: 08:00:20:9c:78:2c
[    0.000000] On node 0 totalpages: 31577
[    0.000000]   DMA zone: 31577 pages, LIFO batch:7
[    0.000000] CPU[0]: Caches D[sz(16384):line_sz(32)] I[sz(16384):line_sz(32)] E[sz(262144):line_sz(64)]
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/hda2 ro quiet splash
[    0.000000] PID hash table entries: 1024 (order: 10, 8192 bytes)
[    8.098680] Console: colour dummy device 80x25
[    8.100450] Dentry cache hash table entries: 32768 (order: 5, 262144 bytes)
[    8.102235] Inode-cache hash table entries: 16384 (order: 4, 131072 bytes)
[    8.125863] Memory: 250112k available (2424k kernel code, 960k data, 160k init) [fffff80000000000,000000001ff44000]
[    8.206014] Calibrating delay using timer specific routine.. 540.40 BogoMIPS (lpj=1080805)
[    8.206384] Security Framework v1.0.0 initialized
[    8.206451] SELinux:  Disabled at boot.
[    8.206573] Mount-cache hash table entries: 512
[    8.208518] checking if image is initramfs... it is
[   11.873707] Freeing initrd memory: 4612k freed
[   11.876925] NET: Registered protocol family 16
[   11.879910] PCI: Probing for controllers.
[   11.882738] PCI: Found SABRE, main regs at 000001fe00000000
[   11.882771] SABRE: Shared PCI config space at 000001fe01000000
[   11.887616] SABRE: DVMA at c0000000 [20000000]
[   11.895231] PCI0(PBMA): Bus running at 33MHz
[   11.897983] PCI-IRQ: Routing bus[ 1] slot[ 1] to INO[21]
[   11.898263] PCI-IRQ: Routing bus[ 1] slot[ 2] to INO[0f]
[   11.898498] PCI-IRQ: Routing bus[ 1] slot[ 3] to INO[20]
[   11.898530] PCI0(PBMB): Bus running at 33MHz
[   11.898750] ebus0: [auxio] [power] [SUNW,pll] [se] [su] [su] [ecpp] [fdthree] [eeprom] [flashprom] [SUNW,CS4231]
[   11.904687] power: Control reg at 000001fff1724000 ... powerd running.
[   11.909647] usbcore: registered new driver usbfs
[   11.910162] usbcore: registered new driver hub
[   11.914512] NET: Registered protocol family 2
[   11.950495] IP route cache hash table entries: 2048 (order: 1, 16384 bytes)
[   11.951426] TCP established hash table entries: 8192 (order: 3, 65536 bytes)
[   11.951883] TCP bind hash table entries: 4096 (order: 2, 32768 bytes)
[   11.952119] TCP: Hash tables configured (established 8192 bind 4096)
[   11.952145] TCP reno registered
[   11.961342] audit: initializing netlink socket (disabled)
[   11.961428] audit(1162480027.240:1): initialized
[   11.961882] Total HugeTLB memory allocated, 0
[   11.962854] VFS: Disk quotas dquot_6.5.1
[   11.963063] Dquot-cache hash table entries: 1024 (order 0, 8192 bytes)
[   11.963651] Initializing Cryptographic API
[   11.963699] io scheduler noop registered
[   11.963755] io scheduler anticipatory registered
[   11.963803] io scheduler deadline registered
[   11.963908] io scheduler cfq registered (default)
[   11.965243] atyfb: 3D RAGE II+ (Mach64 GT) [0x4754 rev 0x9a]
[   11.967115] atyfb: 2M SGRAM (1:1), 14.31818 MHz XTAL, 200 MHz PLL, 67 Mhz MCLK, 67 MHz XCLK
[   12.072065] Console: switching to colour frame buffer device 160x64
[   12.072115] atyfb: fb0: ATY Mach64 frame buffer device on PCI
[   12.455758] rtc_init: no PC rtc found
[   12.456095] [drm] Initialized drm 1.0.1 20051102
[   12.471074] su0 at 0x000001fff13062f8 (irq = 5,7ea) is a 16550A
[   12.471192] su1 at 0x000001fff13083f8 (irq = 9,7e9) is a 16550A
[   12.471346] ttyS0 at MMIO 0x1fff1400000 (irq = 7961248) is a SAB82532 V3.2
[   12.473308] ttyS1 at MMIO 0x1fff1400040 (irq = 7961248) is a SAB82532 V3.2
[   12.475205] mice: PS/2 mouse device common for all mice
[   12.483680] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.487425] loop: loaded (max 8 devices)
[   12.487662] sunhme.c:v2.02 8/24/03 David S. Miller (davem@redhat.com)
[   12.489318] eth0: HAPPY MEAL (PCI/CheerIO) 10/100BaseT Ethernet 08:00:20:9c:78:2c 
[   12.490971] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   12.491017] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   12.492864] rtc_sun_init: Registered Mostek RTC driver.
[   12.492895] usbmon: debugfs is not available
[   12.493249] usbcore: registered new driver libusual
[   12.493603] usbcore: registered new driver usbhid
[   12.493633] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   12.494942] TCP bic registered
[   12.495001] NET: Registered protocol family 1
[   12.495062] NET: Registered protocol family 17
[   13.185267] input: Sun Type 5 keyboard as /class/input/input0
[   13.186632] input: Sun Mouse as /class/input/input1
[   14.157439] Capability LSM initialized
[    0.800820] CMD646: IDE controller at PCI slot 0000:01:03.0
[    0.800889] CMD646: chipset revision 3
[    0.800912] CMD646: chipset revision 0x03, MultiWord DMA Force Limited
[    0.800974] CMD646: 100% native mode on irq 5,7e0
[    0.801023]     ide0: BM-DMA at 0x1fe02c00020-0x1fe02c00027, BIOS settings: hda:pio, hdb:pio
[    0.801129]     ide1: BM-DMA at 0x1fe02c00028-0x1fe02c0002f, BIOS settings: hdc:pio, hdd:pio
[    0.801212] Probing IDE interface ide0...
[    1.090445] hda: WDC WD1200BB-00CJA1, ATA DISK drive
[    1.763280] ide0 at 0x1fe02c00000-0x1fe02c00007,0x1fe02c0000a on irq 5,7e0
[    1.763553] Probing IDE interface ide1...
[    2.162332] hdc: CRD-8240B, ATAPI CD/DVD-ROM drive
[    2.498289] ide1 at 0x1fe02c00010-0x1fe02c00017,0x1fe02c0001a on irq 5,7e0 (shared with ide0)
[    2.569574] hda: max request size: 128KiB
[    2.602483] hda: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=65535/16/63, (U)DMA
[    2.602541] hda: cache flushes not supported
[    2.602803]  hda: hda1 hda2 hda3 hda4
[    2.775893] hdc: ATAPI 24X CD-ROM drive, 128kB Cache
[    2.775946] Uniform CD-ROM driver Revision: 3.20
[    3.869923] kjournald starting.  Commit interval 5 seconds
[    3.870012] EXT3-fs: mounted filesystem with ordered data mode.
[   12.497581] Adding 747000k swap on /dev/disk/by-uuid/46afe17c-6eb8-474c-bee8-4aab5be3c8e7.  Priority:-1 extents:1 across:747000k
[   13.052888] EXT3 FS on hda2, internal journal
[   13.456180] NET: Registered protocol family 10
[   13.456878] lo: Disabled Privacy Extensions
[   13.458053] IPv6 over IPv4 tunneling driver
[   13.914358] eth0: Link is up using internal transceiver at 100Mb/s, Full Duplex.
[   14.040482] kjournald starting.  Commit interval 5 seconds
[   14.050482] EXT3 FS on hda3, internal journal
[   14.050520] EXT3-fs: mounted filesystem with ordered data mode.
[    6.702430] eth0: no IPv6 routers present
[   16.243995] ioctl32(Xorg:3189): Unknown cmd fd(5) cmd(40584606){00} arg(ff9fdb74) on /dev/fb0
[   16.246641] ioctl32(Xorg:3189): Unknown cmd fd(5) cmd(40184600){00} arg(ff9fdb7c) on /dev/fb0
[   16.774541] parport0: PC-style at 0x1fff13043bc (0x1fff13047bc), irq 7960960, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.886724] lp0: using parport0 (interrupt-driven).
[   17.087946] ppdev: user-space parallel port driver
[    3.832258] ioctl32(Xorg:3258): Unknown cmd fd(5) cmd(40584606){00} arg(ff139b74) on /dev/fb0
[    3.834884] ioctl32(Xorg:3258): Unknown cmd fd(5) cmd(40184600){00} arg(ff139b7c) on /dev/fb0
[    8.550011] ioctl32(Xorg:3335): Unknown cmd fd(5) cmd(40584606){00} arg(ff53db74) on /dev/fb0
[    8.552621] ioctl32(Xorg:3335): Unknown cmd fd(5) cmd(40184600){00} arg(ff53db7c) on /dev/fb0
[    7.963748] ioctl32(Xorg:3573): Unknown cmd fd(5) cmd(40584606){00} arg(ff93d864) on /dev/fb0
[    7.966380] ioctl32(Xorg:3573): Unknown cmd fd(5) cmd(40184600){00} arg(ff93d86c) on /dev/fb0
[    6.041194] ioctl32(Xorg:3598): Unknown cmd fd(5) cmd(40584606){00} arg(ffe15864) on /dev/fb0
[    6.043971] ioctl32(Xorg:3598): Unknown cmd fd(5) cmd(40184600){00} arg(ffe1586c) on /dev/fb0
[   16.799536] ioctl32(Xorg:3866): Unknown cmd fd(5) cmd(40584606){00} arg(ff01f824) on /dev/fb0
[   16.801397] ioctl32(Xorg:3866): Unknown cmd fd(5) cmd(40184600){00} arg(ff01f82c) on /dev/fb0
```

```

root@dagobah:~# lspci
00:00.0 Host bridge: Sun Microsystems Computer Corp. Ultra IIi
00:01.0 PCI bridge: Sun Microsystems Computer Corp. Simba Advanced PCI Bridge (rev 11)
00:01.1 PCI bridge: Sun Microsystems Computer Corp. Simba Advanced PCI Bridge (rev 11)
01:01.0 Bridge: Sun Microsystems Computer Corp. EBUS (rev 01)
01:01.1 Ethernet controller: Sun Microsystems Computer Corp. Happy Meal (rev 01)
01:02.0 VGA compatible controller: ATI Technologies Inc 3D Rage I/II 215GT [Mach64 GT] (rev 9a)
01:03.0 IDE interface: Silicon Image, Inc. PCI0646 (rev 03)

```


Xorg.0.log is attached to message it was a bit large I thought for cut and paste. :)

Thanks again for the help.

---

### Post by netztier on 2006-11-02
> **trmentry said:**
> 
```

root@dagobah:~# dmesg
[    0.000000] PROMLIB: Sun IEEE Boot Prom 'OBP [COLOR="Red"]3.11.12[/COLOR] 1998/05/19 11:30'

```


This needs updating, before anything else. Latest version available is 3.31. Best way to do is: install a minimal solaris on some IDE spare disk you have floating around and install the OBP upgrade from there. There's a few forum posts floating around about OBP upgrade and googleing for it might also help.

> **trmentry said:**
> 
```

[   11.965243] atyfb: 3D RAGE II+ (Mach64 GT) [0x4754 rev 0x9a]
[   11.967115] atyfb: 2M SGRAM (1:1), 14.31818 MHz XTAL, 200 MHz PLL, 67 Mhz MCLK, 67 MHz XCLK

```


It's only 2MBytes of video memory, not 4 as mine has. I'm not sure if this is enough fr 1280x1024 @ 16bit color depth.
regards

Marc



And, for the reference: my xorg.conf:

---

### Post by trmentry on 2006-11-02
> **netztier said:**
> This needs updating, before anything else. Latest version available is 3.31. Best way to do is: install a minimal solaris on some IDE spare disk you have floating around and install the OBP upgrade from there. There's a few forum posts floating around about OBP upgrade and googleing for it might also help.

hrmmm.. ok.  Never tried this before.  I have Solaris 10 sitting here and attempted to install it to get a minimal Solaris on there to upgrade with.

UPDATE:  I can't see to get Solaris 10 to install.  It keeps telling me:

```

ERROR: File system creation failed for / (c0t0d0s0)
ERROR: Could not check or create system critical file systems
ERROR: Could not update disks with new configuration
mkdir: "/a/var/sadm/launcher": Read-only file system

```

I'm a bit lost as to what to do next.  All I did was download Solaris 10 and burn to CDs and boot cd1 and follow the prompts.  Letting it auto partion the  disk. (120g)

Any ideas?


> 
It's only 2MBytes of video memory, not 4 as mine has. I'm not sure if this is enough fr 1280x1024 @ 16bit color depth.
regards


I tried 8 bit 1024x768 and it bombed too.  I'll get OBP upgraded first and then revisit this.  

Is it possible to slap a consumer PCI video card into this thing and use that instead of onboard?

---

### Post by trmentry on 2006-11-03
I finally got the OBP updated.  I reinstalled Ubuntu since I had just used that drive for teh Solaris install.  

Installed xubuntu-desktop

When it was done, I made sure I was set to 1024x768 16bit in xorg.conf and startx

I get the same fatal error as before.  I'm thinking that I'm not going to be abel to get x going on this thing.

---

### Post by lizardking on 2006-11-03
trmentry,
I think you have my  similar error..take a look at my unanswered post [Monitor resolution fails in xubuntu at start every time]("http://www.ubuntuforums.org/showthread.php?t=291649")

Do U have this problem?I think it 's a usplash problem...](*,)

---

### Post by jfinn on 2006-11-03
You might want to try entering the following line into your xorg.conf file under the Device Section.

"ReferenceClock"     "29.500MHz"

I'm not sure if it will make a difference on the Ultra5 but my Blade 150 was doing the same thing as yours before I made the change.  Worth a shot.

---

