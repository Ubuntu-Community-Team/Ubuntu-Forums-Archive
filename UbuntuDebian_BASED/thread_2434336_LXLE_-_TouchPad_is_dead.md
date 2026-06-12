---
title: "LXLE - TouchPad is dead"
date: 2020-01-03
forum: Ubuntu/Debian BASED
---

### Post by quenyan on 2020-01-03
It's my first time using LXLE, upon installing the touchpad is working fine. I didn't connect to the wifi for the update, but it has the update, If I wasn't wrong I saw 199 updates. Everything was fine, only couple problem that I have to set manually which are Brightness button and Audio button. everything else were just fine. Supposedly, everything became better after the update, but after running the update and rebooted, the touchpad stopped working, I tought it was a lag, when I pressed CTRL+ESC it brings up menu, also ALT+X brings up TERMINAL. so it wasn't a lag. The touchpad menu says "enabled" so it suppose to work, but somehow it is dead. Lucky enough the mouse is working, well, not a bad experience since I can type on the keyboard without touching the touchpad, that's the bright side, but I am afraid that is a serious problem. So, how do i fix it? 


inxi output:
```
System:    Host: qwerty-Inspiron-14-3452 Kernel: 4.15.0-72-generic x86_64
           bits: 64
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04.3 LTS
Machine:   Device: portable System: Dell product: Inspiron 14-3452 v: 4.4.0 serial: N/A
           Mobo: Dell model: 0KT6WF v: A02 serial: N/A
           UEFI [Legacy]: Dell v: 4.4.0 date: 03/06/2018
Battery    BAT0: charge: 41.4 Wh 138.0% condition: 30.0/41.4 Wh (72%)
CPU:       Dual core Intel Celeron N3050 (-MCP-) cache: 1024 KB
           clock speeds: max: 2160 MHz 1: 629 MHz 2: 999 MHz
Graphics:  Card: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
           Display Server: x11 (X.Org 1.19.6 ) driver: intel
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 400 (Braswell)
           version: 4.5 Mesa 19.0.8
Audio:     Card Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Def. Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-72-generic
Network:   Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k
           IF: wlp1s0 state: up mac: <filter>
           Card-2: Atheros
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 500.1GB (2.1% used)
           ID-1: /dev/sda model: ST500LT012 size: 500.1GB
Partition: ID-1: / size: 458G used: 8.8G (3%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 0.50GB used: 0.03GB (7%)
           fs: swap dev: /dev/zram0
           ID-3: swap-2 size: 0.50GB used: 0.03GB (7%)
           fs: swap dev: /dev/zram1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 26.0C mobo: 26.8C
           Fan Speeds (in rpm): cpu: 0
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
           deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
           deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
           deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
           deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
           deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
           deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
           deb http://archive.canonical.com/ubuntu/ bionic partner
           deb http://security.ubuntu.com/ubuntu/ bionic-security main restricted
           deb http://security.ubuntu.com/ubuntu/ bionic-security universe
           deb http://security.ubuntu.com/ubuntu/ bionic-security multiverse
           deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/ all main
           Active apt sources in file: /etc/apt/sources.list.d/anonbeat-ubuntu-guayadeque-bionic.list
           deb http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu/ bionic main
           Active apt sources in file: /etc/apt/sources.list.d/apandada1-ubuntu-brightness-controller-bionic.list
           deb http://ppa.launchpad.net/apandada1/brightness-controller/ubuntu/ bionic main
           Active apt sources in file: /etc/apt/sources.list.d/bookworm-team-ubuntu-bookworm-bionic.list
           deb http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu/ bionic main
           Active apt sources in file: /etc/apt/sources.list.d/kelleyk-ubuntu-compton-bionic.list
           deb http://ppa.launchpad.net/kelleyk/compton/ubuntu/ bionic main
           Active apt sources in file: /etc/apt/sources.list.d/libreoffice-ubuntu-ppa-bionic.list
           deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ bionic main
           Active apt sources in file: /etc/apt/sources.list.d/linrunner-ubuntu-tlp-bionic.list
           deb http://ppa.launchpad.net/linrunner/tlp/ubuntu/ bionic main
           Active apt sources in file: /etc/apt/sources.list.d/lxle-ubuntu-stable-bionic.list
           deb http://ppa.launchpad.net/lxle/stable/ubuntu/ bionic main
           Active apt sources in file: /etc/apt/sources.list.d/maarten-baert-ubuntu-simplescreenrecorder-bionic.list
           deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu/ bionic main
           Active apt sources in file: /etc/apt/sources.list.d/philip_scott-ubuntu-spice-up-daily-bionic.list
           deb http://ppa.launchpad.net/philip.scott/spice-up-daily/ubuntu/ bionic main
           Active apt sources in file: /etc/apt/sources.list.d/utappia-ubuntu-stable-bionic.list
           deb http://ppa.launchpad.net/utappia/stable/ubuntu/ bionic main
           Active apt sources in file: /etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-bionic.list
           deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu/ bionic main
Info:      Processes: 153 Uptime: 21:18 Memory: 893.8/1905.8MB
           Client: Shell (bash) inxi: 2.3.56 


```

---

### Post by Rex Bouwense on 2020-01-04
I had the same problem with my Dell Inspiron 14-3452.  [https://ubuntuforums.org/showthread.php?t=2432565](https://ubuntuforums.org/showthread.php?t=2432565).  The previous kernel functions normally or you can install the 5.xx kernel which also functions normally.

---

### Post by deadflowr on 2020-01-04
*Thread moved to **Ubuntu/Debian BASED***

---

### Post by quenyan on 2020-01-04
> **Rex Bouwense said:**
> I had the same problem with my Dell Inspiron 14-3452.  [https://ubuntuforums.org/showthread.php?t=2432565](https://ubuntuforums.org/showthread.php?t=2432565).  The previous kernel functions normally or you can install the 5.xx kernel which also functions normally.

Hi rex, I found the solution, you must check it out, now my touchpad is revived, and my life is complete in LXLE, for now.

[https://askubuntu.com/a/831846/996893](https://askubuntu.com/a/831846/996893)

I'll mark this thread as solved.

---

