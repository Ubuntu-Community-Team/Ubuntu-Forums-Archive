---
title: "HOWTO: Make your TI internal card reader work for you"
date: 2006-12-09
forum: Tutorials
---

### Post by ThrobbingBrain66 on 2006-12-09
[COLOR="Red"]A new card reader HOWTO for Hardy is in the works.  Stay tuned!

For now, I've included the original content of this thread as an attachment.[/COLOR]

---

### Post by halocaridina on 2006-12-11
ThrobbingBrain66,

Thanks a million.

Been trying for months to get my internal SD card reader to operate.

This HOWTO worked perfectly on a Toshiba M105-S3041 running an up-to-date Edgy system.

FYI, I also didn't need to load the modules (i.e., skipped the first step).

Cheers and thanks again!!

---

### Post by kwisatz on 2006-12-11
Thank you very much, this works fine on my HP Pavilion DV1067, the strange thing is that with Dapper my card-reader worked fine without any workaround...howewer now it works! 
Thank you again!

---

### Post by greyash99 on 2006-12-18
do you know if this will workd with my hp psc 1350 printer's built in card reader?

---

### Post by ThrobbingBrain66 on 2006-12-19
> **greyash99 said:**
> do you know if this will workd with my hp psc 1350 printer's built in card reader?

No, this won't work for a printer card reader.  Your printer is attached via USB, so the device won't show up when you issue the 'lspci' command.  Anyway, I think that would be controlled by the printer's driver.

---

### Post by galroth on 2006-12-21
No joy on my HP Pavilion zd8000.  I followed the directions exactly, and when I put the card in the reader, the blue light flickered once, and nothing came up on screen.

---

### Post by ThrobbingBrain66 on 2006-12-21
> **galroth said:**
> No joy on my HP Pavilion zd8000.  I followed the directions exactly, and when I put the card in the reader, the blue light flickered once, and nothing came up on screen.

What is the output of lspci?

---

### Post by galroth on 2006-12-21
```
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
```
I believe that is the relevant line.

---

### Post by ThrobbingBrain66 on 2006-12-21
Could you please post the last 10 lines of output of 'dmesg' (w/o the quotes).

---

### Post by galroth on 2006-12-21
Ah Ha!  It is detecting the card when I insert it.
```
tifm_7xx1: demand removing card from socket 2
tifm_7xx1: xd card detected in socket 2
tifm_7xx1: demand removing card from socket 2
tifm_7xx1: xd card detected in socket 2
```
I'm using an xD digital media card.  Now I just have to figure out how to mount that card.

---

### Post by ThrobbingBrain66 on 2006-12-21
When you have the card inserted, look around in /media or /dev for any files or folders contain the card's name.

Also, enter ```
sudo fdisk -l
``` and see if it lists your card there


For example, my fdisk output looks like this:
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         663     5325516   83  Linux
/dev/sda2             664       12096    91835572+  83  Linux
/dev/sda3           12097       12161      522112+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              21      167680     1005958+   6  FAT16

```

---

### Post by galroth on 2006-12-21
No changes in /media or /dev when I inserted the card, and my fdisk -l only showed my hard drive.

---

### Post by ThrobbingBrain66 on 2006-12-21
I'll do more research when I have some time.  Although I think you may have to wait until the tifm_xd module is implemented.  Have you tried an SD card at all?

---

### Post by galroth on 2006-12-21
Unfortunately, I don't have an SD card.  Thanks for all your help, though.  I look forward to being able to wipe Winblows from my laptop permanently.  :D

---

### Post by heffo_j on 2006-12-23
Thanks for the How To:

I've got the internal reader on my HPdv2000 working with the MMC/SD card but not the XD. Is this soemthing still in the development stage or is there are fix?

Regards
John

---

### Post by ThrobbingBrain66 on 2006-12-24
> **heffo_j said:**
> Thanks for the How To:

I've got the internal reader on my HPdv2000 working with the MMC/SD card but not the XD. Is this soemthing still in the development stage or is there are fix?

Regards
John

All the research I've done leads me to believe that the xD module is still in development, but I'm still looking around for a solution.

---

### Post by rcrook on 2006-12-24
Awesome,

Worked a charm.:)

Thanks:)

Randall.

---

### Post by chudder on 2006-12-28
I've tried the same thing and I get nothing at all, maybe I'm just not noticing something but nothing is happening so I don't think that is the case.

```
0000:07:06.2 Mass storage controller: Texas Instruments: Unknown device 803b

sudo setpci -s 07:06.2 4c.b=0x02 
```

---

### Post by ThrobbingBrain66 on 2006-12-28
> **chudder said:**
> I've tried the same thing and I get nothing at all, maybe I'm just not noticing something but nothing is happening so I don't think that is the case.

```
0000:07:06.2 Mass storage controller: Texas Instruments: Unknown device 803b

sudo setpci -s 07:06.2 4c.b=0x02 
```

what kind of card are you using?

---

### Post by chudder on 2006-12-28
> 
Originally Posted by chudder
[I]I've tried the same thing and I get nothing at all, maybe I'm just not noticing something but nothing is happening so I don't think that is the case.
[/I]

```

0000:07:06.2 Mass storage controller: Texas Instruments: Unknown device 803b 
sudo setpci -s 07:06.2 4c.b=0x02 
```

Posted by ThrobbingBrain66
*what kind of card are you using?* 

I'm using an SD card, I hope to also use Memory Stick but I remember you didn't mention that in the beginning, I just want to focus on the SD right now.  I don't know if this makes a difference but I'm in Dapper as well.  I haven't switched to Edgy because I got my wireless working and I don't want to potentially jeopardize that.

---

### Post by ThrobbingBrain66 on 2006-12-29
> **chudder said:**
> I'm using an SD card, I hope to also use Memory Stick but I remember you didn't mention that in the beginning, I just want to focus on the SD right now.  I don't know if this makes a difference but I'm in Dapper as well.  I haven't switched to Edgy because I got my wireless working and I don't want to potentially jeopardize that.

I was just about to ask that.  You will have to upgrade if you want your reader to work.  A few card readers worked under Dapper, but most had to wait until Edgy for card reader support.  When I first wrote the HOWTO, I mentioned that at the top of the post, I think I should add that again.

---

### Post by [knap] on 2006-12-29
Worked great in my Toshiba Sattelite A100-498. Thanks a lot. :D

---

### Post by eitan_a on 2006-12-29
on edgy...this doesn't work for me.

lscpi gives me..

08:03.0 CardBus bridge: Texas Instruments Unknown device 8039
08:03.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
08:03.2 Mass storage controller: Texas Instruments Unknown device 803b

Any help appreciated..

---

### Post by Jefim on 2006-12-30
Great howto! Everything worked! And this TI card reader was the last piece of hardware not working on my laptop! Thanks.

---

### Post by ThrobbingBrain66 on 2006-12-30
> **eitan_a said:**
> on edgy...this doesn't work for me.

lscpi gives me..

08:03.0 CardBus bridge: Texas Instruments Unknown device 8039
08:03.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
08:03.2 Mass storage controller: Texas Instruments Unknown device 803b

Any help appreciated..

Assuming you are using SD/MMC memory cards for this (as these are the only two currently supported) what errors are being thrown?  You did insert 08:03.2 in place of the n's in the command, correct? I need a little more infor before I can help :)

---

### Post by Hitman1 on 2006-12-30
I have a bit of a strange situation with my sd card reader and I appreciate help to get it to work. I installed kernel 2.6.19.1 from source just to get the module tifm_sd. When I modprobe tifm_sd the card reader is recognized and my card is automounted perfectly. I can read from it just fine, but when I try to write anything to it, the card would get unmounted and the device /dev/mmcblk0 would disappear. removing the card and inserting it again, does the same thing exactly: I would be able to read, but if I try to write, it would crash or something like that. 

The computer is an HP nc6400. The card is an SD 1GB.

I tried the workaround of writing:
> setpci -s 02:06.2 4c.b=0x02
Now when I insert the card, nothing happens at all and the card is not recognized with no device in /dev either. All modules are loaded.

Here is my lspci output:
> 0000:02:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:02:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:02:06.3 0805: Texas Instruments: Unknown device 803c
0000:02:06.4 Communication controller: Texas Instruments: Unknown device 803d

Anything I can do?

---

### Post by ThrobbingBrain66 on 2007-01-01
I don't have any experience using this on Breezy, if in fact you are still using it.  As stated at the top of the howto, it's only been tested on Edgy.

---

### Post by imonlyhuman on 2007-01-02
I can't seem to get my card reader to work. Here's the lspci:
> 
00:09.3 Mass storage controller: <pci_lookup_name: buffer too small>

so, I insert that into

> sudo setpci -s 00:09.3 4c.b=0x02

Fdisk shows nothing, and dmesg
> 
[17225354.920000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17225354.920000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17225354.920000] ide: failed opcode was: unknown
[17225354.920000] end_request: I/O error, dev hdc, sector 1036
[17225354.924000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[17225354.924000] hdc: command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17225354.924000] ide: failed opcode was: unknown
[17225354.924000] end_request: I/O error, dev hdc, sector 1036


Any help appreciated. Thanks in advanced.

Oh, yes I am running Edgy, and if it matters, i have a Fujitsu N5010 Notebook with a sd/memory stick reader.

---

### Post by greenfrog on 2007-01-02
Here is the output of lspci  using Drapper on my HP zv5340us laptop.

I don't see a hardware signature for my built in SD/MMC reader.
Am I using the wrong instruction?

0000:00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
0000:00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
0000:00:06.1 Modem: nVidia Corporation: Unknown device 00d9 (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
0000:00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go  32M] (rev a3)
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C ontroller (PHY/Link)
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 03)
0000:02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 0 1)
0000:02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 0 1)
0000:02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Funct ion (rev 01)

Thanks

---

### Post by ThrobbingBrain66 on 2007-01-02
> **greenfrog said:**
> Here is the output of lspci  using Drapper on my HP zv5340us laptop.

I don't see a hardware signature for my built in SD/MMC reader.
Am I using the wrong instruction?

0000:00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
0000:00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
0000:00:06.1 Modem: nVidia Corporation: Unknown device 00d9 (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
0000:00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Hyp erTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Add ress Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRA M Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Mis cellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go  32M] (rev a3)
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C ontroller (PHY/Link)
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless  LAN Controller (rev 03)
0000:02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 0 1)
0000:02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 0 1)
0000:02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Funct ion (rev 01)

Thanks

Once again I'll say that this howto only works for Edgy. :)  I have no experience with this howto and Dapper or any other  Ubuntu release.  Edgy's kernel was the first to officially support card readers.

---

### Post by Rhubarb on 2007-01-02
@ThrobbingBrain66:-
For some reason your howto doesn't really work with my HP Pavillion DV5000 laptop.
Output of lspci:
```
08:06.2 Mass storage controller: Texas Instruments Unknown device 803b
```
I'm running the most up-to-date Edgy Eft.

The good news is, is that I got it working by a far easier method than you had proposed.
(Ok, it was just a small section of the last part of your proposal, but this may solve some people's simular SD card problems easier).
And by the way, the following is all I had to do to get my internal TI SD card reader to work, I didn't have to make up any bash scripts or anything else:-
[http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working](http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working)

>  Ubuntu 6.10 'edgy eft':

To get the card reader working on edgy:

Add the module 'tifm_sd' to /etc/modules and restart. Now this module gets loaded on sys bootup and a card is detected when inserted. The card reader is found as /dev/mmcblk0 and mounted automatically on card insert.

Step-by-step:

1. Make a backup of your 'modules' in case something goes wrong:
```
sudo cp /etc/modules /etc/modules.backup
```
> 2. Open the file with gedit:
```
sudo gedit /etc/modules
```
> 3. Add the following entry to the end of the file:
```
tifm_sd
```
> 4. Save and close the file. On the next boot, the sd-card reader works.

---

### Post by dgriff2 on 2007-01-02
Hi, thanks for the fix for this. I am dual booting on a Toshiba m45. My SD card reader was detected, shows up in device manager, but would never show up. Works beautifully. Thanks again.

---

### Post by imonlyhuman on 2007-01-03
UPDATE:
Well, I ran 
> 
sudo update-pciids
and 
> 00:09.3 Mass storage controller: <pci_lookup_name: buffer too small>
became 
> 00:09.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller

Now, I am certain it is a TI card reader, and again, I am running Edgy, I also tried loading the modules

ThrobbingBrain66:
> 
***If this doesn't work, you may have to load some modules:

My reader works without loading the modules, so I didn't include it as a necessary step.

In a terminal:
Code:

gksu gedit /etc/modules

Add tifm_core, tifm_7xx1 and tifm_sd to this file on separate lines.
Save and close the file.

But, I still have no luck at all???:-k 

Im thinking of trying the Rioch method from the link Rhubarb gave.(Hey, you never know it may work) I'll post any updates.

Thanks for the help in advanced.

---

### Post by ThrobbingBrain66 on 2007-01-03
> **Rhubarb said:**
> @ThrobbingBrain66:-
For some reason your howto doesn't really work with my HP Pavillion DV5000 laptop.
Output of lspci:
```
08:06.2 Mass storage controller: Texas Instruments Unknown device 803b
```
I'm running the most up-to-date Edgy Eft.

The good news is, is that I got it working by a far easier method than you had proposed.
(Ok, it was just a small section of the last part of your proposal, but this may solve some people's simular SD card problems easier).
And by the way, the following is all I had to do to get my internal TI SD card reader to work, I didn't have to make up any bash scripts or anything else:-
[http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working](http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working)


```
sudo cp /etc/modules /etc/modules.backup
```

```
sudo gedit /etc/modules
```

```
tifm_sd
```

Thanks for this, I'll add the link to the first post.

---

### Post by imonlyhuman on 2007-01-03
Ok, so I was able to completely rebuild/reconfigure my kernel (ther Rioch method from [http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working)](http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working)), but still no luck, when I go to mount it it says, 
```
mount: special device /dev/mmcblk0p1 does not exist

```

So, Im still confused, and I don't know what I am doing wrong. I have tried so many things, but still no luck. This is one tricky TI card to get working. Anybody have any ideas? Oh, by the way, My reader works with neither, Sd, nor Memory Stick Duo Pro. So if anyone has any ideas. Send them my way.

Thanks

---

### Post by amphoterous on 2007-01-04
I upgraded to Edgy and now I'm trying to get my card reader to work. I tried the modules thing and I would try the other way but I don't have a Mass Storage Controller. ](*,) 

Output from lspci:
```
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
```

---

### Post by imonlyhuman on 2007-01-04
> **amphoterous said:**
> I upgraded to Edgy and now I'm trying to get my card reader to work. I tried the modules thing and I would try the other way but I don't have a Mass Storage Controller. ](*,) 

Output from lspci:
```
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
```

Try running ```
sudo setpci -s nn:nn.n 4c.b=0x02
``` with 02:04.0, 02:04.1, and 02:04.2, a quickk google seach showed the that probably is your TI card reader.

lspci shows TI next to it, and the model refers to a card reader, so it is worth a shot, some people have reported success with using devices other than the Mass Storage Controller.

---

### Post by Burkey on 2007-02-10
Worked perfectly on my LG P1-Express dual

lspci relevant parts..

```

06:00.2 Mass storage controller: Texas Instruments Unknown device 803b

```

I do not need to load modules either

---

### Post by bigbadmoshe on 2007-02-15
awesome awesome thanks all for the great help :popcorn:

---

### Post by rykel on 2007-02-18
[QUOTE=ThrobbingBrain66;1864311]**[COLOR="Red"]This HOWTO also only works with Edgy (not Dapper).[/COLOR]**

Hi,

Thank you for the wonderful HOWTO.

I used to get it working as well under Edgy, but had to switch to Dapper because just too many things were not working right as they used to in Dapper.

However, now I read your heading that the HOWTO is only for Edgy... do you know of any HOWTOs for Dapper?

Thanks once again.

---

### Post by faferreyra on 2007-02-18
Thanks a lot for the tip! It works on a HP Pavillion ze2200la. And there's an interesting bit. On Windows XP, the card is really SLOW, as a 1.1 usb device. On Ubuntu, it has the full 2.0 usb speed. Thanks again!

---

### Post by vicnov on 2007-02-20
I have a problem with TI cardreader in Ubuntu Edgy 6.10, Kernel 2.6.17-11-generic.

What I did:
- Enabled SD host controller with "setpci" command (as described in the 1st post)
- Inserted a MMC card (the same problem was with SD card last time)

If I insert a SD card, it is visible (MMC - not).
BUT... seems that there is a bug in the driver because the mouse pointer begins moving very slowly and twitching (unusable in fact). Ejecting the card does not help.

What I can see in "dmesg" after inserting the MMC card:
...
[17256316.004000] irq 185: nobody cared (try booting with the "irqpoll" option)
[17256316.004000] <c01499a4> __report_bad_irq+0x24/0x80 <c0149a9d> note_interrupt+0x9d/0x270
[17256316.004000] <f8ba7c72> ipw_isr+0x22/0xf0 [ipw3945] <c0149323> handle_IRQ_event+0x33/0x60
[17256316.004000] <c0149448> __do_IRQ+0xf8/0x110 <c0105c89> do_IRQ+0x19/0x30
[17256316.004000] <c010408a> common_interrupt+0x1a/0x20 <f88626dd> acpi_processor_idle+0x220/0x3af [processor]
[17256316.004000] <c0102122> cpu_idle+0x42/0xb0 <c03f27a1> start_kernel+0x321/0x3a0
[17256316.004000] <c03f2210> unknown_bootoption+0x0/0x270
[17256316.004000] handlers:
[17256316.004000] [<f88eb830>] (usb_hcd_irq+0x0/0x60 [usbcore])
[17256316.004000] [<f8afd840>] (yenta_interrupt+0x0/0xe0 [yenta_socket])
[17256316.004000] [<f8ba7c50>] (ipw_isr+0x0/0xf0 [ipw3945])
[17256316.004000] Disabling IRQ #185
[17256564.240000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[17256564.308000] input: SynPS/2 Synaptics TouchPad as /class/input/input3

Does somebody have a similar problem?

---

### Post by omezrich on 2007-02-23
imonlyhuman - 

I have the same card: 
> 02:00.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller

and notice it's vendor and device id:
lspci -n:
> ...
02:00.3 0180: 104c:ac8f
...

Apparently support for our card was added in kernel 2.6.21-rc1 (A new version of tifm_7xx1 driver):

> (from 2.6.21-rc1 changelog):
tifm_7xx1: recognize device 0xac8f as supported


And ubuntu feisty will apparently have 2.6.20, so we're outa luck. Maybe this driver can be backported?

---

### Post by treesurf on 2007-02-24
Just adding the tfim_sd module did the trick for me on a Gateway NX570X.  Thanks for the howto!

---

### Post by treesurf on 2007-02-25
Well, it worked once, and now it won't anymore!  Ack!  

I added tfim_sd to /etc/modules, rebooted and it recognized the card no problem.  Rebooted again and now it doesn't work at all.  Any suggestions?

---

### Post by treesurf on 2007-02-25
It seems to be working reliably now.  I added tfim_7xx1 and tfim_core to the modules and switched up the order that I had them in and now it's all good.

Thanks again for the Howto!

---

### Post by vicnov on 2007-02-26
For me, it works good now - I have added the following strings to the end of file /etc/modules (in this order) and made reboot:

```
tifm_7xx1
tifm_core
tifm_sd
```
No more problems with mouse. I can read and write SD cards (have not yet tested other cards).

Just to summarize my knowledge about TI drivers:
there are 2 alternative drivers;
[LIST=1]
[*]Secure Digital Host Controller driver
[http://mmc.drzeus.cx/wiki/Linux/Drivers/sdhci](http://mmc.drzeus.cx/wiki/Linux/Drivers/sdhci)
```
This is a project to develop a Linux driver for the Secure Digital Host Controller Interface controller. This is a generic interface supported by many manufacturers, so it will provide support for lots of controllers, including many TI controllers which will not work otherwise.
```
[*]TI FlashMedia driver
[http://developer.berlios.de/projects/tifmxx/](http://developer.berlios.de/projects/tifmxx/)
```
Alternative attempt to develop linux driver for TI FlashMedia xx12/xx21 storage controllers.
```
[/LIST]

When you load tifm_* modules like mentioned above (tifm_7xx1, tifm_core, tifm_sd), you will enable TI FlashMedia driver.
When you follow instructions in [the first post]("http://ubuntuforums.org/showpost.php?p=1864311&postcount=1") (enable the interrupt via "setpci" command), you will enable SDHC driver.

Seems that SDHC driver has some problems - for example, on my laptop, mouse moves very strangely (sometimes) after the "setpci" command,
but TI FlashMedia driver seems to work better.

---

### Post by fog on 2007-03-04
I am using an sdmsv card. Is this a compatible card;
[IMG]http://images.amazon.com/images/P/B0001F1XNC.01-A1PY46IM1CBEG3._SCMZZZZZZZ_V38989079_.jpg[/IMG]
I'm using Feisty on a [Toshiba Satellite A100-003]("http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=EU&PRODUCT_ID=124678"):

> fog@road:~$ lsmod | grep tifm
tifm_sd                12808  0 
tifm_7xx1               8960  0 
tifm_core              11396  2 tifm_sd,tifm_7xx1
mmc_core               27780  2 tifm_sd,sdhci

> fog@road:~$ lspci | grep Texas
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
**07:06.2** Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

then:
> sudo setpci -s **07:06.2** 4c.b=0x02
but still no luck. Is it a compatible card; What I'm doing wrong;
Thanx for your help.

---

### Post by vicnov on 2007-03-04
**fog**
your card is Memory Stick Pro.

TI FlashMedia driver (implemented in tifm_* modules) does not yet support such cards, but work is in progress on tifm_ms module:
[http://openfacts.berlios.de/index-en.phtml?title=TI+FlashMedia+xx12%2Fxx21+driver](http://openfacts.berlios.de/index-en.phtml?title=TI+FlashMedia+xx12%2Fxx21+driver)

Another driver (SDHCI, enabled via "setpci") maybe (?) supports Memory Stick cards, but it seems to be buggy even with other cards (like SD).

---

### Post by fog on 2007-03-04
Thanx **vicnov** for your answer and the link. 
I don't know much about memory cards, this is my first... :oops: 

I 'll wait for the tifm_ms driver. Thanx again :)

---

### Post by raimund on 2007-03-07
hi guys,
 I have a problem with a pci1620, the pcmcia slot works, but the built in cardreader not. Can not even able to see any kind of storage controller in the lspci output.
all I have :

02:09.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:09.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:09.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

One of this I think, supposed to be the cardreader. 

 I was read all back this topic, but it didn't help to me. I might miss something ?

Rajmund

---

### Post by ramesh_thiru on 2007-03-09
Thanks a million Dude; this works perfect on my HP Compaq NX6120 (let's hope next version of Ubuntu will support it out of the box...)

---

### Post by explemonk on 2007-03-10
Awesome.  This worked great for me.  I just hope that the Memory Stick drivers come around relatively soon (I have a Sony digital camera).

Edit: This is on my Compaq Presario R4000 series laptop.

---

### Post by arron on 2007-03-11
> **explemonk said:**
> Awesome.  This worked great for me.  I just hope that the Memory Stick drivers come around relatively soon (I have a Sony digital camera).

Edit: This is on my Compaq Presario R4000 series laptop.

You got you MS working on your R4000?  I have tried and tried everything i can find, including this post with no luck.  What kernel are you running, is this howto all it took to get you going?

---

### Post by IcarusR on 2007-03-12
ThrobbingBrain66

Thanks for the excellent Howto. 
Got TI reader to work on my Tosh A100. Thanks

---

### Post by poadshaw on 2007-03-28
I went through the steps described but so far not able to access my internal SD card.  I am using 7.04 & everything is running pretty smoothly.  I know I probably shouldn't have started using the beta as i am pretty newb still, but I wanted to branch out.  the more problems i have the more i learn LOL.

the command prompt and relevent responces follow:

~$ lspci

06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

~$ sudo setpci -s 06:04.3 4c.b=0x02

(at this point nothing poped up)

~$ dmesg

[ 7148.708000] mmcblk0: mmc3:9ffc SU01G 992000KiB 
[ 7148.708000]  mmcblk0: p1
[ 7538.232000] tifm_7xx1: demand removing card from socket 3
[ 7540.656000] tifm_7xx1: sd card detected in socket 3
[ 7540.972000] mmcblk0: mmc3:9ffc SU01G 992000KiB 
[ 7540.972000]  mmcblk0: p1
[ 7860.512000] tifm_7xx1: demand removing card from socket 3
[ 7913.572000] mmcblk0: mmc2:9ffc SU01G 992000KiB 
[ 7913.572000]  mmcblk0: p1

~$ sudo fdisk -l

Disk /dev/sda: 59.8 GB, 59814236160 bytes
255 heads, 63 sectors/track, 7272 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7087    56926296   83  Linux
/dev/sda2            7088        7272     1486012+   5  Extended
/dev/sda5            7088        7272     1485981   82  Linux swap / Solaris

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1         983      990832+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(983, 31, 63) logical=(982, 31, 63)



I then when into /Dev and found two items:  
mmcblk0  &  mmcblk0p1

Both are locked and will not let me open them or cd into them even when using sudo.  

I am pretty new to (k)ubuntu.  if you have any suggestions I'd love to hear them.

Thanks!!

---

### Post by poadshaw on 2007-03-28
never mind i see that this is an "Edgy-Only" post sorry.

---

### Post by explemonk on 2007-03-28
> **arron said:**
> You got you MS working on your R4000?  I have tried and tried everything i can find, including this post with no luck.  What kernel are you running, is this howto all it took to get you going?

Sorry, my post wasn't clear.  These instructions worked great to get my SD cards to read... MS still doesn't work.

---

### Post by arron on 2007-04-02
Is there any hope for the memory stick to work under linux?  This is the last thing I cant get to work on my Compaq R4000 (R4125CA).

Does anyone know the status?

---

### Post by ThrobbingBrain66 on 2007-04-09
> **poadshaw said:**
> I went through the steps described but so far not able to access my internal SD card.  I am using 7.04 & everything is running pretty smoothly.  I know I probably shouldn't have started using the beta as i am pretty newb still, but I wanted to branch out.  the more problems i have the more i learn LOL.

**[snip]**

I am pretty new to (k)ubuntu.  if you have any suggestions I'd love to hear them.

Thanks!!

I am actually still having troubles getting my SD card reader to work under Feisty now.  I haven't had much time to visit this thread to help others or get my own reader working, so I apologize for that.  I haven't been able to figure out what changed between Edgy and Feisty that would cause the problems.  As soon as I figure it out however, I'll update this thread.

---

### Post by ChemicalStorm on 2007-04-11
Hello,

I've done all the steps the How To described, but nothing gets better...

Indeed, once the **setpci** command done, and a SD card inserted, my **dmesg** doesn't mention anymore than usual.

I've also tried loading module by **sudo modprobe tifm_core tifm_sd**, but nothing more...

Any help will be appreciated :)

---

### Post by JoaoMachado on 2007-04-11
I have upgraded to fiesty and my media card reader seems to have an issue with SD cards and reading them. System is an HP ZD8000 series notebook. When I insert the SD card, the indicator light comes on for two seconds then off then on for one second then blank for about two seconds then starts the whole thin over.

Running dmesg I get:

```
[ 1927.172989] end_request: I/O error, dev mmcblk0, sector 102
[ 1927.173005] mmcblk0: error 1 sending read/write command
[ 1927.173011] end_request: I/O error, dev mmcblk0, sector 103
[ 1927.173027] mmcblk0: error 1 sending read/write command
[ 1927.173032] end_request: I/O error, dev mmcblk0, sector 104
```

but if I run dmesg right after I install the card I get:

```
[ 2091.341223] tifm_7xx1: sd card detected in socket 3
[ 2091.548831] mmcblk0: mmc3:bfc6 SD128 123008KiB 
[ 2091.548889]  mmcblk0: p1
```

fdisk output is :
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9447    75882996   83  Linux
/dev/sda2            9448        9729     2265165    5  Extended
/dev/sda5            9448        9729     2265133+  82  Linux swap / Solaris
joao@ZD8000:~$
```

Obviously it is being recognized (sort of), but nothing mounts, I tried another SD card and it does the same thing? Any ideas would be greatly appreciated.

---

### Post by Snyper64 on 2007-04-15
I am running Edgy 6.10 64bit but I can not find the mass storage controller. I have a TI PCI1620 cardreader. Heres my lspci output:
```
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

```
I have tried using the sudo setpci -s nn:nn.n 4c.b=0x02 command on all three of the TI outputs but to no avail. I have tried several SD cards but it will not light up or read the card. Anybody have any idea on how to fix this and get my internal card reader working?

Thanks

---

### Post by vicnov on 2007-04-16
**Snyper**
did you try another method described [here]("http://ubuntuforums.org/showpost.php?p=2214382&postcount=47") ?

---

### Post by Snyper64 on 2007-04-16
Thanks, I'll take a look.

---

### Post by cbs on 2007-04-20
Working off of these instructions (along with others) on feisty, I've run into some trouble.

I have the tifm_sd, mmc_core, tifm_7xx1, tifm_core and mmc_core modules all loaded, and when I insert a SD card it doesn't mount, the following is from dmsg.

Intimately after I insert the card:
```
[  405.488000] tifm_7xx1: xd card detected in socket 0
[  405.596000] tifm_7xx1: demand removing card from socket 0
[  405.872000] tifm_7xx1: sd card detected in socket 1
[  406.476000] mmcblk0: mmc1:758b SD01G 1006080KiB 
[  406.476000]  mmcblk0: p1
[  407.488000] tifm_sd: card failed to respond for a long period of time<6>tifm_7xx1: demand removing card from socket 1
[  407.488000] mmcblk0: error 1 sending read/write command
[  407.488000] end_request: I/O error, dev mmcblk0, sector 2012096
[  407.488000] Buffer I/O error on device mmcblk0, logical block 251512
```
Those last three lines repeat ~10 times (with different sector and logical block) and then the following two lines will repeat until I remove the card.
```
[  407.612000] mmcblk0: error 1 sending read/write command
[  407.612000] end_request: I/O error, dev mmcblk0, sector 0
```
It clearly detects the card, but I tried `setpci -s 08:06.2 4c.b=0x02` like recommended just to see, but afterwards when I insert the card, it doesn't appear that anything happens and there is nothing about it in the logs.

Any input is greatly appreciated.

---

### Post by whistlerspa on 2007-04-20
Thanks a million for the shellscript solution - finally got my SD cardreader to work on my Toshiba laptop by this method

---

### Post by pinan on 2007-04-22
> **whistlerspa said:**
> Thanks a million for the shellscript solution - finally got my SD cardreader to work on my Toshiba laptop by this method
Great thread, worked on previous version of ubuntu on Toshiba Qosmio :) 
, but seems to break on Feisty Fawn.:( :

Sd card shows up in lspci
shows up in /proc/devices
Doing a  setpci -s '06:0b.2' '4c.b=0x2'

results in 
 irq 19: nobody cared (try booting with the "irqpoll" option)
[ 1933.760000]  [<c0143694>] __report_bad_irq+0x24/0x80
[ 1933.760000]  [<c01438f8>] note_interrupt+0x208/0x240
[ 1933.760000]  [<c0142c70>] handle_IRQ_event+0x30/0x60
[ 1933.760000]  [<c0143d10>] handle_fasteoi_irq+0x70/0xa0
[ 1933.760000]  [<c0105680>] do_IRQ+0x40/0x80
[ 1933.760000]  [<c011c87e>] profile_tick+0x3e/0x80
[ 1933.760000]  [<c0104003>] common_interrupt+0x23/0x30
[ 1933.760000]  [<f8855e99>] acpi_processor_idle+0x1dd/0x384 [processor]
[ 1933.760000]  [<c01013cc>] cpu_idle+0x1c/0x60
[ 1933.760000]  [<c03ba6c5>] start_kernel+0x235/0x380
[ 1933.760000]  [<c03ba230>] unknown_bootoption+0x0/0x260
[ 1933.760000]  =======================
[ 1933.760000] handlers:
[ 1933.760000] [<f8b138b0>] (yenta_interrupt+0x0/0xe0 [yenta_socket])
[ 1933.760000] Disabling IRQ #19
in dmesg

doing a lsmod
results in 
tifm_7xx1               9216  0 
tifm_core               8720  1 tifm_7xx1
sdhci                  17420  0 
mmc_core               25748  1 sdhci

Any suggestions?

---

### Post by tuxata on 2007-04-23
have you try this:
mkdir /mnt/mmc
chmod 777 /mnt/mmc
mount /dev/mmcblk0p1 /mnt/mmc

insert your card and type 
cd /mnt/mmc

it works for me.
Best regards

---

### Post by RafaelRadu on 2007-05-01
Hi guys! 
I'm using Feisty Fawn and try it out on my Lenovo C100 3000...
got nothing!

Does any tip to make it work on 7.04? 


Tks for anyhelp

---

### Post by openback on 2007-05-01
It's not working on my Dell Inspiron 710m with Feisty:

02:04.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller

I ran the command, and got no output, but when I placed my SD card in, nothing happened. dmesg didn't report seeing anything at all either.

---

### Post by jarpiw on 2007-05-02
Hey, it works great now! Thank You :)


06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

on Ubuntu Feisty 7.04, Fujitsu-Siemens Amilo Pro 8010 laptop

---

### Post by Copter on 2007-05-23
> **omezrich said:**
> 
...
Apparently support for our card was added in kernel 2.6.21-rc1 (A new version of tifm_7xx1 driver):

And ubuntu feisty will apparently have 2.6.20, so we're outa luck. Maybe this driver can be backported?
...


hi!

same here
```

copter@xidgex:~$ lspci -n
...
02:00.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
...
copter@xidgex:~$ lspci -n
...
02:00.3 0180: 104c:ac8f
...

```
thanks for this info. it is a shame that we need to wait for this to be officialy supported :(

copter :]

---

### Post by Jad on 2007-05-23
```

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


```
/etc/modules
```

fuse
lp
sbp2
tifm_7xx1
tifm_core
tifm_sd

```

Advise, suggestions, chocolate, anything ?

---

### Post by jx2150 on 2007-05-23
> **Jad said:**
> 
Advise, suggestions, chocolate, anything ?

Did you try: setpci -s nn:nn.n 4c.b=0x2   ??
----

I have this reader: 
Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller

I cannot get it to work in Feisty. Same problems as others.

```
May 23 16:18:57 dell kernel: [  145.116000] tifm_7xx1: sd card detected in socket 0
May 23 16:18:57 dell kernel: [  145.476000] mmcblk0: mmc0:c7a2 SD512 500224KiB 
May 23 16:18:57 dell kernel: [  145.476000]  mmcblk0: p1
May 23 16:18:58 dell kernel: [  146.488000] end_request: I/O error, dev mmcblk0, sector 1000384
May 23 16:18:58 dell kernel: [  146.488000] printk: 702 messages suppressed.
May 23 16:18:58 dell kernel: [  146.488000] end_request: I/O error, dev mmcblk0, sector 1000384
May 23 16:18:58 dell kernel: [  146.488000] end_request: I/O error, dev mmcblk0, sector 1000432
May 23 16:18:58 dell kernel: [  146.488000] end_request: I/O error, dev mmcblk0, sector 1000432
May 23 16:18:58 dell kernel: [  146.488000] end_request: I/O error, dev mmcblk0, sector 0
May 23 16:18:58 dell last message repeated 2 times
May 23 16:18:58 dell kernel: [  146.492000] end_request: I/O error, dev mmcblk0, sector 0
May 23 16:18:58 dell last message repeated 11 times
May 23 16:18:58 dell kernel: [  146.496000] end_request: I/O error, dev mmcblk0, sector 0
May 23 16:18:58 dell last message repeated 13 times
May 23 16:18:58 dell kernel: [  146.500000] end_request: I/O error, dev mmcblk0, sector 1000297
May 23 16:18:58 dell kernel: [  146.500000] end_request: I/O error, dev mmcblk0, sector 1000298
May 23 16:18:58 dell kernel: [  146.500000] end_request: I/O error, dev mmcblk0, sector 1000299
May 23 16:18:58 dell kernel: [  146.500000] end_request: I/O error, dev mmcblk0, sector 1000300
May 23 16:18:58 dell kernel: [  146.500000] end_request: I/O error, dev mmcblk0, sector 1000301
May 23 16:18:58 dell kernel: [  146.500000] end_request: I/O error, dev mmcblk0, sector 1000302
May 23 16:18:58 dell kernel: [  146.500000] end_request: I/O error, dev mmcblk0, sector 1000303
```


Anyone get it to work?

-jx

---

### Post by Jad on 2007-05-23
Sure, I did.

---

### Post by jx2150 on 2007-05-23
Jad... you mean you got it working or you tried that command?

---

### Post by treesurf on 2007-05-23
This howto worked great for me with edgy.  I just installed Feisty and am having no luck with it at all.  dmesg does not even register that the card has been recognized.  Bummer!

---

### Post by treesurf on 2007-05-23
Here's a clue that might help someone more knowledgeable than me.  I removed the /etc/init.d/card-reader.sh file and now dmesg at least recognizes that the card has been inserted, although it still does not mount.

---

### Post by treesurf on 2007-05-23
Just found the solution for Feisty here!

[http://ubuntuforums.org/showthread.php?t=420721&highlight=card+reader+feisty](http://ubuntuforums.org/showthread.php?t=420721&highlight=card+reader+feisty)

---

### Post by holyowned on 2007-07-02
How do I backup??  I coded lspci, and this is the tail of my output:

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

No Mass Storage Device.......
I coded setpci, using the numbers from the cardbus bridge,  nothing.  I tried it with the SD card numbers, nothing.  Now, I have the following in my dmesg output:

[17188348.800000] mmc0: unrecognised SCR structure version 1
[17189582.608000] mmc0: unrecognised SCR structure version 1
[17189612.008000] mmc0: unrecognised SCR structure version 1
[17190746.688000] mmc0: unrecognised SCR structure version 1
[17192008.372000] mmc0: unrecognised SCR structure version 1


How do I back up?
TIA

---

### Post by holyowned on 2007-07-02
How do I backup??  I coded lspci, and this is the tail of my output:

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

No Mass Storage Device.......
I coded setpci, using the numbers from the cardbus bridge,  nothing.  I tried it with the SD card numbers, nothing.  Now, I have the following in my dmesg output:

[17188348.800000] mmc0: unrecognised SCR structure version 1
[17189582.608000] mmc0: unrecognised SCR structure version 1
[17189612.008000] mmc0: unrecognised SCR structure version 1
[17190746.688000] mmc0: unrecognised SCR structure version 1
[17192008.372000] mmc0: unrecognised SCR structure version 1


How do I back up?
TIA

---

### Post by chrisrx on 2007-07-03
I can't get this to work for me on a toshiba sattelite pro a120, possibly because I don't have "mass storage controller listed.

lspci gives me
```
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

So I've tried ```
sudo setpci -s 03:0b.3 4c.b=0x02
``` but it doesn't change anything, and dmesg doesn't show any recognition of entering an sd card.

---

### Post by jimmigoo on 2007-09-12
Hi....

I've followed all the instruction without loading modules in /etc/modules, 
The card reader works very well, everytime I boot the machine....
I've got a  Texas Instruments PCIxx21 Integrated FlashMedia Controller on 
Fujitsu-Siemens AMILO L1310G, 
I've tried a SD card ;)

Thanks a lot!!

Bye, 

jim

---

### Post by ikey_d on 2007-09-15
Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) on a Gateway MX3210 running Feisty... SD/MMC works fine with READ & WRITE capabilties... UBUNTU ROCKS!!! Thanks for the howto, BIG HELP!

---

### Post by Tobba25 on 2007-10-12
Ok, I need my XD card to work... how far are they on making that wish come true?

---

### Post by phen on 2007-11-26
hello all,

what about gutsy? an sd card mounts, but as soon as you try to open a file, this error appears, the card unmounts and mounts again.
```

 [ 1343.904000] Buffer I/O error on device mmcblk0p1, logical block 769853
[ 1343.904000] lost page write due to I/O error on mmcblk0p1
[ 1344.124000] tifm_core: MMC/SD card detected in socket 0:0
[ 1345.084000] mmcblk0: mmc0:39ba SD512 500224KiB 
[ 1345.084000]  mmcblk0: p1

```

shall I report a bug? is there a simple trick? thanks for help?

---

### Post by frasene on 2010-06-22
Hi,

I have an Compaq nx9105 and Ubuntu 10.04 and I have the same problem with the internal SD Card Reader...

```

lspci | grep Texas

02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

```

When I put an 512 MO SD Card or other, no disk is mounted...

I put in the /etc/modules :

```

tifm_7xx1
tifm_core
tifm_sd

```

I reboot the computer... No card mounted after insertion...

I try :
```

sudo setpci -s 02:04.0 4c.b=0x02
sudo setpci -s 02:04.1 4c.b=0x02
sudo setpci -s 02:04.2 4c.b=0x02

```

No change...

In the first post, the setpci was applied on the number mm:nn.o associated with <Mass Storage Controller> but there is no corresponding line in the lspci results...

Do you have an idea ?

Even if this computer is old, it is surprising to see how Ubuntu is a very good system for it (3D Desktop, speed with only 512 Mo of RAM...) !

Thanks

---

### Post by greenblob on 2011-10-15
Hi all,
I'm running 11.04 natty.

I have an internal Samsung card reader. I can't get any details from nautilus, but I know it's a Samsung. 

Nautilus recognises it, and all of it's ports, but is unable to open cards through it, or recognise the fact that there is a card present.

I'm able to give more info if you tell me how.

_[SIZE="4"]**[COLOR="Red"]Does anybody know how I can get this working please?[/COLOR]**[/SIZE]_    #-o:sad::-?:confused::confused::confused:

Thanks very much
Luke

---

