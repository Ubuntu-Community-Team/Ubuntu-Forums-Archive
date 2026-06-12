---
title: "Kernel 5.10"
date: 2020-10-27
forum: Ubuntu Development Version
---

### Post by zika on 2020-10-27
5.10rc1 not yet done as plain in Mainline.
5.10.0-051000rc1drmtip20201027-lowlatency
5.10.0-051000rc1daily20201027-lowlatency
Working nicely.

---

### Post by Doug S on 2020-10-28
> **zika said:**
> 5.10rc1 not yet done as plain in Mainline.Gee, the mainline builds have been breaking more often than normal over the last 1/2 year.

I was able to compile the kernel myself, but haven't run it yet.
I do see the issue has already been mentioned on [IRC]("https://irclogs.ubuntu.com/2020/10/27/%23ubuntu-kernel.html").

---

### Post by zika on 2020-11-12
HU:
[https://kernel.ubuntu.com/~kernel-ppa/mainline/drm-tip/current/](https://kernel.ubuntu.com/~kernel-ppa/mainline/drm-tip/current/)
Installs fine, stalls on boot. Not destructive, just obstructive.

---

### Post by Doug S on 2020-11-13
> **zika said:**
> HU:
[https://kernel.ubuntu.com/~kernel-ppa/mainline/drm-tip/current/](https://kernel.ubuntu.com/~kernel-ppa/mainline/drm-tip/current/)
Installs fine, stalls on boot. Not destructive, just obstructive.
Hi zika,
I compiled mainline as of just now (kernel 5.10-rc3 plus a few tens of patches (I didn't count)):

```
585e5b17b92d (HEAD -> master, origin/master, origin/HEAD) Merge tag 'fscrypt-for-linus' of git://git.kernel.org/pub/scm/fs/fscrypt/fscrypt
```

It booted fine.

---

### Post by zika on 2020-11-14
All 5.10s (I guess Your &#8220;5.3&#8222; is just typo) are fine here too, just drmtip from mainline is still obstructive... No retreat...

---

### Post by P-I H on 2020-11-15
Built a new computer with Ryzen 5 5600X and Asus TUF Gaming B550M.
Changed first to kernel 5.9 to enable fixed network, but in this kernel's k10temp-pci-00c3 don't show any value.
Changed to kernel 5.10-rc3 which works better
```
p-i@pi-TUF-B550M:~$ sensors
iwlwifi_1-virtual-0
Adapter: Virtual device
temp1:        +33.0°C  


k10temp-pci-00c3
Adapter: PCI adapter
Tctl:         +34.9°C  
Tdie:         +34.9°C  


nvme-pci-0500
Adapter: PCI adapter
Composite:    +37.9°C  (low  =  -0.1°C, high = +74.8°C)
                       (crit = +79.8°C)


amdgpu-pci-0a00
Adapter: PCI adapter
vddgfx:      775.00 mV 
fan1:           0 RPM  (min =    0 RPM, max = 2970 RPM)
edge:         +56.0°C  (crit = +100.0°C, hyst = -273.1°C)
                       (emerg = +105.0°C)
junction:     +56.0°C  (crit = +110.0°C, hyst = -273.1°C)
                       (emerg = +115.0°C)
mem:          +66.0°C  (crit = +105.0°C, hyst = -273.1°C)
                       (emerg = +110.0°C)
power1:       33.00 W  (cap = 180.00 W)


nvme-pci-0100
Adapter: PCI adapter
Composite:    +38.9°C  (low  = -273.1°C, high = +84.8°C)
                       (crit = +84.8°C)
Sensor 1:     +38.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +46.9°C  (low  = -273.1°C, high = +65261.8°C)


p-i@pi-TUF-B550M:~$ 

```
Logs show also less problems

---

### Post by zika on 2020-11-21
Still no bootable drm-tip... ;)

---

### Post by P-I H on 2020-11-21
What's the difference between to fetch from
[https://kernel.ubuntu.com/~kernel-ppa/mainline/drm-tip/current/](https://kernel.ubuntu.com/~kernel-ppa/mainline/drm-tip/current/)
or
[https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)

---

### Post by Doug S on 2020-11-21
> **P-I H said:**
> What's the difference between to fetch from
[https://kernel.ubuntu.com/~kernel-ppa/mainline/drm-tip/current/](https://kernel.ubuntu.com/~kernel-ppa/mainline/drm-tip/current/)
or
[https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)The mainline is only updated once per week, but the dailies are as of that day. So consider the dailies as kernels 5.10-rc4-1 through 7. There are also a couple of sort of "main" git sources, that ultimately feed into linus's master mainline, the drms are one.
I am not very knowledgeable about them, see also [the upstream descriptions on the mainline page]("https://wiki.ubuntu.com/Kernel/MainlineBuilds#Upstream_kernel_details"), noting that the page is a little obsolete in terms of the actual master branch locations (I think).

Every so often one will observe merges to/from drm-fixes (for example) in the master:

```
46cbc18ed852 Merge tag 'drm-fixes-2020-11-20-2' of git://anongit.freedesktop.org/drm/drm
6600f9d52213 Merge tag 'drm-intel-fixes-2020-11-19' of git://anongit.freedesktop.org/drm/drm-intel into drm-fixes
9336127d8cbc Merge tag 'drm-misc-fixes-2020-11-19' of git://anongit.freedesktop.org/drm/drm-misc into drm-fixes
```

I do not know how many of these, let us call them, lower level there are, nor why Ubuntu decided to always have drm's and not some others. For example, I mainly (pretend to) contribute via the power management group, and would love to have a daily for "linux-pm" (git://git.kernel.org/pub/scm/linux/kernel/git/rafael/linux-pm). Example merges:

```
131ad0b6f529 Merge tag 'acpi-5.10-rc5' of git://git.kernel.org/pub/scm/linux/kernel/git/rafael/linux-pm
4ca35b4f4509 Merge tag 'pm-5.10-rc5' of git://git.kernel.org/pub/scm/linux/kernel/git/rafael/linux-pm
```

---

### Post by Doug S on 2020-11-22
Kernel 5.10-rc5 is available. Either there are build problems for [the Ubuntu mainline PPA]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10-rc5/"), or it isn't finished yet [edit: It simply wasn't finished yet]. I used the Ubuntu kernel configuration from mainline PPA 5.10-rc3 (I never got around to -rc4) to compile:

```
doug@s18:~$ uname -a
Linux s18 5.10.0-rc5-stock #838 SMP PREEMPT Sun Nov 22 16:36:19 PST 2020 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by cecilpierce on 2020-11-25
I D/L the 5.10, are there any good instructions on installing ?
Thanks

---

### Post by P-I H on 2020-11-25
These are my instructions.
- make a folder in home called kernel
- Open [COLOR=#000000][FONT=Arial]https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D in a browser and fetch the latest available packages
- [/FONT][/COLOR]linux-headers-5.10.0-051000rc5_5.10.0-051000rc3.202011082030_all.deb
- linux-headers-5.10.0-051000rc5-generic_5.10.0-051000rc3.202011082030_amd64.deb
- linux-image-unsigned-5.10.0-051000rc5-generic_5.10.0-051000rc3.202011082030_amd64.deb
- linux-modules-5.10.0-051000rc5-generic_5.10.0-051000rc3.202011082030_amd64.deb
[COLOR=#000000][FONT=Arial]I'm using rc3 now and will change to the released version when available
- copy the downloaded packages to the kernel folder
- Open a terminal and do these commands
[/FONT][/COLOR]```
cd ~/kernel
[COLOR=#000000][FONT=Arial]sudo dpkg -i *.deb
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo reboot[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by ping-wu on 2020-11-25
If I mess up, how do I go back to my previous kernel?

---

### Post by P-I H on 2020-11-26
To remove use this command
sudo apt-get remove linux-headers-x.y.z-* linux-image-x.y.z-* and replace x.y.z with the actual kernel values
It's also possible to use Synaptic and also to select another kernel when booting with the Grub menu.
I think you aren't able to remove a running kernel. 

In case you want grub to always boot an older kernel you may do
sudo nano /etc/default/grub
Inside nano, look for GRUB_DEFAULT=0. Change it to GRUB_DEFAULT=saved. Then, press the Enter key on the keyboard and paste this (using the keyboard shortcut “Ctrl + Shift + V”) below the GRUB_DEFAULT line:
GRUB_SAVEDEFAULT=true
After the changes you have to run
sudo update-grub

---

### Post by cecilpierce on 2020-11-26
Thank you for the help.

---

### Post by corradoventu on 2020-11-26
good instructions on installing a new kernel: [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by Doug S on 2020-11-27
I am a server type, and so use "wget" to get the mainline kernel .deb files. I copy and paste the links from a browser on a windows computer and into a putty ssh session to the server. I do a lot of kernel stuff and often end up with over 50 kernel installed. I have found [this tool]("https://code.launchpad.net/linux-purge") to be extremely valuable for kernel removal management.

If I do end up manually removing a kernel, I use dkpg directly.

---

### Post by zika on 2020-11-28
> **zika said:**
> Still no bootable drm-tip... ;)5.10.0-051000rc5drmtip20201128 is the first in this series that boots and it does it very nice.

---

### Post by Doug S on 2020-12-10
I have been using a self compiled kernel 5.10-rc7 for a few days now. I only now noticed that [the Ubuntu PPA version]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.10-rc7/") failed to compile. 

```
FAILED unresolved symbol __add_to_page_cache_locked
```

The mainline builds sure get broken more often than they used to.

for a test I need a 250 Hz kernel (generic), whereas I normally use a 1000 Hz kernel (low latency). I already know that the Ubuntu kernel configurations differ by much more than just the 250/1000 switch, so had wanted to start with the Ubuntu version. I'll use -rc6 for now.

---

### Post by corradoventu on 2020-12-14
```
corrado@corrado-x5-hh-1207:~$ inxi -Fx
System:    Host: corrado-x5-hh-1207 Kernel: 5.10.0-051000-generic x86_64 bits: 64 compiler: gcc 
           v: 10.2.0 Desktop: GNOME 3.38.1 Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:   Type: Desktop Mobo: ASRock model: H110M-G/M.2 serial: <superuser/root required> 
           UEFI: American Megatrends v: P1.10 date: 05/11/2017 
CPU:       Info: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake rev: 9 
           L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31199 
           Speed: 3900 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 3900 2: 3900 3: 3900 
           4: 3900 
Graphics:  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel bus ID: 00:02.0 
           Device-2: ARC USB 2.0 Camera type: USB driver: uvcvideo bus ID: 1-8:6 
           Display: x11 server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa Intel HD Graphics 630 (KBL GT2) v: 4.6 Mesa 20.2.4 
           direct render: Yes 
Audio:     Device-1: Intel 100 Series/C230 Series Family HD Audio vendor: ASRock 
           driver: snd_hda_intel v: kernel bus ID: 00:1f.3 
           Device-2: Logitech QuickCam Pro 9000 type: USB driver: snd-usb-audio,uvcvideo 
           bus ID: 1-2:3 
           Sound Server: ALSA v: k5.10.0-051000-generic 
Network:   Device-1: Intel Ethernet I219-V vendor: ASRock driver: e1000e v: kernel port: f040 
           bus ID: 00:1f.6 
           IF: enp0s31f6 state: up speed: 100 Mbps duplex: full mac: 70:85:c2:44:7b:86 
Drives:    Local Storage: total: 2.05 TiB used: 10.98 GiB (0.5%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SKC2000M8250G size: 232.89 GiB 
           ID-2: /dev/sda vendor: Toshiba model: DT01ACA100 size: 931.51 GiB 
           ID-3: /dev/sdb vendor: Hitachi model: HDS721010CLA332 size: 931.51 GiB 
Partition: ID-1: / size: 31.25 GiB used: 10.98 GiB (35.1%) fs: ext4 dev: /dev/nvme0n1p5 
Swap:      ID-1: swap-1 type: partition size: 8.00 GiB used: 0 KiB (0.0%) dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 40.5 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 238 Uptime: 2m Memory: 7.48 GiB used: 1.07 GiB (14.3%) Init: systemd 
           runlevel: 5 Compilers: gcc: 10.2.1 Packages: 2056 Shell: Bash v: 5.1.0-rc3 inxi: 3.1.09 
corrado@corrado-x5-hh-1207:~$ 

```

---

### Post by P-I H on 2020-12-14
Suspend stopped working on my Ubuntu 20.10 installation. I believe after update of linux-firmware. Now I will use hirute as my main installation.
```
p-i@pi-TUF-Gaming-B550M:~$ inxi -Fz
System:    Kernel: 5.10.0-051000-generic x86_64 bits: 64 Desktop: GNOME 3.38.1 Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:   Type: Desktop System: ASUS product: N/A v: N/A serial: <filter> 
           Mobo: ASUSTeK model: TUF GAMING B550M-PLUS (WI-FI) v: Rev X.0x serial: <filter> UEFI: American Megatrends v: 1212 
           date: 11/04/2020 
CPU:       Info: 6-Core model: AMD Ryzen 5 5600X bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 1956 MHz min/max: 2200/3700 MHz Core speeds (MHz): 1: 1889 2: 2007 3: 3361 4: 1871 5: 2458 6: 1944 7: 3444 
           8: 1901 9: 2000 10: 1896 11: 2612 12: 1910 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] driver: amdgpu 
           v: kernel 
           Display: x11 server: X.Org 1.20.9 driver: amdgpu,ati unloaded: fbdev,modesetting,radeon,vesa 
           resolution: 2560x1440~60Hz 
           OpenGL: renderer: AMD Radeon RX 5700 (NAVI10 DRM 3.40.0 5.10.0-051000-generic LLVM 11.0.1) v: 4.6 Mesa 20.2.4 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Starship/Matisse HD Audio driver: snd_hda_intel 
           Device-3: Logitech Webcam C250 type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server: ALSA v: k5.10.0-051000-generic 
Network:   Device-1: Intel Wi-Fi 6 AX200 driver: iwlwifi 
           IF: wlp6s0 state: up mac: <filter> 
           Device-2: Realtek RTL8125 2.5GbE driver: r8169 
           IF: enp7s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 1.36 TiB used: 58.50 GiB (4.2%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 EVO 500GB size: 465.76 GiB 
           ID-2: /dev/nvme1n1 vendor: Kingston model: SA2000M8500G size: 465.76 GiB 
           ID-3: /dev/sda vendor: Samsung model: SSD 860 EVO 500GB size: 465.76 GiB 
Partition: ID-1: / size: 456.96 GiB used: 58.46 GiB (12.8%) fs: ext4 dev: /dev/sda2 
Swap:      ID-1: swap-1 type: file size: 2.00 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:   System Temperatures: cpu: 40.4 C mobo: 43.0 C gpu: amdgpu temp: 60.0 C 
           Fan Speeds (RPM): fan-1: 853 fan-2: 896 fan-3: 834 fan-7: 0 gpu: amdgpu fan: 0 
Info:      Processes: 351 Uptime: 24m Memory: 15.54 GiB used: 2.97 GiB (19.1%) Shell: Bash inxi: 3.1.09 
p-i@pi-TUF-Gaming-B550M:~$ 

```

---

### Post by IanW on 2020-12-15
WARNING - RAID storage bugs found in 5.10. Kernel 5.10.1 already inbound.

[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.10.1-Released](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.10.1-Released)
[http://lkml.iu.edu/hypermail/linux/kernel/2012.1/07324.html](http://lkml.iu.edu/hypermail/linux/kernel/2012.1/07324.html)

---

