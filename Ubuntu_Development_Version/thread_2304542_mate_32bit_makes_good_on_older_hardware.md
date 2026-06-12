---
title: "mate 32bit makes good on older hardware"
date: 2015-11-27
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-11-27
Downloading and installing xenial xerus on a 10 year old Acer Aspire that was marked for scrap is now up and running with compiz and a very fine looking desktop experience.

Don't throw out that old tower or laptop just yet :)

Regards..

```

ventrical@ventrical-Aspire-3620:~$ inxi -b
System:    Host: ventrical-Aspire-3620 Kernel: 4.2.0-19-generic i686 (32 bit)
           Desktop: MATE 1.10.2  Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire 3620 v: 0100
           Mobo: Acer model: Garda-910 v: Rev
           Bios: Phoenix v: V1.01 date: 12/15/2005
CPU:       Single core Intel Celeron M (-UP-) speed: 1496 MHz (max)
Graphics:  Card: Intel Mobile 915GM/GMS/910GML Express Graphics Controller
           Display Server: X.Org 1.17.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1280x800@59.97hz
           GLX Renderer: Mesa DRI Intel 915GM x86/MMX/SSE2
           GLX Version: 1.4 Mesa 11.0.5
Network:   Card-1: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg]
           driver: ath5k
           Card-2: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
           driver: 8139too
Drives:    HDD Total Size: 80.0GB (5.8% used)
Info:      Processes: 136 Uptime: 5 min Memory: 220.0/991.4MB
           Client: Shell (bash) inxi: 2.2.28 
ventrical@ventrical-Aspire-3620:~$ 

```

---

### Post by QDR06VV9 on 2015-11-27
He He He! I have an old Shuttle Bare Bone with an AMD Athlon 2800 in there 2 Gigs of ram and A Nvidia 8500 with 512 ram
I have to see how it runs on that.
Thanks Vent i was getting sooo bored.
Cheers

---

### Post by slickymaster on 2015-11-27
It runs like a charm on a 8 year Toshiba```
System:    Host: PaPir Kernel: 4.2.0-19-generic i686 (32 bit) Desktop: Xfce 4.12 Distro: Ubuntu 16.04 xenial
Machine:   System: TOSHIBA product: TECRA A7 version: PTA71E-0U600VPT
           Mobo: Intel model: CAPELL VALLEY(NAPA) CRB Bios: Phoenix version: 6.00 date: 07/12/2007
CPU:       Dual core Intel Core2 CPU T7200 (-MCP-) clocked at 1000.00 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV515/M54 [Mobility Radeon X1400] 
           X.Org: 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1280x800@60.0hz 
           GLX Renderer: Gallium 0.4 on ATI RV515 GLX Version: 2.1 Mesa 10.1.3
Network:   Card-1: Intel 82573L Gigabit Ethernet Controller driver: e1000e 
           Card-2: Intel PRO/Wireless 3945ABG [Golan] Network Connection driver: iwl3945 
Drives:    HDD Total Size: 120.0GB (28.6% used)
Info:      Processes: 181 Uptime: 48 min Memory: 1223.0/3033.8MB Client: Shell (bash) inxi: 1.9.17
```

---

### Post by ventrical on 2015-11-27
> **runrickus said:**
> He He He! I have an old Shuttle Bare Bone with an AMD Athlon 2800 in there 2 Gigs of ram and A Nvidia 8500 with 512 ram
I have to see how it runs on that.
Thanks Vent i was getting sooo bored.
Cheers

If you get a pae error you may want to try this - [https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Processor_.28CPU.29](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Processor_.28CPU.29)

It worked for me with Lubuntu. I think it may work with Mate also. Will try it.

Regards..

---

### Post by ventrical on 2015-11-27
> **slickymaster said:**
> It runs like a charm on a 8 year Toshiba```
System:    Host: PaPir Kernel: 4.2.0-19-generic i686 (32 bit) Desktop: Xfce 4.12 Distro: Ubuntu 16.04 xenial
Machine:   System: TOSHIBA product: TECRA A7 version: PTA71E-0U600VPT
           Mobo: Intel model: CAPELL VALLEY(NAPA) CRB Bios: Phoenix version: 6.00 date: 07/12/2007
CPU:       Dual core Intel Core2 CPU T7200 (-MCP-) clocked at 1000.00 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV515/M54 [Mobility Radeon X1400] 
           X.Org: 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1280x800@60.0hz 
           GLX Renderer: Gallium 0.4 on ATI RV515 GLX Version: 2.1 Mesa 10.1.3
Network:   Card-1: Intel 82573L Gigabit Ethernet Controller driver: e1000e 
           Card-2: Intel PRO/Wireless 3945ABG [Golan] Network Connection driver: iwl3945 
Drives:    HDD Total Size: 120.0GB (28.6% used)
Info:      Processes: 181 Uptime: 48 min Memory: 1223.0/3033.8MB Client: Shell (bash) inxi: 1.9.17
```

One thing I noticed right off (with today's daily/current) is that there were no errors, no verbose code, no systemd problems. It rolled right out of the box .. almost like a System7 product!

Regards..

---

### Post by VMC on 2015-11-27
I might have to excavate an old P4 from its grave, and install ubuntu-mate 32bit. Right now it runs quite well on XP and an old 32bit xubuntu.

---

### Post by ventrical on 2015-11-27
> **VMC said:**
> I might have to excavate an old P4 from its grave, and install ubuntu-mate 32bit. Right now it runs quite well on XP and an old 32bit xubuntu.

I retired a lot of machines that used to work really well (with compiz)+(unity) but during raring ringtail (13.04) testing, unity and compiz would break up , not work or roll over to some sort of obscure video driver running on llvmpipe which was just a horrible desktop experience. Maybe Mate has a couple of tricks up it's sleeve. It's worth checking out.

Regards..

---

### Post by ventrical on 2015-11-28
Got er going on this old beast :)

---

### Post by mikewhatever on 2015-11-28
> **ventrical said:**
> Downloading and installing xenial xerus on a 10 year old Acer Aspire that was marked for scrap is now up and running with compiz and a very fine looking desktop experience.

Don't throw out that old tower or laptop just yet :)

Regards..


...and have you managed to do anything useful with it, other then installing Mate and looking at the desktop?

I often find 10 year old machines so limiting, that they hardly justify investments of time and effort, let alone repairs and upgrades.
They are not really suitable as media hubs for the lack of codec and driver support, since most will struggle with 560p or above videos. They will also provide a sub-par browsing experience with both Firefox and Chrome, and those with 10Mbps ethernet are too slow for server or torrenting tasks. 
Last, but not least, they are usually noisy and power hungry heaters, so, why keep them?

---

### Post by sammiev on 2015-11-28
The 64bit is running great on this 8 year old Toshiba.

May have to get an SSD for this guy. :)

---

### Post by kurt18947 on 2015-11-28
> **mikewhatever said:**
> ...and have you managed to do anything useful with it, other then installing Mate and looking at the desktop?

I often find 10 year old machines so limiting, that they hardly justify investments of time and effort, let alone repairs and upgrades.
They are not really suitable as media hubs for the lack of codec and driver support, since most will struggle with 560p or above videos. They will also provide a sub-par browsing experience with both Firefox and Chrome, and those with 10Mbps ethernet are too slow for server or torrenting tasks. 
Last, but not least, they are usually noisy and power hungry heaters, so, why keep them?

I have an HP desktop  that was born with WinME. I upgraded the RAM (all the way from 64 MB to 512 MB. by cracky!!:p) and installed Ubuntu Mate. It's really too slow for desktop use but is doing yeoman service as a torrent box. I have a few resource-limited community distro .iso s on there. Nothing copyright protected of course.

---

### Post by ventrical on 2015-11-28
> **mikewhatever said:**
> ...and have you managed to do anything useful with it, other then installing Mate and looking at the desktop?


 One of the core ideas of Ubuntu Development Version is to test ISO images on different machines (to those who have access to several different machines). ubuntu-mate has made the claim that it can work on older computers - so - we test that claim. We can either report the findings at qa/tracker or share basic findings here. Uhh .. yes .. one case in point : I have a Sony Vaio mini mobile laptop with 1GHz Centrino. I rebuilt it with scrap parts. I installed Lucid Lynx (10.04LTS) 4 years ago. It is currently employed at a local retirement home where it plays Gregorian Chants on YouTube for a resident that lives there. Some people like prayer hours and holy hours and that little PC with Lucid on it has yet to fail. It also is a litmus test for the particular brand of USB I had chose to use for the harddrive. Testing older machines keeps me busy when there is downtime in current development.


> 
I often find 10 year old machines so limiting, that they hardly justify investments of time and effort, let alone repairs and upgrades.
They are not really suitable as media hubs for the lack of codec and driver support, since most will struggle with 560p or above videos. They will also provide a sub-par browsing experience with both Firefox and Chrome, and those with 10Mbps ethernet are too slow for server or torrenting tasks. 
Last, but not least, they are usually noisy and power hungry heaters, so, why keep them?

  I have not had very many fails running Ubuntu on older equipment and where I reside - computer parts and accessories are very cheap and I get a lot of stuff for free. I work with some seniors and they basically just want to check their e-mails, transfer pictures from their slabs and print documents , all of which can be accomplished with ubuntu on older machines. Some individuals have a conservative mindset and want to get the best of what they invested.  So that older  machine that at one time cost $2000  can now be deployed back to a working state. Classic Computering will be here to stay for some time and Ubuntu , overall, provides a ways and means to carry that on.

Regards...

---

### Post by ventrical on 2015-11-28
> **sammiev said:**
> The 64bit is running great on this 8 year old Toshiba.

May have to get an SSD for this guy. :)

I am being off topic on my own thread (nothing new ) :) but the SSD cards work on some AMD based older PCs on SATAII with a real fast bootup/load-up time.!!

Regards..

---

### Post by ventrical on 2015-11-28
> **kurt18947 said:**
> I have an HP desktop  that was born with WinME. I upgraded the RAM (all the way from 64 MB to 512 MB. by cracky!!:p) and installed Ubuntu Mate. It's really too slow for desktop use but is doing yeoman service as a torrent box. I have a few resource-limited community distro .iso s on there. Nothing copyright protected of course.

+1 :)

---

### Post by QDR06VV9 on 2015-11-28
> **ventrical said:**
> If you get a pae error you may want to try this - [https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Processor_.28CPU.29](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Processor_.28CPU.29)

It worked for me with Lubuntu. I think it may work with Mate also. Will try it.

Regards..
Thanks Vent I am still waiting for the servers to calm down 18 hrs to Download:o
I discovered that I all ready had Lubuntu installed on it, But want to see how Mate dose on this little box.
Regards

---

### Post by ventrical on 2015-11-28
> **runrickus said:**
> Thanks Vent I am still waiting for the servers to calm down 18 hrs to Download:o
I discovered that I all ready had Lubuntu installed on it, But want to see how Mate dose on this little box.
Regards

Just a side note - the xenial 32bit version daily ubuntu-mate works just fine in standard graphics mode.  It is smooth enough not to have to have compiz loaded just for the sake of eye candy. As kurt18947 pointed out .. he is using his install as a torrent box.

Also .. another note in that I had noticed 32bit Mate having very low memory requirement so one could always install razorqt or even lubuntu-desktop.

Regards..

---

