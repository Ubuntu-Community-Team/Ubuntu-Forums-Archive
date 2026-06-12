---
title: "Beta testers for the new Perl inxi release requested"
date: 2018-03-17
forum: Ubuntu, Linux and OS Chat
---

### Post by user232 on 2018-03-17
Hi Ubuntu users. I'm in the process of releasing, fairly soon, the new Perl rewrite of inxi, the system info program packaged by Unit193. It would be helpful if as many people as possible could look and find weaknesses, bugs, glitches, errors, etc, before the first release happens, which should be this coming week.  

The new release, 2.9.01 will lead into the 3.0.0 version of inxi. The development branch is called pinxi, so you can run pinxi and inxi together to compare etc. Once all the bugs and issues that are going to be found are found, the pinxi branch will move to inxi master and become inxi 3.0.0. Pinxi is a full rewrite, in Perl5, of inxi. There have been a lot of bugs found and fixed so far. 

Git branch: [https://github.com/smxi/inxi/tree/inxi-perl](https://github.com/smxi/inxi/tree/inxi-perl) 

To test, install/download, as root/sudo:  

```
sudo wget -O /usr/local/bin/pinxi https://github.com/smxi/inxi/raw/inxi-perl/pinxi; sudo chmod +x /usr/local/bin/pinxi
``` 

Once installed, updating works the same as with inxi: 

```
pinxi -U
``` 

I want to release version 3.0.0 of inxi with no real bugs, at least as few as possible, and as many improvements over inxi 2.3.56 as possible.  

I"m probably now in my final days of beta testing (unless new bugs show up), but I'd like if other distros would give it a spin and see if there are any errors, bugs, issues, glitches, etc.  

Once there are no active issues or bugs, pinxi will move to inxi 2.9.01, as the first official Perl inxi release. After a few weeks, this will become inxi 3.0.0, again assuming, all bugs fixed etc. 

Of particular interest to me is ARM testing, zfs or mdraid software RAID, and weird old systems, or weird new systems, that might expose unfound bugs. 

All short form args for normal options are the same, only now there are also long form args for everything as well, which means any tools that use inxi should see few changes, though you want to check that to make sure. See --help for new options. 

There's an enhanced debugger as well, called with --debug 21 (leaves tar.gz data file on your system) or --debug 22 (removes all debugging data after automatic upload), which is helping a lot with debugging issues. 

The most useful testing command is: pinxi -zv8 

-zv8 is basically everything it can do, so any bugs will show there if they exist, plus the -z output filter.

---

### Post by Bashing-om on 2018-03-17
No fault found:
```

sysop@x1604:/$ pinxi -zv8
System:
  Host: x1604 Kernel: 4.4.0-116-generic x86_64 bits: 64 compiler: gcc 
  v: 5.4.0 Desktop: Xfce 4.12.3 (Gtk 2.24.28) info: xfce4-panel 
  dm: lightdm 1.18.3 Distro: Ubuntu 16.04.4 LTS 
Machine:
  Type: Desktop Mobo: Abit model: KN9(NF-MCP55 series) v: 1.x serial: N/A 
  BIOS: Phoenix LTD v: 6.00 PG date: 11/19/2007 
Memory:
  RAM Report: permissions: Unable to run dmidecode. Are you root? 
PCI Slots:
  Permissions: Unable to run dmidecode. Are you root? 
CPU:
  Topology: Dual Core model: AMD Athlon 64 X2 5000+ type: MCP 
  arch: K8 rev.F+ rev: 2 L2 cache: 1024 KB 
  flags: lm nx pae sse sse2 sse3 svm bogomips: 3999 
  Speed: 1000 MHz min/max: 1000/2600 MHz Core speeds: 1: 1000 2: 1000 
Graphics:
  Card-1: NVIDIA GK208 [GeForce GT 710B] driver: nvidia v: 384.111 
  bus ID: 06:00.0 chip ID: 10de:128b 
  Display Server: x11 (X.Org 1.18.4) driver: nvidia 
  unloaded: modesetting,nouveau,fbdev,vesa resolution: 1600x900~60Hz 
  OpenGL: renderer: GeForce GT 710/PCIe/SSE2 version: 4.5.0 NVIDIA 384.111 
  direct render: Yes 
Audio:
  Card-1: NVIDIA MCP55 High Definition Audio driver: snd_hda_intel 
  v: kernel bus ID: 00:06.1 chip ID: 10de:0371 
  Card-2: NVIDIA GK208 HDMI/DP Audio Controller driver: snd_hda_intel 
  v: kernel bus ID: 06:00.1 chip ID: 10de:0e0f 
  Sound Server: ALSA v: k4.4.0-116-generic 
Network:
  Card-1: Accton SMC2-1211TX driver: 8139too v: 0.9.28 port: 9c00 
  bus ID: 01:09 chip ID: 1113:1211 
  IF: enp1s9 state: unknown speed: 100 Mbps duplex: full mac: <filter> 
  IP v4: <filter> type: dynamic enp1s9 scope: global broadcast: <filter> 
  IP v6: <filter> scope: link 
  IF-ID-1: enp0s8 state: down mac: <filter> 
  IF-ID-2: enp0s9 state: down mac: <filter> 
  WAN IP: <filter>
Drives:
  HDD Total Size: 344.68 GB used: 8.44 GB (2.5%) 
  ID-1: /dev/sda model: Samsung_SSD_850 size: 232.89 GB serial: <filter> 
  rev: 2B6Q 
  ID-2: /dev/sdb model: PNY_CS900_120GB size: 111.79 GB serial: <filter> 
  rev: 0711 temp: 33 C 
  Optical-1: /dev/sr0 vendor: TOSHIBA model: DVD-ROM SD-M1502 rev: 1012 
  dev-links: cdrom 
  Features: speed: 48 multisession: yes audio: yes dvd: yes rw: none 
  state: running 
  Optical-2: /dev/sr1 vendor: HL-DT-ST model: DVD-RAM GH22NP20 rev: 2.00 
  dev-links: cdrw,dvd,dvdrw 
  Features: speed: 48 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram state: running 
RAID:
  Message: No RAID data was found. 
Partition:
  ID-1: / size: 136.37 GB used: 8.44 GB (6.2%) fs: ext4 dev: /dev/sda1 
  label: x1604 uuid: d9c2a8e6-d014-42a6-846f-7e7892f4aef5 
  ID-2: swap-1 size: 4.39 GB used: 0 KB (0.0%) fs: swap dev: /dev/sda5 
  label: N/A uuid: 8d4743bc-8e47-4650-b5fd-1ea904d4ecda 
Unmounted:
  ID-1: /dev/sdb1 size: 7.81 GB fs: ext4 label: m1804root 
  uuid: 060f35b0-f64d-4c96-8f37-0b35c27113a7 
  ID-2: /dev/sdb2 size: 9.77 GB fs: ext4 label: m1804home 
  uuid: ba850e4f-2af7-4261-96e4-b5ccd9317902 
  ID-3: /dev/sdb3 size: 5.86 GB fs: ext4 label: m1804var 
  uuid: 64edeaf6-307c-4b3d-be88-1f293e06b081 
  ID-4: /dev/sdb5 size: 29.30 GB fs: ext4 label: u1804 
  uuid: 0b89d785-9ba8-4bd5-a41a-43462459c230 
  ID-5: /dev/sdb6 size: 9.77 GB fs: ext4 label: bups 
  uuid: a0c6dc1f-51d3-4824-b770-ce42d777277a 
  ID-6: /dev/sdb7 size: 9.77 GB fs: ext4 label: data 
  uuid: fe9cee2e-6812-46e1-b0a0-b03d5094763a 
USB:
  Hub: 1:1 usb: 2.00 type: Full speed (or root) hub chip ID: 1d6b:0002 
  Hub: 2:1 usb: 1.10 type: Full speed (or root) hub chip ID: 1d6b:0001 
  Device-1: SiGma Micro bus ID: 2:2 usb: 1.10 type: Mouse 
  chip ID: 1c4f:0034 
Sensors:
  System Temperatures: cpu: 33.0 C mobo: N/A gpu: nvidia temp: 34 C 
  Fan Speeds (in RPM): N/A gpu: nvidia fan: 40% 
Repos:
  Active apt sources in: /etc/apt/sources.list 
  1: deb [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) xenial main restricted universe multiverse
  2: deb [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) xenial-security main restricted universe multiverse
  3: deb [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) xenial-updates main restricted universe multiverse
  4: deb [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) xenial-backports main restricted universe multiverse
  5: deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
  Active apt sources in: /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-xenial.list 
  1: deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial main
Processes:
  CPU  % used - Command - pid - Memory: MB / % used - top: 5 
  1: cpu: 24.0% command: pinxi started by: perl pid: 12821 
  mem: 19.9MB (0.5%) 
  2: cpu: 1.9% command: chromium-browser pid: 3722 mem: 326.9MB (8.2%) 
  3: cpu: 1.7% command: chromium-browser pid: 3775 mem: 182.4MB (4.6%) 
  4: cpu: 1.0% command: chromium-browser pid: 32055 mem: 80.7MB (2.0%) 
  5: cpu: 0.7% command: xorg pid: 979 mem: 63.0MB (1.5%) 
  Memory MB/% used - Command - pid - CPU: % used - top: 5 
  1: mem: 326.9 MB (1.9%) command: chromium-browser pid: 3722 cpu: 8.2% 
  2: mem: 182.4 MB (1.7%) command: chromium-browser pid: 3775 cpu: 4.6% 
  3: mem: 160.1 MB (0.1%) command: chromium-browser pid: 3844 cpu: 4.0% 
  4: mem: 98.6 MB (0.1%) command: chromium-browser pid: 6381 cpu: 2.4% 
  5: mem: 96.2 MB (0.1%) command: chromium-browser pid: 10856 cpu: 2.4% 
Info:
  Processes: 180 Uptime: 5:27 Memory: 3.86 GB used: 974.8 MB (24.7%) 
  Init: systemd v: 229 runlevel: 5 default: 2 Compilers: gcc: 5.4.0 alt: 5 
  Shell: bash 4.3.48 running in: xfce4-terminal pinxi: 2.9.00-440-p 
sysop@x1604:/$

```

[INDENT][INDENT]Good Deed done
[INDENT][INDENT]dirt cheap
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by user232 on 2018-03-17
looks good, except for the enp0s8 enp0s9 interfaces, which do not appear to have been connected with any device/card. What are those?

---

### Post by wildmanne39 on 2018-03-17
*Thread moved to **Ubuntu, Linux and OS Chat, a more appropriate forum**.*

Thanks for all the work you are putting into inxi.

---

### Post by Bashing-om on 2018-03-17
user232; Hey -

> **user232 said:**
> looks good, except for the enp0s8 enp0s9 interfaces, which do not appear to have been connected with any device/card. What are those?

Old server box - 3 NICs of which only one is presently in use.

[INDENT][INDENT]old hardware never dies ( with linux )[/INDENT][/INDENT]

---

### Post by mc4man on 2018-03-17
I would suggest for the install line in 1st post either separate the 2 commands + add another sudo for the chmod or add a ; sudo  or && sudo in between them.
Otherwise doesn't set as executable..
ex. of now.
```
$ sudo wget -O /usr/local/bin/pinxi https://github.com/smxi/inxi/raw/inxi-perl/pinxi chmod +x /usr/local/bin/pinxi
[sudo] password for doug: 
--2018-03-17 23:15:27--  https://github.com/smxi/inxi/raw/inxi-perl/pinxi
Resolving github.com (github.com)... 192.30.253.112, 192.30.253.113
Connecting to github.com (github.com)|192.30.253.112|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/smxi/inxi/inxi-perl/pinxi [following]
--2018-03-17 23:15:27--  https://raw.githubusercontent.com/smxi/inxi/inxi-perl/pinxi
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.20.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.20.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 474531 (463K) [text/plain]
Saving to: ‘/usr/local/bin/pinxi’

/usr/local/bin/pinxi            100%[=======================================================>] 463.41K  --.-KB/s    in 0.07s   

2018-03-17 23:15:27 (6.34 MB/s) - ‘/usr/local/bin/pinxi’ saved [474531/474531]

--2018-03-17 23:15:27--  http://chmod/
Resolving chmod (chmod)... failed: Name or service not known.
wget: unable to resolve host address ‘chmod’
--2018-03-17 23:15:27--  http://+x/
Resolving +x (+x)... failed: Name or service not known.
wget: unable to resolve host address ‘+x’
/usr/local/bin/pinxi: Scheme missing.
FINISHED --2018-03-17 23:15:27--
Total wall clock time: 0.4s
Downloaded: 1 files, 463K in 0.07s (6.34 MB/s)


```

This works better
```
$ sudo wget -O /usr/local/bin/pinxi https://github.com/smxi/inxi/raw/inxi-perl/pinxi; sudo chmod +x /usr/local/bin/pinxi
--2018-03-17 23:17:42--  https://github.com/smxi/inxi/raw/inxi-perl/pinxi
Resolving github.com (github.com)... 192.30.253.113, 192.30.253.112
Connecting to github.com (github.com)|192.30.253.113|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/smxi/inxi/inxi-perl/pinxi [following]
--2018-03-17 23:17:42--  https://raw.githubusercontent.com/smxi/inxi/inxi-perl/pinxi
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.20.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.20.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 474531 (463K) [text/plain]
Saving to: ‘/usr/local/bin/pinxi’

/usr/local/bin/pinxi            100%[=======================================================>] 463.41K  --.-KB/s    in 0.06s   

2018-03-17 23:17:42 (7.17 MB/s) - ‘/usr/local/bin/pinxi’ saved [474531/474531]
```

---

### Post by cariboo on 2018-03-18
I ran pinxi using the same command as Bashing-om on my Raspberry pi 3B, here are the results:

```
pinxi -zv8
System:
  Host: haven Kernel: 4.9.80-v7+ armv7l bits: 32 compiler: gcc v: 4.9.3 
  Console: tty 0 dm: N/A Distro: Raspbian GNU/Linux 9 (stretch) 
Machine:
  Message: No machine data: try newer kernel. Is dmidecode installed? Try -M 
  --alt 33. 
Memory:
  RAM Report: permissions: Unable to run dmidecode. Are you root? 
PCI Slots:
  ARM: PCI data type is not supported on ARM systems. 
CPU:
  Topology: Quad Core model: ARMv7 rev 4 (v7l) type: MCP arch: ARMv7 rev: 4 
  features: Use -f option to see features bogomips: 307 
  Speed: 1200 MHz min/max: 600/1200 MHz Core speeds: 1: 1200 2: 1200 3: 1200 
  4: 1200 
Graphics:
  ARM: PCI data type is not supported on ARM systems. 
  Display Server: No display server data found. Headless server? tty: 80x24 
  Message: Unable to show advanced data. Required tool glxinfo missing. 
Audio:
  ARM: PCI data type is not supported on ARM systems. 
Network:
  ARM: PCI data type is not supported on ARM systems. 
  IF-ID-1: eth0 state: up speed: 100 Mbps duplex: full mac: <filter> 
  IP v4: <filter> scope: global broadcast: <filter> 
  IP v6: <filter> type: mngtmpaddr noprefixroute dynamic scope: global 
  IP v6: <filter> scope: link 
  IF-ID-2: wlan0 state: down mac: <filter> 
  WAN IP: <filter> 
Drives:
  HDD Total Size: 29.82 GB used: 2.05 GB (6.9%) 
  ID-1: /dev/sda type: USB model: Cruzer_Edge size: 29.82 GB 
  serial: <filter> rev: 1.26 
  Message: No Optical or Floppy data was found. 
RAID:
  Message: No RAID data was found. 
Partition:
  ID-1: / size: 29.28 GB used: 2.03 GB (6.9%) fs: ext4 dev: /dev/root 
  label: N/A uuid: N/A 
  ID-2: /boot size: 41.2 MB used: 21.0 MB (50.9%) fs: vfat dev: /dev/sda1 
  label: boot uuid: D3AB-52BD 
Unmounted:
  ID-1: /dev/sda2 size: 29.77 GB fs: ext4 label: N/A 
  uuid: 3fd50dbb-b3fe-4c19-8d40-f67b938b8cf8 
USB:
  Hub: 1:1 usb: 2.00 type: Full speed (or root) hub chip ID: 1d6b:0002 
  Hub: 1:2 usb: 2.00 type: Standard Microsystems SMC9514 Hub 
  chip ID: 0424:9514 
  Device-1: Standard Microsystems SMSC9512/9514 Fast Ethernet Adapter 
  bus ID: 1:3 usb: 2.00 type: Vendor Specific Class chip ID: 0424:ec00 
  Device-2: SanDisk bus ID: 1:4 usb: 2.00 type: Mass Storage 
  chip ID: 0781:556b 
Sensors:
  Missing: Required tool sensors not installed. Check --recommends 
Repos:
  Active apt sources in: /etc/apt/sources.list 
  1: deb http://mirrordirector.raspbian.org/raspbian/ stretch main contrib non-free rpi
  Active apt sources in: /etc/apt/sources.list.d/mosquitto-stretch.list 
  1: deb http://repo.mosquitto.org/debian stretch main
  Active apt sources in: /etc/apt/sources.list.d/raspi.list 
  1: deb http://archive.raspberrypi.org/debian/ stretch main ui
Processes:
  CPU  % used - Command - pid - Memory: MB / % used - top: 5 
  1: cpu: 8.7% command: [kworker/2:2] pid: 28458 mem: 0.00MB (0.0%) 
  2: cpu: 4.2% command: hass started by: python3 pid: 28556 
  mem: 64.4MB (6.9%) 
  3: cpu: 0.3% command: -bash pid: 32176 mem: 3.95MB (0.4%) 
  4: cpu: 0.1% command: sshd: pid: 32141 mem: 5.61MB (0.6%) 
  5: cpu: 0.0% command: init pid: 1 mem: 5.86MB (0.6%) 
  Memory MB/% used - Command - pid - CPU: % used - top: 5 
  1: mem: 64.4 MB (4.2%) command: hass started by: python3 pid: 28556 
  cpu: 6.9% 
  2: mem: 13.4 MB (0.0%) command: smbd pid: 562 cpu: 1.4% 
  3: mem: 12.7 MB (0.0%) command: pinxi started by: perl pid: 32508 
  cpu: 1.3% 
  4: mem: 10.1 MB (0.0%) command: systemd-journald pid: 116 cpu: 1.0% 
  5: mem: 5.86 MB (0.0%) command: init pid: 1 cpu: 0.6% 
Info:
  Processes: 131 Uptime: 3 days Memory: 927.3 MB used: 126.9 MB (13.7%) 
  Init: systemd v: 232 runlevel: 5 Compilers: gcc: 6.3.0 alt: 6 
  Shell: bash 4.4.12 running in: tty 0 pinxi: 2.9.00-443-p
```

---

### Post by user232 on 2018-03-18
cariboo, I'd have to see the output of: df -kTP 

to see what went wrong there with disk size vs partitions vs unmounted partitions, the /dev/root causes problems sometimes but it's hard to know why without seeing the data. Thanks

---

### Post by mörgæs on 2018-03-18
Lots of good information. Thanks for providing the package.

The list of CPU flags is much shorter than ```
sudo lshw -C cpu
```Is this on purpose?


Also the line
```
Sensors:   Missing: Required tool sensors not installed. Check --recommends 
```
might be difficult to understand for some users. Maybe ```
The program *sensors* is needed for this function. It can be installed using the command *sudo apt install sensors*
``` in stead?

---

### Post by cariboo on 2018-03-18
> **user232 said:**
> cariboo, I'd have to see the output of: df -kTP 

to see what went wrong there with disk size vs partitions vs unmounted partitions, the /dev/root causes problems sometimes but it's hard to know why without seeing the data. Thanks

I should say that the pi is running on a 32Gb usb drive, here is what you asked for:

```

 df -kTP
Filesystem     Type     1024-blocks    Used Available Capacity Mounted on
/dev/root      ext4        30714616 1641944  27792688       6% /
devtmpfs       devtmpfs      217968       0    217968       0% /dev
tmpfs          tmpfs         222260       0    222260       0% /dev/shm
tmpfs          tmpfs         222260    3168    219092       2% /run
tmpfs          tmpfs           5120       4      5116       1% /run/lock
tmpfs          tmpfs         222260       0    222260       0% /sys/fs/cgroup
/dev/mmcblk0p1 vfat           42136   21469     20667      51% /boot
tmpfs          tmpfs          44452       0     44452       0% /run/user/1000
```

**Edit:** oops I posted the output of the wrong pi :) this is the B3:

```
pi@haven:~ $  df -kTP
Filesystem     Type     1024-blocks    Used Available Capacity Mounted on
/dev/root      ext4        30706352 2135208  27290140       8% /
devtmpfs       devtmpfs      470180       0    470180       0% /dev
tmpfs          tmpfs         474788       0    474788       0% /dev/shm
tmpfs          tmpfs         474788   48056    426732      11% /run
tmpfs          tmpfs           5120       4      5116       1% /run/lock
tmpfs          tmpfs         474788       0    474788       0% /sys/fs/cgroup
/dev/sda1      vfat           42152   21470     20682      51% /boot
tmpfs          tmpfs          94956       0     94956       0% /run/user/1000
```

---

### Post by user232 on 2018-03-18
mörgæs, there are two reasons the suggestion is short: 1, to be short and concise. 2. To fit on one line. The reason it points to --recommends is that recommends has the capacity to do per package manager tests and package install suggestions, thus avoiding cluttering up the output unnecessarily. If you look for example at your idea, that only applies to ubuntu, whereas the short concise one applies to all linux distros, so that will remain as is.  

Error messages should be clear and concise in my opinion, and not be so long that they make the user brain cloud over. If they want more information, all they have to do is follow the advice to run --recommends, which has that information in it. Every line that can have this type of error has similar short but accurate output, if I were to extend each error message out to that long, the output would be really unreadable and a total mess. think: 80 column display width as minimum. But --recommends functions as that tool, which is why rather than trying to redo the output of recommends, which is very accurate and informative, it points to it.    

cariboo, great, thanks a lot, my suspiction was that you had only the /dev/root, so that may correctable, usually when you see /dev/root it's a dual entry, so it looks like that single case was simply a failure.

---

### Post by user232 on 2018-03-18
cariboo, can you show me one more piece of data? 

```
readlink /dev/root
``` I think it's simply pointing somewhere that pinxi didn't expect. I'm doing one small change to avoid one possible circumstance, but your output will show me the reason it's not correctly finding the real dev id of /dev/root, which is usually a link to somewhere else.

---

### Post by cariboo on 2018-03-18
I don't get any output when running the command.

---

### Post by user232 on 2018-03-18
mörgæs, sorry, missed the flags question, You're looking for the -f option, which prints all the flags. That's again, to avoid clutter. Back in the day I dealt with some kernel guys from a few distros, and they had a list of the flags they considered most important to see, so that's why the regular -Cx output shows the short list of those flags (and none for ARM, but with a message to show all with -f). pinxi has many different verbosity and output levels, -zv8 for example basically turns everything on. See --help for the full list of options. inxi was initially developed as an IRC support tool first, and a forum support tool second, so terseness of output was a high priority, and still is for the shorter forms, since there's no point in having short forms if they aren't short.

---

### Post by #&amp;thj^% on 2018-03-18
> **cariboo said:**
> I don't get any output when running the command.

+1
Same Here
How ever:
```
pinxi -D
Drives:
  HDD Total Size: 1.36 TB used: 29.32 GB (2.1%) 
  ID-1: /dev/sda model: WDC_WD1001FALS-0 size: 931.51 GB 
  ID-2: /dev/sdb model: WDC_WD5000AAKS-0 size: 465.76 GB 

```

---

### Post by user232 on 2018-03-18
cariboo, that explains it. Usually /dev/root is a link to either /dev/sda1 or something like that, or to /dev/disk/by-uuid 

Please post the output of: 

```
cat /proc/cmdline
``` 

This appears to a newish variant,, in the past, /dev/root was always a symbolic link to the real location, but now that is hidden for some inexplicable reason.

---

### Post by user232 on 2018-03-18
cariboot, also the output of the command: mount 

Basically over the past years, the old way to do this changed, and the internet has not yet caught on to this. I don't really like either solution but one of them will work almost for sure.

---

### Post by Bashing-om on 2018-03-18
user232; 

Is it to soon for the wish list ?
Weather - what is is important to me, and I sure like having it available in terminal:
> 
sysop@x1604:~$ inxi -xxw
Weather:   Conditions: 59 F (15 C) - Mostly Cloudy Wind: From the East at 6 MPH Humidity: 51%
           Pressure: 29.89 in (1012 mb) Time: March 18, 3:40 PM CDT (America/Chicago)
sysop@x1604:~$ 


Yeah, I do have a couple of other scripts to scrape NOAA's data base - inxi is just fast and immediate.

[INDENT]thanks for your effort :)
[/INDENT]

---

### Post by user232 on 2018-03-18
Bashing-om, it's worth checking the command before assuming it's not there. pinxi --help is currently I believe feature complete as of a few days ago, that is, everything in there that is listed currently works. 

A core requirement for pinxi was that it would be feature complete or better with inxi before release. I've learned from watching terrible major new version changes from gnome, kde, gtk, etc, where nothing works, and the say, 5.0 release is actually little better than an early alpha development branch release. KDE, for example, usually is not feature complete until years into the cycle, usually by version x.10 or x.12 (which is why I no longer use those big desktops, but that's not relevant to this thread). Gnome is similar. I decided to follow the exact opposite course, and deliver all the features, plus new ones, on the new major version upgrade that inxi has, only better. And just to be on the safe side, based on the number of issues I've now gotten during beta testing, I'm also going to release 2.9.01 first, so that a wider testing pool can bang it around before I do the 3.0.0 major release. 

Most of the issues I'm now getting are also inxi bugs, by the way, the failure to handle /dev/root for example, some ARM stuff, the just completed issue about showing the actual audio and network USB device drivers, not just the generic string I was showing, those are actually all enhancements over inxi.

---

### Post by #&amp;thj^% on 2018-03-18
> **user232 said:**
> Bashing-om, it's worth checking the command before assuming it's not there. pinxi --help is currently I believe feature complete as of a few days ago, that is, everything in there that is listed currently works. 



Did read the help guide:
```
pinxi -W 
Error 20: Option: W has been disabled by the pinxi distribution maintainer.

```

---

### Post by user232 on 2018-03-18
Oh, this is a NEW bug!!! I must have initroduced that by accident very recently, will correct asap. But fear not, -w/W both work fine, that's just a bug.

---

### Post by #&amp;thj^% on 2018-03-18
> **user232 said:**
> Oh, this is a NEW bug!!! I must have initroduced that by accident very recently, will correct asap. But fear not, -w/W both work fine, that's just a bug.

Thanks for your contributions. :)
Best Regards

---

### Post by user232 on 2018-03-18
That was a silly bug I introduced by accident, sorry about that. 2.9.00-435-p corrects it, and a few other issues.

---

### Post by #&amp;thj^% on 2018-03-18
Yes Sir that did the trick! ;)
```
pinxi -w
Weather:
  Conditions: 77 F (25 C) - Scattered Clouds 
  Time: Sun 18 Mar 2018 04:44:49 PM MDT (America/Chicago) 
```

---

### Post by Bashing-om on 2018-03-18
user232; Hey ..

Good work ! But a very slight Uh Ohh ..

Uppercase W option returns:
> 
sysop@x1604:~$ pinxi -W
Error 10: Unsupported value:  for option: W
Check -h for correct parameters.
sysop@x1604:~$


it is shown in help as a valid option:
> 
-w -W  Humidity, barometric pressure.


[INDENT][INDENT]picky picky picky
[/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2018-03-18
Just add a needed parameter like a zip code or location code or City and State EG:
```
pinxi -W 84115
```
And:
```
pinxi -W Sandy,Ut
Weather:
  Conditions: 40 F (4 C) - Mostly Cloudy 
  Time: Sun 18 Mar 2018 11:33:28 PM MDT 
```

```

>> pinxi -W Portland,Or
Weather:
  Conditions: 53 F (12 C) - Mostly Cloudy 
  Time: Sun 18 Mar 2018 11:33:57 PM PDT 
```

---

### Post by Bashing-om on 2018-03-18
1fallen; Uhhh :)

> **1fallen said:**
> Just add a needed parameter like a zip code or location code or City and State EG:
```
pinxi -W 84115
```

As I live and learn :)

---

### Post by #&amp;thj^% on 2018-03-18
I'm Liking this Version. ;)
```
sudo pinxi -CGm 
[sudo] password for me: 
Memory:
  RAM: total: 11.64 GB used: 1.17 GB (10.0%) 
  Array-1: capacity: 32 GB slots: 2 EC: None 
  Device-1: XMM1 size: 4 GB speed: 2133 MT/s 
  Device-2: XMM3 size: 8 GB speed: 2400 MT/s 
CPU:
  Topology: Quad Core model: Intel Core i5-6400 type: MCP L2 cache: 6144 KB 
  Speed: 900 MHz min/max: 800/3300 MHz Core speeds: 1: 900 2: 900 3: 900 
  4: 900 
Graphics:
  Card-1: Intel HD Graphics 530 driver: i915 v: kernel 
  Card-2: NVIDIA GF114 [GeForce GTX 560 Ti] driver: nvidia v: 390.42 
  Display Server: X.Org 1.19.6 driver: nvidia,modesetting 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: GeForce GTX 560 Ti/PCIe/SSE2 
  version: 4.6.0 NVIDIA 390.42 direct render: Yes 

```

```
sudo pinxi -CGmxx 
Memory:
  RAM: total: 11.64 GB used: 1.17 GB (10.1%) 
  Array-1: capacity: 32 GB slots: 2 EC: None max module size: N/A 
  Device-1: XMM1 size: 4 GB speed: 2133 MT/s type: DDR4 
  manufacturer: Samsung part-nu: M378A5143EB1-CPB 
  Device-2: XMM3 size: 8 GB speed: 2400 MT/s type: DDR4 
  manufacturer: Kingston part-nu: HP24D4U7S8MBP-8 
CPU:
  Topology: Quad Core model: Intel Core i5-6400 type: MCP arch: Skylake-S 
  rev: 3 L2 cache: 6144 KB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 21696 
  Speed: 3181 MHz min/max: 800/3300 MHz Core speeds: 1: 3241 2: 3299 3: 3243 
  4: 3222 
Graphics:
  Card-1: Intel HD Graphics 530 driver: i915 v: kernel bus ID: 00:02.0 
  chip ID: 8086:1912 
  Card-2: NVIDIA GF114 [GeForce GTX 560 Ti] driver: nvidia v: 390.42 
  bus ID: 01:00.0 chip ID: 10de:1200 
  Display Server: X.Org 1.19.6 driver: nvidia,modesetting 
  resolution: 1920x1080~60Hz 

```

---

### Post by user232 on 2018-03-18
1fallen, the auto start line wrap is a configuration option as well, currently the Start key wraps to its own line by default if display width is less than 90 columns. I was tired of trying to squeeze data into a tiny 80 column display and wasting 10 or 11 of those columns on the indentation, so now it wraps, and only indents 2 columsn.    

Iif the INDENT config item is set to < 11, it will also trip that Starter key wrap for any width.   

The just released 2.9.00-0447-p has a fix for the max module size: N/A item, now it's going to provide a reasonable guess if it can about max module size, noting that it's an estimate.   

I had also forgotten to include the confg file options:   

 ```
# if < 11, forces Line main key to wrap to its own line and sets indent to 2  
# if > 11, expands output indent 
INDENT=integer  
# Changes trip point where the line key wraps to its own line. Default is 90 columns
INDENT_MIN=integer 
```   

Those are now in 0437-p

---

### Post by #&amp;thj^% on 2018-03-18
> **user232 said:**
> 
The just released 2.9.00-0436-p has a fix for the max module size: N/A item, now it's going to provide a reasonable guess if it can about max module size, noting that it's an estimate.
Very Nice! 2 Thumbs Up. ;)
```
Memory:
  RAM: total: 11.64 GB used: 1.18 GB (10.1%) 
  Array-1: capacity: 32 GB slots: 2 EC: None max module size: 16 GB 
  note: est 
  Device-1: XMM1 size: 4 GB speed: 2133 MT/s type: DDR4 
  manufacturer: Samsung part-nu: M378A5143EB1-CPB 
  Device-2: XMM3 size: 8 GB speed: 2400 MT/s type: DDR4 
  manufacturer: Kingston part-nu: HP24D4U7S8MBP-8 

```
Very helpful!

---

### Post by user232 on 2018-03-18
1fallen, be very careful trusting that RAM data, of all the features I've put into inxi, by far the worst in terms of quality of data used was RAM. Those capacity and max module size values are often total fictions, often literally I've seen the mobo vendors paste in data from a totally different motherboard, that is completely wrong. inxi/pinxi takes a stab of correcting obvious logical errors, such as if the actual max size module found is greater than the listed max module size, it will note the actually largest size found in a slot, and say: note: est. The capacity is the same, even if you don't see 'note: est/check', that doesn't mean it's actually right, it simply means that no logical contradictions were found in the math. The per slot data, on the other hand, is very reliable, because it comes from the actual ram installed, which is why pinxi always trusts the per slot data over the capacity/max module size data.

---

### Post by #&amp;thj^% on 2018-03-18
> **user232 said:**
> 1fallen, be very careful trusting that RAM data, of all the features I've put into inxi, by far the worst in terms of quality of data used was RAM. Those capacity and max module size values are often total fictions, often literally I've seen the mobo vendors paste in data from a totally different motherboard, that is completely wrong. inxi/pinxi takes a stab of correcting obvious logical errors, such as if the actual max size module found is greater than the listed max module size, it will note the actually largest size found in a slot, and say: note: est. The capacity is the same, even if you don't see 'note: est/check', that doesn't mean it's actually right, it simply means that no logical contradictions were found in the math. The per slot data, on the other hand, is very reliable, because it comes from the actual ram installed, which is why pinxi always trusts the per slot data over the capacity/max module size data.
Understood, But an experienced eye would know that! Still useful for my personal needs. And in helping others.
Very Nice work user232.
Looking Forward to the Final Version 3

---

### Post by user232 on 2018-03-18
> Looking Forward to the Final Version 3  

Believe, me, so am I, but I said in the very beginning that pinxi would not become inxi until there were no outstanding issues or bugs, and unfortunately for me, but good for users, not only have we found and fixed a myriad of pinxi bugs, we're now moving in on a lot of old inxi weaknesses and bugs, all the stuff I've worked on almost over the last days has been actual bugs in inxi, or weaknesses, or new features like export to json.

---

### Post by #&amp;thj^% on 2018-03-18
No Rush Intended, please take all the time you need, I find this tool very valuable.
And your work is respected and appreciated. I find it Fun to watch Linux Apps Grow and Evolve! ;)
I know coding can be at times a Thankless Ordeal.
But Not Here!

---

### Post by user232 on 2018-03-18
1fallen, thanks, I appreciate it. I can't do this stuff at this level all the time, but I have actually enjoyed most of this process, from start to now. I'm very impressed by the quality of beta testing so far, by the way, it's helped make pinxi much, much stronger than it would have been.

---

### Post by hrsetrdr on 2018-03-19
```
 user@Inspiron-15-7000-Gaming:/usr/local/bin$ sudo pinxi -zv8
System:
  Host: Inspiron-15-7000-Gaming Kernel: 4.13.0-36-generic x86_64 bits: 64 
  compiler: gcc v: 5.4.0 Desktop: MATE 1.12.1 info: mate-panel 
  dm: lightdm 1.18.3 Distro: Ubuntu 16.04.3 LTS 
Machine:
  Type: Laptop System: Dell product: Inspiron 15 7000 Gaming v: N/A 
  serial: <filter> Chassis: type: 10 serial: <filter> 
  Mobo: Dell model: 0TXG2N v: X02 serial: <filter> UEFI: Dell v: 1.5.3 
  date: 01/25/2018 
Battery:
  BAT-0: charge: 49.3 Wh condition: 64.7/74.0 Wh (87%) volts: 12.1/11.4 
  model: SMP DELL 71JF452 type: Li-poly serial: <filter> status: Discharging 
Memory:
  Array-1: capacity: 32 GB slots: 2 EC: None max module size: 16 GB 
  note: est 
  Device-1: ChannelA-DIMM0 size: No Module Installed 
  Device-2: DIMM B size: 8 GB speed: 2400 MHz type: DDR4 detail: synchronous 
  bus width: 64 bits total: 64 bits manufacturer: SK Hynix 
  part-nu: HMA81GS6AFR8N-UH serial: 280C9336 
PCI Slots:
  Slot: 0 type: x16 PCI Express J6B2 status: In Use length: Long 
  Slot: 1 type: x1 PCI Express J6B1 status: Available length: Short 
  Slot: 2 type: x1 PCI Express J6D1 status: Available length: Short 
  Slot: 3 type: x1 PCI Express J7B1 status: Available length: Short 
  Slot: 4 type: x1 PCI Express J8B4 status: Available length: Short 
  Slot: 5 type: x1 PCI Express J8D1 status: In Use length: Short 
  Slot: 6 type: x1 PCI Express J8D2 status: Available length: Short 
  Slot: 7 type: 32-bit PCI J8B3 status: Available length: Short 
CPU:
  Topology: Quad Core model: Intel Core i5-7300HQ type: MCP arch: Skylake 
  rev: 9 L2 cache: 6144 KB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 19968 
  Speed: 1146 MHz min/max: 800/3500 MHz Core speeds: 1: 1146 2: 1146 3: 1149 
  4: 1162 
Graphics:
  Card-1: Intel Device driver: i915 v: kernel bus ID: 00:02.0 
  chip ID: 8086:591b 
  Card-2: NVIDIA Device driver: N/A bus ID: 01:00.0 chip ID: 10de:1c8d 
  Display Server: X.Org 1.19.3 driver: modesetting unloaded: vesa,fbdev 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel Kabylake GT2 version: 4.5 Mesa 17.0.7 
  compat-v: 3.0 direct render: Yes 
Audio:
  Card-1: Intel Device driver: snd_hda_intel v: kernel bus ID: 00:1f.3 
  chip ID: 8086:a171 
  Sound Server: ALSA v: k4.13.0-36-generic 
Network:
  Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
  driver: r8169 v: 2.3LK-NAPI port: d000 bus ID: 02:00 chip ID: 10ec:8168 
  IF: enp2s0 state: down mac: <filter> 
  Card-2: Intel Wireless 3165 driver: iwlwifi v: kernel bus ID: 03:00 
  chip ID: 8086:3165 
  IF: wlp3s0 state: up mac: <filter> 
  IP v4: <filter> type: dynamic wlp3s0 scope: global broadcast: <filter> 
  IP v6: <filter> scope: link 
  WAN IP: <filter> 
Drives:
  HDD Total Size: 232.89 GB used: 6.18 GB (2.7%) 
  ID-1: /dev/nvme0n1 model: Samsung_SSD_960_EVO_250GB size: 232.89 GB 
  serial: <filter> 
  Message: No Optical or Floppy data was found. 
RAID:
  Message: No RAID data was found. 
Partition:
  ID-1: / size: 220.87 GB used: 6.17 GB (2.8%) fs: ext4 dev: /dev/nvme0n1p2 
  label: N/A uuid: 91ab4c33-b9b6-454d-ad44-d5387c8ca062 
  ID-2: /boot/efi size: 511.0 MB used: 3.4 MB (0.7%) fs: vfat 
  dev: /dev/nvme0n1p1 label: N/A uuid: 2628-6EBB 
  ID-3: swap-1 size: 7.87 GB used: 0 KB (0.0%) fs: swap dev: /dev/nvme0n1p3 
  label: N/A uuid: c1806d25-830c-4c58-aa6e-2f93d18a5ced 
Unmounted:
  ID-1: /dev/nvme0n1 size: 232.89 GB fs: root required label: N/A uuid: N/A 
USB:
  Hub: 1:1 usb: 2.00 type: Full speed (or root) hub chip ID: 1d6b:0002 
  Device-1: Intel bus ID: 1:2 usb: 2.00 type: Bluetooth chip ID: 8087:0a2a 
  Device-2: Microdia bus ID: 1:3 usb: 2.00 type: Video chip ID: 0c45:6a06 
  Hub: 2:1 usb: 3.00 type: Full speed (or root) hub chip ID: 1d6b:0003 
Sensors:
  Missing: Required tool sensors not installed. Check --recommends 
Repos:
  Active apt sources in: /etc/apt/sources.list 
  1: deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
  2: deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
  3: deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
  4: deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
  5: deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
  6: deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
  7: deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
  8: deb http://security.ubuntu.com/ubuntu xenial-security main restricted
  9: deb http://security.ubuntu.com/ubuntu xenial-security universe
  10: deb http://security.ubuntu.com/ubuntu xenial-security multiverse
  Active apt sources in: /etc/apt/sources.list.d/google-chrome.list 
  1: deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
Processes:
  CPU  % used - Command - pid - Memory: MB / % used - top: 5 
  1: cpu: 3.3% command: chrome pid: 3719 mem: 215.2MB (2.7%) 
  2: cpu: 2.3% command: chrome pid: 5560 mem: 202.8MB (2.5%) 
  3: cpu: 2.0% command: chrome pid: 3808 mem: 117.4MB (1.4%) 
  4: cpu: 0.7% command: xorg pid: 948 mem: 63.1MB (0.8%) 
  5: cpu: 0.3% command: mate-terminal pid: 5613 mem: 26.3MB (0.3%) 
  Memory MB/% used - Command - pid - CPU: % used - top: 5 
  1: mem: 215.2 MB (3.3%) command: chrome pid: 3719 cpu: 2.7% 
  2: mem: 202.8 MB (2.3%) command: chrome pid: 5560 cpu: 2.5% 
  3: mem: 117.4 MB (2.0%) command: chrome pid: 3808 cpu: 1.4% 
  4: mem: 67.9 MB (0.0%) command: mate-panel pid: 1752 cpu: 0.8% 
  5: mem: 63.1 MB (0.7%) command: xorg pid: 948 cpu: 0.8% 
Info:
  Processes: 181 Uptime: 4:43 Memory: 7.66 GB used: 657.9 MB (8.4%) 
  Init: systemd v: 229 runlevel: 5 Compilers: gcc: N/A Shell: bash 4.3.48 
  running in: mate-terminal pinxi: 2.9.00-448-p 

```

---

### Post by user232 on 2018-03-19
hrsetrdr, thanks, that was an unmounted failure to handle nvme0n1 primary disk id, the rule it used to check was too loose, I've tightened the test to exclude that device name when it's not followed by p1 type partition data. 

that is corrected in 2.9.00-0450-p

---

### Post by cariboo on 2018-03-19
Been off at work and just saw your questions, here you go:

```
pi@haven:~ $ cat /proc/cmdline
8250.nr_uarts=0 bcm2708_fb.fbwidth=656 bcm2708_fb.fbheight=416 bcm2708_fb.fbswap=1 vc_mem.mem_base=0x3ec00000 vc_mem.mem_size=0x40000000  dwc_otg.lpm_enable=0 console=ttyS0,115200 console=tty1 root=PARTUUID=d2099afb-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait
```

and

```
pi@haven:~ $ mount
/dev/sda2 on / type ext4 (rw,noatime,data=ordered)
devtmpfs on /dev type devtmpfs (rw,relatime,size=470180k,nr_inodes=117545,mode=755)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,mode=755)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
sunrpc on /run/rpc_pipefs type rpc_pipefs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/sda1 on /boot type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=94956k,mode=700,uid=1000,gid=1000)
```

---

### Post by user232 on 2018-03-19
cariboo, thanks, I see there is another variant in root=PARTUUID=d2099afb-02, and that's not one I know about yet, but happily, the output of mounts shows a very clear way to get the real /dev,  

/dev/sda2 on / type ext4 (rw,noatime,data=ordered) 

so that's an easy match. 2.9.00-0452-p has this update, so the disk size / partition / unmounted stuff should hopefully now be corrected. Thanks for exposing this very old issue re /dev/root, I'd never realized that was a simple kernel configuration option whether to make that virtual device also show a symbolic link path. Hopefully the mount method will handle 'most' cases, which is I think the best pinxi should try to do in such corner cases.

---

### Post by #&amp;thj^% on 2018-03-19
BTW you get a 2 for one here with me>>>Arch Linux and Ubuntu.
This was a big treat for me with;
```
inxi --usb
/usr/bin/inxi: illegal option -- -
Error 7: One of the options you entered in your script parameters: --usb
is not supported.The option may require extra arguments to work.
For supported options (and their arguments), check the help menu: inxi -h

```
Now with:
```
pinxi --usb
USB:
  Hub: 1:1 usb: 2.00 type: Full speed (or root) hub 
  Device-1: Logitech Unifying Receiver bus ID: 1:2 type: Keyboard 
  Device-2: Realtek 3-in-1 (SD/SDHC/SDXC) Card Reader bus ID: 1:4 
  type: Mass Storage 
  Device-3: Intel bus ID: 1:5 type: Bluetooth 
  Hub: 1:6 usb: 1.01 type: Genesys Logic USB 1.1 Hub 
  Device-4: Logitech Unifying Receiver bus ID: 1:7 type: Keyboard 
  Device-5: Linksys WUSB100 v1 RangePlus Wireless Network Adapter [Ralink 
  RT2870] 
  bus ID: 1:8 type: Vendor Specific Protocol 
  Hub: 2:1 usb: 3.00 type: Full speed (or root) hub 

```
So I'm a happy camper. :)

---

### Post by user232 on 2018-03-19
Re --usb, it was actually just something I threw out because as I was developing perl pinxi, I wanted to test as proof of concept adding a few new items using existing data sources that already were there internally, but used for different things, so once I got the usb data internal logic done, I was like, hmm, well, I did have a feature request made a long time ago for usb, but I didn't feel like fighting against inxi's headaches to add it, so I ignored it.  

--slots were the same, I already had the data source processed, so I said, hmmm, ok, well, the data is there, I have the data, so let's see how the new row generator logic works on a brand new item. 

The answer in both cases was, it works really, really well. No comparison to inxi. You'll notice that visibly in the output, for example, the lines almost always wrap correctly, that's because that line length logic is now fully automated internally, and all I have to do is feed it the data it's expecting, and poof, it 'just  works'. 

there are  lot of such hidden or not so hidden little nuggets in pinxi, the better you know inxi, the easier it is to find them. A recent example is the just added usb audio and network device actual driver output, not the static string 'driver: USB Audio/Network' you saw before. But there a lot of those in new inxi, pinxi. --usb and --slots are just the more visible one. Note that one of the HUGE changes in pinxi is that I can use long options, which frees me to add new stuff without worrying, and without using the convoluted -! or -@ syntax inxi used. inxi was almost literally also out of single letter options, and was definitely out of letter options that would actually match the feature name.

---

### Post by Bashing-om on 2018-03-19
user232;

Still look'n good :)
release 18.04 to be - wayland DE - results:
```

sysop@ubie1804:~$ sudo pinxi -zv8 
System:
  Host: ubie1804 Kernel: 4.15.0-12-generic x86_64 bits: 64 compiler: gcc 
  v: 7.3.0 Desktop: N/A dm: gdm3 
  Distro: Ubuntu Bionic Beaver (development branch) 
Machine:
  Type: Desktop Mobo: Abit model: KN9(NF-MCP55 series) v: 1.x serial: N/A 
  BIOS: Phoenix LTD v: 6.00 PG date: 11/19/2007 
Memory:
  Array-1: capacity: 16 GB slots: 4 EC: None max module size: 4 GB 
  Device-1: A0 size: 2 GB info: double-bank speed: Unknown type: Unknown 
  detail: none bus width: 64 bits total: 64 bits manufacturer: N/A 
  part-nu: Not Specified serial: Not Specified 
  Device-2: A1 size: 2 GB info: double-bank speed: Unknown type: Unknown 
  detail: none bus width: 64 bits total: 64 bits manufacturer: N/A 
  part-nu: Not Specified serial: Not Specified 
  Device-3: A2 size: No Module Installed 
  Device-4: A3 size: No Module Installed 
PCI Slots:
  Slot: 1 type: 32-bit PCI PCI0 status: In Use length: Long 
  Slot: 2 type: 32-bit PCI PCI1 status: Available length: Long 
  Slot: 3 type: 32-bit PCI PCI2 status: In Use length: Long 
  Slot: 4 type: 32-bit PCI Express PCI3 status: In Use length: Long 
  Slot: 5 type: 32-bit PCI Express PCI4 status: In Use length: Long 
  Slot: 6 type: 32-bit PCI Express PCI5 status: In Use length: Long 
  Slot: 7 type: 32-bit PCI Express PCI6 status: In Use length: Long 
CPU:
  Topology: Dual Core model: AMD Athlon 64 X2 5000+ type: MCP 
  arch: K8 rev.F+ rev: 2 L2 cache: 1024 KB 
  flags: lm nx pae sse sse2 sse3 svm bogomips: 3999 
  Speed: 1000 MHz min/max: 1000/2600 MHz Core speeds: 1: 1000 2: 1000 
Graphics:
  Card-1: NVIDIA GK208 [GeForce GT 710B] driver: nouveau v: kernel 
  bus ID: 06:00.0 chip ID: 10de:128b 
  Display Server: X.org 1.19.6 driver: nouveau tty: 80x24 
  Message: Unable to show advanced data. Required tool glxinfo missing. 
Audio:
  Card-1: NVIDIA MCP55 High Definition Audio driver: snd_hda_intel v: kernel 
  bus ID: 00:06.1 chip ID: 10de:0371 
  Card-2: NVIDIA GK208 HDMI/DP Audio Controller driver: snd_hda_intel 
  v: kernel bus ID: 06:00.1 chip ID: 10de:0e0f 
  Sound Server: ALSA v: k4.15.0-12-generic 
Network:
  Card-1: Accton SMC2-1211TX driver: 8139too v: 0.9.28 port: 9c00 
  bus ID: 01:09 chip ID: 1113:1211 
  IF: enp1s9 state: unknown speed: 100 Mbps duplex: full mac: <filter> 
  IP v4: <filter> type: dynamic noprefixroute enp1s9 scope: global 
  broadcast: <filter> 
  IP v6: <filter> virtual: noprefixroute scope: link 
  IF-ID-1: enp0s8 state: down mac: <filter> 
  IF-ID-2: enp0s9 state: down mac: <filter> 
  WAN IP: <filter>
Drives:
  HDD Total Size: 344.68 GB used: 13.23 GB (3.8%) 
  ID-1: /dev/sda model: Samsung_SSD_850 size: 232.89 GB serial: <filter> 
  rev: 2B6Q 
  ID-2: /dev/sdb model: PNY_CS900_120GB size: 111.79 GB serial: <filter> 
  rev: 0711 
  Optical-1: /dev/sr0 vendor: TOSHIBA model: DVD-ROM SD-M1502 rev: 1012 
  dev-links: cdrom,dvd 
  Features: speed: 48 multisession: yes audio: yes dvd: yes rw: none 
  state: running 
  Optical-2: /dev/sr1 vendor: HL-DT-ST model: DVD-RAM GH22NP20 rev: 2.00 
  dev-links: cdrw,dvdrw 
  Features: speed: 48 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r,dvd-ram state: running 
RAID:
  Message: No RAID data was found. 
Partition:
  ID-1: / size: 28.71 GB used: 4.78 GB (16.6%) fs: ext4 dev: /dev/sdb5 
  label: u1804 uuid: 0b89d785-9ba8-4bd5-a41a-43462459c230 
  ID-2: /media/sysop/x1604 size: 136.37 GB used: 8.45 GB (6.2%) fs: ext4 
  dev: /dev/sda1 label: x1604 uuid: d9c2a8e6-d014-42a6-846f-7e7892f4aef5 
  ID-3: swap-1 size: 4.39 GB used: 0 KB (0.0%) fs: swap dev: /dev/sda5 
  label: N/A uuid: 8d4743bc-8e47-4650-b5fd-1ea904d4ecda 
Unmounted:
  ID-1: /dev/sdb1 size: 7.81 GB fs: ext4 label: m1804root 
  uuid: 060f35b0-f64d-4c96-8f37-0b35c27113a7 
  ID-2: /dev/sdb2 size: 9.77 GB fs: ext4 label: m1804home 
  uuid: ba850e4f-2af7-4261-96e4-b5ccd9317902 
  ID-3: /dev/sdb3 size: 5.86 GB fs: ext4 label: m1804var 
  uuid: 64edeaf6-307c-4b3d-be88-1f293e06b081 
  ID-4: /dev/sdb6 size: 9.77 GB fs: ext4 label: bups 
  uuid: a0c6dc1f-51d3-4824-b770-ce42d777277a 
  ID-5: /dev/sdb7 size: 9.77 GB fs: ext4 label: data 
  uuid: fe9cee2e-6812-46e1-b0a0-b03d5094763a 
USB:
  Hub: 1:1 usb: 2.00 type: Full speed (or root) hub chip ID: 1d6b:0002 
  Hub: 2:1 usb: 1.10 type: Full speed (or root) hub chip ID: 1d6b:0001 
  Device-1: SiGma Micro bus ID: 2:2 usb: 1.10 type: Mouse chip ID: 1c4f:0034 
Sensors:
  Missing: Required tool sensors not installed. Check --recommends 
Repos:
  Active apt sources in: /etc/apt/sources.list 
  1: deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) bionic main restricted
  2: deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) bionic-updates main restricted
  3: deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) bionic universe
  4: deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) bionic-updates universe
  5: deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) bionic multiverse
  6: deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) bionic-updates multiverse
  7: deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) bionic-backports main restricted universe multiverse
  8: deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
  9: deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) bionic-security main restricted
  10: deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) bionic-security universe
  11: deb [http://mirror.steadfast.net/ubuntu/](http://mirror.steadfast.net/ubuntu/) bionic-security multiverse
Processes:
  CPU  % used - Command - pid - Memory: MB / % used - top: 5 
  1: cpu: 5.4% command: gnome-shell pid: 1463 mem: 198.6MB (5.0%) 
  2: cpu: 4.7% command: firefox pid: 2090 mem: 263.4MB (6.6%) 
  3: cpu: 2.6% command: firefox pid: 2145 mem: 200.6MB (5.0%) 
  4: cpu: 2.5% command: packagekitd pid: 1085 mem: 33.5MB (0.8%) 
  5: cpu: 1.4% command: [kworker/u4:1] pid: 39 mem: 0.00MB (0.0%) 
  Memory MB/% used - Command - pid - CPU: % used - top: 5 
  1: mem: 263.4 MB (4.7%) command: firefox pid: 2090 cpu: 6.6% 
  2: mem: 200.6 MB (2.6%) command: firefox pid: 2145 cpu: 5.0% 
  3: mem: 198.6 MB (5.4%) command: gnome-shell pid: 1463 cpu: 5.0% 
  4: mem: 164.9 MB (1.2%) command: gnome-software pid: 1738 cpu: 4.1% 
  5: mem: 130.1 MB (0.7%) command: gnome-shell pid: 963 cpu: 3.2% 
Info:
  Processes: 218 Uptime: 8 min Memory: 3.85 GB used: 1.31 GB (33.9%) 
  Init: systemd v: 237 runlevel: 5 Compilers: gcc: N/A Shell: bash 4.4.18 
  running in: gnome-terminal- pinxi: 2.9.00-454-p 
sysop@ubie1804:~$ 

```


[INDENT][INDENT]come on wayland
[/INDENT][/INDENT]

---

### Post by user232 on 2018-03-19
Just as aside re the wayland detections, it doesn't look like that prerelease version has the required stuff running for pinxi to ID wayland, or xorg for that matter. The giveaway is the tty: and the glxiinfo message, plus the lack of Waylan (xorg 1....) in the graphics output. Pinxi gets wayland data from a few places, which if none are set, it has no way to know it's wayland.  

$WAYLAND_DISPLAY $XDG_SESSION_TYPE 

If neither of those are set, there's no way for pinxi/inxi to detect it's running in wayland. 

pinxi/inxi also have a longer term problem that once wayland fully replaces x, all the x reporting tools that currently run in xwayland won't be there, and as far as I know, wayland developers have not done anything to resolve this issue. At least not that I'm aware of, so that's in the wayland dev ballpark in terms of users being able to get display server data from querying various tools.

---

### Post by user232 on 2018-03-20
Release 2.9.00-456-p hopefully closes the last significant issue I'm aware of, failure to ID correctly USB networking devices. The failure is visible when you see ID-IF-x: in the start of the line instead of IF: that means it failed to actually get the data at the right time. 

I'm hoping the last fix corrects this issue, if it does, I'm releasing inxi 2.9.01 tomorrow.

---

### Post by user232 on 2018-03-21
Last comment: I've decided that I like using pinxi as the inxi development branch, so I'm doing that. So pinxi is not going away, it's going to stay the development branch for inxi.

---

### Post by mc4man on 2018-03-21
Re: usb network
seems ok
previous - 
Network: ...
           Card-3: Realtek RTL8812AU 802.11a/b/g/n/ac WLAN Adapter type: USB driver: rtl8812au bus ID: 3:4 
           chip ID: 0bda:8812 
           IF-ID-1: wlx00c0ca952733 state: up speed: N/A duplex: N/A mac: <filter> 
          ....

current - 
Network: Network:  ... 
           Card-3: Realtek RTL8812AU 802.11a/b/g/n/ac WLAN Adapter type: USB driver: rtl8812au bus ID: 3:4 
           chip ID: 0bda:8812 
           IF: wlx00c0ca952733 state: up mac: 00:c0:ca:95:27:33 
          ...

---

### Post by user232 on 2018-03-21
mc4man, thanks a lot, that confirms my fix worked, great to see. You'll notice that it's now aware better that it's wifi so it doesn't print the duplex and speed items, which aren't relevant for wifi. Good, I thought that fix should do it, but you never know until real data confirms it.

---

### Post by mörgæs on 2018-03-22
After updating with the command ```
sudo pinxi -U
``` and receiving the output ```
Starting pinxi self updater.
Using tiny as downloader.
Currently running pinxi version number: 2.9.03
Current version patch number: 05
Current version release date: 2018-03-22
Updating pinxi in /usr/local/bin using inxi-perl branch as download source...
Successfully updated to inxi-perl branch version: 2.9.03
New inxi-perl branch version patch number: 05
New inxi-perl branch version release date: 2018-03-22
To run the new version, just start pinxi again.
----------------------------------------

Starting download of man page file now.
Skipping man download because branch version is being used.


```

I tried again the command ```
pinxi -fzv8
```

Output was partly garbled:

```
(end of Repos section)
           1: deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

$VAR1 = [
          'tux      11187  4.1  8.6 2298632 348392 ?      sl   20:05   0:47 /usr/lib/firefox/firefox',
          'tux      11365  1.5  4.4 1744968 181248 ?      sl   20:06   0:16 /usr/lib/firefox/firefox -contentproc -childid 4 -isforbrowser -intprefs 6:50|7:-1|19:0|34:1000|42:20|43:5|44:10|51:0|57:128|58:10000|63:0|65:400|66:1|67:0|68:0|69:100|74:0|75:120|76:120 ... (snip some 25 lines)

(beginning of Processes section)
```

Tux is my user name. 

Do you need me to run more tests in order to see what's wrong?

---

### Post by user232 on 2018-03-22
mörgæs, I left  a debugger in place, that's been corrected. Remember also that -f lower case just means show all cpu flags, and will trip the -C option, -F is probably the one you want. pinxi also now will install its own man page if you also use the --man option with -U. 

pinxi -U --man

---

### Post by mörgæs on 2018-03-23
The flag I wanted was -f as discussed [here]("https://ubuntuforums.org/showthread.php?t=2387337&page=2&p=13749507&viewfull=1#post13749507"). 

Thanks for the fast bug fixes. Output is correct now.

A little surprised to see a variable with the name $VAR1 but as I'm not going to use the source code I can live with that :-)

---

### Post by user232 on 2018-03-23
$VAR1 is what Perl Dumper calls its output variable. Has no meaning, not mine, it's what it is. Dumper is what dumps complex data structures into visible form, very useful for debugging complicated issues, but the problem is, now and then I forget to turn it off, heh.

---

### Post by mc4man on 2018-03-25
So it seems the master branch (inxi) is now at the perl branch (pinxi) to the 3/24 commits. Is there a means to in place update the master branch? (-U

---

### Post by uniqueason on 2018-03-25
Hi guys!! 
I wonder what is wrong with my  command 
pinxi -zv8 --output xml --output-file /tmp/inventaire

---

### Post by user232 on 2018-03-25
uniqueason, what do you mean? Actually, I see, there's a glitch. Looks like the validation is confused. I'll have that fixed shortly.     

mc4man, master -U working depends on the configuration options made by the packagers.  If you want the current latest however, you can just use pinxi since that's either at the same point as master, or ahead. Right now for example it's ahead.

---

### Post by user232 on 2018-03-25
uniqueason, that's corrected in inxi/pinxi 2.9.07, thanks for bringing that to my attention. Someone had requested a slight modification to the output but then never tested it, I assumed they had, so I forgot to.

---

### Post by mörgæs on 2018-03-26
Another test on another computer. The command 

```
sudo pinxi -zv8
```

yields

```
Use of uninitialized value $server in lc at /usr/local/bin/pinxi line 7626.
```

---

### Post by mc4man on 2018-03-26
> **user232 said:**
> 

mc4man, master -U working depends on the configuration options made by the packagers.  If you want the current latest however, you can just use pinxi since that's either at the same point as master, or ahead. Right now for example it's ahead.
No big deal, was just something I had in mind. Based on your orig. post  I assumed the git master branch could be self-updated also, apparently not.

---

### Post by cruzer001 on 2018-03-26
Using pinxi -zv8

```
Memory:
  RAM Report: permissions: Unable to run dmidecode. Are you root? 
PCI Slots:
  Permissions: Unable to run dmidecode. Are you root?
```

It works fine if sudo is used, but is it suppose to be like this?

System:    Host: lu1 Kernel: 4.4.0-116-generic i686 (32 bit)
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 16.04 xenial

Different computer, same results
System:
  Host: gc Kernel: 4.15.0-12-generic x86_64 bits: 64 Desktop: Gnome 3.28.0 
  Distro: Ubuntu Bionic Beaver (development branch)

---

### Post by user232 on 2018-03-26
mörgæs, that issue was just fixed, getting ready to commit the changes, sorry about that one, it was an oversight while handling another issue.   

mc4man, all the branches and master are self-updating, but don't use one and two because those have ancient inxi's in them, which reminds me to add a  more current one to those.   

 It's up to distribution maintainers to enable or disable the -U option, if you are using an Ubuntu packaged inxi, then it's disabled by default,   

All the git branches by default assuming you don't have the /etc/inxi.conf from the packaged version update, if they don't, that means it's been disabled, nothing more.  the pinxi and master branch are the same program except pinxi leads it a bit usually now as the development branch. pinxi installs man pinxi if --man is used. inxi does NOT install man if --no-man is used. If you do not see the -U option in help, it means the maintainers have that disabled.  

By the way, am I missing something very obvious about these forums? They refuse to respect whitespace line breaks and force me to insert manually html line breaks to get line breaks. Is there some switch to enable what should always be the normal case?

---

### Post by mc4man on 2018-03-26
I see what was happening, a packaged inxi was installed & even though the I was using the git inxi script the self-updater somehow looks to the packaged version
(I even removed the package's /usr/bin/inxi, didn't matter, -U won't work on git master if the ubuntu package is installed.

Edit: the ubuntu package installs a inxi.conf file to disable self-updates, minor mystery solved.

---

### Post by user232 on 2018-03-26
Yes, I don't interfere with packager or distro decisions like that. That's a nice side effect of keeping pinxi as the current active dev branch, which it now is, pinxi will remain active and upgradable, and can be run by itself without interfering with distro packaged versions.

---

### Post by mörgæs on 2018-03-27
Works correctly now, thanks.

---

### Post by user232 on 2018-03-27
cruzer001, yes, features that require root/sudo require root/sudo. RAM, dmi data, is in that set of things. Last choice in inxi is always root required, so if you see root required, it generally means root is required for that feature.

---

### Post by cariboo on 2018-03-28
It seems the latest update is broken on my arm based Raspberrypi B 3. Here's the output when running the command:

```
pi@haven:~ $ pinxi -F
System:
  Host: haven Kernel: 4.9.80-v7+ armv7l bits: 32 Console: tty 0 
  Distro: Raspbian GNU/Linux 9 (stretch) 
Machine:
  Type: ARM Device System: BCM2835 rev: a22082 serial: 000000002c5f6294 
CPU:
  Topology: Quad Core model: ARMv7 v7l type: MCP 
  Speed: 1200 MHz min/max: 600/1200 MHz Core speeds (MHz): 1: 1200 2: 1200 
  3: 1200 4: 1200 
Graphics:
  ARM: PCI data type is not supported on ARM systems. 
  Display Server: No display server data found. Headless server? tty: 80x24 
  Message: Unable to show advanced data. Required tool glxinfo missing. 
Use of uninitialized value $file in open at /usr/local/bin/pinxi line 3062.
Use of uninitialized value $one in concatenation (.) or string at /usr/local/bin/pinxi line 2133.
Error 45: Error opening file:  
Error: No such file or directory
```

I running Debian Stretch and using the system as a home automation server running [Home Assistant]("https://www.home-assistant.io/"). The only change I've made since running pinxi earlier is adding [Node-RED]("https://nodered.org/")

---

### Post by user232 on 2018-03-28
The error happened in Audio section, I think, where it should have been showing no pci data error instead, if that was the last line read.   I've added a quick patch at pinxi 2.9.08-07 though I prefer to know why a file that has always been there isn't. I can see that it was recognized as ARM, which should have shown the no pci data for ARM, so the faliure was one step or row down from that. 

Tracking down into the Audio section, I believe the glitch came in the USB secction, so I'll have to add in  some protections there.

---

### Post by user232 on 2018-03-28
It appears that somewhere  in your system a file that was checked to exist doesn't exist, but it's hard to know without the debugger logs. You can generate one by this: pinxi -F --debug 10  

then in $HOME/.local/share/pinxi/ you will find pinxi.log which you can paste somewhere like pastebin.com  that will show me exactly where it crashed and on what file, otherwise I'm basically just guessing at a few different locations.

---

### Post by user232 on 2018-03-28
If this was working a few days ago, then I don't believe anything in that area changed in pinxi, so changes to the system are slightly suspect, particularly because after checking, all those files are checked to exist before being sent to the reader. So there's something odd there, only the pinxi.log file will really show me what is happening, hopefully.

---

### Post by cariboo on 2018-03-31
Here is the output of the pinxi.log. It's to large to paste into the post, so I used pastebin:

[https://paste.ubuntu.com/p/2P6GfzB2NR/](https://paste.ubuntu.com/p/2P6GfzB2NR/)

---

### Post by user232 on 2018-03-31
Thank you, that confirms it. I made a mistake in the logic there, thanks for providing that  log file. The mistake only showed up in cases where it was arm system, otherwise it would not show up, which is how I missed it. Thanks for providing the data so I could correct the actual logic bug, and not just hide it with some other patches.

---

### Post by cariboo on 2018-04-02
Thanks, that fixed the problem.

---

### Post by mc4man on 2018-06-28
For those that don't want to install from git a ppa version for 16.04 & 18.04 is here. This is a single use ppa, self-updating has been enabled.
Instructions on page.
[https://launchpad.net/~mc3man/+archive/ubuntu/inxi1](https://launchpad.net/~mc3man/+archive/ubuntu/inxi1)

---

### Post by #&amp;thj^% on 2018-07-03
> **mc4man said:**
> For those that don't want to install from git a ppa version for 16.04 & 18.04 is here. This is a single use ppa, self-updating has been enabled.
Instructions on page.
[https://launchpad.net/~mc3man/+archive/ubuntu/inxi1](https://launchpad.net/~mc3man/+archive/ubuntu/inxi1)

Thanks mc4man this is very helpful!
Though i have no clue why he would lock it from upgrading it with "sudo inxi -U"???
Results from your PPA
```
sudo inxi -U
Starting inxi self updater.
Using tiny as downloader.
Currently running inxi version number: 3.0.00
Current version patch number: 00
Current version release date: 2018-04-09
Updating inxi in /usr/bin using main branch as download source...
Successfully updated to main branch version: 3.0.14
New main branch version patch number: 00
New main branch version release date: 2018-06-27
To run the new version, just start inxi again.
----------------------------------------

Starting download of man page file now.
Downloading Man page file...
Download successful. Compressing file...
Download and install of man page successful.
Check to make sure it works: man inxi

```
Best Regards ;)

---

### Post by mc4man on 2018-07-06
> **1fallen said:**
> Thanks mc4man this is very helpful!
Though i have no clue why he would lock it from upgrading it with "sudo inxi -U"???
Results from your PPA
```
sudo inxi -U
Starting inxi self updater.
Using tiny as downloader.
Currently running inxi version number: 3.0.00
Current version patch number: 00
Current version release date: 2018-04-09
Updating inxi in /usr/bin using main branch as download source...
Successfully updated to main branch version: 3.0.14
New main branch version patch number: 00
New main branch version release date: 2018-06-27
To run the new version, just start inxi again.
----------------------------------------

Starting download of man page file now.
Downloading Man page file...
Download successful. Compressing file...
Download and install of man page successful.
Check to make sure it works: man inxi

```
Best Regards ;)

The disabling of self updating feature is done by Debian & Ubuntu via a .conf file. (/etc/inxi.conf) 
By default inxi would not install a .conf, that's why I say one would need to remove the repo package first, that removes the .conf file.
Otherwise I would have had to include an empty .conf file to overwite the existing or used a preinstall or postinstall script. Easier to just have the existing package removed.

Edit: users could also just edit or remove the .conf with the repo version to allow updating..

---

