---
title: "screen &quot;crumbles&quot; for few seconds at login"
date: 2018-03-06
forum: Ubuntu Development Version
---

### Post by corradoventu on 2018-03-06
In the last few days immediately after login (I enter the password and hit enter) the screen "crumbles" for few seconds, then all becomes normal and the system works fine. I have done apt update+upgrade many times, also with proposed enabled, I have also installed a new ISO (from the Alpha dated 20180305) but the problem remains. The problem happens with the x11 session but not with wayland. 

On another partition of same PC running Bionic from the Alpha dated 20180214 and not updated for some time I did not have the problem until the last update.
Inxi output for my system is as follows:

```
corrado@corrado-p3-bb:~$ inxi -Fx
System:    Host: corrado-p3-bb Kernel: 4.15.0-10-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.27.91 (Gtk 3.22.28-1ubuntu3) Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: desktop Mobo: ASRock model: H110M-G/M.2 serial: N/A UEFI: American Megatrends v: P1.10 date: 05/11/2017
CPU:       Dual core Intel Core i3-7100 (-MT-MCP-) arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz 4: 800 MHz
Graphics:  Card: Intel HD Graphics 630 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915 Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2)
           version: 4.5 Mesa 18.0.0-rc4 Direct Render: Yes
Audio:     Card Intel Sunrise Point-H HD Audio driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.15.0-10-generic
Network:   Card: Intel Ethernet Connection (2) I219-V driver: e1000e v: 3.2.6-k bus-ID: 00:1f.6
           IF: enp0s31f6 state: up speed: 100 Mbps duplex: full mac: 70:85:c2:44:7b:86
Drives:    HDD Total Size: 1000.2GB (6.2% used)
           ID-1: /dev/sda model: TOSHIBA_DT01ACA1 size: 1000.2GB
Partition: ID-1: / size: 32G used: 5.4G (18%) fs: ext4 dev: /dev/sda3
           ID-2: swap-1 size: 8.59GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 37.5C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 234 Uptime: 3:22 Memory: 1443.0/7680.8MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.181) inxi: 2.3.56 
corrado@corrado-p3-bb:~$ 
```

Here is the apt-log of the updates causing the problem.
[https://pastebin.com/WVjUuqzr](https://pastebin.com/WVjUuqzr)

---

### Post by jbicha on 2018-03-06
I noticed that yesterday too. Please file a bug using
```

ubuntu-bug display

```

And then add gnome-shell/Ubuntu as an affected package if you can.

Also, there was a new gnome-shell and mutter 3.27.92 release today so maybe try installing that update when it becomes available and rebooting first to see if the new version fixes the issue.

---

### Post by dino99 on 2018-03-06
Reported as lp:1753752

---

### Post by corradoventu on 2018-03-06
Installed gnome-shell 3.27.92 does not fix. You suggest to file a bug, I should just login and then Alt+F2 and 'ubuntu-bug display' ... will try
```
corrado@corrado-p7-bb-0305:~$ inxi -SCGx
System:    Host: corrado-p7-bb-0305 Kernel: 4.15.0-10-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Gnome 3.27.92 (Gtk 3.22.28-1ubuntu3) Distro: Ubuntu Bionic Beaver (development branch)
CPU:       Dual core Intel Core i3-7100 (-MT-MCP-) arch: Skylake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 15648
           clock speeds: max: 3900 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz 4: 800 MHz
Graphics:  Card: Intel HD Graphics 630 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) driver: i915 Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2)
           version: 4.5 Mesa 18.0.0-rc4 Direct Render: Yes
corrado@corrado-p7-bb-0305:~$ 

```

---

### Post by corradoventu on 2018-03-06
filed bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1753776](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1753776)

---

