---
title: "Slow performance after updates"
date: 2017-07-03
forum: Ubuntu/Debian BASED
---

### Post by amtrakuk on 2017-07-03
Hi,

I have done a reinstall of Ubuntu 16.04 LTS yesterday due to a creeping performance issue, especially with Firefox and Flash.  Playing a resource intensive Flash based browser game on a daily basis got so bad the game was almost unplayable even after clearing the cache etc.

First i thought i'd try LMDE MATE and what blinding performance it gave - until I installed the updates.  Then I tried Manjaro XFCE, similar story after the updates.

I downloaded a fresh version of 16.04 LTS x64 yesterday, burn it to USB and performed a reinstall.  I enabled the Install the 3rd party add-ons (flash etc) and install updates during installation process.

Once installed, logged in and flashed up Firefox, Logged onto the flash game and the performance was superb, no stuttering or drop outs at all, the desktop was back to the snappy performance I remember, also LAN File transfer is noticeably faster.  I could almost say it was ideal.

I have checked the update settings and they are set to "download and install" security updates.

There are a stack of updates in the Software Centre and I suspect if I run an update.  I can guess what's going to happen if I install them :(

It seems to be a common issue across distros but I can't accept installing updates should hobble an installation 

Does anyone know what maybe crippling the general performance of the machine once I install the updates?

I'm using a Dell latitude E6410 (i5 3.2 Ghz, 4GB Ram, 120 GB SSD)

---

### Post by ajgreeny on 2017-07-03
But what graphics card do you have? 
This problem sounds as if it might be caused by a poor driver for that hardware.

---

### Post by amtrakuk on 2017-07-03
I was thinking along the lines of the kernel version (as it happens on all the distros)

IIRC its an integrated Intel GMA HD chipset

---

### Post by vasa1 on 2017-07-03
If you want, you can post the output of```
inxi -Fx
``` assuming you've installed *inxi*.

That's a convenient way to share your system's specs.

---

### Post by amtrakuk on 2017-07-03
Here is the output, I have not yet installed any "updates",  Should I install them yet?

```
System:    Host: ajh-Latitude-E6410 Kernel: 4.8.0-36-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Dell (portable) product: Latitude E6410 v: 0001
           Mobo: Dell model: 0K42JR v: A01 Bios: Dell v: A04 date: 07/08/2010
CPU:       Dual core Intel Core i5 M 520 (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9576
           clock speeds: max: 2400 MHz 1: 1733 MHz 2: 1333 MHz 3: 1333 MHz
           4: 1333 MHz
Graphics:  Card: NVIDIA GT218M [NVS 3100M] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1280x800@60.14hz
           GLX Renderer: Gallium 0.4 on NVA8
           GLX Version: 3.0 Mesa 12.0.6 Direct Rendering: Yes
Audio:     Card-1 Intel 5 Series/3400 Series High Definition Audio
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.8.0-36-generic
Network:   Card-1: Intel 82577LM Gigabit Network Connection
           driver: e1000e v: 3.2.6-k port: 8040 bus-ID: 00:19.0
           IF: eno1 state: down mac: 00:26:b9:f5:96:e4
           Card-2: Broadcom BCM43224 802.11a/b/g/n
           driver: bcma-pci-bridge bus-ID: 03:00.0
           IF: wlp3s0b1 state: up mac: 5c:ac:4c:7f:a2:ee
Drives:    HDD Total Size: 128.0GB (31.6% used)
           ID-1: /dev/sda model: ADATA_SU800 size: 128.0GB temp: 49C
Partition: ID-1: / size: 114G used: 34G (32%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.22GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 70.0C mobo: N/A gpu: 74.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 245 Uptime: 7 min Memory: 1789.6/3876.9MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35
```

Good job as I was wrong about the graphics card!

---

### Post by amtrakuk on 2017-07-03
Right I think I have found the problem, Firefox.  I've installed all the updates and rebooted, the desktop doesn't seemed to be affected but Flash in Firefox is very laggy.  As a test In have installed Chromium, It runs fast even under flash.  Any ideas what could be the cause or has Firefox put a but of weight on recently?

---

### Post by ajgreeny on 2017-07-03
I have never used an nvidia graphic card but as you have one, and it is currently using the nouveau driver, it may be that you can get better performance by installing the recommended nvidia driver from **Additional Drivers** if you are still using Ubuntu 16.04; I am a bit confused about which OS you're actually using at present.

---

### Post by amtrakuk on 2017-07-03
Hi there.   Yeah tried the NVIDIA propiertry drivers but it made no difference.   I've tried downloading and installing flash from the adobe website incase that was the issues.   I've worked it down to Firefox.   Chromium works fine.  Question is what has happened to Firefox this build and why is it slow

---

### Post by vasa1 on 2017-07-03
> **amtrakuk said:**
> ... or has Firefox put a but of weight on recently?
Multiprocess is being rolled out. It may or may not be available to you depending on your extensions. And that may or may not be relevant to your issue.

You can check in *about:support*. Look for multiprocess windows. And look at [http://www.omgubuntu.co.uk/2017/05/ubuntu-firefox-multiprocess-enable](http://www.omgubuntu.co.uk/2017/05/ubuntu-firefox-multiprocess-enable) as well.

---

### Post by amtrakuk on 2017-07-04
Mine are set to

```
 Multiprocess Windows     0/1 (Disabled by add-ons)
```

I have tried disabling hardware acceleration but that hasn't made any difference.

The symptom is the flash stops for about half a second then catches up with itself every few seconds,  Thinking on it I have had the banner come across the top of the web page saying it has stopped responding.  I thought it was lag on the game but the problem doesn't happen pre-update.

---

