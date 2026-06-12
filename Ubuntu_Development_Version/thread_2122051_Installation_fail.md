---
title: "Installation fail"
date: 2013-03-03
forum: Ubuntu Development Version
---

### Post by Bradley129 on 2013-03-03
Sorry for bothoring the community with another one of Bradley's dumb questions haha but I wanted to test 13.04 do some testing provide some devolopers some tests and logs but for the life of me I can't get it install well I boot from USB use ran to edit add the nomodeset like I always have to do now press enter (to boot it from USB) it shows the Ubuntu slash screen like normal the little.menu dots is loading then all suddenly it freezes the little dots freeze white and there's a little Spinny cirlse thing in the top right corner and it never loads any ideas I would love to get this working?!

---

### Post by ikt on 2013-03-04
> **Bradley129 said:**
> Sorry for bothoring the community with another one of Bradley's dumb questions haha

The only dumb question is one not asked :)

> **Bradley129 said:**
> but I wanted to test 13.04 do some testing provide some devolopers some tests and logs but for the life of me I can't get it install well I boot from USB use ran to edit add the nomodeset like I always have to do now press enter (to boot it from USB) it shows the Ubuntu slash screen like normal the little.menu dots is loading then all suddenly it freezes the little dots freeze white and there's a little Spinny cirlse thing in the top right corner and it never loads any ideas I would love to get this working?!

What hardware are you trying to install it on and what iso image did you download?

---

### Post by grahammechanical on 2013-03-04
I sometimes have to put irqpoll into the boot paramenters. Other times I had to tick all the F6 options or some combination of them. Regards.

---

### Post by ibjsb4 on 2013-03-04
I have had this problem in the past and found that just doing a "release-upgrade -d" from the previous version to be the easy way out.

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

---

### Post by ventrical on 2013-03-04
Appears as if it is an obsoleted graphics card - no way to tell until we get some lspci info.

---

### Post by Bradley129 on 2013-03-04
Its a hp dv6 it has a a4-3305m Dual core Proccesor which does support pae and a radeon 6480g GPU 4gb of ddr3 RAM and everything else is based off from the amd Hudson culture I'm currently running Ubuntu 12.04.2 and its runs fine I was able to boot up install graphics drivers no problem okay 3d games everything so what seems to be the problem with 13.04?

---

### Post by Bradley129 on 2013-03-04
> **ibjsb4 said:**
> I have had this problem in the past and found that just doing a "release-upgrade -d" from the previous version to be the easy way out.

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

But if I do that won't I risk my fallback 12.04 install?

---

### Post by ventrical on 2013-03-04
My next questions are:

1. Is it a zsynced iso or a daily raw image that you are using?
2. is it 64bit or 32 bit iso?
3. I assume VGA pallete snoop is off in BIOS?


  I have 3 radeon systems and I have seen what you have described. I doubt you can get to terminal from where you are at.

if you are using 64bit iso then try 32bit , or , if you are using 32bit (and your system is 64bit capable) then try 64bit iso.

---

### Post by ventrical on 2013-03-04
> **Bradley129 said:**
> But if I do that won't I risk my fallback 12.04 install?

I assume that this is correct. Unless you have a btrfs system format.

---

### Post by Budovi on 2013-03-04
You could install fresh 12.10 alongside your 12.04 and upgrade that safely :)

or I did not get something? :confused:

---

### Post by Bradley129 on 2013-03-04
> **ventrical said:**
> My next questions are:

1. Is it a zsynced iso or a daily raw image that you are using?
2. is it 64bit or 32 bit iso?
3. I assume VGA pallete snoop is off in BIOS?


  I have 3 radeon systems and I have seen what you have described. I doubt you can get to terminal from where you are at.

if you are using 64bit iso then try 32bit , or , if you are using 32bit (and your system is 64bit capable) then try 64bit iso.

1. Raw iso from here:[http://cdimage.ubuntu.com/daily-live/20130301/](http://cdimage.ubuntu.com/daily-live/20130301/)
2.its a 64bit computer so im using the 64bit version my 12.04 is on amd64.iso so thats what im using for 13.04
3. I do not belive i have that option in bios about the only option have is to enable amd64 virtualazion which i have enabled where would i find this vga option? 

one extra detail: my computer didnt come pre installed with windows 8 so no secure boot or anything just good old bios so that isnt causing issues either

---

### Post by ventrical on 2013-03-04
> **Bradley129 said:**
> 1. Raw iso from here:[http://cdimage.ubuntu.com/daily-live/20130301/](http://cdimage.ubuntu.com/daily-live/20130301/)
2.its a 64bit computer so im using the 64bit version my 12.04 is on amd64.iso so thats what im using for 13.04
3. I do not belive i have that option in bios about the only option have is to enable amd64 virtualazion which i have enabled where would i find this vga option? 

one extra detail: my computer didnt come pre installed with windows 8 so no secure boot or anything just good old bios so that isnt causing issues either

I am zsyncing that 64bit iso right  now to see if I can replicate your symptooms on my AMD opteron dual core.

 I'll be back.

 i am assuming it is usual bugs. There have been a lot of users who had probs with 64bit.

---

### Post by Bradley129 on 2013-03-04
> **ventrical said:**
> I am zsyncing that 64bit iso right  now to see if I can replicate your symptooms on my AMD opteron dual core.

 I'll be back.

 i am assuming it is usual bugs. There have been a lot of users who had probs with 64bit.

Ahh i cant thank you ehnough this is one of the best forums around allways helpfull answers and no fussing about whoes a noob :p. Its like the old fascinate community on xda everybody knows everybody and were all freinds :):KS

---

### Post by ventrical on 2013-03-04
I just zsynced the daily  amd64bit and it works just great on:

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:06.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
ubuntu@ubuntu:~$ 

```

and now I will try my ATi graphics card.

Works great with nvidia.

Be back.

---

### Post by ventrical on 2013-03-04
I was able to boot with the daily-live session. ( I am typing from there now). The Ati drivers seem to be in really bad shape for 64bit - but 32bit works great.

Try:

32bit iso

or

re-burn your USB stick with 'Discard on shutdown..' options if you are using Startup Disk Creator.

or 

wai until they get this thing fixed. I think it had to do with a Gnome-Daemon-Setting, but could be much more.

```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (Internal gfx)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI1)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI2)
00:13.3 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI3)
00:13.4 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB (OHCI4)
00:13.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB600 IDE
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690 [Radeon X1200 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:06.0 Ethernet cont


```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.8.0-9-generic #18-Ubuntu SMP Thu Feb 28 17:02:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
ubuntu@ubuntu:~$ 


But I zsynced that just an hour ago ..

---

### Post by ventrical on 2013-03-04
ok.. back to normal here :)

On the Ati bootup with raring-desktop-amd64.iso daily the Ubuntu logo started to jump around, almost as if it was like the old Windows XP screensaver (I kid you not!!). There was also some major flickering during the Plymouth routine. Unity presented a distorted background on the dash but I was still able to work through it. Cariboo907 started a thread on this a while back , about the AMD processors AND 64bit Ubuntu. Looks like it is still really touchy.

---

### Post by Bradley129 on 2013-03-04
Ahh I'll guees I'll wait till the issues are fixed they should be by the official release around next month huh?

---

### Post by ventrical on 2013-03-04
With Mir, Wayland and compiz .. anything is possible ! :)

---

