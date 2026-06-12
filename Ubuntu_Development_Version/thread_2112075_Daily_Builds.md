---
title: "Daily Builds"
date: 2013-02-03
forum: Ubuntu Development Version
---

### Post by kuvanito on 2013-02-03
latest daily builds are dated 02-Feb-2013 both 32 and 64 bits are a disaster,neither one boots up to install.
not the usb created or the dvd burned.
i do this almost everyday to check if they work or not
real testing here

---

### Post by VinDSL on 2013-02-03
Hope you have a docking station (not pictured)...  :)

---

### Post by zika on 2013-02-04
> **VinDSL said:**
> Hope you have a docking station (not pictured)...  :)
I think I see a slot for HD in case front...
But, speaking of daily's: (16 wake hours/day)/(at least 6 HD and 8 FD I see)<(72 wake minutes/day )...

---

### Post by VinDSL on 2013-02-04
> **zika said:**
> I think I see a slot for HD in case front...

Oh, okay... I see.

I use a [Thermaltake BlacX]("http://www.hardwaresecrets.com/article/531") dock. You toss them in, like 8-track tapes.

Best invention since water!

His rig is more like a VHS recorder...  :D

---

### Post by grahammechanical on 2013-02-04
I am impressed. Your work area is so tidy. :)

I do not test ISO images daily but the Edubuntu 31 Jan ISO burned to USB was the first Raring ISO that would load a live session without needing changes to the boot parameters to by-pass being dumped to a Busybox prompt. It took me weeks to discover the right combination. I now have 'irqpoll' in my list of boot parameters to try.

I have not had a good experience with Raring ISO images at all this cycle.

Regards.

---

### Post by kuvanito on 2013-02-04
> **VinDSL said:**
> Hope you have a docking station (not pictured)...  :)

yeap i do
it's rigth at the front
i change hard drives like 8 track tapes
is an antec trayless bay.

---

### Post by kuvanito on 2013-02-04
Failed to load libutil.c32
Failed to load com32 file menu.32

I get this two errors and can not continue testing the latest builds 
this got something to to with the new syslinux 5.0 this file must be copied to the iso compilation in order for it to work.
no test today :(

---

### Post by ventrical on 2013-02-04
I have had only one incident of 'busybox' come up on generally 9 different machines. The iso's will either work, or they don't.  They are not as snappy as the Nov 22 releases.

  Not sure if I am doing anything different than anybody else. What I am doing is zsynching the i386 and amd64 daily's  on a Maveric Install (10.10) and I am using startup disk creator from maveric with the Option 'Discarded on shutdown unless you save them  elsewhere" on the USB and they are working most of the time. I just get bored because I thought there was going to be some new stuff, some showstoppers, punchy, twilry thingys ..  but it is still very very kewl Ubuntu Unity.  Just busy around here alot. Hope I can contribute more soon.

Thanks Kuvanito! Nice pic!

---

### Post by grahammechanical on 2013-02-05
I tried with today's ISO image (20130204) amd64 on a DVD. Here are the results

1) Live session fails = Busybox prompt.
2) acpi=off and irqpoll as boot parameter + Try Ubuntu = live session.
3) acpi=off and irqpoll as boot parameter + Install Ubuntu = Busybox prompt.
4) Install from live session works (once in live session that is).

---

### Post by kuvanito on 2013-02-05
just got back from work 2 hours ago
today's build 05-Feb-2013 64bit is Green Light GO!
all is working and well.
will report tomorrow again on the day's build :)

---

### Post by kuvanito on 2013-02-06
todays builds 32 and 64 bits work fine
i do test ubuntu to the xtreme and i have come to preffer 32bit over 64bit
on my rig 32bit runs faster and crash free,the other way around with 64bit
althou one of my favourite apps does not run in either bits (simple image reducer) :(

---

### Post by kuvanito on 2013-02-09
02/09/2013 @ 6:33 AM EDT
25 kb/s is the max download speed from the servers
thanks,no thanks
there will be no test for me today

---

### Post by ventrical on 2013-02-21
Yesterdays daily i386 is a complete fail. BusyBox then lock up across nvidia and Ati graphics platforms.

---

### Post by Budovi on 2013-02-21
Today's version 20130221 is available to download now. Built at 9:00...

---

### Post by kuvanito on 2013-02-21
thanks,i am downloading it right now.

---

### Post by startas on 2013-02-21
Well, i don't know what about ubuntu, but i tried many xubuntus daily images, and it isn't even booting live mode or installing... Firstly xubuntu logo appears, and then it just stucks with black screen and mouse pointer :D And depending on connected cables and hardware, i can get it to stuck at xubuntu logo screen :D

---

### Post by Budovi on 2013-02-21
New build released, 20130221.1, giving it another try (:

...also with [[COLOR=#000000]grahammechanical[/COLOR]]("http://ubuntuforums.org/member.php?u=1087323")'s advice [here]("http://ubuntuforums.org/showthread.php?p=12522175#post12522175"), thanks btw (:

---

### Post by grahammechanical on 2013-02-21
@Budovi

you might find as I have just found that build 20130221 needs all the F6 options checked in order to get to a live session. 

Regards.

---

### Post by startas on 2013-02-21
Well, it's almost useless to try any daily builds other then final release.

---

### Post by zika on 2013-02-21
> **startas said:**
> Well, it's almost useless to try any daily builds other then final release.And, still, we test them from the very first day final is released...
We use them as if we would use that released final to make new final even better...

---

### Post by Budovi on 2013-02-21
@zika: +1 (:

@grahammechanical: I'm actually able to launch live session without problem (20130221.1), problem is, that I ran install and it crashed so now I'm stuck on live session, not so comfortable :D

I raised a bug against ubiquity, but ... :D will see... Problems seems to be with localization, it crashed almost in the end and that screw me up... Maybe I could chroot and repair at least grub so I can use Windows and create new "live-USB" when released new build...

---

### Post by ventrical on 2013-02-21
> **grahammechanical said:**
> @Budovi

you might find as I have just found that build 20130221 needs all the F6 options checked in order to get to a live session. 

Regards.


 Oh.. I forgot about those. I thought they were not working either.

---

### Post by ventrical on 2013-02-23
> **grahammechanical said:**
> @Budovi

you might find as I have just found that build 20130221 needs all the F6 options checked in order to get to a live session. 

Regards.


  I zsynced raring-desktop-i386 (again), today!! and the result is just horrible. There is no 'punchy' no 'sexy' and no "effervessence". I did the F6 nomodeset and no acpi and it is still just like molases on the 'live' session. One can't really test it when it is in a useless state like this. I'll try my Intel based machine.

current machine:

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI-X Root Port
00:11.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce G210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:03.0 Ethernet controller: VIA Technologies, Inc. VT86C100A [Rhine] (rev 06)
ventrical@ventrical-desktop:~$ 

```

edit:

And then it works just fine on the Dell Dimension 3100!
```

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:02.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)
ubuntu@ubuntu:~


```

---

