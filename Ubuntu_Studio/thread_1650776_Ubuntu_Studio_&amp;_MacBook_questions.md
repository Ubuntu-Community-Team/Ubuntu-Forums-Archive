---
title: "Ubuntu Studio &amp; MacBook questions"
date: 2010-12-22
forum: Ubuntu Studio
---

### Post by FreDeas on 2010-12-22
Hello,

I installed ubuntu-studio on a black MacBook 2.1

I' ve been experiencing problems with the wi-fi - I did a search in the forum and found out this is common but found no way to address this..

I had no wifi icon in the panel bar, I installed the network manager and then I had no wifi icon & neither wired access as well - I uninstalled it to get back to the previous stage with wifi

I read somewhere that there is a conflict with ubuntu studio kernel and network manager 

I was also wandering how can I change the keyboard shortcuts - they are very confusing at this point - I know there is a relevant manager in the system/preferences but it only has options for a bunch of commands, what about copy/paste for example ?? 

then,

I was wandering whether ubuntu studio is really what I need or maybe I should use ubuntu instead ?? 

I am a professional working mainly in the fields of exploratory-academic sound-art staff, so I mostly use supercollider, processing and the likes - I rarely record staff or use midi/ladspa and similar

is there any gain for me to use ubuntu-studio or should I use ubuntu instead ?? I tried Apodio - that is obviously based on ubuntu rather than ubuntu studio, right? - and I had almost everything set-up WITH wifi access out of the box.. 

that said 

thx in advance

m

---

### Post by Joe of loath on 2010-12-22
I think the macbook uses a broadcom wifi chip. Please post the output of 'lspci' from the terminal.

---

### Post by FreDeas on 2010-12-22
marinosk@marinosk-black:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)

---

### Post by Joe of loath on 2010-12-22
Oh, it's an atheros.

The method I used to get mine working was to update via a wired network, then install the package 'linux-kernel-headers'. Then reboot, and you SHOULD have wireless.

---

### Post by FreDeas on 2010-12-22
I did sudo apt-get install linux-kernel-headers and it posted that I should use instead linux-libc-dev that is already in the newest version..

it also suggested I should run apt-get autoremove - and I did

I can see the BlueTooth icon in the panel but not the wireless one I tried to enable the wifi in Network Settings, but I cannot switch it on... should I try to install network manager again ??

---

### Post by kroon78 on 2010-12-23
this is a long shot, i had to do it to my first laptop.  Neither the wifi or ethernet controllers worked by default.  I had to get the driver for the the wifi (broadcom) driver and compile it myself.  Worked great for over a year and then an update broke it.  This may be what you have to do with the Atheros chipset.

---

### Post by Pablo_F on 2010-12-24
Hi,

> I was also wandering how can I change the keyboard shortcuts - they are very confusing at this point - I know there is a relevant manager in the system/preferences but it only has options for a bunch of commands, what about copy/paste for example ?? 

There are several ways to do copy/paste. [Control-C] / [Ctrl-V] works except in the terminal, where [Ctrl-Shift-C] / [Ctrl-Shift-V] does the trick. That said, to copy/paste text to and from the terminal (or almost any other text editing field) you can use select-drop with the mouse. Just highlight text (by selecting it the normal way) and drop it somewhere else with the middle button. This is unintuitive at first but extremely fast and useful.

Back to the main question, 

> I am a professional working mainly in the fields of exploratory-academic sound-art staff, so I mostly use supercollider, processing and the likes - I rarely record staff or use midi/ladspa and similar

is there any gain for me to use ubuntu-studio or should I use ubuntu instead ?? I tried Apodio - that is obviously based on ubuntu rather than ubuntu studio, right? - and I had almost everything set-up WITH wifi access out of the box.. 

Ubuntustudio is ubuntu with a few tweaks, a theme and some packages installed out of the box. 

One of these tweaks has been a drawback for you and the others you don't need them. If any, add your user to the audio group.

As for the packages, US does not have a special repo, so you can install exactly the same software from the software center or synaptic.

My two cents: Use plain ubuntu and install what you need. It is a breeze with the software center. You could have overkilling desktop features but you can always disable some start-up applications if you wish.

Note that, as ubuntu is not a rolling distro, apps in the software center could be outdated. Install them normally but also check the official sites of the apps that matter to you. 

Cheers, Pablo

---

