---
title: "KDE is buggy in Ubuntu 12.10 64 bit Beta 2"
date: 2012-10-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Welly Wu on 2012-10-12
I installed kubuntu-desktop and kde-full on Ubuntu 12.10 64 bit Beta 2 and I noticed a lot of problems. It seems that the biggest problem is the graphics. I am getting various graphics glitches such as when I created a LibreOffice Writer document and I saved and closed the file. Then, I reopened the file and I can not see my document in KDE. It works in Ubuntu Unity. Another graphics glitch that I noticed is that there are squiggly lines all over the KDE Plasma desktop whenever I switch windows. They appear randomly and they don't seem to go away unless I launch a new application with a new window which gives me a brand new graphics glitch.

I am wondering if anyone else is experiencing similar problems and how you have solved these types of problems.

Thank you.

---

### Post by PaulW2U on 2012-10-12
> **Welly Wu said:**
> I am wondering if anyone else is experiencing similar problems and how you have solved these types of problems.

Sorry Welly Wu, no problems here and I've not seen any reports of similar problems either.

I've been running Kubuntu 12.10 64-bit since June and it's been rock solid, hardly a bug to be found. I think your problems are either hardware related or are a result of installing KDE on top of Ubuntu.

---

### Post by Welly Wu on 2012-10-12
According to the Ubuntu System Settings -> Details information, my GPU is not installed. It should list Intel HD Graphics 4000. However, it does not. The System76 driver is not installed because I am using Ubuntu 12.10 64 bit Release Candidate. So, I am hoping that this is the source of my problems and it will be resolved on October 18th, 2012 when Ubuntu 12.10 64 bit is officially released.

KDE is not working properly for me. The graphics are not displaying correctly.

I will continue to use Software Updater daily and I will see if I can install the System76 device driver next Thursday. If it installs correctly, then I think that it will solve the problem that I am having right now.

---

### Post by robtygart on 2012-10-12
I think your correct about the graphics driver 

Please post the output of this 

```
lspci -nnk | grep -iA2 vga
```

---

### Post by Welly Wu on 2012-10-12
wellywu@System76:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
    Kernel driver in use: i915
wellywu@System76:~$ 

What does this mean? Am I using the Intel HD Graphics 4000?

---

### Post by robtygart on 2012-10-12
> I will continue to use Software Updater daily and I will see if I can install the System76 device driver next Thursday. If it installs correctly, then I think that it will solve the problem that I am having right now.

Question? 

You are looking in "Additional Drivers" correct?

---

### Post by Welly Wu on 2012-10-12
My Additional Drivers list is empty. Ubuntu says that it is not using any proprietary drivers which tells me that the System76 device driver is not installed on Ubuntu 12.10 64 bit Release Candidate yet.

This must be the source of my problems with KDE right now.

---

### Post by robtygart on 2012-10-12
I am confused! This is what mine looks like

```
rob@mobile:~$ lspci -nnk | grep -iA2 vga
00:12.0 VGA compatible controller [0300]: NVIDIA Corporation C67 [GeForce 7150M / nForce 630M] [10de:0531] (rev a2)
        Subsystem: Hewlett-Packard Company Device [103c:30cf]
        Kernel driver in use: nvidia
rob@mobile:~$ 

```
The part I am looking for on yours
[GeForce 7150M / nForce 630M] (Replaced with your card)

```
wellywu@System76:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
Subsystem: CLEVO/KAPOK Computer Device [1558:0240]
Kernel driver in use: i915
wellywu@System76:~$ 
```

Also your using the i915 driver

> This driver provides support for the Intel i8xx and i9xx family of chipsets, including i810, i815, i830, i845, i855, i865, i915, and i945 series chips.

This package provides debugging symbols for this Xorg X driver.

Canonical does not provide updates for xserver-xorg-video-intel-dbg. Some updates may be provided by the Ubuntu community.

---

### Post by Welly Wu on 2012-10-12
I will ask System76 directly to solve this problem. Thanks for your help so far.

---

### Post by bra|10n on 2012-10-12
I vote this as the best thread title of the year :KS

A bit like saying it's dark at midnight without the lights on...
:popcorn:

---

### Post by cariboo on 2012-10-13
To help the op along a bit in his quest, there are no closed source Intel drivers, so looking in Additional Drivers, isn't going to help. The drivers you get included in the kernel are all there is.

---

### Post by Welly Wu on 2012-10-13
Thank you for that bit of information.

Why does Ubuntu 12.10 64 bit say that my graphics driver is unknown? When I used Ubuntu 12.04.1 64 bit LTS, it said Intel HD 4000.

Could this be due to the fact that I am using Beta 2 or Release Candidate version?

Please answer this question if possible. Thank you.

---

### Post by Welly Wu on 2012-10-13
sudo apt-get install mesa-utils

Now, Ubuntu says that I have Intel Ivybridge Mobile and standard experience.

I will test KDE soon.

---

### Post by Welly Wu on 2012-10-13
Installing mesa-utils seems to have solved my graphics problems in KDE. I am still testing it, but I am not seeing any of the same graphics glitches anymore after I installed mesa-utils and I rebooted my System76 PC.

---

### Post by ELD on 2012-10-13
Are you fully up to date? I had to switch to xrender rather than opengl in the compositing settings to get rid of graphical corruption.

---

### Post by Welly Wu on 2012-10-13
I am using KDE 4.9.2 and QT 4.8.3. Ubuntu 12.10 64 bit Release Candidate is fully up to date to this minute. I use OpenGL compositing type and QT graphics system to native instead of render. This seems to have solved most of my graphics corruption issues so far. I am still testing KDE 4.9.2 so I will update this as I go along.

---

### Post by BigSilly on 2012-10-13
You're using KDE installed on Ubuntu 12.10? You mjight be better off using Kubuntu 12.10 directly. I've just installed the latest daily myself, and have to say it's solid, solid, solid. Really great release I think. KDE is simply stunning, and Kubuntu does such an amazing job with it imho.

---

### Post by buzzmandt on 2012-10-13
my kde kubuntu 12.10 is running fantastic, intel graphics here too.  in case this helps
```
buzzmandt@buzzmandt-main:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
        Subsystem: Hewlett-Packard Company Device [103c:360b]
        Kernel driver in use: i915
buzzmandt@buzzmandt-main:~$ 

```

---

### Post by oldos2er on 2012-10-13
> **BigSilly said:**
> I've just installed the latest daily myself, and have to say it's solid, solid, solid. Really great release I think. KDE is simply stunning, and Kubuntu does such an amazing job with it imho.

I have to agree, Kubuntu 12.10's been working extremely well for me. I have an Nvidia card though, a GT218.

---

### Post by BigSilly on 2012-10-13
> **oldos2er said:**
> I have to agree, Kubuntu 12.10's been working extremely well for me. I have an Nvidia card though, a GT218.

Yeah me too. A 9800GT. All good. I had to go into system settings and set up Plymouth, otherwise I was just getting a low-res text backdrop when booting. Other than than, most impressive.

---

### Post by ventrical on 2012-10-13
You can get great compiz  effects on older cards in the *kubuntu* package as well as if you download the KDE desktop, however, if you had originally installed -ubuntu-unity- then you will not get the old video graphics adapters enabled. Why? I don't know but Kubuntu is the way to go for older graphics cards with animated effects.

```

ventrical@ventrical-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
ventrical@ventrical-desktop:~$ 



```

---

### Post by kamranm1200 on 2012-10-13
If you are having this issue, try going to the [Ubuntu 12.10 RC Download site]("http://iso.qa.ubuntu.com/qatracker/milestones/240/builds/25701/downloads")

---

### Post by jerrylamos on 2012-10-15
> **kamranm1200 said:**
> If you are having this issue, try going to the [Ubuntu 12.10 RC Download site]("http://iso.qa.ubuntu.com/qatracker/milestones/240/builds/25701/downloads")

I had a lot of bugs and anklebiters on Beta 2, both 32 bit and 64 bit.  The RC (really I'm using yesterday's daily build) is much cleaner.

---

