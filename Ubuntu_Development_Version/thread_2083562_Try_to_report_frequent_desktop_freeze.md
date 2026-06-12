---
title: "Try to report frequent desktop freeze"
date: 2012-11-12
forum: Ubuntu Development Version
---

### Post by BertN45 on 2012-11-12
I have a frequent desktop freeze on my intel graphics. The corresponding wiki says I have to ssh in from another computer, but I do not have another computer available. I use CTRL+ALT+F2 to enter in CLI mode and I start ubuntu-bug. It nicely comes with the standard questions. At the end of that sequence it asks to start the browser, but that does not work. It also says you can report the problem using another computer, but the bug-identification to be used for launchpad is at least 50 characters long and it is easy to make a mistake if you write it down.

I also tries the option to keep the crashdump and to report it later, but the crashdump is not in the /tmp directory as promised.

So how to report that desktop freeze?

---

### Post by cariboo on 2012-11-13
Have you looked in /var/crash?

---

### Post by BertN45 on 2012-11-13
Yes I looked there too, but nothing with the promised name and/or crash date and time.

---

### Post by ventrical on 2012-11-13
I'm just curious as to which type of graphical hardware you are using.

Oh yes .. Intel graphics but..

lspci


thanks..

---

### Post by BertN45 on 2012-11-14
My complaint is not so much that a freeze occurs in the development version, but that there is no way to report it, if you have only one system with Ubuntu. 
OK the hardware:

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
[COLOR="Blue"][COLOR="Navy"]00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)[/COLOR][/COLOR]
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
05:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
40:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

I tried the third method to report the freeze using CTRL+ALT+F2, by writing down the complete URL, that they promised I needed to complete the bug-report and I typed that URL in the browser. That URL is not known by launchpad. That failed too, so I give up. Hopefully someone else with two computers will file that freeze. It is an old problem, since it also occurs say once a week in 12.04, but in 13.04 it seems to happen a couple of times per day.

---

### Post by ventrical on 2012-11-16
Here is what I was able to do. So it appears that apport is now working here from the GUI/terminal.



[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1079758](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1079758)

---

### Post by BertN45 on 2012-11-16
Yes, but that does not help me. Because in case of a desktop freeze, everything related to the desktop is frozen, I cannot start the terminal anymore. The only thing left is a forced power-off or CTRL+ALT+F2 and there [COLOR="Blue"]ubuntu-bug[/COLOR] does not work.
Partly because it assumes it can start the browser also from this text mode.
Today the updates included a new kernel version, so I will try it again and if it does not work, I will file a bug report on ubuntu bug.

---

### Post by cariboo on 2012-11-16
You can file a bug without using apport:

[http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect](http://bugs.launchpad.net/ubuntu/+source/PACKAGENAME/+filebug?no-redirect)

I'd suggest you have a look at this [page]("https://help.ubuntu.com/community/ReportingBugs"), as there are a lot of links on how to gather information to create a good bug report.

---

### Post by ventrical on 2012-11-16
> **BertN45 said:**
> Yes, but that does not help me. Because in case of a desktop freeze, everything related to the desktop is frozen, I cannot start the terminal anymore. The only thing left is a forced power-off or CTRL+ALT+F2 and there [COLOR=Blue]ubuntu-bug[/COLOR] does not work.
Partly because it assumes it can start the browser also from this text mode.
Today the updates included a new kernel version, so I will try it again and if it does not work, I will file a bug report on ubuntu bug.


 I would wonder if you could use recovery mode from GRUB and choose fail-safe graphics mode and see where that would go. It is very strange because all my Intel set  units are working exceptionally well. I am wondering if there is a power drop in your power supply. Should have at least 400watts. 250 will work.. but if it is refurbrished then that could present a hardware problem.

---

### Post by erkiha on 2012-11-16
> **ventrical said:**
> I would wonder if you could use recovery mode from GRUB and choose fail-safe graphics mode and see where that would go. It is very strange because all my Intel set  units are working exceptionally well. I am wondering if there is a power drop in your power supply. Should have at least 400watts. 250 will work.. but if it is refurbrished then that could present a hardware problem.

I experience exactly the same thing, intel i5 laptop with integrated graphics. It has happened to me when some large data reading is done i.e. copy 10G of files from usb disk and when starting a virtualbox.

---

### Post by ventrical on 2012-11-16
I tired to emulate that bug on:

```

ventrical@ventrical-PY028AA-ABA-A1106N:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

```but no luck.

Linux ventrical-PY028AA-ABA-A1106N 3.7.0-030700rc2-generic #201210220428 SMP Mon Oct 22 08:37:05 UTC 2012 i686 i686 i686 GNU/Linux
ventrical@ventrical-PY028AA-ABA-A1106N:~$

```

VinDSL Unity Debug Script 12.9.30 (vindsl.com) ~
Current Date/Time: Fri Nov 16 18:12:40 EST 2012
Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.7.0-030700rc2-generic
Unity Release: unity 6.10.0

OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) 915G x86/MMX/SSE2
OpenGL version string:  1.4 Mesa 9.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

dpkg-query: package 'mesa-utils' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

Xserver Xorg Core Branch:
  Installed: 2:1.13.0-0ubuntu6

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
           +-02.0  Intel Corporation 82915G/GV/910GL Integrated Graphics Controller
           +-1b.0  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
           +-1c.0-[01]--
           +-1d.0  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
           +-1d.1  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
           +-1d.2  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
           +-1d.3  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
           +-1d.7  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
           +-1e.0-[02]--+-01.0  VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
           |            +-02.0  Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
           |            \-05.0  LSI Corporation V.92 56K WinModem
           +-1f.0  Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
           +-1f.1  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
           +-1f.2  Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller
           \-1f.3  Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1440x900 pixels (380x238 millimeters)
  resolution:    96x96 dots per inch

ventrical@ventrical-PY028AA-ABA-A1106N:~$ 

```

---

### Post by BertN45 on 2012-11-16
> **ventrical said:**
> I am wondering if there is a power drop in your power supply. Should have at least 400watts. 250 will work.. but if it is refurbrished then that could present a hardware problem.
The power is very shaky here, a number of power breaks each day, but I have a surge protector that also switches off, if the power gets too low. It is an old refurbished system. But anyhow that does not explain, why: 
[LIST]
[*]- It happens much more frequently in 13.04. 
[*]- It only happens, if I open the Dash while other windows are open under the dash.
[/LIST]
It also happens under low cpu loads and less then 600MB used. So for me it looks like a software problem, parallel processing locking issue related to starting the dash? After the next freeze tomorrow, I could switch off multi threading in the BIOS and see what happens.

---

### Post by ventrical on 2012-11-17
> **BertN45 said:**
> The power is very shaky here, a number of power breaks each day, but I have a surge protector that also switches off, if the power gets too low. It is an old refurbished system. But anyhow that does not explain, why: 
[LIST]
[*]- It happens much more frequently in 13.04.
[*]- It only happens, if I open the Dash while other windows are open under the dash.
[/LIST]
It also happens under low cpu loads and less then 600MB used. So for me it looks like a software problem, parallel processing locking issue related to starting the dash? After the next freeze tomorrow, I could switch off multi threading in the BIOS and see what happens.

Actually my next followup was to be to check BIOS and see if multi-threading is *enabled*!.

 On this current unit I am using (Dell Opti GX27G) , has Intel chip-set but it stopped running properly after Natty Narwahl. I beta tested in Oneric and it started to do exactly what you have described - with the freezy screen when opneing dash and random freezes. (There is a post somewhere in the older forums that are closed now.)

 Of course this is a test machine and has been through the mill. The video graphics driver is just one step behind (obsoleted) and will not run Unity 3D but will run Unity 2D in Oneric. The problem with the Dell are the power supplies.  After a time of use they are intermittently 'slow to start' . However I can run 3D graphics games with no problem so it seems  like a software bug.

  I really do hope it is only software bug. If you can assign more memory to video in BIOS ? try that ?

Let us know..

Thanks.

---

### Post by BertN45 on 2012-11-17
> **ventrical said:**
> Actually my next followup was to be to check BIOS and see if multi-threading is *enabled*!.

The problem with the Dell are the power supplies.  After a time of use they are intermittently 'slow to start'. 

just a remark about power supplies I think all power supplies age especially the capacitors in it. My antique file server has a "external" 400 watt power supply now, because the old one could not handle the two disk anymore after 9 years of solid duty.

I am a little bit closer to writing a useful bug report. The error always occurs if I play music with Clementine taking a large part of the desktop. If I open the Dash the desktop freezes. I do not think it has anything to do with clementine, but everything with the dash software

If I switch off multi-threading everything works without any problem. So it is a parallel processing problem. An interesting problem I would call it in the past. I start with writing the bug for ubuntu-bug and open another one for Unity.

---

### Post by ventrical on 2012-11-17
> **BertN45 said:**
> just a remark about power supplies I think all power supplies age especially the capacitors in it. My antique file server has a "external" 400 watt power supply now, because the old one could not handle the two disk anymore after 9 years of solid duty.

I am a little bit closer to writing a useful bug report. The error always occurs if I play music with Clementine taking a large part of the desktop. If I open the Dash the desktop freezes. I do not think it has anything to do with clementine, but everything with the dash software

If I switch off multi-threading everything works without any problem. So it is a parallel processing problem. An interesting problem I would call it in the past. I start with writing the bug for ubuntu-bug and open another one for Unity.


Ahh.. it could be that the processor is not HT and not a Dual Core.  Some processors will emulate a Dual Core in System Monitor when HT is enabled but that is not to say it represents a true Dual Core processor. I have units that have HT option but no HT processor.

So my followup is : what type of processor do you have under the hood?

regards,

ventrical

---

### Post by BertN45 on 2012-11-17
No it is not dual core, it is an late model P-IV 3.2GHz and those models did support multi-threading with a single CPU. That multi-threading works, because I see the two CPU bars in conky move more or less independently. If a disable multi-threading, they move in sync as one would expect. So it is one CPU able to process two threads and changing threads, if the active thread has to wait for the cache to be reloaded. It is supposed to give a 10%-20% performance boost for the CPU, because the CPU does not have to wait for the cache to be reloaded. From a OS point of view, it is like having two processors.

I do not think the gods want me to report this bug, because a few minutes ago, while filing the bug, launchpad crashed on me. Time for me to buy a Presidente (local beer).

---

### Post by BertN45 on 2012-11-18
How to report a desktop freeze:

1. Press CTRL+ALT+F2
2. Log in and type
3. [COLOR="blue"]sudo -s[/COLOR]
4. [COLOR="blue"]ubuntu-bug[/COLOR]
5. Answer all the question and keep the crash information.
6. Copy the crash file to your home directory and add [COLOR="blue"].crash[/COLOR] to the name.
7. Reload the system
8. Start nautilus with [COLOR="Blue"]sudo nautilus[/COLOR] as root (permissions)
9. Double click the .crash file and report the bug.

This time I used the sudo -s and I copied and saved the dump-file to my home directory in the CTRL+ALT+F2 mode. I think the last one is essential because also now the crash report disappeared from /tmp after re-loading Ubuntu. Appending the name with .crash is just to be able to start the bug-report by double clicking.

---

### Post by ventrical on 2012-11-18
Bravo ! :)

Regards...

---

### Post by BertN45 on 2012-11-21
I filed the report, but it seems to be incomplete and again thet wanted me to ssh into the system using another linux system, I currently don't have. If I get these freezes again tomorrow, I will try to add the additional files to the bug-report. It should also be possible using CTRL+ALT+F2, using the same trick moving those to my home directory. It is about these files: the output of 'dmesg' and the /sys/kernel/debug/dri/0/i915_error_state

---

