---
title: "Network manager keeps asking for wireless password after suspend"
date: 2013-03-10
forum: Ubuntu Development Version
---

### Post by ahleron on 2013-03-10
[COLOR=#333333][FONT=Ubuntu Beta]When I first boot up my laptop computer, my computer logs in to my wireless network without any problem and it does so automatically.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]If I close the lid on my my laptop/suspend/hibernate computer, and then wake it and unlock it, I keep getting prompted for my wireless network password, even though the prompt for my network actually shows that it has my password saved. My network connection properties also have the network settings and password saved for all users.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]It doesn't matter what desktop environment I use. Both Gnome 3.6 and Unity have the same problem. I'm using Ubuntu 13.04.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I've looked at some of the previous posts on this topic and they seem to refer to earlier versions of Ubuntu (a lot of 10.x and 11.x). None of those answers seem to help. Any ideas on how to fix this?[/FONT][/COLOR]

---

### Post by Bucky Ball on 2013-03-11
Welcome to the forums. 

You are aware that 13.04 is still testing and not released until end of April? Unless you are already familiar with Ubuntu/Linux it is not a good place to start. If you are just getting into it I would suggest starting with a stable, known beast, 12.04 LTS, which is supported until April 2017 (13.04 will be supported for 18 months from release date). 

Cheers.

---

### Post by serdotlinecho on 2013-03-11
@[**[COLOR=#000000]ahleron[/COLOR]**]("http://ubuntuforums.org/member.php?u=1796316") 	 , could you please share your network wireless card?

```
lspci | grep Network
```

---

### Post by ahleron on 2013-03-11
I didn't even want to upgrade to 13.04. I was installing gnome and blamo...along the way I ended up with 13.04. Not sure what I did. Obviously I must have typed a bad command into terminal during apt-get. On the upside, everything else about 13.04 seems to work pretty well, but I thought it was a good idea to post this since 13.04 is still under development. I figured the developers would see it.

---

### Post by ahleron on 2013-03-11
It is a: 

0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

Thanks

---

### Post by ahleron on 2013-03-11
> **Bucky Ball said:**
> Welcome to the forums. 

You are aware that 13.04 is still testing and not released until end of April? Unless you are already familiar with Ubuntu/Linux it is not a good place to start. If you are just getting into it I would suggest starting with a stable, known beast, 12.04 LTS, which is supported until April 2017 (13.04 will be supported for 18 months from release date). 

Cheers.
 Well aware of that. In fact, I had not intended to run 13.04 at all. I had downloaded and installed Ubuntu 12.10, but then decided that I wanted to run Gnome Shell so I updated everything and then followed the instructions listed here:
[http://www.webupd8.org/2012/10/how-to-get-complete-gnome-3-desktop-in.html](http://www.webupd8.org/2012/10/how-to-get-complete-gnome-3-desktop-in.html)

The next thing I knew, I had 13.04. I'm not exactly sure what step along the way did it, but that's what happened to lead me to 13.04. I figured meh...it gets released next month anyway...no big deal, I'll just keep it.

While I certainly would like to resolve the problem, I also wanted to post it here since I figured the developers would see it and be made aware of the problem so it might be fixed prior to release.

---

### Post by serdotlinecho on 2013-03-12
> Well aware of that. In fact, I had not intended to run 13.04 at all. I  had downloaded and installed Ubuntu 12.10, but then decided that I  wanted to run Gnome Shell so I updated everything and then followed the  instructions listed here:
[http://www.webupd8.org/2012/10/how-t...esktop-in.html]("http://www.webupd8.org/2012/10/how-to-get-complete-gnome-3-desktop-in.html")

Really? By just installing ubuntu-gnome-desktop packages will upgrade 12.10 to 13.04?

Could you please share the output of the following commands:

```
cat /etc/issue && echo -n && lsb_release -a && echo -n && uname -a
```

---

### Post by ahleron on 2013-03-12
> **serdotlinecho said:**
> Really? By just installing ubuntu-gnome-desktop packages will upgrade 12.10 to 13.04?

Could you please share the output of the following commands:

```
cat /etc/issue && echo -n && lsb_release -a && echo -n && uname -a
```

Huh...interesting. Wasn't familiar with that...but it says 12.1 though system details (what I used to check version) reports that I have 13.04 (see screenshot).

Ubuntu 12.10 \n \l


LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
Linux Laptop 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 19:02:34 UTC 2013 i686 i686 i686 GNU/Linux


[ATTACH=CONFIG]240078[/ATTACH]

---

### Post by dino99 on 2013-03-12
Google around "ubuntu wireless password", and you'll get an Askubuntu answer (sorry here the copy/paste is broken right now)

---

### Post by Bucky Ball on 2013-03-12
> **ahleron said:**
> ... it says 12.1 though system details (what I used to check version) reports that I have 13.04 (see screenshot).



Hmmm. I vaguely remember this being reported as a 12.10 bug. The output from the command shows that you are using 12.10 and I think the appropriate kernel so not sure you have upgraded to 13.04. 

@ dino99: Not sure what you mean about the copy/paste not working. On the forums or on your machine? Please clarify. ;)

---

### Post by dino99 on 2013-03-12
you miss the most important "here", meaning on my system i actually cant select an url, copy it then paste (FF different tabs). Its an issue with the kernel: only 3.8.0.10/11 have worked with that asus usb mouse (before 3.8 that was ok too). Grabbing a line is not possible , or resizing a windows: click/double-click act as random russian roulette.

---

### Post by serdotlinecho on 2013-03-12
> **ahleron said:**
> Huh...interesting. Wasn't familiar with that...but it says 12.1 though system details (what I used to check version) reports that I have 13.04 (see screenshot).

Ubuntu 12.10 \n \l


LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal
Linux Laptop 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 19:02:34 UTC 2013 i686 i686 i686 GNU/Linux


[ATTACH=CONFIG]240078[/ATTACH]

This thread already talking about the details bug: [http://ubuntuforums.org/showthread.php?t=2121795](http://ubuntuforums.org/showthread.php?t=2121795)
And here's from [askubuntu]("http://askubuntu.com/questions/263506/why-does-ubuntu-12-10-update-to-13-04-on-its-own") and [google plus communities]("https://plus.google.com/104488658054788253034/posts/62cDJXDaETU").

---

### Post by cariboo on 2013-03-12
> **dino99 said:**
> you miss the most important "here", meaning on my system i actually cant select an url, copy it then paste (FF different tabs). Its an issue with the kernel: only 3.8.0.10/11 have worked with that asus usb mouse (before 3.8 that was ok too). Grabbing a line is not possible , or resizing a windows: click/double-click act as random russian roulette.

It must be something in your setup, as copy/paste works well here, mind you I'm using chromium, kernel version is:

```
Linux alexis 3.8.0-12-generic #21-Ubuntu SMP Thu Mar 7 19:08:49 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by grahammechanical on 2013-03-12
So, mystery solved (may be) but original issue not resolved. I do not have a laptop but I would guess that to save battery power the wireless adapter has to be switched off when the lid is closed. This would naturally break the connection between Network Manager and the wireless adapter. Do, you select "suspend" before closing the lid? If you disabled networking before closing lid, would that make a difference? And before you say, "I do not have to do this with Windows," remember the OEM has done all kinds of tweaks with the hardware to stop you getting this experience with Windows but the OEM cares nothing for your Ubuntu experience.

Regards.

---

### Post by ahleron on 2013-03-12
> **dino99 said:**
> Google around "ubuntu wireless password", and you'll get an Askubuntu answer (sorry here the copy/paste is broken right now)

I did that already.

---

### Post by ahleron on 2013-03-12
> **grahammechanical said:**
> So, mystery solved (may be) but original issue not resolved. I do not have a laptop but I would guess that to save battery power the wireless adapter has to be switched off when the lid is closed. This would naturally break the connection between Network Manager and the wireless adapter. Do, you select "suspend" before closing the lid? If you disabled networking before closing lid, would that make a difference? And before you say, "I do not have to do this with Windows," remember the OEM has done all kinds of tweaks with the hardware to stop you getting this experience with Windows but the OEM cares nothing for your Ubuntu experience.

Regards.

Turning off wireless before closing the lid results in the same exact behavior. There is something in the OS that can't get the wireless password to the wireless connection even though the information is saved, once the computer has been put into a suspend/sleep/hibernate state regardless of whether or not you switch the wireless off beforehand.

---

### Post by ahleron on 2013-03-13
Some additional info:

lspci -vv -s 0d:00.0
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 54
    Region 0: Memory at c4500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi


```
Laptop:~$ modinfo iwlwifi
filename:       /lib/modules/3.5.0-25-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
alias:          iwlagn
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
srcversion:     3620EFC6E68BB62239F0B14
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.5.0-25-generic SMP mod_unload modversions 686 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           5ghz_disable:disable 5GHz band (default: 0 [enabled]) (bool)
```

---

### Post by ahleron on 2013-03-18
Found how to fix it. You add the following to /etc/rc.local

modprobe -r iwlagn
modprobe iwlagn bt_coex_active=0

---

### Post by zika on 2013-03-19
Or, to skip unloading and loading module at every boot,  create file /etc/modprobe.d/iwlagn.conf with line```
options [COLOR=#000000]iwlagn bt_coex_active=0[/COLOR]
```[COLOR=#000000]and perform update-initramfs for either all kernels or (for test) just for the one that is currently active...[/COLOR]

---

### Post by dino99 on 2013-03-19
its also a regression bug that should be reported (if not yet done)

---

