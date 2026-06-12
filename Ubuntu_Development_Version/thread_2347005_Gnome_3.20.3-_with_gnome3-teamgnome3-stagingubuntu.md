---
title: "Gnome 3.20.3- with gnome3-team/gnome3-staging/ubuntu on Unity"
date: 2016-12-20
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2016-12-20
[COLOR=#ff0000]***This is just TESTING do NOT follow if you want a STABLE Desktop***
[/COLOR][COLOR=#000000]Gnome 3.20 and Unity seem to play nicely together.[/COLOR][COLOR=#ff0000][/COLOR]
Been playing with the Gnome Staging PPA on Unity for a few hours (about 6 hrs) now and I really like it.
I have not seen anything adverse after tweaking some here and there ;)...yet. "some" themes are a little hickey.
Long story short here I'm keeping it.

```
System:    Host: me-System-Product-Name Kernel: 4.9.0-040900-lowlatency x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial

```
And Evolution:
```
apt policy evolution
evolution:
  Installed: 3.20.5-0ubuntu1~ubuntu16.04.2
  Candidate: 3.20.5-0ubuntu1~ubuntu16.04.2
  Version table:
 *** 3.20.5-0ubuntu1~ubuntu16.04.2 500
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     3.18.5.2-0ubuntu3.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages
     3.18.5.2-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     3.18.5.2-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages

```
Nautilus:
```
 apt policy nautilus
nautilus:
  Installed: 1:3.20.3-1ubuntu2~ubuntu16.04.1
  Candidate: 1:3.20.3-1ubuntu2~ubuntu16.04.1
  Version table:
 *** 1:3.20.3-1ubuntu2~ubuntu16.04.1 500
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     1:3.18.4.is.3.14.3-0ubuntu6 500
        500 http://archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
     1:3.18.4.is.3.14.3-0ubuntu5 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     1:3.18.4.is.3.14.3-0ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```
The Staging Team so far is doing a bang up job.:D

---

### Post by jbicha on 2016-12-20
Your icon theme is funny. :)

My opinion is that if you want GNOME 3.20, you're better off with Ubuntu 16.10. Of course, that will require you to update twice per year until 18.04 LTS at least.

---

### Post by #&amp;thj^% on 2016-12-20
> **jbicha said:**
> Your icon theme is funny. :)

My opinion is that if you want GNOME 3.20, you're better off with Ubuntu 16.10. Of course, that will require you to update twice per year until 18.04 LTS at least.

That takes all the fun out of testing then..:p
But Thanks for the opinion. I really at this point can't see the logic in not including it in 16.04 (Nautilus 3.20)...but we will see over a bit of time here...maybe I will be eating some Crow...;)
Kind Regards

---

### Post by jbicha on 2016-12-21
It can't be included in Ubuntu 16.04 LTS because 16.04 is a stable  release. It took until well into the summer (Northern Hemisphere) for  Unity and especially light-themes to be adapted to work with GNOME 3.20.  But 16.04 had to be stable in April. And 'stable' in Ubuntu means we  don't get new major versions of core components like GNOME (without an  exception).

The GNOME3 PPAs are mostly either an early look at  the next Ubuntu release or a backport from the next release, depending  on where we are in the release schedule. So once the next Ubuntu release  is out, I don't see a lot of reason to use the old one if you want New  Stuff.

---

### Post by #&amp;thj^% on 2016-12-21
Yes I understand all you have said (I guess I like it so much thought I would share my joy)...but just the past few days of running the "new" from the PPA
has given me New Spark..it seems to have solved a few minor glitch's I had and I must admit it also has made OS just bit more snappy and Crisp.
**Now whether this remains stable for me...(using the PPA and taking the updates from Main) is for future finding. (More of a warning to newer users)**
You Guys are doing a Fantastic Job...A Big Kudos to you all.:D
And this is just a topic in testing...and not meant to be followed. (Just to be clear)
After all that's why we test.

---

### Post by #&amp;thj^% on 2017-01-02
Just updating this...One week has past and I still could not be happier with 16.04.
But I have not had a lot of updates in the past week or so either,... but I have tweaked the system quite a bit though.
I have to say this is running better than 16.10 on the same Specs.
```
System:    Host: me-System-Product-Name Kernel: 4.9.0-040900-lowlatency x86_64 (64 bit gcc: 6.2.0)
           Desktop: Unity 7.4.0 (Gtk 2.24.30) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASUSTeK model: M3A32-MVP DELUXE v: Rev 1.xx
           Bios: American Megatrends v: 2202 date: 09/23/2010
CPU:       Quad core AMD Phenom 9600 (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4a svm) bmips: 18454
           clock speeds: max: 2300 MHz 1: 2300 MHz 2: 2300 MHz 3: 2300 MHz
           4: 2300 MHz
Graphics:  Card: NVIDIA GF106 [GeForce GTS 450] bus-ID: 05:00.0
           Display Server: X.Org 1.18.4 driver: nvidia
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTS 450/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 375.26 Direct Rendering: Yes
Audio:     Card-1 NVIDIA GF106 High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 05:00.1
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel bus-ID: 00:14.2
           Card-3 Creative Labs SB Audigy
           driver: snd_emu10k1 port: e400 bus-ID: 06:06.0
           Sound: ALSA v: k4.9.0-040900-lowlatency
Network:   Card-1: Marvell 88E8056 PCI-E Gigabit Ethernet Controller
           driver: sky2 v: 1.30 port: a800 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express)
           driver: ath5k bus-ID: 04:00.0
           IF: wlp4s0 state: down mac: <filter>
           Card-3: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too v: 0.9.28 port: e800 bus-ID: 06:05.0
           IF: enp6s5 state: down mac: <filter>
Drives:    HDD Total Size: 3500.7GB (1.1% used)
           ID-1: /dev/sda model: WDC_WD5000AADS size: 500.1GB
           ID-2: /dev/sdb model: WDC_WD20EADS size: 2000.4GB
           ID-3: /dev/sdc model: WDC_WD1001FALS size: 1000.2GB
Partition: ID-1: / size: 231G used: 26G (12%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 3.22GB used: 0.00GB (0%) fs: swap dev: /dev/sdc2
           ID-3: swap-2 size: 7.51GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 43.0C mobo: 44.0C gpu: 0.0:37C
           Fan Speeds (in rpm): cpu: 2410 psu: 0 sys-1: 0
Info:      Processes: 254 Uptime: 3:33 Memory: 1455.7/6975.1MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35 

```

I also have proposed enabled.

Regards

---

### Post by #&amp;thj^% on 2017-01-16
Week 2 has now passed....still very pleased!
This also has survived a complete machine transplant.(From AMD to Intel...No Nvidia yet)
New Specs:
```
$ inxi -Fxz
System:    Host: me-System-Product-Name Kernel: 4.9.4-040904-lowlatency x86_64 (64 bit gcc: 6.2.0)
           Desktop: Unity 7.4.0 (Gtk 2.24.30) Distro: Ubuntu 16.04 xenial
Machine:   Mobo: HP model: 828A v: 1.01 Bios: AMI v: F.14 date: 09/19/2016
CPU:       Quad core Intel Core i5-6400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 21696
           clock speeds: max: 3300 MHz 1: 1180 MHz 2: 1746 MHz 3: 890 MHz
           4: 1677 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card Intel Sunrise Point-H HD Audio
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: ALSA v: k4.9.4-040904-lowlatency
Network:   Card-1: Intel Device 24fb driver: iwlwifi bus-ID: 02:00.0
           IF: wlp2s0 state: down mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1000.2GB (4.6% used)
           ID-1: /dev/sda model: TOSHIBA_MK5065GS size: 500.1GB
           ID-2: /dev/sdb model: WDC_WD5000AADS size: 500.1GB
Partition: ID-1: / size: 231G used: 37G (17%) fs: ext4 dev: /dev/sdb1
           ID-2: swap-1 size: 7.51GB used: 0.00GB (0%) fs: swap dev: /dev/sdb5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 267 Uptime: 24 min Memory: 1340.3/11923.9MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35 

```

---

### Post by #&amp;thj^% on 2017-02-22
Just keeping this updated.
Yep still going strong here...took the hwe-stack update.
That's not to say I did not have a few minor bumps with the upgrade...I had to disable and downgrade first from the proposed repo && gnome3-staging PPA...then I was fine with my upgrade process.
This time I did not go with evolution.
```
apt policy nautilus evolution gedit && uname -r && lsb_release -a
nautilus:
  Installed: 1:3.20.3-1ubuntu2~ubuntu16.04.1
  Candidate: 1:3.20.3-1ubuntu2~ubuntu16.04.1
  Version table:
 *** 1:3.20.3-1ubuntu2~ubuntu16.04.1 500
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     1:3.18.4.is.3.14.3-0ubuntu6 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages
     1:3.18.4.is.3.14.3-0ubuntu5 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     1:3.18.4.is.3.14.3-0ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
evolution:
  Installed: (none)
  Candidate: 3.20.5-0ubuntu1~ubuntu16.04.2
  Version table:
     3.20.5-0ubuntu1~ubuntu16.04.2 500
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu xenial/main amd64 Packages
     3.18.5.2-0ubuntu3.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
     3.18.5.2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
gedit:
  Installed: 3.20.2-2ubuntu1~ubuntu16.04.1
  Candidate: 3.20.2-2ubuntu1~ubuntu16.04.1
  Version table:
 *** 3.20.2-2ubuntu1~ubuntu16.04.1 500
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     3.18.3-0ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
4.9.11-040911-lowlatency
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

```

---

### Post by #&amp;thj^% on 2017-04-25
Still going strong here also...no changes.
This set-up suits me to a tee.
New readers....Please read all warnings here in this thread. (Best Advice do not follow this...testing only)
[COLOR=#ff0000]******Not for production or mission critical machines**** **[/COLOR]

---

### Post by Frogs Hair on 2017-04-25
> **1fallen said:**
> Still going strong here also...no changes.
This set-up suits me to a tee.
New readers....Please read all warnings here in this thread. (Best Advice do not follow this...testing only)
[COLOR=#ff0000]******Not for production or mission critical machines**** **[/COLOR]

All attempts to use these PPA's have ended badly. Staying far far away. :o

---

### Post by #&amp;thj^% on 2017-04-25
> **Frogs Hair said:**
> All attempts to use these PPA's have ended badly. Staying far far away. :o

;) Wise choice.
Only for dummy's like me.:D

---

### Post by ventrical on 2017-04-25
> **1fallen said:**
> ;) Wise choice.
Only for dummy's like me.:D

I have four hardwired boxes on a bare metal KVM so it don't matter what breaks here.  I broke 4 installs in the last 24 hours. usually sleep like a baby after that :) We're earning our keep eh :)

Regards..

---

### Post by jbicha on 2017-04-25
Did you see the [announcement]("https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004229.html") that the GNOME3 PPAs will no longer be updated for Ubuntu 16.04 LTS as of this week? It's recommend to ppa-purge them and then either stay with 16.04 LTS or upgrade to 17.04.

---

### Post by #&amp;thj^% on 2017-04-25
> **ventrical said:**
> I have four hardwired boxes on a bare metal KVM so it don't matter what breaks here.  I broke 4 installs in the last 24 hours. usually sleep like a baby after that :) We're earning our keep eh :)

Regards..
Indeed...But having fun in the process. :D

> **jbicha said:**
> Did you see the [announcement]("https://lists.ubuntu.com/archives/ubuntu-gnome/2017-March/004229.html") that the GNOME3 PPAs will no longer be updated for Ubuntu 16.04 LTS as of this week? It's recommend to ppa-purge them and then either stay with 16.04 LTS or upgrade to 17.04.
You know I was just going to ask if newer packages were going to be pushed there....So now question answered.
Thanks for the heads up Jeremy
Kind Regards

---

