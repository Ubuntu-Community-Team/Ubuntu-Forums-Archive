---
title: "AMDGPU broken after today's updates"
date: 2018-03-02
forum: Ubuntu Development Version
---

### Post by P-I H on 2018-03-02
Made these updates today
```
Start-Date: 2018-03-02  10:07:25
Commandline: /usr/sbin/synaptic
Requested-By: p-i (1000)
Install: 
libegl1:amd64 (0.2.999+git20170802-2, automatic), 
libwebpdemux2:amd64 (0.6.1-1, automatic), 
libgnome-desktop-3-17:amd64 (3.27.90-1ubuntu1,automatic), 
libglvnd0:amd64 (0.2.999+git20170802-2,automatic)
Upgrade: 
evince:amd64 (3.26.0-3, 3.27.91-1), 
gnome-control-center-data:amd64 (1:3.26.2-0ubuntu3, 1:3.26.2-0ubuntu5), 
gnome-settings-daemon-schemas:amd64 (3.26.2-0ubuntu2, 3.26.2-0ubuntu3), 
gnome-session:amd64 (3.26.1-0ubuntu9, 3.26.1-0ubuntu10), 
gnome-session-common:amd64 (3.26.1-0ubuntu9, 3.26.1-0ubuntu10), 
gir1.2-mutter-1:amd64 (3.26.2-1, 3.26.2-1build1), 
gnome-control-center:amd64 (1:3.26.2-0ubuntu3, 1:3.26.2-0ubuntu5), 
libevdocument3-4:amd64 (3.26.0-3, 3.27.91-1), 
gnome-software-plugin-snap:amd64 (3.26.6-0ubuntu1, 3.27.90-1ubuntu1), 
gnome-desktop3-data:amd64 (3.26.2-1ubuntu1, 3.27.90-1ubuntu1), 
gnome-software:amd64 (3.26.6-0ubuntu1, 3.27.90-1ubuntu1), 
eog:amd64 (3.26.2-3, 3.27.90-1ubuntu1), 
libmutter-1-0:amd64 (3.26.2-1, 3.26.2-1build1), 
ubuntu-session:amd64 (3.26.1-0ubuntu9, 3.26.1-0ubuntu10), 
gnome-settings-daemon:amd64 (3.26.2-0ubuntu2, 3.26.2-0ubuntu3), 
libmircore1:amd64 (0.29.0-0ubuntu1, 0.30.0.1-0ubuntu2), 
cheese:amd64 (3.26.0-4ubuntu1, 3.26.0-4ubuntu2), 
mutter-common:amd64 (3.26.2-1, 3.26.2-1build1), 
gir1.2-gnomedesktop-3.0:amd64 (3.26.2-1ubuntu1, 3.27.90-1ubuntu1), 
gnome-font-viewer:amd64 (3.26.0-3, 3.27.90-1), 
evince-common:amd64 (3.26.0-3, 3.27.91-1), 
nautilus:amd64 (1:3.26.0-0ubuntu1, 1:3.26.2-0ubuntu1), 
libnautilus-extension1a:amd64 (1:3.26.0-0ubuntu1, 1:3.26.2-0ubuntu1), 
libmirprotobuf3:amd64 (0.29.0-0ubuntu1, 0.30.0.1-0ubuntu2), 
ubuntu-software:amd64 (3.26.6-0ubuntu1, 3.27.90-1ubuntu1), 
libevview3-3:amd64 (3.26.0-3, 3.27.91-1), 
libmirclient9:amd64 (0.29.0-0ubuntu1, 0.30.0.1-0ubuntu2), 
libwebkit2gtk-4.0-37:amd64 (2.18.6-1, 2.19.91-1ubuntu1), 
totem-plugins:amd64 (3.26.0-0ubuntu3, 3.26.0-0ubuntu5), 
libtotem0:amd64 (3.26.0-0ubuntu3, 3.26.0-0ubuntu5), 
gir1.2-totem-1.0:amd64 (3.26.0-0ubuntu3, 3.26.0-0ubuntu5), 
gnome-screensaver:amd64 (3.6.1-8ubuntu1, 3.6.1-8ubuntu2), 
gnome-session-bin:amd64 (3.26.1-0ubuntu9, 3.26.1-0ubuntu10), 
libcheese-gtk25:amd64 (3.26.0-4ubuntu1, 3.26.0-4ubuntu2), 
cheese-common:amd64 (3.26.0-4ubuntu1, 3.26.0-4ubuntu2), 
gnome-control-center-faces:amd64 (1:3.26.2-0ubuntu3, 1:3.26.2-0ubuntu5), 
gir1.2-webkit2-4.0:amd64 (2.18.6-1, 2.19.91-1ubuntu1), 
libcheese8:amd64 (3.26.0-4ubuntu1, 3.26.0-4ubuntu2), 
totem-common:amd64 (3.26.0-0ubuntu3, 3.26.0-0ubuntu5), 
totem:amd64 (3.26.0-0ubuntu3, 3.26.0-0ubuntu5), 
nautilus-data:amd64 (1:3.26.0-0ubuntu1, 1:3.26.2-0ubuntu1), 
gnome-software-common:amd64 (3.26.6-0ubuntu1, 3.27.90-1ubuntu1), 
libjavascriptcoregtk-4.0-18:amd64 (2.18.6-1, 2.19.91-1ubuntu1), 
libmircommon7:amd64 (0.29.0-0ubuntu1, 0.30.0.1-0ubuntu2), 
gir1.2-javascriptcoregtk-4.0:amd64 (2.18.6-1, 2.19.91-1ubuntu1), 
mutter:amd64 (3.26.2-1, 3.26.2-1build1)
End-Date: 2018-03-02  10:07:34

```
Instead of GPU: RX 580, GPU: llvmpipe is used.
```
p-i@pi-MS-7A34:~$ screenfetch
                          ./+o+-       p-i@pi-MS-7A34
                  yyyyy- -yyyyyy+      OS: Ubuntu 18.04 bionic
               ://+//////-yyyyyyo      Kernel: x86_64 Linux 4.15.0-10-generic
           .++ .:/++++++/-.+sss/`      Uptime: 28m
         .:++o:  /++++++++/:--:/-      Packages: 2102
        o:+o+:++.`..```.-/oo+++++/     Shell: bash 4.4.18
       .:+o:+o/.          `+sssoo+/    Resolution: 1920x1200
  .++/+:+oo+o:`             /sssooo.   DE: GNOME 
 /+++//+:`oo+o               /::--:.   WM: GNOME Shell
 \+/+o+++`o++o               ++////.   WM Theme: 
  .++.o+++oo+:`             /dddhhh.   GTK Theme: Communitheme [GTK2/3]
       .+.o+oo:.          `oddhhhh+    Icon Theme: Suru
        \+.++o+o``-````.:ohdhhhhh+     Font: Ubuntu 11
         `:o+++ `ohhhhhhhhyo++os:      CPU: AMD Ryzen 7 1700 Eight-Core @ 16x 3.015GHz [29.0°C]
           .o:`.syhhhhhhh/.oo++o`      GPU: llvmpipe (LLVM 5.0, 128 bits)
               /osyyyyyyo++ooo+++/     RAM: 2342MiB / 16053MiB
                   ````` +oo+++o\:    
                          `oo++.      
p-i@pi-MS-7A34:~$ 

```

---

### Post by bmaring on 2018-03-02
Same issue here.  Downloaded and installed 3/2 iso, which installed fine.  After updates 3/2 AMDGPU no longer works.  When might a fix be available?

---

### Post by exploder on 2018-03-02
Completely broken here too... Screen full of text and can not start gnome display manager.

---

### Post by flocculant on 2018-03-02
There's been talk all over irc today about some graphics thing I think - could be related: [https://bugs.launchpad.net/ubuntu/+source/libglvnd/+bug/1751414](https://bugs.launchpad.net/ubuntu/+source/libglvnd/+bug/1751414) [https://bugs.launchpad.net/ubuntu/+source/libglvnd/+bug/1752901](https://bugs.launchpad.net/ubuntu/+source/libglvnd/+bug/1752901) 

Check the #u-dev, #u+1 and #u-desktop logs.

---

### Post by exploder on 2018-03-02
Thanks flocculant! Tried for 40 minutes to get it going again. I know there is always the possibility of breakage but just was not expecting it today... Got to get ready and go to work. I will mess with it tonight when I get home.

---

### Post by acheronuk on 2018-03-02
By my understanding the issue is things building in -proposed picking up a dependency on libegl1 from libglvnd etc, but the version in -release is too old and acceleration breaks when it migrates to -release. Ideally such things should not migrate if they break things (versioned dependency etc), but some oddities in this mesa/libglvnd transition mean that is not being prevented.

The happened to a Kubuntu desktop package the other day which I was able to rectify on a new build, but now there seems to be more things depending on libegl1 popping up.

Hopefully as soon as mesa and newer libglvnd etc migrate this will resolve itself.

Don't have an ETA for that, but the ubuntu developers are aware and working on it.

---

### Post by bmaring on 2018-03-02
Here is my screenfetch:
                 ```
yyyyy- -yyyyyy+      OS: Ubuntu 18.04 bionic
               ://+//////-yyyyyyo      Kernel: x86_64 Linux 4.15.0-10-generic
           .++ .:/++++++/-.+sss/`      Uptime: 53m
         .:++o:  /++++++++/:--:/-      Packages: 1670
        o:+o+:++.`..```.-/oo+++++/     Shell: bash 4.4.18
       .:+o:+o/.          `+sssoo+/    Resolution: 1920x1080
  .++/+:+oo+o:`             /sssooo.   DE: GNOME 
 /+++//+:`oo+o               /::--:.   WM: GNOME Shell
 \+/+o+++`o++o               ++////.   WM Theme: Adwaita
  .++.o+++oo+:`             /dddhhh.   GTK Theme: Ambiance [GTK2/3]
       .+.o+oo:.          `oddhhhh+    Icon Theme: ubuntu-mono-dark
        \+.++o+o``-````.:ohdhhhhh+     Font: Ubuntu 11
         `:o+++ `ohhhhhhhhyo++os:      CPU: AMD A6-3400M APU with Radeon HD Graphics @ 4x 1.4GHz [58.5°C]
           .o:`.syhhhhhhh/.oo++o`      GPU: AMD/ATI BeaverCreek [Radeon HD 6520G]
               /osyyyyyyo++ooo+++/     RAM: 1508MiB / 7449MiB
                   ````` +oo+++o\:    
                          `oo++.
```

---

### Post by P-I H on 2018-03-03
I was able to start software rendering ([COLOR=#000000]GPU: llvmpipe) [/COLOR]with Ctrl+Alt+F2.
After updates the GPU is back to GPU: Radeon RX 580 Series (AMD POLARIS10 / DRM 3.23.0 / 4.15.4-041504-generic, LLVM 5.0.0).
However the mouse isn't working correctly.
Mouse pointer is working, but left and right click gives no function.

---

### Post by exploder on 2018-03-03
I ended up reinstalling with the iso from 3/01/18 and updating from there. Everything is now working again. I could not get my original install to update and it was quicker to just start over.

---

### Post by P-I H on 2018-03-03
The system is working OK with Gnome login.

Logged in with Recovery mode and could change login to Gnome. Rebooted and made a "normal" boot.
```
p-i@pi-MS-7A34:~$ screenfetch
                          ./+o+-       p-i@pi-MS-7A34
                  yyyyy- -yyyyyy+      OS: Ubuntu 18.04 bionic
               ://+//////-yyyyyyo      Kernel: x86_64 Linux 4.15.0-10-generic
           .++ .:/++++++/-.+sss/`      Uptime: 48m
         .:++o:  /++++++++/:--:/-      Packages: 2113
        o:+o+:++.`..```.-/oo+++++/     Shell: bash 4.4.18
       .:+o:+o/.          `+sssoo+/    Resolution: 1920x1200
  .++/+:+oo+o:`             /sssooo.   DE: GNOME 
 /+++//+:`oo+o               /::--:.   WM: GNOME Shell
 \+/+o+++`o++o               ++////.   WM Theme: 
  .++.o+++oo+:`             /dddhhh.   GTK Theme: Communitheme [GTK2/3]
       .+.o+oo:.          `oddhhhh+    Icon Theme: Suru
        \+.++o+o``-````.:ohdhhhhh+     Font: Ubuntu 11
         `:o+++ `ohhhhhhhhyo++os:      CPU: AMD Ryzen 7 1700 Eight-Core @ 16x 3.001GHz [28.0°C]
           .o:`.syhhhhhhh/.oo++o`      GPU: Radeon RX 580 Series (POLARIS10 / DRM 3.23.0 / 4.15.0-10-generic, LLVM 5.0.1)
               /osyyyyyyo++ooo+++/     RAM: 3660MiB / 16053MiB
                   ````` +oo+++o\:    
                          `oo++.      
p-i@pi-MS-7A34:~$ 

```

---

### Post by exploder on 2018-03-03
P-I H, yeah gdm is missing the session selector and mouse clicks on it do not work either.

---

### Post by P-I H on 2018-03-03
After the upgrade the fbdev graphic driver is used instead of amdgpu.
I suppose the problem is related to the change of X.Org driver from 1.19.5 to 1.19.6 and mesa from 17.x to mesa 18.x.
I installed the oibaf ppa and the problem with the mouse is fixed, but amdgpu still isn't used

How to revert to standard Ubuntu drivers are explained in the ppa description.

---

### Post by JhonnyOliveira on 2018-03-08
I'm facing the exact same issue here. Can't find a solution anywhere...

---

### Post by P-I H on 2018-03-08
The oibaf ppa fixed the problem with the mouse.
For the usage of amdgpu driver there are different information.
Settings/Details shows AMDGPU driver.(see picture)
inxi -F shows drivers: fbdev,ati (unloaded: modesetting,vesa,radeon)
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.15.0-10-generic x86_64 bits: 64
           Desktop: Gnome 3.27.92
           Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: N/A
           UEFI: American Megatrends v: 1.90 date: 09/19/2017
CPU:       8 core AMD Ryzen 7 1700 Eight-Core (-MT-MCP-) cache: 4096 KB
           clock speeds: max: 3736 MHz 1: 3005 MHz 2: 3024 MHz 3: 3736 MHz
           4: 3585 MHz 5: 3007 MHz 6: 3030 MHz 7: 3007 MHz 8: 3037 MHz
           9: 2896 MHz 10: 2987 MHz 11: 3000 MHz 12: 3027 MHz 13: 3016 MHz
           14: 3033 MHz 15: 3018 MHz 16: 3036 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/580]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,ati (unloaded: modesetting,vesa,radeon)
           Resolution: 2560x1440@143.99hz
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 / DRM 3.23.0 / 4.15.0-10-generic, LLVM 6.0.0)
           version: 4.5 Mesa 18.1.0-devel
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 580]
           driver: snd_hda_intel
           Card-2 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-3 Logitech Webcam C250 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.15.0-10-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp33s0 state: up speed: 1000 Mbps duplex: full
Drives:    HDD Total Size: 740.2GB (17.2% used)
           ID-1: /dev/nvme0n1 model: Samsung_SSD_960_EVO_250GB size: 250.1GB
           ID-2: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-3: /dev/sdb model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 219G used: 119G (58%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 41.0C mobo: 43.0C gpu: 42.0
           Fan Speeds (in rpm): cpu: N/A fan-1: 516 fan-2: 419 fan-3: 1002 fan-4: 0 fan-5: 794
Info:      Processes: 377 Uptime: 1:45 Memory: 3278.9/16053.6MB
           Client: Shell (bash) inxi: 2.3.56 
p-i@pi-MS-7A34:~$ 

```
dmesg shows amdgpu
```
p-i@pi-MS-7A34:~$ dmesg | grep -i amdgpu
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-10-generic.efi.signed root=UUID=527726c6-7d7b-4747-a720-5516b68ae81a ro “amdgpu.dc=1” quiet splash vt.handoff=1
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-10-generic.efi.signed root=UUID=527726c6-7d7b-4747-a720-5516b68ae81a ro “amdgpu.dc=1” quiet splash vt.handoff=1
[    1.005420] [drm] amdgpu kernel modesetting enabled.
[    1.009132] fb: switching to amdgpudrmfb from EFI VGA
[    1.009585] amdgpu 0000:24:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
[    1.009638] amdgpu 0000:24:00.0: VRAM: 8192M 0x000000F400000000 - 0x000000F5FFFFFFFF (8192M used)
[    1.009639] amdgpu 0000:24:00.0: GTT: 256M 0x0000000000000000 - 0x000000000FFFFFFF
[    1.009704] [drm] amdgpu: 8192M of VRAM memory ready
[    1.009705] [drm] amdgpu: 8192M of GTT memory ready.
[    1.009831] amdgpu 0000:24:00.0: amdgpu: using MSI.
[    1.009847] [drm] amdgpu: irq initialized.
[    1.009864] amdgpu: [powerplay] amdgpu: powerplay sw initialized
[    1.010046] amdgpu 0000:24:00.0: fence driver on ring 0 use gpu addr 0x0000000000400040, cpu addr 0x0000000042d025f6
[    1.010083] amdgpu 0000:24:00.0: fence driver on ring 1 use gpu addr 0x00000000004000c0, cpu addr 0x000000002df4c457
[    1.010118] amdgpu 0000:24:00.0: fence driver on ring 2 use gpu addr 0x0000000000400140, cpu addr 0x00000000f7e21242
[    1.010146] amdgpu 0000:24:00.0: fence driver on ring 3 use gpu addr 0x00000000004001c0, cpu addr 0x000000000a40ebc2
[    1.010175] amdgpu 0000:24:00.0: fence driver on ring 4 use gpu addr 0x0000000000400240, cpu addr 0x00000000316c5ebb
[    1.010211] amdgpu 0000:24:00.0: fence driver on ring 5 use gpu addr 0x00000000004002c0, cpu addr 0x000000003aff3a14
[    1.010244] amdgpu 0000:24:00.0: fence driver on ring 6 use gpu addr 0x0000000000400340, cpu addr 0x000000003b2c6418
[    1.010275] amdgpu 0000:24:00.0: fence driver on ring 7 use gpu addr 0x00000000004003c0, cpu addr 0x00000000f28b782f
[    1.010304] amdgpu 0000:24:00.0: fence driver on ring 8 use gpu addr 0x0000000000400440, cpu addr 0x0000000013d67d9c
[    1.010318] amdgpu 0000:24:00.0: fence driver on ring 9 use gpu addr 0x00000000004004e0, cpu addr 0x0000000051ad2b80
[    1.010654] amdgpu 0000:24:00.0: fence driver on ring 10 use gpu addr 0x0000000000400560, cpu addr 0x000000004d2999f7
[    1.010688] amdgpu 0000:24:00.0: fence driver on ring 11 use gpu addr 0x00000000004005e0, cpu addr 0x000000004aae92af
[    1.011201] amdgpu 0000:24:00.0: fence driver on ring 12 use gpu addr 0x000000f4001e7a80, cpu addr 0x000000005e9c3f8f
[    1.011230] amdgpu 0000:24:00.0: fence driver on ring 13 use gpu addr 0x00000000004006e0, cpu addr 0x00000000800fa223
[    1.011257] amdgpu 0000:24:00.0: fence driver on ring 14 use gpu addr 0x0000000000400760, cpu addr 0x000000006a6a7153
[    1.011354] amdgpu 0000:24:00.0: fence driver on ring 15 use gpu addr 0x00000000004007e0, cpu addr 0x00000000e4a78e00
[    1.011383] amdgpu 0000:24:00.0: fence driver on ring 16 use gpu addr 0x0000000000400860, cpu addr 0x000000002770a0b6
[    1.798761] fbcon: amdgpudrmfb (fb0) is primary device
[    1.798849] amdgpu 0000:24:00.0: fb0: amdgpudrmfb frame buffer device
[    1.829039] amdgpu 0000:24:00.0: kfd not supported on this ASIC
[    1.829049] [drm] Initialized amdgpu 3.23.0 20150101 for 0000:24:00.0 on minor 0
p-i@pi-MS-7A34:~$ 

```
Graphic acceleration seems to work and my assumption is that amdgpu is used

---

