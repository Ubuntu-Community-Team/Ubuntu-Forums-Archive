---
title: "Dell Latitude D620 Script"
date: 2007-03-05
forum: The Cafe
---

### Post by CrypticBlade on 2007-03-05
**[SIZE="5"][COLOR="Red"]*** Update ***[/COLOR][/SIZE]**
[COLOR="Red"][SIZE="3"]I have moved my script into the public domain by publishing it to SourceForge.net under the project name Laptop Configuration for Ubuntu Linux.

Please send me any modifications or improvements you make to this program so I can consider them for merge into my version.

[http://sourceforge.net/projects/lc4ul/](http://sourceforge.net/projects/lc4ul/)

 I am looking for testers, Perl developers, or anyone interested in participating in this great project. Contact me through my SourceForge email.[/SIZE][/COLOR]

I am in the process of writing a script (currently in Perl) to fully automate the configuration and installation of my new Dell Latitude D620 laptop. I intend for my script to automate hardware configuration in the same manner that Automatix and Easy Ubuntu automate package configuration.

The goal is that after a clean install a user simply runs this script and reboots. When the user boots back into Ubuntu everything &#8220;just works&#8221;. The unsupported wireless card, WPA for wireless, 3D video driver; EVERYTHING.

Currently the script is very focused on the hardware that I have on my Latitude D620, but fortunately the hardware on most modern Dell laptops is not that varied. For example you either have an Intel integrated, NVidia, or ATI graphics card.

Currently my script is non-interactive, you simply run it and it prints status messages as it goes. I imaging that enabling more robust support for more laptops would require an interactive experience requiring the script to ask the user what hardware they have. Another alternative might be to &#8220;grep&#8221; the result of &#8220;lspci&#8221; to determine certain hardware?

At any rate I hope to expand this script to service all those Ubuntu users who want to configure their hardware with one click after a clean install of Ubuntu.

I am entertaining the idea of starting a SourceForge project for this script and enlisting the help of one or two dedicated Perl gurus. Let it be known that I am a Java programmer and learned just enough Perl to create the script that I currently have.

The script I have now is fully functional and completely configures my hardware perfectly. I would have killed for something like this if it had already existed and I hope that some other Dell laptop owners out there get excited by this.

Maybe there is something out there that already does this, please let me know if there is, but I have never heard of this existing before, therefore I wrote my own.

I am looking for some feedback and volunteers for this idea and possible project.

Currently my Perl script does the following:

Resolve High Pitch CPU Noise:
Sets CPU ACPI state &#8211; by default Ubuntu&#8217;s ACPI implementation sets the &#8220;max_cstate&#8221; to C3 for processors. While this setting may save slightly more power when running on batteries, it cause an annoying subtle high-pitch noise to eminate from the processor every 5 to 15 seconds. Setting the &#8220;max_cstate&#8221; to C2 resolves this issue.

Resolve Internal Speaker Beeps at Max Volume on Shutdown:
Blacklists kernel module &#8220;pcspkr&#8221; &#8211; this modules causes annoying loud beeps during shutdown and other operations.

Resolve Default Wireless Driver Breaks ndiswrapper:
Blacklists kernel module &#8220;bcm43xx&#8221; &#8211; this driver does not support my Dell 1390 wireless adapter and conflicts with ndiswrapper.

Resolve Synaptic Touchpad Lags and Not Very Sensitive:
Tweaks Synaptic Touchpad sensitivity &#8211; makes the touchpad more sensitive to mimic behavior experienced when running other operating systems.

Resolve Synaptic Touchpad Lacks Vertical and Horizontal Scroll:
Adds vertical and horizontal scrolling to Synaptic Touchpad &#8211; vertical and horizontal scrolling don&#8217;t work by default.

Resolve Dell 1390 Wireless Not Natively Supported:
Downloads, compiles, installs, and configures wireless network support &#8211; my Dell 1390 wireless card is not natively supported so downloading, compiling, and installing ndiswrapper and the proper drivers is always something I have had to do manually. This portion of the script also downloads and configured NetworkManager. When it is finished and I reboot, my wireless &#8220;just works&#8221; WITH WPA SUPPORT!

Resolve Beryl Window Manager Not Installed By Default:
Downloads, installs, and configures Beryl window manager &#8211; Beryl takes several steps to be enabled; these steps were easily automated.


Regards,
CB

---

### Post by H.E. Pennypacker on 2007-03-05
This is the kind of thing I am talking about!  What if there was a script for all the troubled computers out there?  It is a great idea, and completes what Ubuntu has not already completed, because many of us need extra tweaking.

I own a Dell Inspiron 2200, and while its great, there are a few kinks that need to be worked out, and I may very well have to use parts of your script if I ever create a script.

---

### Post by hibernatus on 2007-03-06
Hi CrypticBlade,

I think this is a good solution, i'would switch my laptop from win to lnx, but i can't spent to many times to configure it (this is my work tools => i need it every day).

If you have a script who help me to install on my laptop i will be verry happy.

At this time i'm stuck a the boot from the cd it can't lauch the xserveur.


Regard

---

### Post by hibernatus on 2007-03-06
The informations about my laptop :

MODEL  	Dell D620

INTEL PROCESSOR 	Intel Pentium T2400 Core duo (1.83GHz)
CHIPSET / BUS SPEED 	Intel 945GM / 667MHz FSB, 2MB L2
HARD DRIVE / SPEED 	100GB SATA 7200RPM
MEMORY 	 2Gb Options 
GRAPHICS 	Intel Integrated Graphics Media Accelerator 950 (up to 128MB shared)
DISPLAY 	14.1" TFT WXGA+
SCREEN RESOLUTION: INTERNAL / EXTERNAL 	1440x900 / 1920x1200
CD / DVD DRIVE 	8X DVD+/-RW
MODEM / ETHERNET 	Integrated 56K (V.92) modem / 10/100/1000 Ethernet
WIRELESS 	Intel 3945AG WLAN (802.11 a/g)
BLUETOOTH 	YES
WIRELESS BROADBAND ANTENNA 	YES
EVDO mini card (Verizon) 	YES
UMTS/HSDPA mini card (Cingular) 	YES

Is that compatible with your script?

Regard

---

### Post by CrypticBlade on 2007-03-06
hibernatus,

I found this post concerning an XServer crash on a Latitude D620:

[http://www.ubuntuforums.org/showpost.php?p=933059&postcount=4](http://www.ubuntuforums.org/showpost.php?p=933059&postcount=4)


I have WXGA on my Latitude D620, not WGA+, so I can't test the fix.

My script deals with hardware configuration AFTER installing Ubuntu. If you are having problems installing you will need to search the forums for a solution so you can get Ubuntu installed.

If you do manage to get Ubuntu loaded can you send me the output from the following commands:

```
lspci
```

```
cat /proc/acpi/processor/CPU0/power
```

This would allow me to possibly incorporate your hardware into my script.

Regards,
CB

---

### Post by hibernatus on 2007-03-06
Thanks 
I will try like that tonight, but i'm still ok to test the most part of your script after that (will have to check for the WXGA+

---

### Post by CrypticBlade on 2007-03-06
hibernatus,

This site is also a great resource for anyone having issues installing Ubuntu on their D620:

[http://seclab.cs.sunysb.edu/sekar/d620/ubuntu-d620.html](http://seclab.cs.sunysb.edu/sekar/d620/ubuntu-d620.html)

- CB

---

### Post by hibernatus on 2007-03-07
Thanks a lot,

know the ubuntu is installed on my laptop, i'm now in front of the same issues as every body for the screen resolution :-(

I will try to find in the forum, i'm still oki to test your script 

Hibern.

---

### Post by CrypticBlade on 2007-03-07
hibernatus,

My script currently only supports this graphics card:
**NVIDIA Quadro Graphics Card**

And this wireless card:
**Dell Wireless 1390 (802.11g) Mini Card**

I will need to modify my script to support your hardware.

I also need answers to the following questions:
[LIST]
[*]Does your internal PC speaker beep at full volume when you shutdown Ubuntu?
[*]Does your CPU make a high pitch noise that can be heard when placing your ear close to the upper-left section of the keyboard?
[/LIST]
Can you also post the results for the following commands?

```
lspci
```

```
cat /proc/acpi/processor/CPU0/power
```

Thanks,
CB

---

### Post by hibernatus on 2007-03-07
Hi ,

To made the more shorter answer possible :

Does your internal PC speaker beep at full volume when you shutdown Ubuntu?
=> No

Does your CPU make a high pitch noise that can be heard when placing your ear close to the upper-left section of the keyboard?
=> I can hear something, but i'm not sure that's corresponding


the command lspci give :

> jdechamp@jdechamp-lnx:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
jdechamp@jdechamp-lnx:~$ 


and the command cat /proc/acpi/processor/CPU0/power

> jdechamp@jdechamp-lnx:~$ cat /proc/acpi/processor/CPU0/power
active state:            C3
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010] duration[00000000000000000000]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00031124] duration[00000000000126443775]
   *C3:                  type[C3] promotion[--] demotion[C2] latency[057] usage[00230081] duration[00000000001255775116]
jdechamp@jdechamp-lnx:~$ 

Thanks

Hibern

---

### Post by CrypticBlade on 2007-03-08
hibernatus,

Thanks for the info. I'm working on adding support for your computer hardware to my script, but I have a few more questions.

- Was your wireless card properly detected and setup by Ubuntu?

- Was your video card properly detected and configured by Ubuntu?

- Was 3D support enabled on your video card, or did you have to install a 3D enabled driver after installing Ubuntu?


Thanks,
CB

---

### Post by hibernatus on 2007-03-08
Hi,

Actually to install on my laptop, i have :

1 : boot from the CD, have to restart the XServeur 

2 : My video card wasn't supported, i have to install 915resolution_0.5-2_i386.deb

like it's describe in this thread 

[http://www.ubuntuforums.org/showthread.php?t=326864&highlight=945GM](http://www.ubuntuforums.org/showthread.php?t=326864&highlight=945GM)

3 : The 3D Wasn't activated immediately, and the screen resolution wasn't correct.

I had to edit the config file from 915resolution to have the correct screen resolution

4 : I haven't try yet the wireless

For the rest i think this is ok, but i still have to test

Regard 

Hibernatus

---

### Post by CrypticBlade on 2007-03-10
hibernatus,

Thanks for the update. Please let me know how you get your wireless card working or if it is natively supported so I can update my script appropriately.

Thanks,
CB

---

### Post by malixor on 2007-03-10
CrypticBlade,

Could you post your perl script please? I just got a Latitude D620 with a different configuration and would like to run parts of the script I haven't configured already. I could also add my configuration to the script or just give you the information to add to it.

Thanks

---

### Post by CrypticBlade on 2007-03-10
malixor,

I have moved my script into the public domain by publishing it to SourceForge.net under the project name Laptop Configuration for Ubuntu Linux.

Please send me any modifications or improvements you make to this program so I can consider them for merge into my version.

[http://sourceforge.net/projects/lc4ul/](http://sourceforge.net/projects/lc4ul/)

I am looking for testers, Perl developers, or anyone interested in participating in this great project. Contact me through my SourceForge email.

Thanks,
CB

---

