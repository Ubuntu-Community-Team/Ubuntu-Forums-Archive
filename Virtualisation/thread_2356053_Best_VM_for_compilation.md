---
title: "Best VM for compilation?"
date: 2017-03-19
forum: Virtualisation
---

### Post by Patrick_Jeeves on 2017-03-19
I want to add a windows VM to my machine so I can compile windows software--using minGW didn't produce good results--and I want to know which one to use.  I initially tried virtualBox but I'm having huge problems getting it to share files between ubuntu and windows properly, and everything on it is very slow in general. I also looked at xen, but I think that's used for remote servers and thin terminals, though I could be wrong about that.

Are there any recommendations for what to use?

---

### Post by &amp;KyT$0P# on 2017-03-19
> **Patrick_Jeeves said:**
> I initially tried virtualBox but I'm having huge problems getting it to share files between ubuntu and windows properly, and everything on it is very slow in general. 
I don't have any of those problems with VirtualBox.  I regularly compile software in VMs and share files to the host without problems.  All at expected speeds.

Do you have hardware virtualisation enabled, in both the host's BIOS/EFI and the VM settings?
How much RAM are you giving the guest?
Did you install Guest Additions in the guest?

Also might be worth seeing the host's specs.  Please install inxi if you don't have it...
```
sudo apt-get install inxi
```
... then post the output of running this command in Terminal -
```
inxi -! 31 -Fxxz
```

---

### Post by Patrick_Jeeves on 2017-03-19
virtualization is enabled, I'm giving it 2GB RAM for a copy of XP--I wanted to test that it would work before shelling out for windows 10--I don't think I installed any additions.

Based on what you said I bet it was because I used my liscence key on a torrented copy of XP, because I don't have a disk drive.
  
Host Specs:

```
System:    Kernel: 4.4.0-67-generic x86_64 (64 bit gcc: 5.4.0) Desktop: KDE Plasma 5.5.5 (Qt 5.5.1) dm: sddm,sddm                                                           
           Distro: Ubuntu 16.04 xenial
Machine:   System: Gigabyte product: N/A Chassis: type: 3
           Mobo: Gigabyte model: F2A55M-HD2 v: x.x Bios: American Megatrends v: F4 date: 04/09/2013
CPU:       Quad core AMD A8-5600K APU with Radeon HD Graphics (-MCP-) cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 28748
           clock speeds: min/max: 1400/3600 MHz 1: 1900 MHz 2: 1900 MHz 3: 3600 MHz 4: 2400 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Device 67df bus-ID: 01:00.0 chip-ID: 1002:67df
           Display Server: X.Org 1.18.4 driver: amdgpu Resolution: 2560x1440@59.95hz
           GLX Renderer: AMD Radeon RX 480 Graphics GLX Version: 4.5.13448 - CPC 16.30.3 Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel bus-ID: 00:14.2 chip-ID: 1022:780d
           Card-2 Advanced Micro Devices [AMD/ATI] Device aaf0
           driver: snd_hda_intel bus-ID: 01:00.1 chip-ID: 1002:aaf0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-67-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 02:00.0 chip-ID: 10ec:8168
           IF: enp2s0 state: down mac: <filter>
           Card-2: Qualcomm Atheros AR9227 Wireless Network Adapter
           driver: ath9k bus-ID: 03:06.0 chip-ID: 168c:002d
           IF: wlp3s6 state: up mac: <filter>
Drives:    HDD Total Size: 2120.4GB (13.8% used)
           ID-1: /dev/sda model: SanDisk_SDSSDA12 size: 120.0GB serial: 162181405368 temp: 28C
           ID-2: /dev/sdb model: ST1000LM014 size: 1000.2GB serial: W7730552 temp: 33C
           ID-3: /dev/sdc model: ST1000LM014 size: 1000.2GB serial: W772ZYXC temp: 33C
Partition: ID-1: / size: 103G used: 61G (63%) fs: ext4 dev: /dev/sda2
           ID-2: /home size: 917G used: 35G (4%) fs: ext4 dev: /dev/sdc1
           ID-3: swap-1 size: 7.74GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 7.8C mobo: N/A gpu: 40.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 203 Uptime: 4:29 Memory: 4184.2/8007.2MB Init: systemd v: 229 runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461 running in konsole) inxi: 2.2.35
```

---

### Post by CharlesA on 2017-03-19
You will need to install the Virtual Box guest additions in order to copy/paste between guest and host.

---

### Post by &amp;KyT$0P# on 2017-03-19
> **Patrick_Jeeves said:**
> I don't think I installed any additions.

Based on what you said I bet it was because I used my liscence key on a torrented copy of XP, because I don't have a disk drive.
Yep, there's both your problems.  If your host can run Kubuntu 16.04 smoothly, it can run a VirtualBox guest smoothly.

In order to fix file sharing - it's like CharlesA says.  In the running VM, go to Devices > Insert Guest Additions CD Image.  With Guest Additions installed, shared folders should work.


I would suspect the slowness is due to some malware in your copy of XP.

---

### Post by ajgreeny on 2017-03-19
There is no way that XP should be running slowly or having sharing problems if running in VBox.

I do not compile anything so can not comment about that but I do run my old retail version of XP in VBox very successfully, and incredibly fast, in fact I wish XP had been as good and fast when I used it previously in an older machine as it is now running as a VM!
Sharing is no problem either but it is absolutely essential to install the guest additions of the same version as your VBox version in order to share or use a shared clipboard.

---

