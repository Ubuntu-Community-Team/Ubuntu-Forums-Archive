---
title: "Copy lot of data to external disk locks the PC"
date: 2019-05-29
forum: Ubuntu Development Version
---

### Post by corradoventu on 2019-05-29
Today i copied a folder with some subfolders containing 46.630 items, totalling 167,4*GB from my hard disk to an external hard disk connected via USB2.
Same problem with another folder with 16.705 items, totalling 44,6*GB
Both disks are ext4. During the copy my PC was locked, all other applications (just terminal and system monitor) answered only after several seconds.
Also after completing the copy my pc looked asleep and i was forced to reboot to have a normal response.
As you can see from the system monitor window visible in the attached picture bot CPU load and memory usage was low.
```
corrado@corrado-p7-ee-0507:~$ inxi -Fxx
System:    Host: corrado-p7-ee-0507 Kernel: 5.0.0-15-generic x86_64 bits: 64 compiler: gcc v: 8.3.0 
           Desktop: Gnome 3.32.2 wm: gnome-shell dm: GDM3 Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:   Type: Desktop Mobo: ASRock model: H110M-G/M.2 serial: <root required> UEFI: American Megatrends 
           v: P1.10 date: 05/11/2017 
CPU:       Topology: Dual Core model: Intel Core i3-7100 bits: 64 type: MT MCP arch: Kaby Lake rev: 9 
           L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31296 
           Speed: 800 MHz min/max: 800/3900 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 800 
Graphics:  Device-1: Intel HD Graphics 630 vendor: ASRock driver: i915 v: kernel bus ID: 00:02.0 
           chip ID: 8086:5912 
           Display: x11 server: X.Org 1.20.4 driver: i915 compositor: gnome-shell resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2) v: 4.5 Mesa 19.0.5 compat-v: 3.0 
           direct render: Yes 
Audio:     Device-1: Intel 100 Series/C230 Series Family HD Audio vendor: ASRock driver: snd_hda_intel v: kernel 
           bus ID: 00:1f.3 chip ID: 8086:a170 
           Device-2: Logitech QuickCam Pro 9000 type: USB driver: snd-usb-audio,uvcvideo bus ID: 1-10:6 
           chip ID: 046d:0990 
           Sound Server: ALSA v: k5.0.0-15-generic 
Network:   Device-1: Intel Ethernet I219-V vendor: ASRock driver: e1000e v: 3.2.6-k port: f040 bus ID: 00:1f.6 
           chip ID: 8086:15b8 
           IF: enp0s31f6 state: up speed: 100 Mbps duplex: full mac: 70:85:c2:44:7b:86 
Drives:    Local Storage: total: 931.51 GiB used: 338.79 GiB (36.4%) 
           ID-1: /dev/sda vendor: Toshiba model: DT01ACA100 size: 931.51 GiB speed: 6.0 Gb/s serial: 37PYNGAFS 
Partition: ID-1: / size: 31.25 GiB used: 16.80 GiB (53.8%) fs: ext4 dev: /dev/sda7 
           ID-2: swap-1 size: 8.00 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 25.0 C mobo: 28.5 C 
           Fan Speeds (RPM): fan-1: 0 fan-2: 2327 fan-3: 0 fan-4: 2213 fan-5: 0 fan-6: 0 
           Voltages: 12v: N/A 5v: N/A 3.3v: 3.52 vbat: 3.15 
Info:      Processes: 217 Uptime: 2h 23m Memory: 7.50 GiB used: 1.36 GiB (18.2%) Init: systemd v: 240 runlevel: 5 
           Compilers: gcc: 8.3.0 alt: 8 Shell: bash v: 5.0.3 running in: gnome-terminal inxi: 3.0.34 
corrado@corrado-p7-ee-0507:~$ 

```

Here the 1st lines from top command after the copy was completed:
```
top - 18:28:53 up  2:31,  1 user,  load average: 0,81, 0,68, 0,61
Tasks: 219 total,   1 running, 218 sleeping,   0 stopped,   0 zombie
%Cpu(s): 10,0 us,  1,4 sy,  0,0 ni, 87,1 id,  0,0 wa,  0,0 hi,  1,4 si,  0,0 st
MiB Mem :   7678,0 total,   4457,2 free,    597,7 used,   2623,1 buff/cache
MiB Swap:   8192,0 total,   7915,5 free,    276,5 used.   6510,6 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
 1660 corrado   20   0  318396  38936  23168 S  11,8   0,5   7:24.81 Xorg
 5402 corrado   20   0   20392   3564   3172 R  11,8   0,0   0:00.03 top
 1031 root      20   0    2500     68      0 S   5,9   0,0   0:00.03 acpid
 1848 corrado   20   0 2971528 180216  45912 S   5,9   2,3   5:04.72 gnome-shell
    1 root      20   0  165492   5712   3472 S   0,0   0,1   0:04.23 systemd
    2 root      20   0       0      0      0 S   0,0   0,0   0:00.00 kthreadd
    3 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_gp
```
Here the 1st lines from top command after reboot:
```
top - 18:31:55 up 1 min,  1 user,  load average: 1,36, 0,72, 0,27
Tasks: 213 total,   1 running, 212 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2,9 us,  1,4 sy,  0,0 ni, 95,7 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
MiB Mem :   7678,0 total,   6406,0 free,    573,6 used,    698,4 buff/cache
MiB Swap:   8192,0 total,   8192,0 free,      0,0 used.   6760,4 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
 1765 corrado   20   0  171076   7084   6420 S  12,5   0,1   0:00.04 ibus-engi+
    1 root      20   0  167124  12476   7720 S   0,0   0,2   0:01.35 systemd
    2 root      20   0       0      0      0 S   0,0   0,0   0:00.00 kthreadd
    3 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_gp
    4 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_par_gp
    5 root      20   0       0      0      0 I   0,0   0,0   0:00.00 kworker/0+
    6 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 kworker/0+
```

I may repeat the operation and run ```
ubuntu-bug nautilus
``` or ```
ubuntu-bug gnome-shell
```???

---

### Post by oldfred on 2019-05-29
Do not use USB2, at best that may take all night.
Use only USB3 ports, or if that much data plug into SATA port if you have one?

Are you using Naulitus to copy data?
Better to use rsync.

I use rsync and multiple commands in a bash file, so I can monitor progress. My copies are mostly to USB flash drives, so still slow.

If not experienced with rsync, you may want to try grsync.
[https://help.ubuntu.com/community/rsync#Grsync](https://help.ubuntu.com/community/rsync#Grsync)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603](http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
of course, do the dry run first 

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by corradoventu on 2019-05-30
I didn't ask how to do it, but if the blocking of all the applications is normal.
I'm using Disco to test it so I will use the standard applications.

---

### Post by eris23 on 2019-06-11
Install and run sudo iotop.  I've found that the  "[jbd2/sdb1-8]" process, apparently journaling related, takes a huge percentage of I/O, slowing everything down dealing with USB drives.

---

