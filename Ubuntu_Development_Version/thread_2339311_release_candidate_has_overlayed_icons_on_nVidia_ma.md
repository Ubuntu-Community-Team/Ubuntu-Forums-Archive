---
title: "release candidate has overlayed icons on nVidia machine"
date: 2016-10-07
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-10-07
Noticed this while testing different form factors from "live" release candidate.

*note* 

Apache forbids screenshot.

so..

[URL="https://www.youtube.com/watch?v=uycOOKTzcBg"]https://www.youtube.com/watch?v=uycOOKTzcBg 
[/URL]
Other info:

```
ubuntu@ubuntu:~$ inxi -Fxz
System:    Host: ubuntu Kernel: 4.8.0-19-generic x86_64 (64 bit gcc: 6.2.0)
           Desktop: Unity 7.5.0 (Gtk 3.20.9-1ubuntu2) Distro: Ubuntu 16.10
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           BIOS: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 12.0.3 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-3 Logitech Webcam C210 driver: USB Audio usb-ID: 001-003
           Sound: Advanced Linux Sound Architecture v: k4.8.0-19-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 82.0GB (3.7% used)
           ID-1: /dev/sda model: WDC_WD800HLFS size: 80.0GB temp: 26C
           ID-2: USB /dev/sdb model: USB_Flash_Memory size: 2.0GB temp: 0C
Partition: ID-1: swap-1 size: 3.22GB used: 0.01GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 33.0C mobo: 34.0C gpu: 35.0
           Fan Speeds (in rpm): cpu: 4245 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 227 Uptime: 1:04 Memory: 1375.1/3007.1MB
           Init: systemd runlevel: 5 Gcc sys: 6.2.0
           Client: Shell (bash 4.3.461) inxi: 2.3.1 
ubuntu@ubuntu:~$ 

```

---

### Post by PaulW2U on 2016-10-07
> **ventrical said:**
> Noticed this while testing different form factors from "live" release candidate.
That's bug [#1611955]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1611955") which was reported as long as ago as 10th August.

We're not seeing the Release Candidate images yet as according to Adam Conrad's [Final Freeze Announcement]("https://lists.ubuntu.com/archives/ubuntu-release/2016-October/003935.html") we won't see those images until Friday night or Saturday morning, presumably UTC time. **lsb_release -a** is still reports "Ubuntu Yakkety Yak (development branch)", normally this is changed once the final images are ready to be spun.

---

### Post by ventrical on 2016-10-07
> **PaulW2U said:**
> That's bug [#1611955]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1611955") which was reported as long as ago as 10th August.

We're not seeing the Release Candidate images yet as according to Adam Conrad's [Final Freeze Announcement]("https://lists.ubuntu.com/archives/ubuntu-release/2016-October/003935.html") we won't see those images until Friday night or Saturday morning, presumably UTC time. **lsb_release -a** is still reports "Ubuntu Yakkety Yak (development branch)", normally this is changed once the final images are ready to be spun.

Well I feel like a donkeys rear end now ! :) I had assumed we had RC yesterday. Not so.
Thanks for bringing this to my attention .. one step forward .. two steps backwards :)

Regards..

---

### Post by ventrical on 2016-10-08
The images are still set at Oct. 6th. Appears to have not budged. Will try a zsync  nonetheless.

Early Saturday morning here, Oct. 8th EST

Regards..

---

### Post by ventrical on 2016-10-08
The iso zsynced by as much as 10% but nothing has changed as far as per the original topic and it reports (development branch) still.

Regards..

Sat. Oct. 8th 4:08am EST

There must be problems and it is Canadian thanksgiving weekend.

---

### Post by PaulW2U on 2016-10-08
> **ventrical said:**
> The iso zsynced by as much as 10% but nothing has changed as far as per the original topic and it reports (development branch) still.
We need an update to base-files first which will remove the development branch tag from the release description. Once the images are released then [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/) will show "Yakkety Final" as being available for testing.

---

### Post by ventrical on 2016-10-08
> **PaulW2U said:**
> We need an update to base-files first which will remove the development branch tag from the release description. Once the images are released then [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/) will show "Yakkety Final" as being available for testing.

It has now moved from Oct 6th to Oct 7th.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

lets see..

---

### Post by ventrical on 2016-10-08
actually made no difference..

```

Read ./yakkety-desktop-amd64.iso. Target 100.0% complete.      
verifying download...checksum matches OK
used 1593835520 local, fetched 0
ventrical@ventrical-MS-7850:~/Downloads$ 

```

---

### Post by PaulW2U on 2016-10-08
Re overlayed icons bug - [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1611955/comments/4](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1611955/comments/4) - now fixed.

Presumably no point releasing images while there are obvious bugs that still need fixing.

---

### Post by ventrical on 2016-10-08
> **PaulW2U said:**
> Re overlayed icons bug - [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1611955/comments/4](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1611955/comments/4) - now fixed.

Presumably no point releasing images while there are obvious bugs that still need fixing.

Agreed.
Obviously I need to curb my enthusiasms;)

[https://www.youtube.com/watch?v=YlkLuWrOGr0&feature=youtu.be](https://www.youtube.com/watch?v=YlkLuWrOGr0&feature=youtu.be)

My cool other stuff. ;)

[https://www.youtube.com/watch?v=2K2wIRGg8pU](https://www.youtube.com/watch?v=2K2wIRGg8pU)

Regards..

---

### Post by PaulW2U on 2016-10-08
> **ventrical said:**
> Obviously I need to curb my enthusiasms;)
There's nothing wrong with being enthusiastic but your post prompted me to see what was waiting in -proposed. It seems that some Yakkety application versions are still behind those of Xenial less than a week before Yakkety's release.

There are updates to Chromium, Firefox and Thunderbird being held there. I would have thought that Yakkety would be **ahead** of other releases but what would I know? I'm only a casual tester after all.  :)

There's also yet another kernel update waiting for us, 4.8.0.21.

---

### Post by ventrical on 2016-10-08
> **PaulW2U said:**
> There's nothing wrong with being enthusiastic but your post prompted me to see what was waiting in -proposed. It seems that some Yakkety application versions are still behind those of Xenial less than a week before Yakkety's release.

There are updates to Chromium, Firefox and Thunderbird being held there. I would have thought that Yakkety would be **ahead** of other releases but what would I know? I'm only a casual tester after all.  :)

There's also yet another kernel update waiting for us, 4.8.0.21.

I think it may have had something to do with the xenial release... uhh .. there were so many upgrade problems when upgrading from trusty to xenial (a project kansasnoob practically took on singlehandedly)  so those are critical bugs in the previous stack. Thanks for your research into this.  I'm pretty well stumped with the exception of the documentation you have provided.

Good things come to those who wait ... :)

regards..

---

### Post by PaulW2U on 2016-10-08
> **ventrical said:**
> Good things come to those who wait ... :)
The ISO testing tracker is now showing some [Yakkety Final]("http://iso.qa.ubuntu.com/qatracker/milestones/368/builds") ISOs.

These are release candidates that will become "final" unless they are updated before they are released on Thursday.

---

### Post by ventrical on 2016-10-08
> **PaulW2U said:**
> The ISO testing tracker is now showing some [Yakkety Final]("http://iso.qa.ubuntu.com/qatracker/milestones/368/builds") ISOs.

These are release candidates that will become "final" unless they are updated before they are released on Thursday.

Yes .. I just recalled that we have to download the images (don't we?) because those appends will not bring any diff up using zsync. So I see ubuntu Base but zsyncing gives nothing.

```

ventrical@ventrical-MS-7850:~/Downloads$ zsync -i ./yakkety-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/yakkety-desktop-amd64.iso.zsync
#################### 100.0% 268.0 kBps DONE     

reading seed file ./yakkety-desktop-amd64.iso: *****************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read ./yakkety-desktop-amd64.iso. Target 100.0% complete.      
verifying download...checksum matches OK
used 1593835520 local, fetched 0
ventrical@ventrical-MS-7850:~/Downloads$ 


```

I know there was a lot of chatter about exclusive automated testing and testing at the q/a tracker only to discern from dupes and incomplete reports. So that could leave freelance testers out of the loop unless they log on to the tracker.

---

### Post by ventrical on 2016-10-08
xubuntu ,core and lubuntu are all in 'final' testing

perhaps will spin xubuntu

here we go :)

---

### Post by ventrical on 2016-10-08
Ubuntu-desktop now in. :)

Zippity doo dah .. zippity day... hehehe

regards..

---

### Post by PaulW2U on 2016-10-10
> **ventrical said:**
> Ubuntu-desktop now in. :)
But expect some respins some time today as base-files has just been updated and "development branch" has been removed.

```
paul@C50B~> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.10
Release:        16.10
Codename:       yakkety

```

---

