---
title: "Seeking advice on building a new PC"
date: 2018-02-16
forum: The Cafe
---

### Post by satimis on 2018-02-16
Hi all,

My desktop PC has been running for about 10 years.  It is time for me to build a new desktop PC eventhough the said PC is still running strong.  Besides I'm prepared to upgrade my 2K 25" monitor to 4K 27" monitor.


Configuration of running desktop PC
===========================

CPU
&#10219; inxi -C```

CPU:       Octa core AMD FX-8320 Eight-Core (-MCP-) cache: 16384 KB 
           clock speeds: max: 3500 MHz 1: 2300 MHz 2: 1700 MHz 3: 1700 MHz
           4: 1700 MHz 5: 1700 MHz 6: 1400 MHz 7: 1700 MHz 8: 1700 MHz

```

Graphic Card
&#10219; inxi -G```

Graphics:  Card: NVIDIA GK208 [GeForce GT 730]
           Display Server: X.Org 1.18.4 driver: nvidia
           Resolution: 2560x1440@59.95hz
           GLX Renderer: GeForce GT 730/PCIe/SSE2
           GLX Version: 4.4.0 NVIDIA 340.104

```

Hard Drives
$ inxi -D```

Drives:    HDD Total Size: 4775.0GB (18.0% used)
           ID-1: /dev/sda model: TS1TSSD370 size: 1024.2GB
           ID-2: /dev/sdb model: SanDisk_SDSSDH32 size: 250.1GB
           ID-3: /dev/sdc model: WDC_WD1502FAEX size: 1500.3GB
           ID-4: /dev/sdd model: WDC_WD2005VBYZ size: 2000.4GB

```
TS1TSSD370 (SSD, storage 1T) running OS and Oracle VirtualBox with all VMs on this drive
SanDisk_SDSSDH32 (SSD, storage 250G) running OS and KVM with guests on /dev/sdc

/dev/sdd is solely for data storage.

Booting is controlled on BIOS

Motherboard
$ inxi -M```

Machine:   Mobo: ASUSTeK model: M5A97 LE R2.0 v: Rev 1.xx
           Bios: American Megatrends v: 2501 date: 04/09/2014

```

Network card
$ inxi -N```

Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169

```

RAM
$ sudo inxi -m```

[sudo] password for satimis: 
Memory:    Array-1 capacity: 32 GB devices: 4 EC: None
           Device-1: DIMM0 size: 8 GB speed: 667 MHz type: DDR3
           Device-2: DIMM1 size: 8 GB speed: 667 MHz type: DDR3
           Device-3: DIMM2 size: 8 GB speed: 667 MHz type: DDR3
           Device-4: DIMM3 size: 8 GB speed: 667 MHz type: DDR3

```

Monitor - DELL U2515H 25"

$ xrandr```

Screen 0: minimum 8 x 8, current 2560 x 1440, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 2560x1440+0+0 (normal left inverted right x axis y axis) 553mm x 311mm
   2560x1440     59.95*+
   2048x1152     60.00  
   1920x1200     59.88  
   1920x1080     60.00    59.94    50.00    29.97    25.00    23.97    60.05    60.00    50.04  
   1680x1050     59.95  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1280x720      60.00    59.94    50.00  
   1200x960      60.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00    50.08  
   720x480       59.94    60.05  
   640x480       75.00    59.94    59.93  

```

The new desktop PC shall be used for webpage design and graphic editing.

I have looked at following AMD CPU;

1)
AMD Ryzen 7 1700X YD170XBCAEWOF 8 Cores/16 Threads, 3.8GHz,20MB Cache, Socket AM4 CPU
[https://www.amd.com/en/products/cpu/amd-ryzen-7-1700x](https://www.amd.com/en/products/cpu/amd-ryzen-7-1700x)

and

2)
AMD Ryzen 7 1800X YD180XBCAEWOF 8 Cores/16 Threads, 4.0GHz,20MB Cache, Socket AM4 CPU
[https://www.amd.com/en/products/cpu/amd-ryzen-7-1800x](https://www.amd.com/en/products/cpu/amd-ryzen-7-1800x)


I have following questions;
1) Which AMD CPU shall I select ?
AMD Ryzen 7 1700X or AMD Ryzen 7 1800X

very small difference in price.  **[COLOR="#FF0000"]OR any other suggestion?[/COLOR]**

2)
For installing OS, Oracle VirtualBox and VMs shall I go 1T SSD?
In this new box I shall not install dual-boot.  Neither I'll install KVM but Oracle VirtualBox only. Booting is very fast on running SSD and so is the VMs.

Shall I get a 250G SSD for OS and VirtualBox with all VMs a new 2T WD Hard Drive?

Or

Get a 1T SSD for running OS, VirtualBox and VMs, data to be installed on a new 1T WD Hard Drive?

3)
RAM - shall I go 64G Kit or 128G Kit or staying on 32G Kit?
128G Kit is quite expensive.  

Please shed me some light on building this new desktop PC.  Thanks in advance

Regards
satimis

---

### Post by wildmanne39 on 2018-02-16
*Thread moved to **The Cafe, a more appropriate forum**.*

---

### Post by satimis on 2018-02-16
> **wildmanne39 said:**
> *Thread moved to **The Cafe, a more appropriate forum**.*

Thanks

satimis

---

### Post by poorguy on 2018-02-16
Your 10 year old build looks to be pretty awesome and unless you are just wanting to dump some cash I see no real need.

Are you running any resource intensive apps although the hardware you have now will run most anything you toss to it.

I'd keep using it until it stopped working older components are superior to the new components produced today imo.

---

### Post by satimis on 2018-02-16
> **poorguy said:**
> Your 10 year old build looks to be pretty awesome and unless you are just wanting to dump some cash I see no real need.

Are you running any resource intensive apps although the hardware you have now will run most anything you toss to it.

I'd keep using it until it stopped working older components are superior to the new components produced today imo.

Hi,

Thanks for your advice.

What causes me thinking of building a new desktop PC are as follows;

1)
I'm prepared to upgrade my 2K 25" monitor to 4K 27" monitor which needs a new video card.  This is a side intention NOT my major intention for building a new desktop PC.  I just purchase a new video card and install it on the running desktop PC.

2)
The 1TB SSD is nearly full.  Besides I expect to reinstall Oracle VirtualBox which has been working for prolonged time.  It was first installed on package download on Oracle website, lately reinstalled on Ubuntu repo and again reinstalled on Oracle website package.  I couldn't recall exactly.

Please see the attached photo - VirtualBox Manager

Is Oracle VirtualBox installed on Oracle website package or on Ubuntu Repo package?

Before reinstalling Oracle VirtualBox I expect to have a desktop PC running VirtualBox, the download package, and all VMs smoothly first.  Then I'll wipe out the 1TB SSD drive.

**[COLOR="#FF0000"]To purchase a new 1TB SSD to get it done or otherwise?[/COLOR]**

Suggestion would be appreciated.  Thanks

Regards
satimis

---

### Post by poorguy on 2018-02-16
Never used virtual box and have no idea about it.

---

### Post by ajgreeny on 2018-02-16
Have a look at the **Debian-based Linux distributions** section at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) where you can add the Oracle VBox repos to your software sources with a single command, and in that way keep your VBox version fully up to date.

You still have to choose either VBox 5.1 or 5.2 from the versions on offer; until recently I still used the 5.1 version as there are still problems with the Guest Additions (mentioned on that site) if 3D acceleration is enabled in the guest Linux OS, though there is an updated iso version you can download from the site. As I don't bother with 3D in my Linux guests it is no problem for me and 5.2.6 is working very well for me now.

---

### Post by satimis on 2018-02-16
> **ajgreeny said:**
> Have a look at the **Debian-based Linux distributions** section at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) where you can add the Oracle VBox repos to your software sources with a single command, and in that way keep your VBox version fully up to date.
Hi,

Thanks for your advice.

At the very beginning when I built this desktop PC I installed VirtualBox on the package download on Oracle website.  Whenever there was a new version a warning would popup on first time starting the VirtualBox Manager and asking me whether I need to install the new version.  With a click I could install the new version and simultaneous the old version would be replaced without any problem.

Later I reinstalled VirtualBox on Ubuntu repo.  After discovering that the repo was not updated then I reinstalled VirtualBox again on the package download on Oracle website.

Abovementioned comes only from my recollection.

Now occasionally when I first time start the Virtualbox Manager the aforesaid warning popup but I couldn't install the new version recommended.  I don't know why?  For such a reason I expect wipe out the OS, Ubuntu 16.04, and reinstall it as well as VirtualBox to be download on Oracle website.

I'm considering to purchase a new 1T SSD to install Ubuntu 16.04 desktop as Host as well as VirturalBox, the download version.  Then I'll migrate all VMs to the new 1T SSD.  The old 1T SSD will be used in my spare desktop PC.

There are >40 VMs created, most of them for testing only.  About 5 VMs are running for daily working.  The Host OS is solely for running VirtualBox and the browser, Firefox.  All works are done on VMs.  I retain the VMs created for testing solely for future reference which is my headache.  They occupy the space of SSD and they may not be used again just like the old data accumulated on the hard-drive.

Any suggestion on above?  There are plenty of space on the 2T WD hard drive.  Thanks

> 
You still have to choose either VBox 5.1 or 5.2 from the versions on offer; until recently I still used the 5.1 version as there are still problems with the Guest Additions (mentioned on that site) if 3D acceleration is enabled in the guest Linux OS, though there is an updated iso version you can download from the site. As I don't bother with 3D in my Linux guests it is no problem for me and 5.2.6 is working very well for me now.
Actually I'm not quite clear about the function of 3D acceleration?  For the guest to run 3D images?

Please advise.  Thanks in advance.

Regards
satimis

---

### Post by satimis on 2018-02-16
Hi all,

The VirtualBox Information tag popup when I first start VirtualBox Manager this morning.  Please see attached photo.

I have following package download
virtualbox-5.2_5.2.6-120293~Ubuntu~xenial_amd64.deb

satimis

---

