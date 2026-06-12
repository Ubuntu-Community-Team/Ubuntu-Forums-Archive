---
title: "Multi user system...."
date: 2010-09-15
forum: Server Platforms
---

### Post by ubun2warrior on 2010-09-15
Hi

i have an intel dual core pc with 2gb ram. I am using ubuntu 10.04. I have one lcd monitor connected to the system. And i also have one spare lcd monitor. 

I have read that linux is a multi user system, and two people can log in to the same pc simultaneously with different user ids and do different work. So i wanted to know that is it possible for two people to use the same system at the same time and do different work by logging in with their own user logins.

If it is possible then, how do i go about it. How to setup such a system.. Please guide me. If this is possible then its going to be very cost effective for me as i won't have to buy a new system for another person using the computer.

Regards

ubun2warrior

---

### Post by dualbus on 2010-09-15
This guide provides all the answers: [http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

---

### Post by Fafler on 2010-09-15
It's called a multiseat system. It seems there are issues with the latest versions of GDM, you should look into that. Also, if possible, use two Nvidia cards for the project. It's possible to use a low end PCIe card like the 8400GS in a 1x slot by cutting out the back of the connector on the motherboard.

---

### Post by ubun2warrior on 2010-09-15
the guide was very nice.. It means that it is possible for me to setup a multiuser system, It would be more helpful if you could elaborate the guide for me.. I mean how should i start and what hardware do i require ?? do i need to do a fresh ubuntu install with all the hardware connected ?? also at the end of the guide there was something mentioned about the system being unstable... 

I need more help

Regards 
ubun2warrior

---

### Post by ubun2warrior on 2010-09-17
hi

please someone help.. i am not able to go about this multiuser system alone... i need help

the link given is very nice but i need more help a step by step solution like where to start. its very important for me to set up this multi user system..

regards

ubun2warrior

---

### Post by Fafler on 2010-09-17
You should start by supplying some info about your current setup. What mainboard and graphics you have. What version of Ubuntu you're running, how much you expect to spend on it and how much performance you expect from it.

---

### Post by ubun2warrior on 2010-09-17
Hi

I am using Intel Dual Core Processor E2220, 1 GB RAM, 320 GB Hard Disk, NVidia GMA 3100 in-built Graphics.
I am running Ubuntu 10.04 LTS. My only use of the system would be browsing the internet and may be viewing PDF fiels and nothing else. I don't know how much do i have to spend. In the above link given they displayed six systems running from a single cpu. i can manage with 2 to 3 system.  You can suggest how much RAM do i need ?? what graphic card do i require ?? etc..

thanks a lot for ur quick replies !!!
i am eagerly waiting for answers..
regards
ubun2warrior

---

### Post by Fafler on 2010-09-17
Theres no such thing as a "NVidia GMA 3100" You probably have a Intel GMA3100 and it is, to my knowledge, not suitable for a multiseat system. Take the top of your case and look into it. You need one PCIe slot pr seat you want to build.
[IMG]http://en.wikipedia.org/wiki/File:PCIExpress.jpg[/IMG][http://en.wikipedia.org/wiki/File:PCIExpress.jpg](http://en.wikipedia.org/wiki/File:PCIExpress.jpg)
From the top, its a 4x, 16x, 1x, 16x and a old fashion PCI slot. The best thing would be 2 16x slots, but you probably only have one. Now, get some graphics cards. I'm using two Nvidia Quadro NVS290 cards, they are pretty much identical to Geforce 8400GS cards. They don't provide much 3D performance, but it's not needed in this case anyway. If you're looking for brand new cards, i think the GT210 would be a good choice, but i haven't tried running them in a modified 1x slot. PCIe cards don't really care which slot they are running in, but the smaller slots can't supply power for larger, more power hungry, cards. You should also look for some more RAM, DDR2 is cheap these days.

I have, by the way, only done this with Debian. It has many similarities to Ubuntu, but there are some differences in the configuration. If you are in doubt whether your system will support two PCIe cards, take a good, high-res picture.

---

### Post by ubun2warrior on 2010-09-17
Hi

I think i have just one PCI slot 16x i suppose, in that case will i not be able to set up a multi seat system ??  Please suggest something by which i can make a multi seat system with the above mentioned config..  If its absolutely impossible then I have another system-  AMD Athlon 64x2 Dual core Processor 5000+, 2GB DDR2 RAM, 320 GB Hard Disk, NVIDIA GeForce 6150SE 3D. The video card is built in. Will this one work ??

Regards

---

### Post by Fafler on 2010-09-17
Well, it might still be possible if you mod a 1x slot to use a 16x card in it, as i tried to say before. The AMD system would also work, although the 6150 is quite slow and not supported with the latest driver, so you would need to find another older card to run along with it.

It /might/ also be possible to use the GMA3100 together with a PCIe card, but i know atleast the binary Nvidia driver install it's own GLX libraries instead of the Mesa ones the Intel drivers use. Maybe someone else can comment on howlikely it is to break things and if it&#347; even worth trying? Anyway, i've always used Nvidia cards for multiseat systems.

---

### Post by ubun2warrior on 2010-09-18
Hi

firstly thanks for ur quick responses... 

lets leave the above PC's.. suppose i want to build a multi seat system from scratch.. plz suggest what all hardware(please give a detailed description) would be suitable for me. 
Also i was going through a website "userful desktop" which says it can support up to 10 users from a single pc. is it possible.

Regards 
ubun2warrior

---

### Post by Fafler on 2010-09-18
You're welcome.

I think you should try playing around with the systems you have first, and when you're satisfied and everything works, upgrade. Yes, it should be possible to add as many systems as you want. But note that theres not a good way to handle sound yet. It's possible to make a alsa configuration file, not all programs respect it and some just use the first sound card, no matter what. It has not been a issue to me, as i only have one set of speakers anyway.

Try looking in the two machines and see if you can identify the boards. It should be printed somewhere, like Asus P5B-Q or similar.

---

### Post by ubun2warrior on 2010-09-19
Hi 

i am least bothered about sound. The most important thing for me is  internet.. the only thing that i will be doing is using a web browser  most of the time...
 
Now as u have said, i will play around with the system that i have.. 

here is a more detailed description of my system :-
  MODEL- Compaq Presario SG3745IL
    
2 GB RAM, 1 slot empty
6 usb ports
cooler master cpu fan
seagate 320Gb hard disk
BeasTec 200-240v power
AMD athlon 64x2 dual core processor 5000+
NVIDIA GeForce 6150SE 3D
PCIE_X1_1
PCIE_X1_2
PCIE X16

Ok now plz tell what video card should i purchase from the market  relevant to my configuration above.
i will be using LCD monitors
As i have already said my only use is web browsing and may be i would be  having 5 to 6 users on the PC, so plz guide me with the  configuration,etc.. 

I have to set this system up as early as possible.. I also  visited a  website: [http://www.userful.com/](http://www.userful.com/)
they say u can connect 10 users very easily .. so i think my 5 or may be  6 users on the PC plan is a humble one.. 

PS :- ) I think it would be nice if more people comment and give some  suggestions...

regards

ubun2warrior

---

### Post by LightningCrash on 2010-09-19
It may be easier to run something like a Sun Ray and Sun Ray Server
Sun Ray 1s are $20 on eBay.

[http://en.wikipedia.org/wiki/Sun_Ray](http://en.wikipedia.org/wiki/Sun_Ray)

---

### Post by Fafler on 2010-09-19
Are you up to modding your board to take more graphics cards? In that case, get 3 8400GS cards. Brand, memory etc. doesn't matter. Just get the cheapest you can find in your area. This will accommodate 3 users, as i don't think the build in 6150 is worth using for this bacuase of the issue with newer drivers. Now, you have to (carefully!) cut out the plastic in the back of the PCIe 1x connectors, so the rest of the 16x connector on the card hangs out. If you're unsure what i mean, i might be able to find a photo.

The 8400GS uses approx. 10 watts power, and the PCIe 1x connector is able to deliver that. Larger cards will probably not work.

Also, get 2 gb more memory. 800 mhz DDR2 memory, if i'm not mistaken. And a USB 2 hub for all the extra keyboards and mice.

Edit: Also, make sure no other components is in the way for the 16x card. I had to solder out the battery on the board where i did this.

---

### Post by ubun2warrior on 2010-09-19
ok so i have to cut out the plastic with some blade or something thats fine.. and will the video cards work like that, i understand what u mean.. the 1x is a very small slot so the 16x card won't fit and so i have to cut at one end.,, right and i can accommodate just 3 users because i have 3 slots ..
also i don't know about 8400 GS cards ... plz be more detailed on that..
After that, what do i have to do. i have ubuntu 10.04 lucid lynx desktop already installed on the PC. Do i have to reinstall it after the changes or will some commands do the trick.
 
Also how do i configure the system to run different sessions for different users so that they use the system separately?

one more question i have i have a laptop and it has a VGA output as all laptops do... so i connect the vga adapter of an LCD monitor that i have ... i also have a usb mouse and a keyboard. so can i try to set up a multi seat system with this? just for experiment purposes... 

if yes then what should i do?

ubun2warrior

---

### Post by Fafler on 2010-09-19
Cards like this: [http://cgi.ebay.com/Geforce-8400GS-256MB-Heatsink-/110580886878?pt=LH_DefaultDomain_0&hash=item19bf226d5e](http://cgi.ebay.com/Geforce-8400GS-256MB-Heatsink-/110580886878?pt=LH_DefaultDomain_0&hash=item19bf226d5e)

After the hardware is in place, we move on to the software. You're going to make quite a few changes to startup scripts etc. But we'll get to that soon enough. It  will also make sure every seat runs as a different user, with a different session and window manager.

Your laptop still only has one graphics chip, so it's not possible to do it the same way as we're going too here. It is, however, possible to do something similar with a nested X server, but it's a different process and i really don't know anything about it.

Edit: For the software, you will be following this howto: [https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

---

### Post by ubun2warrior on 2010-09-21
Hi i bought one  NVIDIA Ge Force 8400GS 512 Mb PCIE 64 bit graphic card (256Mb was not available and the one i purchased costs around $45 US) and i fixed it in the 16x slot.

 I have one question... Does the integrated graphics card stop working if the system detects another card in the PCIE slot like in my case,  I connected one  lcd panel in the integrated slot which was already there and one in the newly purchased 8400GS.

 But i found that the system is not detecting the older integrated card.. 

I also wanted to know that why do i need 256 Mb or 512 Mb graphics can't i manage with VGA cards which are extremely cheap, like the integrated graphics provide only 32 or 64 Mb graphics..

I want to know one more thing, suppose I buy a different graphics card which has less RAM or may be of a local brand, will i be facing a problem while setting up the multi seat system and get the things working...

I will be browsing the internet mostly and will be visiting sites like wikipedia or gmail only. No video sites, no games or anything.  Its just going to be simple text based sites most of the times... so will i be able to manage with 2 Gb RAM bcoz the price for 2 Gb DDR2 RAM was around $60 US. 

The system is not at all turning out to be cost effective... Plz suggest some cheaper options.. I will also search other places for the hardware.. 

Regards
ubun2warrior

---

### Post by the_original_billq on 2010-09-21
I just want to add that there are several ways to create a multi-user system.  The combination of a multi-user, multi-tasking operating system like Ubuntu with the X Window system provides many opportunities for supporting a large number of users with a relatively small amount of hardware.

At home I have one substantial headless server running the server version of Ubuntu.  I then have a variety of much less powerful client systems, ranging from old laptops, desktops, and Sun Ray ultathin clients.  Each client displays an X session running from the server.  The server is connected using switched gig networking throughout the house, so performance of my desktop session is phenomenal, even on an old PC with limited CPU and RAM.

Setting all of this up is also pretty easy, as 90% of the configuration work is done on one piece of gear - the server.  Maintenance and updating is similarly consolidated, so most of my time is spent just using the system instead of constantly maintaining.

I realize this may not work for you, but wanted to provide some options you might consider.

-Bill

---

### Post by Fafler on 2010-09-21
I want to add to the_original_billq that this is in fact what i'm doing now, instead of running a multiseater like before. It works quite well, even with older laptops. The maintenance is the same on a multiseatet  system.

Anyway, 256 mb cards are fine. The reason i'm recommending the 8400GS is that it's relatively cheap, offer some 3D acceleration, and HD video decoding in hardware, and it's supported with the latest Nvidia drivers. If you plan to do light 3D gaming on both cards (i installed Doom 3 on mine and we played deathmatch on the two heads) put the card with 512 mb in the 1x slot (you might as well experiment with it now) because the 1x slot has much less bandwidth, and more memory will compensate for some of it. It is, by the way, still more than fast enough for anything you'll throw at it, browsing, video, light gaming etc., don't worry. The article you linked to used PCI cards which has lower bandwidth than PCIe and shares it among all slots.

No, it shouldn't matter if the cards differ a bit. It seems there can be some BIOS problems if different generations are mixed. I had some really weird errors with a 8600GS and a 6200, like the 6200 randomly showing the picture upside down.

My experiments state that:
8400 + 6200 mostly OK
NVS 290 + 8400 OK
2x NVS 290 OK
2x NVS 290 + 6200 Not OK
2x NVS 290 + 8400 Mostly OK


There might a BIOS option for switching the onboard card on. Or maybe it's just a question of setting it up in software.

You should be able to make some better deals. Last time i brought memory, i brought 2x 2 gb for what equals $50. And you can probably find the graphics cards for around half of that. But just wait with memory upgrade. You'll still get a long way with 2 gb.

One neat thing you also could look into is VirtualBox. The seats can be turned into real Windows machines at the click of a button.

---

### Post by ubun2warrior on 2010-09-22
Hi

I have purchased just one graphics card and one is already there, the integrated one ... so is it possible to create a multi seat for 2 users connected on this pc.. just to start the experiment..before i purchase more graphics card or memory or cut the plastic of the  1x slot..  (because i now have two vga ports and two lcd monitors ready)  

regards
ubun2warrior

---

### Post by ubun2warrior on 2010-09-22
Hi

this is the output of lspci | grep VGA:

00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

i have connected two lcd monitors to my system; one to the onboard graphics and the other to the 8400 GS on the PCIE slot.

what should i do now ?? the display is currently on one lcd panel only(the on board one)

regards 
ubun2warrior

---

### Post by Fafler on 2010-09-22
You should use the hardware driver manager to install the driver for the 6150. It will also work with the 8400, but not the other way around. Now, use the Nvidia panel to get a picture on both monitors. Just to prove that it works. Then get back here.

---

### Post by ubun2warrior on 2010-09-24
hi

i have installed the NVIDIA 6150 SE driver. but i am not able to get the picture in both the monitors using NVIDIA panel.

---

### Post by Fafler on 2010-09-25
Post your /var/log/Xorg.0.log

Did the Nvidia control panel see both cards?

If yes, check if theres any command line options for nvidia-control-panel and run it from the terminal with more verbosity and look for any relevant output.

---

### Post by ubun2warrior on 2010-09-25
hi

when i enter /var/logXorg.0.log

it displays permission denied, evn when i am logged in as root

however when i open with gedit, this is the output:

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux comp5-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=4eff36c2-8478-41b3-a7fc-aa84ef632cab ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 25 16:00:13 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "1"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:13:0) 10de:03d0:103c:2a6c nVidia Corporation C61 [GeForce 6150SE nForce 430] rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(--) PCI: (0:2:0:0) 10de:06e4:0000:0000 nVidia Corporation G98 [GeForce 8400 GS] rev 161, Mem @ 0xf8000000/16777216, 0xe0000000/268435456, 0xf6000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  256.53  Fri Aug 27 21:28:41 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  256.53  Fri Aug 27 21:05:55 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:0d:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) Sep 25 16:00:13 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 25 16:00:13 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 25 16:00:13 NVIDIA(0):     enabled.
(II) Sep 25 16:00:14 NVIDIA(0): NVIDIA GPU GeForce 6150SE nForce 430 (C61) at PCI:0:13:0
(II) Sep 25 16:00:14 NVIDIA(0):     (GPU-0)
(--) Sep 25 16:00:14 NVIDIA(0): Memory: 524288 kBytes
(--) Sep 25 16:00:14 NVIDIA(0): VideoBIOS: 05.61.32.25.02
(--) Sep 25 16:00:14 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Sep 25 16:00:14 NVIDIA(0): Connected display device(s) on GeForce 6150SE nForce 430 at
(--) Sep 25 16:00:14 NVIDIA(0):     PCI:0:13:0:
(--) Sep 25 16:00:14 NVIDIA(0):     HP w15e (CRT-0)
(--) Sep 25 16:00:14 NVIDIA(0): HP w15e (CRT-0): 350.0 MHz maximum pixel clock
(II) Sep 25 16:00:14 NVIDIA(0): Assigned Display Device: CRT-0
(II) Sep 25 16:00:14 NVIDIA(0): Validated modes:
(II) Sep 25 16:00:14 NVIDIA(0):     "nvidia-auto-select+0+0"
(II) Sep 25 16:00:14 NVIDIA(0): Virtual screen size determined to be 1280 x 720
(--) Sep 25 16:00:14 NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) Sep 25 16:00:14 NVIDIA(0):     option
(==) Sep 25 16:00:14 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "nvidia-auto-select +0+0"
(**) Sep 25 16:00:14 NVIDIA(1): Enabling RENDER acceleration
(EE) Sep 25 16:00:15 NVIDIA(1): Failed to initialize the NVIDIA graphics device PCI:2:0:0. 
(EE) Sep 25 16:00:15 NVIDIA(1):     Please check your system's kernel log for additional error
(EE) Sep 25 16:00:15 NVIDIA(1):     messages and refer to Chapter 8: Common Problems in the
(EE) Sep 25 16:00:15 NVIDIA(1):     README for additional information.
(EE) Sep 25 16:00:15 NVIDIA(1): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
(EE) Sep 25 16:00:15 NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device PCI:2:0:0. 
(EE) Sep 25 16:00:15 NVIDIA(GPU-1):     Please check your system's kernel log for additional error
(EE) Sep 25 16:00:15 NVIDIA(GPU-1):     messages and refer to Chapter 8: Common Problems in the
(EE) Sep 25 16:00:15 NVIDIA(GPU-1):     README for additional information.
(EE) Sep 25 16:00:15 NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device!
(II) Sep 25 16:00:15 NVIDIA(0): Initialized GPU GART.
(II) Sep 25 16:00:15 NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) Sep 25 16:00:15 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Sep 25 16:00:15 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

---

### Post by ubun2warrior on 2010-09-26
hi

isn't there some software package in synaptics that will auto configure all the keyboards, mouse, monitors and set up the multiseat system??

sometimes it its very complicated with terminal..

regards 
ubun2warrior

---

### Post by Fafler on 2010-09-26
You should always wrap code tags around very long log output, as it makes your post much more readable.

You are not allowed to execute /var/log/Xorg.0.log because it's a log file, not an executeable file. Opening with gedit was correct.

Now, these are the points of interest:

```
(II) Sep 25 16:00:13 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 25 16:00:13 NVIDIA(0):     enabled.
(II) Sep 25 16:00:14 NVIDIA(0): NVIDIA GPU GeForce 6150SE nForce 430 (C61) at PCI:0:13:0
(II) Sep 25 16:00:14 NVIDIA(0):     (GPU-0)
(--) Sep 25 16:00:14 NVIDIA(0): Memory: 524288 kBytes
(--) Sep 25 16:00:14 NVIDIA(0): VideoBIOS: 05.61.32.25.02
(--) Sep 25 16:00:14 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Sep 25 16:00:14 NVIDIA(0): Connected display device(s) on GeForce 6150SE nForce 430 at
(--) Sep 25 16:00:14 NVIDIA(0):     PCI:0:13:0:
(--) Sep 25 16:00:14 NVIDIA(0):     HP w15e (CRT-0)
(--) Sep 25 16:00:14 NVIDIA(0): HP w15e (CRT-0): 350.0 MHz maximum pixel clock
(II) Sep 25 16:00:14 NVIDIA(0): Assigned Display Device: CRT-0
(II) Sep 25 16:00:14 NVIDIA(0): Validated modes:
(II) Sep 25 16:00:14 NVIDIA(0):     "nvidia-auto-select+0+0"
(II) Sep 25 16:00:14 NVIDIA(0): Virtual screen size determined to be 1280 x 720
(--) Sep 25 16:00:14 NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) Sep 25 16:00:14 NVIDIA(0):     option
(==) Sep 25 16:00:14 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
```

and

```
(**) Sep 25 16:00:14 NVIDIA(1): Enabling RENDER acceleration
(EE) Sep 25 16:00:15 NVIDIA(1): Failed to initialize the NVIDIA graphics device PCI:2:0:0. 
(EE) Sep 25 16:00:15 NVIDIA(1):     Please check your system's kernel log for additional error
(EE) Sep 25 16:00:15 NVIDIA(1):     messages and refer to Chapter 8: Common Problems in the
(EE) Sep 25 16:00:15 NVIDIA(1):     README for additional information.
(EE) Sep 25 16:00:15 NVIDIA(1): Failed to initialize the NVIDIA graphics device
```

What it shows it that it initialises the onboard card correctly, but not the PCIe card. It doesn't give a explanation as to why, but tells us to look at the kernel log.

Do a
```
cat /var/log/messages.1
```
and report any output relevant to this, eg. starting with the word NVIDIA, talking about PCI devices or similar. The file also contains a LOT of irrelevant info. The part you need should be near the end.

You better get used to the terminal, as it is you only friend here. Theres no GUI for this, although you're welcome to write one. That's how all the other Linux software got written.

---

### Post by ubun2warrior on 2010-09-26
hi

i formatted my system and installed ubuntu 10.04 again.
i again installed the nvidia drivers. 
can u plz tell me how do i get picture on both the monitors using the nvidia-setting

regards
ubun2warrior

---

### Post by ubun2warrior on 2010-09-26
In  NVIDIA X Server Setting, in the left hand side i go to X Server Display Configuration.
There in the layout i see 2 monitors but one is disabled. Last time i think i enabled xinerama, that is why it did not work

plz tell me what should i do now...

---

### Post by ubun2warrior on 2010-09-26
hi

is it possible to set up multiseat using virtual box ose

regards

ubun2warrior

---

### Post by Fafler on 2010-09-26
You could setup virtualbox and run a virtual machine on each xinerama screen. But then you might as well use the xnest/xephyr solution i mentioned earlier. But lets stick to the point here and stop running around in circles. Now, follow the instructions i gave you in the last post as we need to get both displays working before you can do anything further.

> What it shows it that it initialises the onboard card correctly, but not  the PCIe card. It doesn't give a explanation as to why, but tells us to  look at the kernel log.

Do a
 	Code:
 	cat /var/log/messages.1 
and report any output relevant to this, eg. starting with the word  NVIDIA, talking about PCI devices or similar. The file also contains a  LOT of irrelevant info. The part you need should be near the end.

---

### Post by ubun2warrior on 2010-09-26
hi

i got the picture on both the monitors using the NVIDIA control panel. The driver detected both the cards. Last time i think i made some error, i enabled xinerama..  So i did a fresh install of ubuntu 10.04 desktop, and installed the driver. now i am able to control both the monitors with a single mouse..

i tried cat /var/log/messages.1
this is what i get :
cat: /var/log/messages.1: No such file or directory

now what do i have to do??

regards

ubun2warrior

---

### Post by Fafler on 2010-09-27
Thats good. I'm going to break things up into smaller steps.

For this, you should have a another working PC and a USB thumb drive, as your system could quite likely break temporarily.

Now, GDM, the program that handles graphical logins, doesn't support multiseats at the moment, så you're going to install KDM instead. Same basic piece of software, but made for KDE instead of Gnome.

sudo apt-get install kdm

Reboot and make sure you get the KDM logins in screen instead of GDM.

Connect both sets of keyboards and mice and do a

find /dev/input/by-path

Post the results with notes about which goes each seat.

Open make a backup of /etc/kde4/kdm/kdmrc and open it in your favourite editor. Remember to gksudo, eg.

sudo cp /etc/kde4/kdm/kdmrc /etc/kde4/kdm/kdmrc.old
gksudo gedit /etc/kde4/kdm/kdmrc

Now replace the text with

```

[General][General] StaticServers=:0,:1 ReserveServers=:2,:3
ServerVTs=7,9
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6 PidFile=/var/run/kdm.pid ...  [X-:0-Core] AutoLoginAgain=false AutoLoginDelay=0 AutoLoginEnable=false AutoLoginLocked=false AutoLoginUser= ClientLogFile=.xsession-errors ServerVT=7 ServerCmd=/usr/bin/X0 -sharevts -layout seat0 -isolateDevice PCI:1:0:0 -keeptty  [X-:1-Core] AutoLoginAgain=false AutoLoginEnable=false AutoLoginLocked=false ClientLogFile=.xsession-errors ServerVT=9 ServerCmd=/usr/bin/X1 -sharevts -novtswitch -layout seat1 -isolateDevice PCI:2:0:0 -keeptty
```Think will make the onboard card the first seat and the PCIe the second.

The last thing to do right now is to symlink X with

sudo ln -s /usr/bin/X /usr/bin/X0
sudo ln -s /usr/bin/X /usr/bin/X1

Now, your system should be broken and unable to boot into X. But never mind that. We'll make a Xorg.conf later to fix it.

Edit: The kdmrc part won't work with the code tags. Copy/paste from here instead. [https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

---

### Post by ubun2warrior on 2010-09-27
hi

take a look at this link, [http://www.ncomputing.com/product-useries](http://www.ncomputing.com/product-useries)

regards
ubun2warrior

---

### Post by Fafler on 2010-09-27
Thats exactly what i had in mind. I'm browsing trough their .deb file right now :-) Quite interesting, but they doesn't say which license it's released under. I'll start by sending them an email. Thanks.

---

### Post by Vishal Agarwal on 2010-09-27
> **ubun2warrior said:**
> hi

take a look at this link, [http://www.ncomputing.com/product-useries](http://www.ncomputing.com/product-useries)

regards
ubun2warrior

Just yesterday I saw their demo. It was fine. I have checked it on Windows Platform, but it support Linux too.

Then have different kind of devices for different type of connectivity. you can try these.

---

### Post by ubun2warrior on 2010-09-27
hi

 also have ubuntu 9.04, so can i use that as it has gdm 2.2 . I tried to install kdm, the installation goes fine and my login screen is also kde but when i log in there just the wall paper. nothing works i even tried to run programs through alt f2 but nothing is being typed..

also i dont line kde much so should i degrade to ubuntu 9.04.. or may be there is some way to degrade to gdm 2.20

regards
ubun2warrior

---

### Post by ubun2warrior on 2010-09-28
hi


check this link [http://wiki.c3sl.ufpr.br/multiseat/index.php/Live-CD](http://wiki.c3sl.ufpr.br/multiseat/index.php/Live-CD)

regards
ubun2warrior

---

### Post by Fafler on 2010-09-28
Yes, you could just use 9.04 instead. Although KDM and GDM shouldn't care if they log into a Gnome or KDE session. I can't remember KDM, but somewhere on the loginscreen it should allow you to choose which window manager you want and you should just choose Gnome.

---

### Post by Fafler on 2010-09-28
I don't know... it looks kinda old and unmaintained. It's a good idea, though. And the Xephyr solution is still not the best as it runs a X server inside another X server. You won't get access to all the good stuff the Nvidia card can do for you. Anyway, somebody should update it. Or make a newer, more interactive setup program. Something using ncurses, allowing the user to easily select the devices wanted for each seat and all that.

---

### Post by ubun2warrior on 2010-09-28
> **Fafler said:**
> Yes, you could just use 9.04 instead. Although KDM and GDM shouldn't care if they log into a Gnome or KDE session. I can't remember KDM, but somewhere on the loginscreen it should allow you to choose which window manager you want and you should just choose Gnome.

ok 

i have installed kdm, the login screen is kdm

what should i do now

---

### Post by Fafler on 2010-09-28
I don't have any KDM machine here. Isn't there a place you can choose to log into Gnome?

---

### Post by ubun2warrior on 2010-09-28
hi 

i have installed kdm.. and i get the kdm login screen.. from there i log in to gnome session from there..

this is the output of find /dev/input/by-path

> /dev/input/by-path
/dev/input/by-path/platform-i8042-serio-1-event-mouse
/dev/input/by-path/platform-i8042-serio-1-mouse
/dev/input/by-path/pci-0000:00:02.0-usb-0:5:1.0-event-kbd
/dev/input/by-path/pci-0000:00:02.0-usb-0:5:1.1-event
/dev/input/by-path/pci-0000:00:02.0-usb-0:6:1.0-event-mouse
/dev/input/by-path/pci-0000:00:02.0-usb-0:6:1.0-mouse
/dev/input/by-path/platform-i8042-serio-0-event-kbd

regards

ubun2warrior

---

### Post by Fafler on 2010-09-28
Great! What goes where?

The PS/2 keyboard and mouse for the first seat and USB for the second?

By the way, once this works, your USB keyboard and mouse will only work in the ports they are connected to right now.

I'll be cooking up a Xorg.conf for you later :-)

---

### Post by ubun2warrior on 2010-09-29
> **Vishal Agarwal said:**
> Just yesterday I saw their demo. It was fine. I have checked it on Windows Platform, but it support Linux too.

Then have different kind of devices for different type of connectivity. you can try these.

 
Hi

Do you know the pricing of the devices that they provide, bcoz i tried searching for the prices but was unsuccessful.

Regards

ubun2warrior

---

### Post by ubun2warrior on 2010-09-29
> **Fafler said:**
> Great! What goes where?

The PS/2 keyboard and mouse for the first seat and USB for the second?

By the way, once this works, your USB keyboard and mouse will only work in the ports they are connected to right now.

I'll be cooking up a Xorg.conf for you later :-)

Hi

the ps/2 mouse and keyboard for the first seat which is connected to the onboard nvidia card and the usb keyboard and mouse for the second seat which is connected to the nvidia 8400 GS on the pci slot..

regards

ubun2warrior

---

### Post by ubun2warrior on 2010-09-29
Hi

i did the following:

sudo cp /etc/kde4/kdm/kdmrc /etc/kde4/kdm/kdmrc.old

gksudo gedit /etc/kde4/kdm/kdmrc
 
.... after this i copied the following code into the text editor
> 
[General]
StaticServers=:0,:1
ReserveServers=:2,:3
ServerVTs=7,9
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
PidFile=/var/run/kdm.pid
...

[X-:0-Core]
AutoLoginAgain=false
AutoLoginDelay=0
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=
ClientLogFile=.xsession-errors
ServerVT=7
ServerCmd=/usr/bin/X0 -sharevts -layout seat0 -isolateDevice PCI:1:0:0 -keeptty

[X-:1-Core]
AutoLoginAgain=false
AutoLoginEnable=false
AutoLoginLocked=false
ClientLogFile=.xsession-errors
ServerVT=9
ServerCmd=/usr/bin/X1 -sharevts -novtswitch -layout seat1 -isolateDevice PCI:2:0:0 -keeptty

after

which i did :


sudo ln -s /usr/bin/X /usr/bin/X0
sudo ln -s /usr/bin/X /usr/bin/X1

now i rebooted my pc 
ands loading in the non graphical mode

---

### Post by ubun2warrior on 2010-09-29
hi

what should i do next ???

regards 

ubun2warrior

---

### Post by Fafler on 2010-09-29
You need a Xorg.conf. Normally, X autoconfigures without the need for a file, but in this case, you need to tell X which keyboard goes where and all that.

If you're up to it, try this:
[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)
Do as told in the 9.10 section.
I don't have time to make one for you right now, but if you're unsure about anything, just say so, and i'll make one for you whenever... It's probably the hardest part to get right.

---

### Post by ubun2warrior on 2010-09-30
i did some editing to my xorg.conf, i disabled the autoenable devices for mouse and keyboard
now my system boot into the graphical session and nothing works plz help ...

---

### Post by ubun2warrior on 2010-09-30
hi

also chek this link [http://wiki.c3sl.ufpr.br/multiseat/index.php/Installing_mdm](http://wiki.c3sl.ufpr.br/multiseat/index.php/Installing_mdm)

ubun2warrior

---

### Post by ubun2warrior on 2010-09-30
i edited my xorg.conf

i think i disabled autoenable devices for keyboard and mouse

now system boots into the graphical interface and keyboard mouse not  working ..

all iam able to do is use the cpu power button to switch off..

will i have to reinstall ubuntu or is there some solution ??


help !!!!

---

### Post by ubun2warrior on 2010-09-30
Hi
found this on wikipedia

In 2005, the team of C3SL (Center for Scientific Computing and Free  Software),[[7]]("http://en.wikipedia.org/wiki/Multiseat_configuration#cite_note-6")  from Federal University of Parana in Brazil, created the solution based  with nested X servers, such [Xnest]("http://en.wikipedia.org/wiki/Xnest") and [Xephyr]("http://en.wikipedia.org/wiki/Xephyr").[[8]]("http://en.wikipedia.org/wiki/Multiseat_configuration#cite_note-7")  With this solution, each nested X server runs in each screen of a host X  server (e.g. [Xorg]("http://en.wikipedia.org/wiki/X.Org_Server")) and a modification in the nested servers  let it get the exclusivity of each set of mouse and keyboard. In 2008,  the [C3SL]("http://www.c3sl.ufpr.br/") group releases the [Multiseat  Display Manager]("http://en.wikipedia.org/w/index.php?title=Multiseat_Display_Manager&action=edit&redlink=1") (MDM) [[9]]("http://en.wikipedia.org/wiki/Multiseat_configuration#cite_note-8")  to ease the process of installation and configuration of a multiseat  box. This group, also in 2008, conceived a live-cd [[10]]("http://en.wikipedia.org/wiki/Multiseat_configuration#cite_note-9")  for tests purposes. Multiseat is a planned feature for [Fedora 12]("http://en.wikipedia.org/wiki/Fedora_%28operating_system%29").[[11]]("http://en.wikipedia.org/wiki/Multiseat_configuration#cite_note-10") 



I wanted to know that does fedora 12 has some graphical way of easily configuring multiseat... i tried to find on their website but all info was about fedora 13.. i have downloaded fedora 13..  i also wanted to know that whether multiseat is supported in f 13 or not


regards
ubun2warrior

---

### Post by ubun2warrior on 2010-10-01
Hi

I am posting some outputs

output of lspci | grep VGA
> 00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

ls /dev/input/mouse*> 
/dev/input/mouse0  /dev/input/mouse1  /dev/input/mouse2

more /proc/bus/input/devices
> I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0001 Vendor=10ec Product=0888 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:05.0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c05a Version=0111
N: Name="Logitech USB Optical Mouse"
P: Phys=usb-0000:00:02.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input6
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=17
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=04d9 Product=1603 Version=0110
N: Name="  USB Keyboard"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=04d9 Product=1603 Version=0110
N: Name="  USB Keyboard"
P: Phys=usb-0000:00:02.0-4/input1
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=13
B: KEY=2000000 39fa d941d001 1e0000 0 0 0
B: MSC=10

I have connected two mouse and two keyboard (one PS/2 and the other USB). I have also connected two monitors and i am getting displays on both the screens. I am also able to move my cursor on both the screens.

I am having trouble in configuring xorg.conf. I am running Ubuntu 10.04 desktop on my PC and I have also installed kdm bcoz gdm does not support multiseat. When i boot my PC i get the kdm login screen and then I boot into gnome session.. (is it ok ?? or do I need to install Kubuntu??)
Also, I have one onboard nvidia graphics 6150SE and I have put one nvidia 8400GS 512Mb in the 16X PCIe slot for the additional seat...

So kindly tell me what should I do now or what things are missing ?? For any further info abt my PC plz tell me to post outputs(specify the commands for the same..)

regards

ubun2warrior

---

### Post by larryjoe701 on 2010-10-03
I built a multi-seat system a few years ago to run MythTV.  Once I understood what was needed in xorg.conf things didn't seem too complicated.  All of the automated or graphical tools didn't seem to work for me.

First off, can you state what currently doesn't work that you need and what does work?  Your most recent post sounds like you've got both mice working, what about keyboard?

Second can you post the xorg.conf you've got.  It can be tiresome, but trust me from personal experience, you need to back up the file with each change, write down what the change was/why you made it, and only change one thing at a time.  I failed to do that once when I was having problems and drove myself mad!  In the end, my video card had burned up and replacing it got my system back up.

Third, I'll most parts of my xorg.conf and describe them.  In my system I am running two independent X servers on two different nVidia cards and using KDM as my login manager.  I use GNOME as my desktop, so there's no problem doing it that way.  It sounds like you're getting close so I'll skip to the trickier part, the input.  I named my two seats "Desktop" and "TV".  Here I declare the keyboard and mouse for the Desktop seat.
> 
Section "InputDevice"
        Identifier     "KeyboardDesktop"
        Driver         "evdev"
        Option         "Device" "/dev/input/event1"
        Option         "CoreKeyboard"
EndSection

Section "InputDevice"
        Identifier     "MouseDesktop"
        Driver         "evdev"
        Option         "Device" "/dev/input/event2"
        Option         "ZAxisMapping" "4 5"
        Option         "GrabDevice" "on"
        #Option         "Protocol" "ExplorerPS/2"
EndSection



Here's the TV seat input devices.  I'm not entirely sure what some of the little differences are, but I don't believe they are significant.  The main thing here is you need to pre-declare the devices you want to use as inputs for each desktop.
> Section "InputDevice"
        Identifier     "KeyboardTV"
        Driver         "evdev"
        Option         "Device" "/dev/input/event3"
        Option         "XkbModel" "pc105"
        Option         "XkbLayout" "us"
        Option         "XkbOptions" "compose:rwin"
        Option         "GrabDevice" "on"
EndSection

Section "InputDevice"
        Identifier     "MouseTV"
        Driver         "evdev"
        Option         "Protocol" "ExplorerPS/2"
        Option         "Device" "/dev/input/event4"
        Option         "ZAxisMapping" "6 7"
        Option         "GrabDevice" "on"
EndSection


The next important bit is the server layout, which collects all the information about each seat together:
> Section "ServerLayout"
        Identifier     "DesktopSeat"
        Screen      0  "ScreenDesktop" 0 0
        InputDevice    "MouseDesktop" "CorePointer"
        InputDevice    "KeyboardDesktop" "CoreKeyboard"
        Option         "GrabDevice" "on"
EndSection

Section "ServerLayout"
        Identifier     "TVSeat"
        Screen      0  "ScreenTV" 0 0
        InputDevice    "MouseTV" "CorePointer"
        InputDevice    "KeyboardTV" "CoreKeyboard"
EndSection

The screen should have a reference to the video card you're using, specified by the PCI address.  The mouse and keyboard are the ones you declared before.

Finally, you need a few server flags so that devices aren't automatically added to X servers.  Because I didn't fully document each change I made, I can't provide a full explanation of what each flag does.
> Section "ServerFlags"
        Option         "RandR" "True"
        Option         "AllowDeactivateGrabs" "true"
        Option         "DontZap" "True"
        Option         "DefaultServerLayout" "DesktopSeat"
        Option         "AllowMouseOpenFail" "true"
        Option         "AutoAddDevices" "false"
        Option         "AutoEnableDevices" "false"
EndSection


Some of the extra complication in my set-up has to do with trying to get a Sony bluetooth keyboard to work.  Over time I lost interest and didn't strip out the things I put in for it.  Hope some of this information helps!  I'll provide some guidance if you post what I requested.

---

### Post by ubun2warrior on 2010-10-05
hi

no i haven't got both the mice or the keyboards working... actually what i meant is that i am able to move the cursor(only the PS/2 one) along both the screens... i dont think i am very close... the kdm login screen just shows on one of the screens and not both the screens. one more thing.. if i open firefox on one screen and try to open it on the other screen the system does not allow to do so says process locked or something what i mean to say is that i am not able to open two same processes simultaneously on both the screens(..plz explain this ).

i am posting the output of my xorg.conf(right now only one PS/2 Keyboard and Mouse and one monitor(the one connected to the onboard nvidia) is connected )

> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 256.53  (buildmeister@builder101)  Fri Aug 27 21:33$

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 256.53  (buildmeister@builder101)  Fri Aug 27 21:34:$

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"

EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "evdev"
    Option         "Protocol" "Standard"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP w15e"
    HorizSync       31.0 - 64.0
    VertRefresh     59.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HP w15e"
    HorizSync       31.0 - 64.0
    VertRefresh     59.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150SE nForce 430"
BusID          "PCI:0:13:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

for any further info regarding my pc etc plz tell me to post the outputs( also specify the commands for the same  )..

i think the xorg.conf is very confusing i am not able to understand what to do..

regards

ubun2warrior

---

### Post by larryjoe701 on 2010-10-05
Based on your existing file and some of your previous posts, I've created the following xorg.conf file for you.  Please save to /etc/X11/xorg.conf as root.  Reboot your system and let me know what, if any problems, occur.  Try to be as specific and clear as possible: second screen is a blinking cursor while I can log in on first screen and the kbd and mouse work.

> # Hacked together by Tim Snyder Oct 5, 2010 based on his own working xorg.conf

# This section specifies your first mouse, named Mouse0.
# It must specify the device, /dev/input/event4 (PS2 mouse based on
# /proc/bus/input/devices), because there are 2 mice
Section "InputDevice"
	Identifier "Mouse0"
	Driver "evdev"
	Option "Protocol" "Standard"
	Option "Device" "/dev/input/event4"
	Option "Emulate3Buttons" "no"
	Option "ZAxisMapping" "4 5"
EndSection

# This section specifies your first keyboard, named Keyboard0.
# It must specify the device, /dev/input/event3 (AT Keyboard based on
# /proc/bus/input/devices), because there are 2 keyboards
Section "InputDevice"
	Identifier "Keyboard0"
	Driver "evdev"
	Option "Device" "/dev/input/event3"
EndSection

# This section specifies your second mouse, named Mouse1.
# It must specify the device, /dev/input/event6 (USB mouse based on
# /proc/bus/input/devices), because there are 2 mice
Section "InputDevice"
	Identifier "Mouse0"
	Driver "evdev"
	Option "Protocol" "Standard"
	Option "Device" "/dev/input/event6"
	Option "Emulate3Buttons" "no"
	Option "ZAxisMapping" "4 5"
EndSection

# This section specifies your second keyboard, named Keyboard1.
# It must specify the device, /dev/input/event7 (USB Keyboard based on
# /proc/bus/input/devices), because there are 2 keyboards
Section "InputDevice"
	Identifier "Keyboard0"
	Driver "evdev"
	Option "Device" "/dev/input/event7"
EndSection

# This section specifies your first monitor, named Monitor0
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Unknown"
	ModelName "HP w15e"
	HorizSync 31.0 - 64.0
	VertRefresh 59.0 - 75.0
	Option "DPMS"
EndSection

# This section specifies your second monitor, named Monitor1
Section "Monitor"
	Identifier "Monitor1"
	VendorName "Unknown"
	ModelName "HP w15e"
	HorizSync 31.0 - 64.0
	VertRefresh 59.0 - 75.0
EndSection

# This section specifies your first video card, named Device0
# The BusID should be the PCI bus address listed by 'lspci'
# If you move the board, this will need to be updated
Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "NVIDIA Corporation"
	BoardName "GeForce 6150SE nForce 430"
	BusID "PCI:0:13:0"
EndSection

# This section specifies your second video card, named Device1
Section "Device"
	Identifier "Device1"
	Driver "nvidia"
	VendorName "NVIDIA Corporation"
	BoardName "GeForce 8400 GS"
	BusID "PCI:2:0:0"
EndSection

# This specifies your first "screen", called Screen0
# The screen pulls together the video card device and the monitor plus some
# resolution and special mode settings (like a double-wide desktop)
Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	Option "metamodes" "nvidia-auto-select +0+0"
	SubSection "Display"
		Depth 24
	EndSubSection
EndSection

# This specifies your second "screen", called Screen1
Section "Screen"
	Identifier "Screen1"
	Device "Device1"
	Monitor "Monitor1"
	DefaultDepth 24
	Option "metamodes" "nvidia-auto-select +0+0"
	SubSection "Display"
		Depth 24
	EndSubSection
EndSection

# This section defines what "things" are grouped into a seat named "Layout0"
# The things include Keyboard0, Mouse0, and Screen0
Section "ServerLayout"
	Identifier "Layout0"
	InputDevice "Keyboard0" "CoreKeyboard"
	InputDevice "Mouse0" "CorePointer"
	Screen 0 "Screen0" 0 0
EndSection

# This section defines what things are grouped into the second seat,
# named "Layout1".
Section "ServerLayout"
	Identifier "Layout1"
	InputDevice "Keyboard1" "CoreKeyboard"
	InputDevice "Mouse1" "CorePointer"
	Screen 0 "Screen1" 0 0
EndSection


# This final section sets a few options for both servers
Section "ServerFlags"
	Option "RandR" "True"				# scaling and resizing
	Option "AllowDeactivateGrabs" "true"
	Option "DontZap" "True"
	Option "DefaultServerLayout" "Layout0"		# default seat
	Option "AllowMouseOpenFail" "true"
	Option "AutoAddDevices" "false"			# use manual setup
	Option "AutoEnableDevices" "false"
EndSection


The remaining work is to instruct KDM to start two X sessions, one on each layout.  I can't look up the file right now, but I will provide an example this evening.  

The basic idea is there is a config file that lists how many servers to start (defaults to 1), which configuration to use for them (normally there's only one), and which command to use to start it.  You'll have to specify a few extra options to instruct it to use the correct video card, but that's it.

Don't get discouraged!  :)  You're almost there, and remember: while any modern computer *could* support 10 concurrent web browsers, you are one of the few who has traded countless hours trying to configure a multi-seat system for the up-front hardware  and years of energy savings!

As for your question about firefox, you can normally only start certain applications (frequently web browsers, but other software as well) once per user because these programs lock certain configuration files.  The solution for a dual-seat setup is to have two different users logged in on the different stations.

---

### Post by ubun2warrior on 2010-10-06
hi

i copied the above file created by you to the specified location and then rebooted the pc. the system got stuck at the ubuntu splash screen(the one with red dots..) which appeared on only one monitor(the one connected to the on board graphics) and nothing happens after that. I rebooted several times with the same outcome. 
Then i had to log in as root with quiet splash and replace the xorg.conf file with the old one.

thanks a lot for the encouragement : )

regards

ubun2warrior

---

### Post by larryjoe701 on 2010-10-06
It may not be a real problem that X isn't coming up, we'll just have to make the changes to /etc/kde4/kdm/kdmrc first to find out.

First update the file to start a server on display :0 and :1 --
```
StaticServers=:0,:1
```

Next we need to update the first server to use the right settings.  Near the bottom of the file look for [X-:0-Core] and update the ServerArgsLocal line like this:
```
ServerArgsLocal=:0 vt07 -audit 0 -isolateDevice PCI:0:13:0 -nolisten tcp -layout Layout0

```

Then you need to copy everything below [X-:0-Core], paste it again at the bottom of the file and update :0 to :1.

Finally you need to set the right arguments to the second X server:
```
ServerArgsLocal=:0 vt08 -audit 0 -isolateDevice PCI:2:0:0 -nolisten tcp -layout Layout1
```

Now, if after rebooting you're still having trouble, please provide the output from Xorg.0.log file and Xorg.1.log file in /var/log, along with kdmrc file.

---

### Post by ubun2warrior on 2010-10-07
hi

i  am still having the same problems.. the screen gets stuck at the ubuntu splash screen

this is the output of my Xorg.0.log


> X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux comp5-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=ba9e53f3-bbc5-4d6d-afbd-5334d2718972 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct  7 17:22:05 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:13:0) 10de:03d0:103c:2a6c nVidia Corporation C61 [GeForce 6150SE nForce 430] rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(--) PCI: (0:2:0:0) 10de:06e4:0000:0000 nVidia Corporation G98 [GeForce 8400 GS] rev 161, Mem @ 0xf8000000/16777216, 0xe0000000/268435456, 0xf6000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  256.53  Fri Aug 27 21:28:41 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) NVIDIA dlloader X Driver  256.53  Fri Aug 27 21:05:55 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:0d:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) Oct 07 17:22:05 NVIDIA(0): Enabling RENDER acceleration
(II) Oct 07 17:22:05 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Oct 07 17:22:05 NVIDIA(0):     enabled.
(II) Oct 07 17:22:06 NVIDIA(0): NVIDIA GPU GeForce 6150SE nForce 430 (C61) at PCI:0:13:0
(II) Oct 07 17:22:06 NVIDIA(0):     (GPU-0)
(--) Oct 07 17:22:06 NVIDIA(0): Memory: 524288 kBytes
(--) Oct 07 17:22:06 NVIDIA(0): VideoBIOS: 05.61.32.25.02
(--) Oct 07 17:22:06 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Oct 07 17:22:06 NVIDIA(0): Connected display device(s) on GeForce 6150SE nForce 430 at
(--) Oct 07 17:22:06 NVIDIA(0):     PCI:0:13:0:
(--) Oct 07 17:22:06 NVIDIA(0):     HP w15e (CRT-0)
(--) Oct 07 17:22:06 NVIDIA(0): HP w15e (CRT-0): 350.0 MHz maximum pixel clock
(II) Oct 07 17:22:06 NVIDIA(0): Assigned Display Device: CRT-0
(II) Oct 07 17:22:06 NVIDIA(0): Validated modes:
(II) Oct 07 17:22:06 NVIDIA(0):     "nvidia-auto-select+0+0"
(II) Oct 07 17:22:06 NVIDIA(0): Virtual screen size determined to be 1280 x 720
(--) Oct 07 17:22:06 NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) Oct 07 17:22:06 NVIDIA(0):     option
(==) Oct 07 17:22:06 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "nvidia-auto-select +0+0"
(**) Oct 07 17:22:06 NVIDIA(1): Enabling RENDER acceleration
(II) Oct 07 17:22:07 NVIDIA(1): NVIDIA GPU GeForce 8400 GS (G98) at PCI:2:0:0 (GPU-1)
(--) Oct 07 17:22:07 NVIDIA(1): Memory: 524288 kBytes
(--) Oct 07 17:22:07 NVIDIA(1): VideoBIOS: 62.98.71.00.00
(II) Oct 07 17:22:07 NVIDIA(1): Detected PCI Express Link width: 16X
(--) Oct 07 17:22:07 NVIDIA(1): Interlaced video modes are supported on this GPU
(--) Oct 07 17:22:07 NVIDIA(1): Connected display device(s) on GeForce 8400 GS at PCI:2:0:0:
(--) Oct 07 17:22:07 NVIDIA(1):     HP w15e (CRT-1)
(--) Oct 07 17:22:07 NVIDIA(1): HP w15e (CRT-1): 400.0 MHz maximum pixel clock
(II) Oct 07 17:22:07 NVIDIA(1): Assigned Display Device: CRT-1
(II) Oct 07 17:22:07 NVIDIA(1): Validated modes:
(II) Oct 07 17:22:07 NVIDIA(1):     "nvidia-auto-select+0+0"
(II) Oct 07 17:22:07 NVIDIA(1): Virtual screen size determined to be 1280 x 720
(--) Oct 07 17:22:07 NVIDIA(1): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) Oct 07 17:22:07 NVIDIA(1):     option
(==) Oct 07 17:22:07 NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Oct 07 17:22:07 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Oct 07 17:22:07 NVIDIA(0): Initialized GPU GART.
(II) Oct 07 17:22:07 NVIDIA(0): Setting mode "nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) Oct 07 17:22:07 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Oct 07 17:22:07 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Oct 07 17:22:07 NVIDIA(1): Initialized GPU GART.
(II) Oct 07 17:22:07 NVIDIA(1): Setting mode "nvidia-auto-select+0+0"
(II) Oct 07 17:22:07 NVIDIA(1): Initialized OpenGL Acceleration
(==) NVIDIA(1): Disabling shared memory pixmaps
(II) Oct 07 17:22:07 NVIDIA(1): Initialized X Rendering Acceleration
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(**) Option "CorePointer"
(**) Mouse0: always reports core events
(**) Mouse0: Device: "/dev/psaux"
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "Mouse0"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event4)
(**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB Optical Mouse: Found 12 mouse buttons
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Found relative axes
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event5)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)

this is the output of my Xorg.1.log


> X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux comp5-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=ba9e53f3-bbc5-4d6d-afbd-5334d2718972 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Wed Oct  6 17:07:57 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
Data incomplete in file /etc/X11/xorg.conf
    Undefined InputDevice "Keyboard1" referenced by ServerLayout "Layout1".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

this is the output of my kdmrc (the original file which i have not edited)

> # KDM master configuration file
#
# Please note: Settings in this file are sometimes ignored (overridden).
# The default KDM startup script /etc/init.d/kdm looks in /etc/default/kdm.d
# for theme-related settings which, if found, take precedence. The possibly 
# overridden settings are: UseBackground, BackgroundCfg, UseTheme, Theme.
# See /usr/share/doc/kdm/README.Debian for details
#
# Definition: the greeter is the login dialog, i.e., the part of KDM
# which the user sees.
#
# You can configure every X-display individually.
# Every display has a display name, which consists of a host name
# (which is empty for local displays specified in {Static|Reserve}Servers),
# a colon, and a display number. Additionally, a display belongs to a
# display class (which can be ignored in most cases; the control center
# does not support this feature at all).
# Sections with display-specific settings have the formal syntax
# "[X-" host [":" number [ "_" class ]] "-" sub-section "]"
# You can use the "*" wildcard for host, number, and class. You may omit
# trailing components; they are assumed to be "*" then.
# The host part may be a domain specification like ".inf.tu-dresden.de".
# It may also be "+", which means non-empty, i.e. remote displays only.
# From which section a setting is actually taken is determined by these
# rules:
# - an exact match takes precedence over a partial match (for the host part),
#   which in turn takes precedence over a wildcard ("+" taking precedence
#   over "*")
# - precedence decreases from left to right for equally exact matches
# Example: display name "myhost:0", class "dpy".
# [X-myhost:0_dpy] precedes
# [X-myhost:0_*] (same as [X-myhost:0]) precedes
# [X-myhost:*_dpy] precedes
# [X-myhost:*_*] (same as [X-myhost]) precedes
# [X-+:0_dpy] precedes
# [X-*:0_dpy] precedes
# [X-*:0_*] (same as [X-*:0]) precedes
# [X-*:*_*] (same as [X-*])
# These sections do NOT match this display:
# [X-hishost], [X-myhost:0_dec], [X-*:1], [X-:*]
# If a setting is not found in any matching section, the default is used.
#
# Every comment applies to the following section or key. Note that all
# comments will be lost if you change this file with the kcontrol frontend.
# The defaults refer to KDM's built-in values, not anything set in this file.
#
# Special characters need to be backslash-escaped (leading and trailing
# spaces (\s), tab (\t), linefeed (\n), carriage return (\r) and the
# backslash itself (\\)).
# In lists, fields are separated with commas without whitespace in between.
# Some command strings are subject to simplified sh-style word splitting:
# single quotes (') and double quotes (") have the usual meaning; the backslash
# quotes everything (not only special characters). Note that the backslashes
# need to be doubled because of the two levels of quoting.

[General]
# This option exists solely for the purpose of a clean automatic upgrade.
# Do not even think about changing it!
ConfigVersion=2.4
# List of permanent displays. Displays with a hostname are foreign. A display
# class may be specified separated by an underscore.
# Default is ":0"
StaticServers=:0
# List of on-demand displays. See StaticServers for syntax.
# Default is ""
ReserveServers=:1,:2,:3
# VTs to allocate to X-servers. A negative number means that the VT will be
# used only if it is free. If all VTs in this list are used up, the next free
# one greater than the last one in this list will be allocated.
# Default is ""
ServerVTs=-7
# TTYs (without /dev/) to monitor for activity while in console mode.
# Default is ""
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
# Where KDM should store its PID (do not store if empty).
# Default is ""
PidFile=/var/run/kdm.pid
# Whether KDM should lock the PID file to prevent having multiple KDM
# instances running at once. Do not change unless you are brave.
# Default is true
#LockPidFile=false
# Where to store authorization files.
# Default is "/var/run/xauth"
#AuthDir=/tmp
# Whether KDM should automatically re-read configuration files, if it
# finds them having changed.
# Default is true
#AutoRescan=false
# Additional environment variables KDM should pass on to all programs it runs.
# LD_LIBRARY_PATH and XCURSOR_THEME are good candidates;
# otherwise, it should not be necessary very often.
# Default is ""
#ExportList=LD_LIBRARY_PATH,ANOTHER_IMPORTANT_VAR
# A character device KDM should read entropy from.
# Empty means use the system's preferred entropy device.
# Default is ""
#RandomDevice=/dev/altrandom
# Where the command sockets should be created; make it empty to disable
# them.
# Default is "/var/run/xdmctl"
#FifoDir=/tmp
# The group to which the global command socket should belong;
# can be either a name or a numerical ID.
# Default is 0
#FifoGroup=xdmctl
# The directory in which KDM should store persistent working data.
# Default is "/var/lib/kdm"
#DataDir=
# The directory in which KDM should store users' .dmrc files. This is only
# needed if the home directories are not readable before actually logging in
# (like with AFS).
# Default is ""
#DmrcDir=/nfs-shared/var/dmrcs

[Xdmcp]
# Whether KDM should listen to incoming XDMCP requests.
# Default is true
Enable=false
# The UDP port on which KDM should listen for XDMCP requests. Do not change.
# Default is 177
#Port=177
# File with the private keys of X-terminals. Required for XDM authentication.
# Default is ""
#KeyFile=/etc/kde4/kdm/kdmkeys
# XDMCP access control file in the usual XDM-Xaccess format.
# Default is "/etc/kde4/kdm/Xaccess"
#Xaccess=
# Number of seconds to wait for display to respond after the user has
# selected a host from the chooser.
# Default is 15
#ChoiceTimeout=10
# Strip domain name from remote display names if it is equal to the local
# domain.
# Default is true
#RemoveDomainname=false
# Use the numeric IP address of the incoming connection on multihomed hosts
# instead of the host name.
# Default is false
#SourceAddress=true
# The program which is invoked to dynamically generate replies to XDMCP
# DirectQuery or BroadcastQuery requests.
# If empty, no program is invoked and "Willing to manage" is sent.
# Default is ""
Willing=/etc/kde4/kdm/Xwilling

[Shutdown]
# The command (subject to word splitting) to run to halt the system.
# Default is "/sbin/halt"
#HaltCmd=
# The command (subject to word splitting) to run to reboot the system.
# Default is "/sbin/reboot"
#RebootCmd=
# Whether it is allowed to shut down the system via the global command socket.
# Default is false
#AllowFifo=true
# Whether it is allowed to abort active sessions when shutting down the
# system via the global command socket.
# Default is true
#AllowFifoNow=false
# The boot manager KDM should use for offering boot options in the
# shutdown dialog.
# "None" - no boot manager
# "Grub" - Grub boot manager
# "Lilo" - Lilo boot manager (Linux on i386 & x86-64 only)
# Default is None
#BootManager=Grub

# Rough estimations about how many seconds KDM will spend at most on
# - opening a connection to the X-server (OpenTime) if the attempt
#   - times out: OpenTimeout
#   - is refused: OpenRepeat * OpenDelay
# - starting a local X-server (ServerTime):
#   ServerAttempts * (ServerTimeout + OpenDelay)
# - starting a display:
#   - local display: ServerTime + OpenTime
#   - foreign display: StartAttempts * OpenTime
#   - XDMCP display: OpenTime (repeated indefinitely by client)

# Core config for all displays
[X-*-Core]
# How long to wait before retrying to connect a display.
# Default is 15
#OpenDelay=15
# How long to wait before timing out a display connection attempt.
# Default is 120
#OpenTimeout=120
# How many connection attempts to make during a start attempt. Note that
# a timeout aborts the entire start attempt.
# Default is 5
#OpenRepeat=5
# Try at most that many times to start a display. If this fails, the display
# is disabled.
# Default is 4
#StartAttempts=4
# Ping remote display every that many minutes.
# Default is 5
#PingInterval=5
# Wait for a Pong that many minutes.
# Default is 5
#PingTimeout=5
# The name of this X-server's Xauth file.
# If empty, a random name in the AuthDir directory will be used.
# Default is ""
#AuthFile=
# Specify a file with X-resources for the greeter, chooser and background.
# The KDE frontend does not use this file, so you do not need it unless you
# use another background generator than krootimage.
# Default is ""
#Resources=
# The xrdb program to use to read the above specified recources.
# Subject to word splitting.
# Default is "/usr/bin/xrdb"
#Xrdb=
# A program to run before the greeter is shown. Can be used to start an
# xconsole or an alternative background generator. Subject to word splitting.
# Default is ""
Setup=/etc/kde4/kdm/Xsetup
# A program to run before a user session starts. Subject to word splitting.
# Default is ""
Startup=/etc/kde4/kdm/Xstartup
# A program to run after a user session exits. Subject to word splitting.
# Default is ""
Reset=/etc/kde4/kdm/Xreset
# The program which is run as the user which logs in. It is supposed to
# interpret the session argument (see SessionsDirs) and start an appropriate
# session according to it. Subject to word splitting.
# Default is "/usr/bin/xterm -ls -T"
Session=/etc/kde4/kdm/Xsession
# The program to run if Session fails.
# Default is "/usr/bin/xterm"
#FailsafeClient=
# The PATH for the Session program.
# Default is "/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games"
#UserPath=
# The PATH for Setup, Startup and Reset, etc.
# Default is "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
#SystemPath=
# The default system shell.
# Default is "/bin/sh"
#SystemShell=/bin/bash
# Where to put the user's X-server authorization file if ~/.Xauthority
# cannot be created.
# Default is "/tmp"
#UserAuthDir=
# If true, UserAuthDir will be used unconditionally.
# Default is false
#ForceUserAuthDir=true
# Whether to automatically restart sessions after X-server crashes.
# Note that enabling this makes circumventing screen lockers other than
# KDE's built-in one possible!
# Default is false
#AutoReLogin=true
# Allow root logins?
# Default is true
AllowRootLogin=false
# Allow to log in, when user has set an empty password?
# Default is true
AllowNullPasswd=false
# Who is allowed to shut down the system. This applies both to the
# greeter and to the command sockets.
# "None" - no "Shutdown..." menu entry is shown at all
# "Root" - the root password must be entered to shut down
# "All" - everybody can shut down the machine
# Default is All
AllowShutdown=Root
# Who is allowed to abort active sessions when shutting down.
# "None" - no forced shutdown is allowed at all
# "Root" - the root password must be entered to shut down forcibly
# "All" - everybody can shut down the machine forcibly
# Default is All
#AllowSdForceNow=Root
# The default choice for the shutdown condition/timing.
# "Schedule" - shut down after all active sessions exit (possibly at once)
# "TryNow" - shut down, if no active sessions are open; otherwise, do nothing
# "ForceNow" - shut down unconditionally
# Default is Schedule
#DefaultSdMode=ForceNow
# How to offer shutdown scheduling options:
# "Never" - not at all
# "Optional" - as a button in the simple shutdown dialogs
# "Always" - instead of the simple shutdown dialogs
# Default is Never
#ScheduledSd=Optional
# The directories containing session type definitions in .desktop format,
# ordered by falling priority.
# Default is "/usr/share/xsessions,/var/lib/menu-xdg/xsessions,/usr/share/apps/kdm/sessions"
#SessionsDirs=/usr/share/xsessions,/var/lib/menu-xdg/xsessions,/usr/share/apps/kdm/sessions
# The file (relative to $HOME) to redirect the session output to. The
# following character pairs are replaced:
# - %d -> current display
# - %u -> current user
# - %r -> empty at first. See below.
# - %% -> a single %
# When the constructed filename cannot be used safely and the specification
# contains %<stuff>r, other names will be tried - this time expanding %<stuff>r
# to <stuff> followed by a random number.
# Default is ".xsession-errors"
ClientLogFile=.xsession-errors-%d
# Fallback when ClientLogFile cannot be used. The same expansions are
# supported. DO NOT use relative paths here.
# Default is "/tmp/xerr-%u-%d%-r"
#ClientLogFallback=/var/log/xsession-errors/%u-%d%-r
# Whether KDM's built-in utmp/wtmp/lastlog registration should be used.
# Default is false
#UseSessReg=true

# Greeter config for all displays
[X-*-Greeter]
# Specify the widget style for the greeter. Empty means to use the
# built-in default which currently is "Oxygen-air".
# Default is ""
#GUIStyle=Plastique
# Specify the widget color scheme for the greeter. Empty means to use the
# built-in default which currently is "Oxygen-air".
# Default is ""
#ColorScheme=MidnightMeadow
# What should be shown in the greeter's logo are:
# "None" - nothing
# "Logo" - the image specified by LogoPixmap
# "Clock" - a neat analog clock
# Default is Clock
LogoArea=Logo
# The image to show when LogoArea=Logo.
# Default is ""
LogoPixmap=/usr/share/kde4/apps/kdm/pics/kdelogo.png
# The relative coordinates (X,Y in percent) of the center of the greeter.
# Default is "50,50"
#GreeterPos=30,40
# The screen the greeter should be displayed on in multi-headed and Xinerama
# setups. The numbering starts with 0. For Xinerama, it corresponds to the
# listing order in the active ServerLayout section of XF86Config; -1 means
# to use the upper-left screen, -2 means to use the upper-right screen.
# Default is 0
#GreeterScreen=-1
# The headline in the greeter. The following character pairs are replaced:
# - %d -> current display
# - %h -> host name, possibly with domain name
# - %n -> node name, most probably the host name without domain name
# - %s -> the operating system
# - %r -> the operating system's version
# - %m -> the machine (hardware) type
# - %% -> a single %
# Default is "Welcome to Kubuntu at %n"
#GreetString=Welcome to Kubuntu at %n
# Whether the fonts used in the greeter should be antialiased.
# Default is false
#AntiAliasing=true
# The font for the greeter headline.
# Default is "Serif,20,bold"
#GreetFont=Serif,20,5,0,50,0
# The normal font used in the greeter.
# Default is "Sans Serif,10"
#StdFont=Sans Serif,10,5,0,50,0
# The font used for the "Login Failed" message.
# Default is "Sans Serif,10,bold"
#FailFont=Sans Serif,10,5,0,75,0
# What to do with the Num Lock modifier for the time the greeter is running:
# "Off" - turn off
# "On" - turn on
# "Keep" - do not change the state
# Default is Keep
#NumLock=Off
# Language and locale to use in the greeter, encoded like $LANGUAGE.
# If empty, the settings from the environment are used.
# Default is ""
#Language=de_DE
# Enable autocompletion in the username line edit.
# Default is false
#UserCompletion=true
# Enable user list (names along with images) in the greeter.
# Default is true
#UserList=false
# User selection for UserCompletion and UserList:
# "NotHidden" - all users except those listed in HiddenUsers
# "Selected" - only the users listed in SelectedUsers
# Default is NotHidden
#ShowUsers=Selected
# For ShowUsers=Selected. @<group> means all users in that group.
# Default is ""
#SelectedUsers=root,johndoe
# For ShowUsers=NotHidden. @<group> means all users in that group.
# Default is ""
#HiddenUsers=root
# Special case of HiddenUsers: users with a non-zero UID less than this number
# will not be shown as well.
# Default is 0
MinShowUID=1000
# Complement to MinShowUID: users with a UID greater than this number will
# not be shown as well.
# Default is 65535
MaxShowUID=29999
# If false, the users are listed in the order they appear in /etc/passwd.
# If true, they are sorted alphabetically.
# Default is true
#SortUsers=false
# Specify, where the users' pictures should be taken from.
# "AdminOnly" - from <FaceDir>/$USER.face[.icon]
# "PreferAdmin" - prefer <FaceDir>, fallback on $HOME
# "PreferUser" - ... and the other way round
# "UserOnly" - from the user's $HOME/.face[.icon]
# Default is AdminOnly
#FaceSource=PreferUser
# The directory containing the user images if FaceSource is not UserOnly.
# Default is "/usr/share/kde4/apps/kdm/faces"
#FaceDir=/usr/share/faces
# Specify, if/which user should be preselected for log in.
# "None" - do not preselect any user
# "Previous" - the user which successfully logged in last time
# "Default" - the user specified in the DefaultUser option
# Default is None
#PreselectUser=Previous
# If this is true, the password input line is focused automatically if
# a user is preselected.
# Default is false
#FocusPasswd=true
# If this is true, the entered password is echoed as bullets. Otherwise,
# no feedback is given at all.
# Default is true
#EchoPasswd=false
# If true, krootimage will be automatically started by KDM; otherwise, the
# Setup script should be used to setup the background.
# Default is true
#UseBackground=false
# The configuration file to be used by krootimage.
# Default is "/etc/kde4/kdm/backgroundrc"
#BackgroundCfg=
# Whether to grab keyboard and mouse while the greeter is visible. Grabs
# may improve security, but make on-screen keyboards, etc. unusable.
# "Never" - never grab
# "IfNoAuth" - grab if the display requires no X authorization
# "Always" - always grab
# Default is IfNoAuth
#GrabInput=Always
# Hold the X-server grabbed the whole time the greeter is visible. This
# may be more secure, but it will disable any background and other
# X-clients started from the Setup script.
# Default is false
#GrabServer=true
# How many seconds to wait for grab to succeed.
# Default is 3
#GrabTimeout=3
# Warn, if display has no X-authorization (local auth cannot be created,
# XDMCP display wants no auth, or display is foreign from StaticServers).
# Default is true
#AuthComplain=false
# Random seed for forging saved session types, etc. of unknown users.
# This value should be random but constant across the login domain.
# Default is 0
#ForgingSeed=0
# Specify conversation plugins for the login dialog. Each plugin can be
# specified as a base name (which expands to $kde_modulesdir/kgreet_$base)
# or as a full pathname.
# Default is "classic"
#PluginsLogin=sign
# Same as PluginsLogin, but for the shutdown dialog.
# Default is "classic"
#PluginsShutdown=modern
# A list of options of the form Key=Value. The conversation plugins can query
# these settings; it is up to them what possible keys are.
# Default is ""
#PluginOptions=SomeKey=randomvalue,Foo=bar
# Show the "Console Login" action in the greeter (if ServerTTY/ConsoleTTYs
# is configured).
# Default is true
#AllowConsole=false
# A program to run while the greeter is visible. It is supposed to preload
# as much as possible of the session that is going to be started (most
# probably).
# Default is ""
Preloader=/usr/bin/preloadkde
# Whether the greeter should be themed.
# Default is false
UseTheme=true
# The theme to use for the greeter. Can point to either a directory or an XML
# file.
# Default is ""
Theme=/usr/share/kde4/apps/kdm/themes/ethais

# Core config for local displays
[X-:*-Core]
# How often to try to run the X-server. Running includes executing it and
# waiting for it to come up.
# Default is 1
#ServerAttempts=1
# How long to wait for a local X-server to come up.
# Default is 15
#ServerTimeout=15
# The command line to start the X-server, without display number and VT spec.
# This string is subject to word splitting.
# Default is "/usr/bin/X"
ServerCmd=/usr/bin/X
# Additional arguments for the X-servers for local sessions.
# This string is subject to word splitting.
# Default is ""
ServerArgsLocal=-nr -nolisten tcp
# Additional arguments for the X-servers for remote sessions.
# This string is subject to word splitting.
# Default is ""
#ServerArgsRemote=
# Restart instead of resetting the local X-server after session exit.
# Use it if the server leaks memory etc.
# Default is false
#TerminateServer=true
# The signal needed to reset the local X-server.
# Default is 1 (SIGHUP)
#ResetSignal=1
# The signal needed to terminate the local X-server.
# Default is 15 (SIGTERM)
#TermSignal=15
# Create X-authorizations for local displays.
# Default is true
#Authorize=false
# Which X-authorization mechanisms should be used.
# Default is "MIT-MAGIC-COOKIE-1"
#AuthNames=
# Need to reset the X-server to make it read initial Xauth file.
# Default is false
#ResetForAuth=true
# See above
AllowNullPasswd=true
# See above
AllowShutdown=All
# Enable password-less logins on this display. USE WITH EXTREME CARE!
# Default is false
#NoPassEnable=true
# The users that do not need to provide a password to log in. NEVER list root!
# "*" means all non-root users. @<group> means all users in that group.
# Default is ""
#NoPassUsers=fred,ethel

# Greeter config for local displays
[X-:*-Greeter]
# See above
PreselectUser=Previous
# See above
FocusPasswd=true
# Specify whether the greeter of local displays should start up in host chooser
# (remote) or login (local) mode and whether it is allowed to switch to the
# other mode.
# "LocalOnly" - only local login possible
# "DefaultLocal" - start up in local mode, but allow switching to remote mode
# "DefaultRemote" - ... and the other way round
# "RemoteOnly" - only choice of remote host possible
# Default is LocalOnly
LoginMode=DefaultLocal
# A list of hosts to be automatically added to the remote login menu. The
# special name "*" means broadcast.
# Default is "*"
#ChooserHosts=*,ugly,sky,dino,kiste.local,login.crap.com
# Show the "Restart X Server"/"Close Connection" action in the greeter.
# Default is true
AllowClose=true

# Core config for 1st local display
[X-:0-Core]
# The VT the X-server should run on; auto-assign if zero, don't assign if -1.
# Better leave it zero and use ServerVTs.
# Default is 0
#ServerVT=7
# Enable automatic login. USE WITH EXTREME CARE!
# Default is false
#AutoLoginEnable=true
# If true, auto-login after logout. If false, auto-login is performed only
# when a display session starts up.
# Default is false
#AutoLoginAgain=true
# The delay in seconds before automatic login kicks in.
# Default is 0
#AutoLoginDelay=10
# The user to log in automatically. NEVER specify root!
# Default is ""
#AutoLoginUser=fred
# The password for the user to log in automatically. This is NOT required
# unless the user is logged into a NIS or Kerberos domain. If you use this
# option, you should "chmod 600 kdmrc" for obvious reasons.
# Default is ""
#AutoLoginPass=secret!
# Immediately lock the automatically started session. This works only with
# KDE sessions.
# Default is false
#AutoLoginLocked=true
# See above
ClientLogFile=.xsession-errors

# Greeter config for 1st local display
[X-:0-Greeter]
# See above
#PreselectUser=Default
# The user to preselect if PreselectUser=Default.
# Default is ""
#DefaultUser=johndoe



regards

ubun2warrior

---

### Post by larryjoe701 on 2010-10-07
Looks like I made a typo in the first xorg.conf file.  The second Keyboard0 and Mouse0 should have been Keyboard1 and Mouse1.  Fixed below.

```
# Hacked together by Tim Snyder Oct 5, 2010 based on his own working xorg.conf

# This section specifies your first mouse, named Mouse0.
# It must specify the device, /dev/input/event4 (PS2 mouse based on
# /proc/bus/input/devices), because there are 2 mice
Section "InputDevice"
Identifier "Mouse0"
Driver "evdev"
Option "Protocol" "Standard"
Option "Device" "/dev/input/event4"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

# This section specifies your first keyboard, named Keyboard0.
# It must specify the device, /dev/input/event3 (AT Keyboard based on
# /proc/bus/input/devices), because there are 2 keyboards
Section "InputDevice"
Identifier "Keyboard0"
Driver "evdev"
Option "Device" "/dev/input/event3"
EndSection

# This section specifies your second mouse, named Mouse1.
# It must specify the device, /dev/input/event6 (USB mouse based on
# /proc/bus/input/devices), because there are 2 mice
Section "InputDevice"
Identifier "Mouse1"
Driver "evdev"
Option "Protocol" "Standard"
Option "Device" "/dev/input/event6"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection

# This section specifies your second keyboard, named Keyboard1.
# It must specify the device, /dev/input/event7 (USB Keyboard based on
# /proc/bus/input/devices), because there are 2 keyboards
Section "InputDevice"
Identifier "Keyboard1"
Driver "evdev"
Option "Device" "/dev/input/event7"
EndSection

# This section specifies your first monitor, named Monitor0
Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "HP w15e"
HorizSync 31.0 - 64.0
VertRefresh 59.0 - 75.0
Option "DPMS"
EndSection

# This section specifies your second monitor, named Monitor1
Section "Monitor"
Identifier "Monitor1"
VendorName "Unknown"
ModelName "HP w15e"
HorizSync 31.0 - 64.0
VertRefresh 59.0 - 75.0
EndSection

# This section specifies your first video card, named Device0
# The BusID should be the PCI bus address listed by 'lspci'
# If you move the board, this will need to be updated
Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 6150SE nForce 430"
BusID "PCI:0:13:0"
EndSection

# This section specifies your second video card, named Device1
Section "Device"
Identifier "Device1"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 8400 GS"
BusID "PCI:2:0:0"
EndSection

# This specifies your first "screen", called Screen0
# The screen pulls together the video card device and the monitor plus some
# resolution and special mode settings (like a double-wide desktop)
Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "metamodes" "nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

# This specifies your second "screen", called Screen1
Section "Screen"
Identifier "Screen1"
Device "Device1"
Monitor "Monitor1"
DefaultDepth 24
Option "metamodes" "nvidia-auto-select +0+0"
SubSection "Display"
Depth 24
EndSubSection
EndSection

# This section defines what "things" are grouped into a seat named "Layout0"
# The things include Keyboard0, Mouse0, and Screen0
Section "ServerLayout"
Identifier "Layout0"
InputDevice "Keyboard0" "CoreKeyboard"
InputDevice "Mouse0" "CorePointer"
Screen 0 "Screen0" 0 0
EndSection

# This section defines what things are grouped into the second seat,
# named "Layout1".
Section "ServerLayout"
Identifier "Layout1"
InputDevice "Keyboard1" "CoreKeyboard"
InputDevice "Mouse1" "CorePointer"
Screen 0 "Screen1" 0 0
EndSection


# This final section sets a few options for both servers
Section "ServerFlags"
Option "RandR" "True" # scaling and resizing
Option "AllowDeactivateGrabs" "true"
Option "DontZap" "True"
Option "DefaultServerLayout" "Layout0" # default seat
Option "AllowMouseOpenFail" "true"
Option "AutoAddDevices" "false" # use manual setup
Option "AutoEnableDevices" "false"
EndSection 
```

For the kdmrc file, I'll post a working file for you in just a few minutes from another computer.

---

### Post by larryjoe701 on 2010-10-07
A little longer than a few minutes, but here's a new kdmrc for ya.

```
# KDM master configuration file
#
# Please note: Settings in this file are sometimes ignored (overridden).
# The default KDM startup script /etc/init.d/kdm looks in /etc/default/kdm.d
# for theme-related settings which, if found, take precedence. The possibly
# overridden settings are: UseBackground, BackgroundCfg, UseTheme, Theme.
# See /usr/share/doc/kdm/README.Debian for details
#
# Definition: the greeter is the login dialog, i.e., the part of KDM
# which the user sees.
#
# You can configure every X-display individually.
# Every display has a display name, which consists of a host name
# (which is empty for local displays specified in {Static|Reserve}Servers),
# a colon, and a display number. Additionally, a display belongs to a
# display class (which can be ignored in most cases; the control center
# does not support this feature at all).
# Sections with display-specific settings have the formal syntax
# "[X-" host [":" number [ "_" class ]] "-" sub-section "]"
# You can use the "*" wildcard for host, number, and class. You may omit
# trailing components; they are assumed to be "*" then.
# The host part may be a domain specification like ".inf.tu-dresden.de".
# It may also be "+", which means non-empty, i.e. remote displays only.
# From which section a setting is actually taken is determined by these
# rules:
# - an exact match takes precedence over a partial match (for the host part),
# which in turn takes precedence over a wildcard ("+" taking precedence
# over "*")
# - precedence decreases from left to right for equally exact matches
# Example: display name "myhost:0", class "dpy".
# [X-myhost:0_dpy] precedes
# [X-myhost:0_*] (same as [X-myhost:0]) precedes
# [X-myhost:*_dpy] precedes
# [X-myhost:*_*] (same as [X-myhost]) precedes
# [X-+:0_dpy] precedes
# [X-*:0_dpy] precedes
# [X-*:0_*] (same as [X-*:0]) precedes
# [X-*:*_*] (same as [X-*])
# These sections do NOT match this display:
# [X-hishost], [X-myhost:0_dec], [X-*:1], [X-:*]
# If a setting is not found in any matching section, the default is used.
#
# Every comment applies to the following section or key. Note that all
# comments will be lost if you change this file with the kcontrol frontend.
# The defaults refer to KDM's built-in values, not anything set in this file.
#
# Special characters need to be backslash-escaped (leading and trailing
# spaces (\s), tab (\t), linefeed (\n), carriage return (\r) and the
# backslash itself (\\)).
# In lists, fields are separated with commas without whitespace in between.
# Some command strings are subject to simplified sh-style word splitting:
# single quotes (') and double quotes (") have the usual meaning; the backslash
# quotes everything (not only special characters). Note that the backslashes
# need to be doubled because of the two levels of quoting.

[General]
# This option exists solely for the purpose of a clean automatic upgrade.
# Do not even think about changing it!
ConfigVersion=2.4
# List of permanent displays. Displays with a hostname are foreign. A display
# class may be specified separated by an underscore.
# Default is ":0"
StaticServers=:0,:1
# List of on-demand displays. See StaticServers for syntax.
# Default is ""
ReserveServers=:2,:3
# VTs to allocate to X-servers. A negative number means that the VT will be
# used only if it is free. If all VTs in this list are used up, the next free
# one greater than the last one in this list will be allocated.
# Default is ""
ServerVTs=-7
# TTYs (without /dev/) to monitor for activity while in console mode.
# Default is ""
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
# Where KDM should store its PID (do not store if empty).
# Default is ""
PidFile=/var/run/kdm.pid
# Whether KDM should lock the PID file to prevent having multiple KDM
# instances running at once. Do not change unless you are brave.
# Default is true
#LockPidFile=false
# Where to store authorization files.
# Default is "/var/run/xauth"
#AuthDir=/tmp
# Whether KDM should automatically re-read configuration files, if it
# finds them having changed.
# Default is true
#AutoRescan=false
# Additional environment variables KDM should pass on to all programs it runs.
# LD_LIBRARY_PATH and XCURSOR_THEME are good candidates;
# otherwise, it should not be necessary very often.
# Default is ""
#ExportList=LD_LIBRARY_PATH,ANOTHER_IMPORTANT_VAR
# A character device KDM should read entropy from.
# Empty means use the system's preferred entropy device.
# Default is ""
#RandomDevice=/dev/altrandom
# Where the command sockets should be created; make it empty to disable
# them.
# Default is "/var/run/xdmctl"
#FifoDir=/tmp
# The group to which the global command socket should belong;
# can be either a name or a numerical ID.
# Default is 0
#FifoGroup=xdmctl
# The directory in which KDM should store persistent working data.
# Default is "/var/lib/kdm"
#DataDir=
# The directory in which KDM should store users' .dmrc files. This is only
# needed if the home directories are not readable before actually logging in
# (like with AFS).
# Default is ""
#DmrcDir=/nfs-shared/var/dmrcs

[Xdmcp]
# Whether KDM should listen to incoming XDMCP requests.
# Default is true
Enable=false
# The UDP port on which KDM should listen for XDMCP requests. Do not change.
# Default is 177
#Port=177
# File with the private keys of X-terminals. Required for XDM authentication.
# Default is ""
#KeyFile=/etc/kde4/kdm/kdmkeys
# XDMCP access control file in the usual XDM-Xaccess format.
# Default is "/etc/kde4/kdm/Xaccess"
#Xaccess=
# Number of seconds to wait for display to respond after the user has
# selected a host from the chooser.
# Default is 15
#ChoiceTimeout=10
# Strip domain name from remote display names if it is equal to the local
# domain.
# Default is true
#RemoveDomainname=false
# Use the numeric IP address of the incoming connection on multihomed hosts
# instead of the host name.
# Default is false
#SourceAddress=true
# The program which is invoked to dynamically generate replies to XDMCP
# DirectQuery or BroadcastQuery requests.
# If empty, no program is invoked and "Willing to manage" is sent.
# Default is ""
Willing=/etc/kde4/kdm/Xwilling

[Shutdown]
# The command (subject to word splitting) to run to halt the system.
# Default is "/sbin/halt"
#HaltCmd=
# The command (subject to word splitting) to run to reboot the system.
# Default is "/sbin/reboot"
#RebootCmd=
# Whether it is allowed to shut down the system via the global command socket.
# Default is false
#AllowFifo=true
# Whether it is allowed to abort active sessions when shutting down the
# system via the global command socket.
# Default is true
#AllowFifoNow=false
# The boot manager KDM should use for offering boot options in the
# shutdown dialog.
# "None" - no boot manager
# "Grub" - Grub boot manager
# "Lilo" - Lilo boot manager (Linux on i386 & x86-64 only)
# Default is None
#BootManager=Grub

# Rough estimations about how many seconds KDM will spend at most on
# - opening a connection to the X-server (OpenTime) if the attempt
# - times out: OpenTimeout
# - is refused: OpenRepeat * OpenDelay
# - starting a local X-server (ServerTime):
# ServerAttempts * (ServerTimeout + OpenDelay)
# - starting a display:
# - local display: ServerTime + OpenTime
# - foreign display: StartAttempts * OpenTime
# - XDMCP display: OpenTime (repeated indefinitely by client)

# Core config for all displays
[X-*-Core]
# How long to wait before retrying to connect a display.
# Default is 15
#OpenDelay=15
# How long to wait before timing out a display connection attempt.
# Default is 120
#OpenTimeout=120
# How many connection attempts to make during a start attempt. Note that
# a timeout aborts the entire start attempt.
# Default is 5
#OpenRepeat=5
# Try at most that many times to start a display. If this fails, the display
# is disabled.
# Default is 4
#StartAttempts=4
# Ping remote display every that many minutes.
# Default is 5
#PingInterval=5
# Wait for a Pong that many minutes.
# Default is 5
#PingTimeout=5
# The name of this X-server's Xauth file.
# If empty, a random name in the AuthDir directory will be used.
# Default is ""
#AuthFile=
# Specify a file with X-resources for the greeter, chooser and background.
# The KDE frontend does not use this file, so you do not need it unless you
# use another background generator than krootimage.
# Default is ""
#Resources=
# The xrdb program to use to read the above specified recources.
# Subject to word splitting.
# Default is "/usr/bin/xrdb"
#Xrdb=
# A program to run before the greeter is shown. Can be used to start an
# xconsole or an alternative background generator. Subject to word splitting.
# Default is ""
Setup=/etc/kde4/kdm/Xsetup
# A program to run before a user session starts. Subject to word splitting.
# Default is ""
Startup=/etc/kde4/kdm/Xstartup
# A program to run after a user session exits. Subject to word splitting.
# Default is ""
Reset=/etc/kde4/kdm/Xreset
# The program which is run as the user which logs in. It is supposed to
# interpret the session argument (see SessionsDirs) and start an appropriate
# session according to it. Subject to word splitting.
# Default is "/usr/bin/xterm -ls -T"
Session=/etc/kde4/kdm/Xsession
# The program to run if Session fails.
# Default is "/usr/bin/xterm"
#FailsafeClient=
# The PATH for the Session program.
# Default is "/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games"
#UserPath=
# The PATH for Setup, Startup and Reset, etc.
# Default is "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
#SystemPath=
# The default system shell.
# Default is "/bin/sh"
#SystemShell=/bin/bash
# Where to put the user's X-server authorization file if ~/.Xauthority
# cannot be created.
# Default is "/tmp"
#UserAuthDir=
# If true, UserAuthDir will be used unconditionally.
# Default is false
#ForceUserAuthDir=true
# Whether to automatically restart sessions after X-server crashes.
# Note that enabling this makes circumventing screen lockers other than
# KDE's built-in one possible!
# Default is false
#AutoReLogin=true
# Allow root logins?
# Default is true
AllowRootLogin=false
# Allow to log in, when user has set an empty password?
# Default is true
AllowNullPasswd=false
# Who is allowed to shut down the system. This applies both to the
# greeter and to the command sockets.
# "None" - no "Shutdown..." menu entry is shown at all
# "Root" - the root password must be entered to shut down
# "All" - everybody can shut down the machine
# Default is All
AllowShutdown=Root
# Who is allowed to abort active sessions when shutting down.
# "None" - no forced shutdown is allowed at all
# "Root" - the root password must be entered to shut down forcibly
# "All" - everybody can shut down the machine forcibly
# Default is All
#AllowSdForceNow=Root
# The default choice for the shutdown condition/timing.
# "Schedule" - shut down after all active sessions exit (possibly at once)
# "TryNow" - shut down, if no active sessions are open; otherwise, do nothing
# "ForceNow" - shut down unconditionally
# Default is Schedule
#DefaultSdMode=ForceNow
# How to offer shutdown scheduling options:
# "Never" - not at all
# "Optional" - as a button in the simple shutdown dialogs
# "Always" - instead of the simple shutdown dialogs
# Default is Never
#ScheduledSd=Optional
# The directories containing session type definitions in .desktop format,
# ordered by falling priority.
# Default is "/usr/share/xsessions,/var/lib/menu-xdg/xsessions,/usr/share/apps/kdm/sessions"
#SessionsDirs=/usr/share/xsessions,/var/lib/menu-xdg/xsessions,/usr/share/apps/kdm/sessions
# The file (relative to $HOME) to redirect the session output to. The
# following character pairs are replaced:
# - %d -> current display
# - %u -> current user
# - %r -> empty at first. See below.
# - %% -> a single %
# When the constructed filename cannot be used safely and the specification
# contains %<stuff>r, other names will be tried - this time expanding %<stuff>r
# to <stuff> followed by a random number.
# Default is ".xsession-errors"
ClientLogFile=.xsession-errors-%d
# Fallback when ClientLogFile cannot be used. The same expansions are
# supported. DO NOT use relative paths here.
# Default is "/tmp/xerr-%u-%d%-r"
#ClientLogFallback=/var/log/xsession-errors/%u-%d%-r
# Whether KDM's built-in utmp/wtmp/lastlog registration should be used.
# Default is false
#UseSessReg=true

# Greeter config for all displays
[X-*-Greeter]
# Specify the widget style for the greeter. Empty means to use the
# built-in default which currently is "Oxygen-air".
# Default is ""
#GUIStyle=Plastique
# Specify the widget color scheme for the greeter. Empty means to use the
# built-in default which currently is "Oxygen-air".
# Default is ""
#ColorScheme=MidnightMeadow
# What should be shown in the greeter's logo are:
# "None" - nothing
# "Logo" - the image specified by LogoPixmap
# "Clock" - a neat analog clock
# Default is Clock
LogoArea=Logo
# The image to show when LogoArea=Logo.
# Default is ""
LogoPixmap=/usr/share/kde4/apps/kdm/pics/kdelogo.png
# The relative coordinates (X,Y in percent) of the center of the greeter.
# Default is "50,50"
#GreeterPos=30,40
# The screen the greeter should be displayed on in multi-headed and Xinerama
# setups. The numbering starts with 0. For Xinerama, it corresponds to the
# listing order in the active ServerLayout section of XF86Config; -1 means
# to use the upper-left screen, -2 means to use the upper-right screen.
# Default is 0
#GreeterScreen=-1
# The headline in the greeter. The following character pairs are replaced:
# - %d -> current display
# - %h -> host name, possibly with domain name
# - %n -> node name, most probably the host name without domain name
# - %s -> the operating system
# - %r -> the operating system's version
# - %m -> the machine (hardware) type
# - %% -> a single %
# Default is "Welcome to Kubuntu at %n"
#GreetString=Welcome to Kubuntu at %n
# Whether the fonts used in the greeter should be antialiased.
# Default is false
#AntiAliasing=true
# The font for the greeter headline.
# Default is "Serif,20,bold"
#GreetFont=Serif,20,5,0,50,0
# The normal font used in the greeter.
# Default is "Sans Serif,10"
#StdFont=Sans Serif,10,5,0,50,0
# The font used for the "Login Failed" message.
# Default is "Sans Serif,10,bold"
#FailFont=Sans Serif,10,5,0,75,0
# What to do with the Num Lock modifier for the time the greeter is running:
# "Off" - turn off
# "On" - turn on
# "Keep" - do not change the state
# Default is Keep
#NumLock=Off
# Language and locale to use in the greeter, encoded like $LANGUAGE.
# If empty, the settings from the environment are used.
# Default is ""
#Language=de_DE
# Enable autocompletion in the username line edit.
# Default is false
#UserCompletion=true
# Enable user list (names along with images) in the greeter.
# Default is true
#UserList=false
# User selection for UserCompletion and UserList:
# "NotHidden" - all users except those listed in HiddenUsers
# "Selected" - only the users listed in SelectedUsers
# Default is NotHidden
#ShowUsers=Selected
# For ShowUsers=Selected. @<group> means all users in that group.
# Default is ""
#SelectedUsers=root,johndoe
# For ShowUsers=NotHidden. @<group> means all users in that group.
# Default is ""
#HiddenUsers=root
# Special case of HiddenUsers: users with a non-zero UID less than this number
# will not be shown as well.
# Default is 0
MinShowUID=1000
# Complement to MinShowUID: users with a UID greater than this number will
# not be shown as well.
# Default is 65535
MaxShowUID=29999
# If false, the users are listed in the order they appear in /etc/passwd.
# If true, they are sorted alphabetically.
# Default is true
#SortUsers=false
# Specify, where the users' pictures should be taken from.
# "AdminOnly" - from <FaceDir>/$USER.face[.icon]
# "PreferAdmin" - prefer <FaceDir>, fallback on $HOME
# "PreferUser" - ... and the other way round
# "UserOnly" - from the user's $HOME/.face[.icon]
# Default is AdminOnly
#FaceSource=PreferUser
# The directory containing the user images if FaceSource is not UserOnly.
# Default is "/usr/share/kde4/apps/kdm/faces"
#FaceDir=/usr/share/faces
# Specify, if/which user should be preselected for log in.
# "None" - do not preselect any user
# "Previous" - the user which successfully logged in last time
# "Default" - the user specified in the DefaultUser option
# Default is None
#PreselectUser=Previous
# If this is true, the password input line is focused automatically if
# a user is preselected.
# Default is false
#FocusPasswd=true
# If this is true, the entered password is echoed as bullets. Otherwise,
# no feedback is given at all.
# Default is true
#EchoPasswd=false
# If true, krootimage will be automatically started by KDM; otherwise, the
# Setup script should be used to setup the background.
# Default is true
#UseBackground=false
# The configuration file to be used by krootimage.
# Default is "/etc/kde4/kdm/backgroundrc"
#BackgroundCfg=
# Whether to grab keyboard and mouse while the greeter is visible. Grabs
# may improve security, but make on-screen keyboards, etc. unusable.
# "Never" - never grab
# "IfNoAuth" - grab if the display requires no X authorization
# "Always" - always grab
# Default is IfNoAuth
#GrabInput=Always
# Hold the X-server grabbed the whole time the greeter is visible. This
# may be more secure, but it will disable any background and other
# X-clients started from the Setup script.
# Default is false
#GrabServer=true
# How many seconds to wait for grab to succeed.
# Default is 3
#GrabTimeout=3
# Warn, if display has no X-authorization (local auth cannot be created,
# XDMCP display wants no auth, or display is foreign from StaticServers).
# Default is true
#AuthComplain=false
# Random seed for forging saved session types, etc. of unknown users.
# This value should be random but constant across the login domain.
# Default is 0
#ForgingSeed=0
# Specify conversation plugins for the login dialog. Each plugin can be
# specified as a base name (which expands to $kde_modulesdir/kgreet_$base)
# or as a full pathname.
# Default is "classic"
#PluginsLogin=sign
# Same as PluginsLogin, but for the shutdown dialog.
# Default is "classic"
#PluginsShutdown=modern
# A list of options of the form Key=Value. The conversation plugins can query
# these settings; it is up to them what possible keys are.
# Default is ""
#PluginOptions=SomeKey=randomvalue,Foo=bar
# Show the "Console Login" action in the greeter (if ServerTTY/ConsoleTTYs
# is configured).
# Default is true
#AllowConsole=false
# A program to run while the greeter is visible. It is supposed to preload
# as much as possible of the session that is going to be started (most
# probably).
# Default is ""
Preloader=/usr/bin/preloadkde
# Whether the greeter should be themed.
# Default is false
UseTheme=true
# The theme to use for the greeter. Can point to either a directory or an XML
# file.
# Default is ""
Theme=/usr/share/kde4/apps/kdm/themes/ethais

# Core config for local displays
[X-:*-Core]
# How often to try to run the X-server. Running includes executing it and
# waiting for it to come up.
# Default is 1
#ServerAttempts=1
# How long to wait for a local X-server to come up.
# Default is 15
#ServerTimeout=15
# The command line to start the X-server, without display number and VT spec.
# This string is subject to word splitting.
# Default is "/usr/bin/X"
ServerCmd=/usr/bin/X
# Additional arguments for the X-servers for local sessions.
# This string is subject to word splitting.
# Default is ""
ServerArgsLocal=-nr -nolisten tcp
# Additional arguments for the X-servers for remote sessions.
# This string is subject to word splitting.
# Default is ""
#ServerArgsRemote=
# Restart instead of resetting the local X-server after session exit.
# Use it if the server leaks memory etc.
# Default is false
#TerminateServer=true
# The signal needed to reset the local X-server.
# Default is 1 (SIGHUP)
#ResetSignal=1
# The signal needed to terminate the local X-server.
# Default is 15 (SIGTERM)
#TermSignal=15
# Create X-authorizations for local displays.
# Default is true
#Authorize=false
# Which X-authorization mechanisms should be used.
# Default is "MIT-MAGIC-COOKIE-1"
#AuthNames=
# Need to reset the X-server to make it read initial Xauth file.
# Default is false
#ResetForAuth=true
# See above
AllowNullPasswd=true
# See above
AllowShutdown=All
# Enable password-less logins on this display. USE WITH EXTREME CARE!
# Default is false
#NoPassEnable=true
# The users that do not need to provide a password to log in. NEVER list root!
# "*" means all non-root users. @<group> means all users in that group.
# Default is ""
#NoPassUsers=fred,ethel

# Greeter config for local displays
[X-:*-Greeter]
# See above
PreselectUser=Previous
# See above
FocusPasswd=true
# Specify whether the greeter of local displays should start up in host chooser
# (remote) or login (local) mode and whether it is allowed to switch to the
# other mode.
# "LocalOnly" - only local login possible
# "DefaultLocal" - start up in local mode, but allow switching to remote mode
# "DefaultRemote" - ... and the other way round
# "RemoteOnly" - only choice of remote host possible
# Default is LocalOnly
LoginMode=DefaultLocal
# A list of hosts to be automatically added to the remote login menu. The
# special name "*" means broadcast.
# Default is "*"
#ChooserHosts=*,ugly,sky,dino,kiste.local,login.cr ap.com
# Show the "Restart X Server"/"Close Connection" action in the greeter.
# Default is true
AllowClose=true

# Core config for 1st local display
[X-:0-Core]
# The VT the X-server should run on; auto-assign if zero, don't assign if -1.
# Better leave it zero and use ServerVTs.
# Default is 0
#ServerVT=7
# Enable automatic login. USE WITH EXTREME CARE!
# Default is false
#AutoLoginEnable=true
# If true, auto-login after logout. If false, auto-login is performed only
# when a display session starts up.
# Default is false
#AutoLoginAgain=true
# The delay in seconds before automatic login kicks in.
# Default is 0
#AutoLoginDelay=10
# The user to log in automatically. NEVER specify root!
# Default is ""
#AutoLoginUser=fred
# The password for the user to log in automatically. This is NOT required
# unless the user is logged into a NIS or Kerberos domain. If you use this
# option, you should "chmod 600 kdmrc" for obvious reasons.
# Default is ""
#AutoLoginPass=secret!
# Immediately lock the automatically started session. This works only with
# KDE sessions.
# Default is false
#AutoLoginLocked=true
# See above
ClientLogFile=.xsession-errors
# The command line to start the X-server, without display number and VT spec.
# This string is subject to word splitting.
# Default is "/usr/bin/X"
ServerCmd=/usr/bin/X
# Additional arguments for the X-servers for local sessions.
# This string is subject to word splitting.
# Default is ""
ServerArgsLocal=:0 vt07 -audit 0 -isolateDevice PCI:0:13:0 -nolisten tcp -layout Layout0

# Greeter config for 1st local display
[X-:0-Greeter]
# See above
#PreselectUser=Default
# The user to preselect if PreselectUser=Default.
# Default is ""
#DefaultUser=johndoe

[X-:1-Core]
# The VT the X-server should run on; auto-assign if zero, don't assign if -1.
# Better leave it zero and use ServerVTs.
# Default is 0
#ServerVT=7
# Enable automatic login. USE WITH EXTREME CARE!
# Default is false
#AutoLoginEnable=true
# If true, auto-login after logout. If false, auto-login is performed only
# when a display session starts up.
# Default is false
#AutoLoginAgain=true
# The delay in seconds before automatic login kicks in.
# Default is 0
#AutoLoginDelay=10
# The user to log in automatically. NEVER specify root!
# Default is ""
#AutoLoginUser=fred
# The password for the user to log in automatically. This is NOT required
# unless the user is logged into a NIS or Kerberos domain. If you use this
# option, you should "chmod 600 kdmrc" for obvious reasons.
# Default is ""
#AutoLoginPass=secret!
# Immediately lock the automatically started session. This works only with
# KDE sessions.
# Default is false
#AutoLoginLocked=true
# See above
ClientLogFile=.xsession-errors
ServerCmd=/usr/bin/X
ServerArgsLocal=:1 vt08 -audit 0 -sharevts -isolateDevice PCI:2:0:0 -nolisten tcp -layout Layout1
```

I think that should do it.  If you run into trouble, please again post the Xorg.0.log and Xorg.1.log.

Good Luck!

---

### Post by Fafler on 2010-10-14
Did you make it work?

---

### Post by leodp on 2010-11-10
Hi warrior,
I'm trying multiseatx too at the moment.
Along the way I have found a quick solution, which is differen but may help you in the meantime: have a single session with two pointers (and mouses and keyboards).
Check this:
[https://wiki.ubuntu.com/X/MPX](https://wiki.ubuntu.com/X/MPX)

Ciao,
leonardo

---

### Post by larryjoe701 on 2010-11-11
> **leodp said:**
> Hi warrior,
I'm trying multiseatx too at the moment.
Along the way I have found a quick solution, which is differen but may help you in the meantime: have a single session with two pointers (and mouses and keyboards).
Check this:
[https://wiki.ubuntu.com/X/MPX](https://wiki.ubuntu.com/X/MPX)

Ciao,
leonardo

Hey Leodp,

That sounds like an interesting solution.  I might use it for other purposes, thanks for the tip.

Is there any way to constrain the pointers, so have multiple focus points for keyboard entry?  Either way, it's a neat feature.

Thanks,
Tim

---

### Post by leodp on 2010-11-16
> **larryjoe701 said:**
> Hey Leodp,

That sounds like an interesting solution.  I might use it for other purposes, thanks for the tip.

Is there any way to constrain the pointers, so have multiple focus points for keyboard entry?  Either way, it's a neat feature.

Thanks,
Tim


Hi larryjoe,

there seems to be a solution:
[http://ubuntuforums.org/showthread.php?t=1181014](http://ubuntuforums.org/showthread.php?t=1181014)
I have not tried it yet thou. Will need some more days to find some spare time.

BR
Leodp

---

