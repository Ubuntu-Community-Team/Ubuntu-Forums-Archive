---
title: "AMD gpu with Xenial ?"
date: 2016-03-06
forum: Ubuntu Development Version
---

### Post by fthx on 2016-03-06
Hi,

I look after a new laptop with W5130 Firepro from AMD.
I owned, a long time ado, an AMD gpu laptop and I remember the wonderful experience it was with Ubuntu (...).

At the moment, where are the proprietary packages ? I did not find any fglrx or catalyst or ... in Xenial repositories. But maybe I'm missing something.
Is the power saving mode efficient with nowadays Ubuntu ? Is it easy to switch to Intel's integrated gpu ?
Does new ampgpu support this gpu ?

Thanks

---

### Post by grahammechanical on 2016-03-06
From posts elsewhere on this forum I get the impression that AMD drivers have not been behaving nice of late. I do not use an AMD video adapter myself. But here are 2 commands that have their uses.

```
ubuntu-drivers list
ubuntu-drivers devices
```

They should show what is availbale in the repositories of a release for the device in the machine.

Regards.

---

### Post by dino99 on 2016-03-06
amdgpu has replaced the old fglrx & catalyst:

 'amdgpu' driver for the AMD Radeon cards. The
following chip families should be supported: Bonaire, Hawaii, Kaveri, Kabini
Mullins, Iceland, Tonga, Carrizo, Fiji, Stoney.



[http://support.amd.com/en-us/kb-articles/Pages/737-28041SupportforATIMobility.aspx](http://support.amd.com/en-us/kb-articles/Pages/737-28041SupportforATIMobility.aspx)

---

### Post by P-I H on 2016-03-06
I have a radeon R9 380 with tonga pro in my desktop. The amdgpu driver works in 16.04, but to get the full performance you have to use linux kernel 4.5 with the powerplay switch set to y. There is more information on this site [https://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PP-4.5-Steps](https://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PP-4.5-Steps).
In 15.10 I havet to use the proprietary driver.

---

### Post by grahammechanical on 2016-03-12
Some further information in this blog post

[https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/)

Regards

---

### Post by P-I H on 2016-03-12
Not ready yet. My system will not boot with the 4.4.0-12 (4.4.0-12.28) kernel. However I am also using the padoka PPA, that include some changes. There are a lot of discussions about performance, and the open driver isn't as good fglrx, but quite close.
This comparison is a little bit old, but there is not much change with the 4.5 release I am using now.

```
Unigine Heaven Benchmark 4.0

FPS:    48.3
Score:    1215
Min FPS:12.3
Max FPS:129.1

System
Platform:Linux 4.2.0-16-generic x86_64
CPU model:AMD FX(tm)-8120 Eight-Core Processor (4026MHz) x8
GPU model:AMD Radeon (TM) R9 380 Series (4096MB) x1

Settings
Render:    OpenGL
Mode:    1920x1200 fullscreen
Preset    Custom
Quality    High
Tessellation:    Disabled

Powered by UNIGINE Engine
Unigine Corp. © 2005-2013


Unigine Heaven Benchmark 4.0

FPS:    46.3
Score:    1167
Min FPS:8.1
Max FPS:97.1

System
Platform:Linux 4.4.0-rc3-4.5-next-phx-xmas x86_64
CPU model:AMD FX(tm)-8120 Eight-Core Processor (4026MHz) x8
GPU model:Unknown GPU (256MB) x1

Settings
Render:    OpenGL
Mode:    1920x1200 fullscreen
Preset    Custom
Quality    High
Tessellation:    Disabled

Powered by UNIGINE Engine
Unigine Corp. © 2005-2013

```

---

### Post by Bashing-om on 2016-03-12
P-I H; Hello;

Take a look at the release notes for 16.04 :
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

There will be no proprietary drivers offered ( or needed ) in 16.04 .
Looks as if ATI is going the way of Intel in support of ubuntu . They will provide !

[INDENT][INDENT]maybe a great thing
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-03-12
Expect upgraders to wonder why this has happened

> When upgrading to Ubuntu 16.04 from a previous release, _both the fglrx  driver and the xorg.conf will be removed_, so that the system is set to  use either the amdgpu driver or the radeon driver (depending on the  available hardware).

Regards

---

### Post by v3.xx on 2016-03-12
An interesting reply

> Dave_Barnes

The last release AMD did can not be used because it is incompatible with the newer x.org version...

[https://ubuntu-mate.community/t/amd-ati-owners-read-this-before-upgrading-to-16-04/4286/7](https://ubuntu-mate.community/t/amd-ati-owners-read-this-before-upgrading-to-16-04/4286/7)

---

### Post by P-I H on 2016-03-15
Today I managed to crash my ssd with the Xenial system. I don't know how. I had to install the Ubuntu 16.04 (Xenial Xerus) Daily Build. The first thing I did was to check if I could use the backport by Alberto Milone of basically every amdgpu kernel driver commit from 4.5 to the xenial kernel. It worked OK.
I made one change in /etc/default/grub
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="amdgpu.powerplay=1"
```
This is the result of the Unigen Valley benchmark
```
Unigine Valley Benchmark 1.0

FPS:    42.9
Score:    1795
Min FPS:15.4
Max FPS:67.6

System
Platform:Linux 4.4.0-13-generic x86_64
CPU model:AMD FX(tm)-8120 Eight-Core Processor (4026MHz) x8
GPU model:Unknown GPU (256MB) x1

SettingsRender:    OpenGL
Mode:    1920x1200 fullscreen
Preset    Custom
Quality    High

Powered by UNIGINE Engine
Unigine Corp. © 2005-2013

```

---

### Post by grahammechanical on 2016-03-15
Not being a gamer, is that score good or bad or in different? I guess that for gamers it is the result that matters most.

Regards.

---

### Post by ventrical on 2016-03-15
I did an ssd swap to my AMD box and ... surprise... llvmpipe .. but I will try from Install.

---

### Post by P-I H on 2016-03-16
I am quite sure the ADM Cedar based card isn't supported by AMDGPU.
From Phoronix site:
There is also the uncertainty over what hardware the AMDGPU driver will end up supporting with by default just handling the few select GCN 1.2+ GPUs while there is experimental but disabled-by-default GCN 1.1 support and we haven't seen any GCN 1.0 support in this driver.

Some data from 
[http://xorg.freedesktop.org/wiki/RadeonFeature/](http://xorg.freedesktop.org/wiki/RadeonFeature/)
```
GCN 1.0    CAPE VERDE, PITCAIRN, TAHITI, OLAND, HAINAN
GCN 1.1    BONAIRE, KABINI, MULLINS, KAVERI, HAWAII
GCN 1.2    TONGA, ICELAND/TOPAZ, CARRIZO, FIJI, STONEY
```

---

### Post by ventrical on 2016-03-16
Yes .. it is a complete fail .. and that AMD video card is only 3 years old. I think I wrote elsewhere in the forums that I am about done with AMD/ATi radeon graphics. It is just useless down time trying to get an install going on the older metal. 

 Intel graphics are ruling the day with the Ubuntus.  Fast , sleek, smooth and 'sexy' as Mark puts it :)

Regards..

---

