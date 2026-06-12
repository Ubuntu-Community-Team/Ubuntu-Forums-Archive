---
title: "mir/unity 8 preview busted and not useable"
date: 2017-02-05
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-02-05
Unity8 previews has progressively become worse. I cannot send a screenshot but the icons in the apps windows are clipped on the top and the bottom. The apps will not work correctly and the mouse  pointer is dragging like a snail. This after todays update/upgrade and yes .. I did re-boot. This on a Nvidia graphics machine with zesty  commit from beggining.Unity7 is working well though.

Regards..

---

### Post by mc4man on 2017-02-06
> **ventrical said:**
> Unity7 is working well though.

Regards..
I found unity7 to have some issues, many surrounding the lack of any zeitgeist logging or activity which makes various Dash lens useless.

---

### Post by zika on 2017-02-07
```
The following NEW packages will be installed:
  dbus-test-runner libdbustest1 libdrm-dev libegl1-mesa-dev libgl1-mesa-dev libgles2-mesa-dev libglu1-mesa-dev libpthread-stubs0-dev libqt5opengl5-dev libwayland-bin libwayland-dev libx11-dev libx11-doc libx11-xcb-dev libxau-dev libxcb-dri2-0-dev libxcb-dri3-dev
  libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev libxcb-render0-dev libxcb-shape0-dev libxcb-sync-dev libxcb-xfixes0-dev libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxshmfence-dev libxxf86vm-dev mesa-common-dev parallel python3-dbusmock
  qt5-default qt5-qmake qtbase5-dev qtbase5-dev-tools sysstat unity8-tests x11proto-core-dev x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev x11proto-xf86vidmode-dev xorg-sgml-doctools
  xtrans-dev xvfb
The following packages will be upgraded:
  binutils gir1.2-gnomedesktop-3.0 gnome-desktop3-data libgnome-desktop-3-12 libtorrent-rasterbar9 libubuntugestures5 libubuntumetrics5 libubuntutoolkit5 libunity-api0 python-libtorrent qml-module-ubuntu-components qml-module-ubuntu-components-labs
  qml-module-ubuntu-layouts qml-module-ubuntu-performancemetrics qml-module-ubuntu-test qtdeclarative5-qtmir-plugin qtdeclarative5-ubuntu-ui-toolkit-plugin qtmir-desktop ubuntu-ui-toolkit-theme unity8 unity8-common unity8-private vivaldi-snapshot
23 upgraded, 52 newly installed, 0 to remove and 0 not upgraded.
Need to get 75,4 MB of archives.
After this operation, 76,3 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```
No comment... ;)
```
:~$ sudo apt purge -s unity8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dbus-test-runner libdbustest1 libdrm-dev libegl1-mesa-dev libgl1-mesa-dev libgles2-mesa-dev libglu1-mesa-dev libpthread-stubs0-dev libqt5opengl5-dev libwayland-bin libwayland-dev libx11-dev libx11-doc libx11-xcb-dev libxau-dev libxcb-dri2-0-dev libxcb-dri3-dev
  libxcb-glx0-dev libxcb-present-dev libxcb-randr0-dev libxcb-render0-dev libxcb-shape0-dev libxcb-sync-dev libxcb-xfixes0-dev libxcb1-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxshmfence-dev libxxf86vm-dev mesa-common-dev parallel python3-dbusmock
  qt5-default qt5-qmake qtbase5-dev qtbase5-dev-tools qtubuntu-appmenutheme x11proto-core-dev x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev x11proto-xf86vidmode-dev xorg-sgml-doctools
  xtrans-dev
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  unity8* unity8-common* unity8-desktop-session* unity8-tests*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Purg unity8-tests [8.15+17.04.20170206-0ubuntu1] [unity8-common:amd64 ]
Purg unity8 [8.15+17.04.20170206-0ubuntu1] [unity8-desktop-session:amd64 unity8-common:amd64 ]
Purg unity8-common [8.15+17.04.20170206-0ubuntu1] [unity8-desktop-session:amd64 ]
Purg unity8-desktop-session [1.0.13+17.04.20170110.1-0ubuntu1]
```... ;)

---

### Post by ventrical on 2017-02-09
> **ventrical said:**
> Unity8 previews has progressively become worse. I cannot send a screenshot but the icons in the apps windows are clipped on the top and the bottom. The apps will not work correctly and the mouse  pointer is dragging like a snail. This after todays update/upgrade and yes .. I did re-boot. This on a Nvidia graphics machine with zesty  commit from beggining.Unity7 is working well though.

Regards..

This breakage also on Intel chipsets.

---

### Post by jbicha on 2017-02-09
zika, the extra -dev packages issue is [bug 1662608]("https://launchpad.net/bugs/1662608")

---

### Post by zika on 2017-02-09
> **jbicha said:**
> zika, the extra -dev packages issue is [bug 1662608]("https://launchpad.net/bugs/1662608")Seen that. Thank You.

---

### Post by ventrical on 2017-02-25
Still busted. Can upload screenshots. Freeze ups. Worse than ever. Oh joy :)

---

### Post by ventrical on 2017-02-25
Just on a side note .. it is working somewhat  on 16.10 with good functionality .

---

### Post by rrnbtter on 2017-02-26
sGreetings,
I am testing Unity 8 on a new low end Lenovo with the Intel chip set. If I was too negative about Unity 8 elsewhere, I take it back. It is actually starting to look like something I may want for a desktop. I am running it with 17.04 and the 4.10 kernel with Proposed enabled. They could have something usable by release time. If the bare necessities work I may make the switch. 
In addition I agree that Unity 7 with few exceptions is first class in the Zesty edition.  Everything is working perfect for me including, Fn Keys, HDMI, sound and video, WIFI and Bluetooth, Sleep and Awake is instantaneous, no Apport pop-ups, it is all perfect.

---

### Post by ventrical on 2017-02-27
> **rrnbtter said:**
> sGreetings,
I am testing Unity 8 on a new low end Lenovo with the Intel chip set. If I was too negative about Unity 8 elsewhere, I take it back. It is actually starting to look like something I may want for a desktop. I am running it with 17.04 and the 4.10 kernel with Proposed enabled. They could have something usable by release time. If the bare necessities work I may make the switch. 
In addition I agree that Unity 7 with few exceptions is first class in the Zesty edition.  Everything is working perfect for me including, Fn Keys, HDMI, sound and video, WIFI and Bluetooth, Sleep and Awake is instantaneous, no Apport pop-ups, it is all perfect.

Did you install it using a new /daily/ ISO? 

Regards..

---

### Post by rrnbtter on 2017-02-28
Greetings,
@Ventrical, Yes, I installed it with the Zesty daily updated with zsync. It installed with the 4.9 kernel and I picked-up the 4.10 kernel when I enabled proposed. I'm not using the 4.10RC kernel my kernel is native installed by the Zesty update. I think we will be in for a few surprises when the April Release occurs. It has happened before that Canonical didn't flip the switches until the very last day. Regarding Unity 8, as you probably already know, it has a new App section, in which some of them work and some don't. If they are all working at release time and i can also have Kompozer, Filezila and some form of PHP like Bluefish then I am good to go. I have been using the dev version since Natty arrived and  I would really like to be using the Unity 8 release without the Unity 7 back and forth switch.  Otherwise I will stick to Zesty Unity 7 which is already top notch with a few exceptions.

PS If I had it to do over I could have bought the touch screen version of my new computer for around $60 more and with 2 more gig of RAM. I think that would have made the Unity 8 more interesting.

---

### Post by ventrical on 2017-02-28
@rrnbtter
Good evening.

 I downloaded the daily ubuntu zapus and it has 4.10 kernel. I installed it and it is a different animal all together. After installing Libertine the Xapps will not come up and I cannot access xapps in containers. Also the left  side panel includes all the unity 7 apps and only a few work in Unity8, disk-usage-analyzer, gnome-system-monitor etc.. but firefox will not load. Do I have to install  xapps again on a new install?

 I have several other installs. Most of them were working beautifully with Libertine. I could run most near any xapps in containers, graphics, games etc.. and then it all just busted across the board (as is expected in development). Unity8 is certainly not a standalone DE . It is heavily dependent on Unity 7 directories and libs. I agree with you that perhaps it will come down to the last few weeks. This has been a frustrating test case and it is more or less my own fault because I have the illusion at times that we can do most anything with containers, well , actually we can. Thats whats keeping my interest up at the moment. But I can see the great effort it will take it will take to maintain the xapps and containers within the xmir server (so my illusion is that Canonical has limitless human resources available for the flagship DE). I have the feeling that behind the scenes that the whole xapps and containers concept may get dropped in favor of running a pure mir server because it would  loose up valuable human resources to work on other bugs and distros.

One good thing , from a testers perspective, is that there is a lot of breakage and it is rather easy to break a container by installing a random app from the USC using libertine. I have also been experimenting with destroying containers and rebuilding new ones.

  I guess it is just a matter of  keep testing, keep updating. In the meantime I am busy with clients Windows 10 installs that are infected with  ransomware and a plethora of backdoor trojans. It's hard to make converts to ubuntu :) Still... I am encouraged by the earlier functionality of unity8 w libertine and I hope they give it back to us :)

Regards..

btw... after installing the new daily the problem that I had mentioned in my first post of this thread has resolved. ie; truncated icons.

---

### Post by ventrical on 2017-03-17
I joined the webinar at ubuntu-on-air  on the IRC   and asked a few questions about unity8/system76. It was verbalized that unity8 is no way near becoming a default desktop. I did an update/upgrade on a zesty install yesterday and it has gone from worse to worser :) No icons in apps window. terminal is gone. firefox will not run. native browser will not run etc.. but it will run  on 16.04 in some cases.

regards..

---

### Post by cariboo on 2017-03-17
I booted into Unity8 yesterday, and was quite surprised at how well it worked. Only two of the applications I tried had a problem, Nautilus and Chromium. Nautilus crashed right away, and Chromium started up and ran, but was black. Scrolling showed the page I was looking at, but it kept flickering.

This was on an my Toshiba laptop with Intel graphincs, specs are:

```
 inxi -F
System:    Host: alexis Kernel: 4.10.0-13-generic x86_64 (64 bit)
           Desktop: Xfce 4.12.3
           Distro: Ubuntu Zesty Zapus (development branch)
Machine:   Device: laptop System: TOSHIBA product: Satellite C50-B v: PSCMLC-02Y00T
           Mobo: TOSHIBA model: ZBWAA v: 1.00
           UEFI: TOSHIBA v: 1.70 date: 12/11/2014
Battery    BAT1: charge: 20.1 Wh 100.0% condition: 20.1/22.0 Wh (91%)
CPU:       Quad core Intel Pentium N3530 (-MCP-) cache: 1024 KB 
           clock speeds: max: 2582 MHz 1: 748 MHz 2: 611 MHz 3: 1034 MHz
           4: 1079 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: X.Org 1.18.4 drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Bay Trail GLX Version: 3.0 Mesa 17.0.1
Audio:     Card Intel Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-13-generic
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169
           IF: enp1s0 state: down mac: f8:a9:63:7a:e4:e3
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k
           IF: wlp2s0 state: up mac: b8:ee:65:8a:1b:f7
Drives:    HDD Total Size: 750.2GB (14.0% used)
           ID-1: /dev/sda model: TOSHIBA_MQ01ABD0 size: 750.2GB
Partition: ID-1: / size: 19G used: 9.1G (53%) fs: ext4 dev: /dev/sda2
           ID-2: /home size: 665G used: 85G (14%) fs: ext4 dev: /dev/sda4
           ID-3: swap-1 size: 4.18GB used: 0.23GB (6%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 55.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 240 Uptime: 5 days Memory: 2120.9/3836.4MB
           Client: Shell (bash) inxi: 2.3.8

```

---

### Post by ventrical on 2017-03-17
Thanks cariboo. I am going to try it on a laptop. Traditionally I  test most of the dev versions on hard desktops.

Regards..

---

### Post by ventrical on 2017-03-18
Unfortunately the gpu on my latest machine is AMD and I am getting lockups. But I have an older lappy with intel I can try.

Wierd thing also is I am running ubuntu-desktop (unity) and it tells me (gnome).

```

ventrical@ventrical-MS-7850:~$ inxi -Fxz
System:    Host: ventrical-MS-7850 Kernel: 4.10.0-13-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Gnome  (Gtk 3.22.7-1ubuntu2)
           Distro: Ubuntu Zesty Zapus (development branch)
Machine:   Device: laptop System: Hewlett-Packard product: HP 2000 Notebook PC v: 0889130000305910000620100
           Mobo: Hewlett-Packard model: 2128 v: KBC Version 11.11
           UEFI: Insyde v: F.37 date: 06/26/2013
Battery    BAT0: charge: 42.1 Wh 100.0% condition: 42.1/42.1 Wh (100%)
           model: Hewlett-Packard Primary status: Full
CPU:       Dual core AMD E2-3000 APU with Radeon HD Graphics (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 6588
           clock speeds: max: 1650 MHz 1: 1500 MHz 2: 1350 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Kabini [Radeon HD 8280 / R3 Series]
           bus-ID: 00:01.0
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1366x768@60.07hz
           GLX Renderer: Gallium 0.4 on AMD KABINI (DRM 2.49.0 / 4.10.0-13-generic, LLVM 4.0.0)
           GLX Version: 3.0 Mesa 17.0.1 Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel bus-ID: 00:14.2
           Card-2 Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio
           driver: snd_hda_intel bus-ID: 00:01.1
           Sound: Advanced Linux Sound Architecture v: k4.10.0-13-generic
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: 2000 bus-ID: 01:00.0
           IF: enp1s0 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k bus-ID: 05:00.0
           IF: wlo1 state: down mac: <filter>
Drives:    HDD Total Size: 128.0GB (26.2% used)
           ID-1: /dev/sda model: SAMSUNG_MZ7PA128 size: 128.0GB
Partition: ID-1: / size: 66G used: 28G (45%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 4.15GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 41.0C mobo: N/A gpu: 43.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 190 Uptime: 6 min Memory: 1271.7/3408.4MB
           Init: systemd runlevel: 5 Gcc sys: 6.3.0
           Client: Shell (bash 4.4.51) inxi: 2.3.8 
ventrical@ventrical-MS-7850:~$ 

```

---

### Post by mc4man on 2017-04-01
As of today the state of 8 barely makes pitiful. 
The main scope is empty other than "Manage' which manages nothing useful
No gnome apps ever complete opening. 
A few unity 8 native apps do open plus libreoffice works, that's it.
A few weeks to go so maybe it'll graduate to usable for a few minutes or so..

app opening bug - [https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1675448](https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1675448)
useless scope bug - [https://bugs.launchpad.net/ubuntu/+source/unity8-desktop-session/+bug/1668700](https://bugs.launchpad.net/ubuntu/+source/unity8-desktop-session/+bug/1668700)

---

### Post by rrnbtter on 2017-04-02
Greetings,
I am testing on a new Lenovo Intel Laptop. There has been a lot of downstream that includes Mir and Mir-desktop. It looks to me that they are getting the project ready for release time.  I agree that much that is there doesn't work however what "is" there works well, at least on my system. It also pays to acknowledge that the current Unity 8 login resolves to a "phone" interface and not a desktop. So two big things that are currently missing is the Mir display server and the Unity 8 desktop. Much of what is being tested isn't what we are awaiting. The downstream gives me some optimism. It looks like what is needed is already there, just not being used. IMO.

---

### Post by ventrical on 2017-04-03
@mac,rrnbttr,

Sorry. mac4man is right. well.. it's not pitiful..it's pathetic! It had regressed into a pile of bricks. It is not even a reasonable facsimile of what it once was during the yakkety release. All my updates on machines that I have worked tirelessly on to experiment with Libertine containers are totally busted (and have been busted for weeks). 

However .. I still have an genuine enthusiasm that these jabberwockys will be worked out in the long run :)



Regards..

---

### Post by ventrical on 2017-04-03
> **rrnbtter said:**
> Greetings,
I am testing on a new Lenovo Intel Laptop. There has been a lot of downstream that includes Mir and Mir-desktop. It looks to me that they are getting the project ready for release time.  I agree that much that is there doesn't work however what "is" there works well, at least on my system. It also pays to acknowledge that the current Unity 8 login resolves to a "phone" interface and not a desktop. So two big things that are currently missing is the Mir display server and the Unity 8 desktop. Much of what is being tested isn't what we are awaiting. The downstream gives me some optimism. It looks like what is needed is already there, just not being used. IMO.

I think a lot of work is going into building a unity8 snap image for ubuntu-core . I am only guessing that some of the original  unity8 classic apps frameworks as been shelved atm.

uhhmm.. check out this old stream and listen to Kevin Gunn real close if you can get through some of the noise..

[https://www.youtube.com/watch?v=oGsA55RvqLI](https://www.youtube.com/watch?v=oGsA55RvqLI)

---

### Post by ventrical on 2017-04-06
@all

I  want to sincerely thank all of the U+1 members and other UbuntuForums members in general who had taken up  to testing the unity8 preview.  I am truly broken about this as per recent news. I ask all U+1 and ubuntuforums members to redirect your testing efforts to the other many fine DE being currently produced by the Canonical Development Team.

Kind regards...

Ventrical

---

