---
title: "unable to access ubuntu wayland"
date: 2017-07-15
forum: Ubuntu Development Version
---

### Post by terry_gardener on 2017-07-15
for the past week i have been unable to access ubuntu wayland option at greeter, ubuntu plain works but get screen tearing and don't want to install the nvidia drivers.
Using stock nouvaeu drivers
nvidia gtx 960 gtx GPU. 

whan i try to login to ubuntu wayland the screen goes black and nothing happens, nothing works, have to shutdown using crtl+alt+prtscn then ctrl+alt+r,e,i,s,u,o. 

any ideas.

---

### Post by rrnbtter on 2017-07-15
Greetings,
My wayland was out after some updates earlier in the week but was subsequently corrected.  I believe it was due to some incomplete GTK updates.  If your "proposed" is not enabled you may not be getting the updates that you need. Mine is work now just fine on Intel system.

---

### Post by mc4man on 2017-07-16
You shouldn't have need for  -proposed, this was fixed 1 version back in gdm3
[https://launchpad.net/ubuntu/+source/gdm3/3.24.2-1ubuntu8](https://launchpad.net/ubuntu/+source/gdm3/3.24.2-1ubuntu8)

---

### Post by rrnbtter on 2017-07-16
Greetings,
Yep, it was the gdm3 update that was the problem. Oddly I had switched to Gnome x11 and when the gdm3 fix came through the login automatically switched back to gnome-wayland after reboot.

---

### Post by terry_gardener on 2017-07-16
i have tried proposed and still unable to access wayland i have checked x11 ubuntu and that isn't working either, just get black screen on wayland and blank screen just different colour on x11. 
this didn't work before i enabled proposed either. i have tried reinstalling and get same issue after updating. used daily build from 14/7

---

### Post by mc4man on 2017-07-16
> this didn't work before i enabled proposed either
Likely the bug
> i have tried proposed and still unable to access wayland i have checked x11 ubuntu and that isn't working either
Probably from using proposed at wrong time & place
> used daily build from 14/7 
If you still have it then  do a fresh install, update fully (no proposed), you should be ok

Otherwise get a new image, I'd wait till next week though maybe today's is usable

---

### Post by terry_gardener on 2017-07-16
did fresh install using 14/07 image it worked but when i did updates and same issue.

don't get to desktop just get this, this is x11. 

[https://drive.google.com/file/d/0B8xMx6UCM5vsVU1BM2RwdFV1dTg/view?usp=sharing]("https://drive.google.com/file/d/0B8xMx6UCM5vsVU1BM2RwdFV1dTg/view?usp=sharing")

---

### Post by mc4man on 2017-07-16
That looks pretty useless. Maybe try current iso in a live session.
nvidia hardware works here but it's optimus not a desktop machine

Otherwise try to pin down what update caused this

---

### Post by terry_gardener on 2017-07-16
i'll download the daily iso tomorrow, retry and let you know

---

### Post by terry_gardener on 2017-07-20
sorry i didn't reply earlier but i have now tested it, wayland i still get the same thing pretty colours on screen but no desktop. 
x11 desktop loads but when i try and do something the screen freezes so can't use it.

---

### Post by VMC on 2017-07-21
> **terry_gardener said:**
> i'll download the daily iso tomorrow, retry and let you know

I've had almost that exact same screen. Its the background image that's messed with using xwayland. I can't install nvidia-legacy with gnome 2.4. The freeze part I don't have.

---

### Post by ventrical on 2017-07-24
It's working very smoothly here.

 I had aproblem a while back , testing nvidia drivers. It borked my system and I got black screen so I removed nvidia and re-installed

```

sudo apt-get install nouveau-firmware

```

and got my screen back and everything- notice display server (wayland)

```

ventrical@ventrical-Precision-WorkStation-T3400:~$ inxi -Fxz
System:    Host: ventrical-Precision-WorkStation-T3400 Kernel: 4.11.0-10-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.3 (Gtk 3.22.17-0ubuntu1)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop System: Dell product: Precision WorkStation T3400
           Mobo: Dell model: 0TP412 BIOS: Dell v: A03 date: 01/31/2008
CPU:       Quad core Intel Core2 Quad Q6600 (-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 19151
           clock speeds: max: 2393 MHz 1: 2393 MHz 2: 2393 MHz 3: 2393 MHz
           4: 2393 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.3) drivers: nouveau (unloaded: modesetting,fbdev,vesa)
           Resolution: 1440x900@59.75hz
           OpenGL: renderer: Gallium 0.4 on NVD9
           version: 4.3 Mesa 17.1.2 Direct Render: Yes
Audio:     Card-1 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.11.0-10-generic
Network:   Card: Broadcom Limited NetXtreme BCM5754 Gigabit Ethernet PCI Express
           driver: tg3 v: 3.137 bus-ID: 04:00.0
           IF: enp4s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 160.0GB (5.8% used)
           ID-1: /dev/sda model: ST3160815AS size: 160.0GB
Partition: ID-1: / size: 74G used: 8.7G (13%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 42.0C mobo: N/A gpu: 32.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 192 Uptime: 5 min Memory: 689.0/3883.1MB
           Init: systemd runlevel: 5 Gcc sys: 6.3.0
           Client: Shell (bash 4.4.121) inxi: 2.3.23 
ventrical@ventrical-Precision-WorkStation-T3400:~$ 

```

---

### Post by Cavsfan on 2017-07-24
Same here. 
I was wondering where the wayland driver was coming from but, installed [COLOR=#483D8B][FONT=&amp]nouveau-firmware [/FONT][/COLOR]and found they were [COLOR=#483D8B][FONT=&amp]wayland-protocols[/FONT][/COLOR].
Rebooted and there it was and seems to work so far.

I was expecting an option in grub but, it's default.
```
cavsfan@cavsfan-le-beast:~$ inxi -Fxz
System:    Host: cavsfan-le-beast Kernel: 4.11.0-10-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.3 (Gtk 3.22.17-0ubuntu1) Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: MICRO-STAR model: G31M3-L V2(MS-7529) v: 1.0 BIOS: American Megatrends v: V2.8 date: 03/11/2010
CPU:       Quad core Intel Core2 Quad Q9550 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 22742
           clock speeds: max: 2842 MHz 1: 2842 MHz 2: 2842 MHz 3: 2842 MHz 4: 2842 MHz
Graphics:  Card: NVIDIA G92 [GeForce 9800 GT] bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.3) driver: N/A Resolution: 1920x1080@59.96hz
           OpenGL: renderer: Gallium 0.4 on NV92 version: 3.3 Mesa 17.1.2 Direct Render: Yes
Audio:     Card Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.11.0-10-generic
Network:   Card: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: e800 bus-ID: 03:00.0
           IF: ens33 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1500.3GB (35.0% used)
           ID-1: /dev/sda model: WDC_WD5003ABYX size: 500.1GB temp: 29C
           ID-2: USB /dev/sdb model: FANTOM_DRIVE size: 1000.2GB temp: 0C
Partition: ID-1: / size: 14G used: 5.0G (38%) fs: ext4 dev: /dev/sda7
           ID-2: swap-1 size: 0.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 38.0C mobo: N/A gpu: 44.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 247 Uptime: 3 min Memory: 1156.1/3949.3MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.23 

```

Anyone gotten Synaptic to work? It won't open for me. Or maybe that's getting off subject...

---

### Post by #&amp;thj^% on 2017-07-24
> **Cavsfan said:**
> 
Anyone gotten Synaptic to work? It won't open for me. Or maybe that's getting off subject...
See my post here: [https://ubuntuforums.org/showthread.php?t=2366995&p=13669316#post13669316](https://ubuntuforums.org/showthread.php?t=2366995&p=13669316#post13669316)

---

### Post by ventrical on 2017-07-24
> **Cavsfan said:**
> Same here. 
I was wondering where the wayland driver was coming from but, installed [COLOR=#483D8B][FONT=&amp]nouveau-firmware [/FONT][/COLOR]and found they were [COLOR=#483D8B][FONT=&amp]wayland-protocols[/FONT][/COLOR].
Rebooted and there it was and seems to work so far.

I was expecting an option in grub but, it's default.
```
cavsfan@cavsfan-le-beast:~$ inxi -Fxz
System:    Host: cavsfan-le-beast Kernel: 4.11.0-10-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.3 (Gtk 3.22.17-0ubuntu1) Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: MICRO-STAR model: G31M3-L V2(MS-7529) v: 1.0 BIOS: American Megatrends v: V2.8 date: 03/11/2010
CPU:       Quad core Intel Core2 Quad Q9550 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 22742
           clock speeds: max: 2842 MHz 1: 2842 MHz 2: 2842 MHz 3: 2842 MHz 4: 2842 MHz
Graphics:  Card: NVIDIA G92 [GeForce 9800 GT] bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.3) driver: N/A Resolution: 1920x1080@59.96hz
           OpenGL: renderer: Gallium 0.4 on NV92 version: 3.3 Mesa 17.1.2 Direct Render: Yes
Audio:     Card Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.11.0-10-generic
Network:   Card: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: e800 bus-ID: 03:00.0
           IF: ens33 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1500.3GB (35.0% used)
           ID-1: /dev/sda model: WDC_WD5003ABYX size: 500.1GB temp: 29C
           ID-2: USB /dev/sdb model: FANTOM_DRIVE size: 1000.2GB temp: 0C
Partition: ID-1: / size: 14G used: 5.0G (38%) fs: ext4 dev: /dev/sda7
           ID-2: swap-1 size: 0.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 38.0C mobo: N/A gpu: 44.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 247 Uptime: 3 min Memory: 1156.1/3949.3MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.23 

```

Anyone gotten Synaptic to work? It won't open for me. Or maybe that's getting off subject...

It works fine in unity-session but not on wayland. A lot of .debs do not work with wayland yet.

---

### Post by Cavsfan on 2017-07-25
> **1fallen said:**
> See my post here: [https://ubuntuforums.org/showthread.php?t=2366995&p=13669316#post13669316](https://ubuntuforums.org/showthread.php?t=2366995&p=13669316#post13669316)

Thanks but, for some reason Synaptic got an error for no reason when I booted up today and then said it was because I hadn't updating my system, which I was doing at the same time.
So, It opened without sudo permissions and would not do anything. I closed it and tried to open it again and it opened just like normal. :)

> **ventrical said:**
> It works fine in unity-session but not on wayland. A lot of .debs do not work with wayland yet.

Thanks! I installed the basic Ubuntu install and cannot see any unity session, only a default one that starts with what looks like a gnome session and wayland for the Display Server and although it says "driver: N/A", I installed the nouveau driver.

I guess we're not installing the Nvida driver yet? it looks like nvidia-current would work for me with my old card.
```
cavsfan@cavsfan-le-beast:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  build-essential dkms dpkg-dev fakeroot g++ g++-6 gcc gcc-6 lib32gcc1 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan3
  libatomic1 libc-dev-bin libc6-dev libc6-i386 libcilkrts5 libcuda1-304 libfakeroot libgcc-6-dev libitm1 liblsan0 libmpx2 libstdc++-6-dev libtsan0 libubsan0
  libxnvctrl0 linux-libc-dev make manpages-dev nvidia-304 nvidia-opencl-icd-304 nvidia-settings pkg-config policykit-1-gnome screen-resolution-extra
Suggested packages:
  menu debian-keyring g++-multilib g++-6-multilib gcc-6-doc libstdc++6-6-dbg gcc-multilib autoconf automake libtool flex bison gcc-doc gcc-6-multilib
  gcc-6-locales libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan3-dbg liblsan0-dbg libtsan0-dbg libubsan0-dbg libcilkrts5-dbg libmpx2-dbg
  libquadmath0-dbg glibc-doc libstdc++-6-doc make-doc
The following NEW packages will be installed:
  build-essential dkms dpkg-dev fakeroot g++ g++-6 gcc gcc-6 lib32gcc1 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan3
  libatomic1 libc-dev-bin libc6-dev libc6-i386 libcilkrts5 libcuda1-304 libfakeroot libgcc-6-dev libitm1 liblsan0 libmpx2 libstdc++-6-dev libtsan0 libubsan0
  libxnvctrl0 linux-libc-dev make manpages-dev nvidia-304 nvidia-current nvidia-opencl-icd-304 nvidia-settings pkg-config policykit-1-gnome
  screen-resolution-extra
0 upgraded, 38 newly installed, 0 to remove and 0 not upgraded.
Need to get 76.7 MB of archives.
After this operation, 340 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

---

### Post by Cavsfan on 2017-07-26
Nvidia drivers definitely did not work. No buttons or anything would work when clicked on. All I could get was Cntl+Alt+t to open a terminal and purge nvidia-current but, all other files were left. 

I downloaded the daily iso yesterday and re-installed this morning.

---

### Post by ventrical on 2017-07-26
> **Cavsfan said:**
> Nvidia drivers definitely did not work. No buttons or anything would work when clicked on. All I could get was Cntl+Alt+t to open a terminal and purge nvidia-current but, all other files were left. 

I downloaded the daily iso yesterday and re-installed this morning.

Maybe in the last week of September nVidia might start to work.

---

### Post by Cavsfan on 2017-07-26
> **ventrical said:**
> Maybe in the last week of September nVidia might start to work.

OK, thanks for the tip. I haven't been involved in the development cycle this early in quite a while.

I installed again and this time I did not install anything but, it looks like Wayland came with it and nouveau is the default. Nouveau has always been default I believe

```
cavsfan@cavsfan-Le-Beast:~$ inxi -Fxz
System:    Host: cavsfan-Le-Beast Kernel: 4.11.0-10-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.3 (Gtk 3.22.17-0ubuntu1) Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: MICRO-STAR model: G31M3-L V2(MS-7529) v: 1.0 BIOS: American Megatrends v: V2.8 date: 03/11/2010
CPU:       Quad core Intel Core2 Quad Q9550 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 22745
           clock speeds: max: 2843 MHz 1: 2843 MHz 2: 2843 MHz 3: 2843 MHz 4: 2843 MHz
Graphics:  Card: NVIDIA G92 [GeForce 9800 GT] bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.3) driver: N/A Resolution: 1920x1080@59.96hz
           OpenGL: renderer: Gallium 0.4 on NV92 version: 3.3 Mesa 17.1.2 Direct Render: Yes
Audio:     Card Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.11.0-10-generic
Network:   Card: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: e800 bus-ID: 03:00.0
           IF: ens33 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1500.3GB (36.2% used)
           ID-1: /dev/sda model: WDC_WD5003ABYX size: 500.1GB temp: 29C
           ID-2: USB /dev/sdb model: FANTOM_DRIVE size: 1000.2GB temp: 0C
Partition: ID-1: / size: 14G used: 5.2G (39%) fs: ext4 dev: /dev/sda7
           ID-2: swap-1 size: 0.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.0C mobo: N/A gpu: 46.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 236 Uptime: 1:29 Memory: 1598.4/3949.3MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.23 

```

[ATTACH=CONFIG]276147[/ATTACH]

---

### Post by ventrical on 2017-07-27
> **Cavsfan said:**
> OK, thanks for the tip. I haven't been involved in the development cycle this early in quite a while.

I installed again and this time I did not install anything but, it looks like Wayland came with it and nouveau is the default. Nouveau has always been default I believe

```
cavsfan@cavsfan-Le-Beast:~$ inxi -Fxz
System:    Host: cavsfan-Le-Beast Kernel: 4.11.0-10-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.3 (Gtk 3.22.17-0ubuntu1) Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: MICRO-STAR model: G31M3-L V2(MS-7529) v: 1.0 BIOS: American Megatrends v: V2.8 date: 03/11/2010
CPU:       Quad core Intel Core2 Quad Q9550 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 22745
           clock speeds: max: 2843 MHz 1: 2843 MHz 2: 2843 MHz 3: 2843 MHz 4: 2843 MHz
Graphics:  Card: NVIDIA G92 [GeForce 9800 GT] bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.3) driver: N/A Resolution: 1920x1080@59.96hz
           OpenGL: renderer: Gallium 0.4 on NV92 version: 3.3 Mesa 17.1.2 Direct Render: Yes
Audio:     Card Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.11.0-10-generic
Network:   Card: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: e800 bus-ID: 03:00.0
           IF: ens33 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1500.3GB (36.2% used)
           ID-1: /dev/sda model: WDC_WD5003ABYX size: 500.1GB temp: 29C
           ID-2: USB /dev/sdb model: FANTOM_DRIVE size: 1000.2GB temp: 0C
Partition: ID-1: / size: 14G used: 5.2G (39%) fs: ext4 dev: /dev/sda7
           ID-2: swap-1 size: 0.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.0C mobo: N/A gpu: 46.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 236 Uptime: 1:29 Memory: 1598.4/3949.3MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.121) inxi: 2.3.23 

```

[ATTACH=CONFIG]276147[/ATTACH]

I have been testing nVidia drivers on 17.10 ubuntusession-wayland and gnome-shell straight and I keep getting blackscreen. It happened during several previous cycles with unity-desktop. It is usually the last component to alway get fixed - most likely due to it being proprietary.

Regards..

---

### Post by terry_gardener on 2017-07-27
i am using nvidia driver and ubuntu on wayland and it works fine for me, you have to enable KMS for it to work though.

```
System:    Host: ubuntu-desktop Kernel: 4.11.0-10-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome 3.24.3 (Gtk 3.22.17-0ubuntu1)
           Distro: Ubuntu Artful Aardvark (development branch)
Machine:   Device: desktop Mobo: ASRock model: Z87 Pro4
           BIOS: American Megatrends v: P2.30 date: 07/11/2014
CPU:       Quad core Intel Core i7-4790K (-HT-MCP-) cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 31991
           clock speeds: max: 4400 MHz 1: 4395 MHz 2: 4289 MHz 3: 4247 MHz
           4: 4397 MHz 5: 4399 MHz 6: 4400 MHz 7: 4399 MHz 8: 4395 MHz
Graphics:  Card: NVIDIA GM206 [GeForce GTX 960] bus-ID: 01:00.0
           Display Server: wayland (X.Org 1.19.3) drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1920x1080@59.96hz
           OpenGL: renderer: N/A version: N/A Direct Render: N/A
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA Device 0fba driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.11.0-10-generic
Network:   Card-1: Intel Ethernet Connection I217-V
           driver: e1000e v: 3.2.6-k port: f040 bus-ID: 00:19.0
           IF: enp0s25 state: down mac: <filter>
           Card-2: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express)
           driver: ath9k bus-ID: 05:00.0
           IF: wlp5s0 state: up mac: <filter>
Drives:    HDD Total Size: 1250.3GB (3.6% used)
           ID-1: /dev/sda model: CT250BX100SSD1 size: 250.1GB temp: 26C
           ID-2: /dev/sdb model: ST1000DM003 size: 1000.2GB temp: 28C
Partition: ID-1: / size: 57G used: 9.3G (18%) fs: ext4 dev: /dev/sdb1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 31.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 269 Uptime: 4:01 Memory: 1706.2/15975.7MB
           Init: systemd runlevel: 5 Gcc sys: 6.3.0
           Client: Shell (bash 4.4.121) inxi: 2.3.23 

```

---

### Post by mc4man on 2017-07-27
> **terry_gardener said:**
> i am using nvidia driver and ubuntu on wayland and it works fine for me, you have to enable KMS for it to work though.
]
Desktops & laptops with only a GPU can get nvidia on wayland with KMS
Laptops with hybrid graphics can't but can get Prime Sync thru xserver, again with KMS

Though it doesn't appear they'll be willing to enable KMS when installing nvidia driver packages so it'll be up to users to take care of.
(even though the vast majority of nvidia driver users would benefit from KMS..

---

### Post by terry_gardener on 2017-07-27
> **mc4man said:**
> Desktops & laptops with only a GPU can get nvidia on wayland with KMS
Laptops with hybrid graphics can't but can get Prime Sync thru xserver, again with KMS

Though it doesn't appear they'll be willing to enable KMS when installing nvidia driver packages so it'll be up to users to take care of.
(even though the vast majority of nvidia driver users would benefit from KMS..

i didn't have much choice if i wanted to use ubuntu development release, because it doesn't work with nouveau as the firmware needs digital signatures (which are non free software) and it isn't installed by default, X11 or Nvidia don't work with nouveau and GPU nvidia 900 series or above (i have gtx 960). 
When i installed nvidia drivers X11 worked great and when i enabled kms wayland worked also. not tried X11 with KMS enabled and nvidia drivers yet. 
and yes i have a desktop with one GPU that i use ubuntu on. 

my worry is if this doesn't get installed when it is released it is not going to work for people who have these GPUs. 
i have used manjaro in the past Gnome+wayland+nouveau and it works well.

---

