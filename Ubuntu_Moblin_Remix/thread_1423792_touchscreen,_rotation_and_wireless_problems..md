---
title: "touchscreen, rotation and wireless problems."
date: 2010-03-07
forum: Ubuntu Moblin Remix
---

### Post by apavl on 2010-03-07
Hello everyone,

I have already posted this message to the ubuntu-users mailing list.

I have a no-name touchscreen netbook (the brand is turbo-x, a proprietary brand name of a greek chain store) with a rotational screen and windows XP pre-installed. I have installed ubuntu netbook remix on it (allong with windows xp) but I could not have the wireless working, as well as the screen rotation, whereas the touchscreen was working partially: I could not move the mose pointer but I could get a response on double click.
I've tried several solutions I found on the net and I was able to make the wireless work, until I rebooted.

I also figured out that the wireless card is probably connected to a usb port internally, which is probably why ubuntu had difficulties configuring it.

Bellow I give the computer's specifications I gathered with dxdiag windows utility. I'm posting only the information that I think is relevant.

Any help is appreciated.
Thanks

------------------
System Information
------------------
Time of this report: 3/6/2010, 10:05:32
      Machine name: USER-BE8FC2F039
  Operating System: Windows XP Home Edition (5.1, Build 2600) Service Pack
3 (2600.xpsp_sp3_gdr.091208-2036)
          Language: Greek (Regional Setting: Greek)
System Manufacturer: Intel
      System Model: Intel powered classmate PC
              BIOS: Ver 1.00PARTTBL
         Processor: Intel(R) Atom(TM) CPU N270   @ 1.60GHz (2 CPUs)
            Memory: 1014MB RAM
         Page File: 651MB used, 1790MB available
       Windows Dir: C:\WINDOWS
   DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
    DxDiag Version: 5.03.2600.5512 32bit Unicode


---------------
Display Devices
---------------
       Card name: Mobile Intel(R) 945 Express Chipset Family
    Manufacturer: Intel Corporation
       Chip type: Intel(R) GMA 950
        DAC type: Internal
      Device Key: Enum\PCI\VEN_8086&DEV_27AE&SUBSYS_0778152D&REV_03
  Display Memory: 64.0 MB
    Current Mode: 1024 x 600 (32 bit) (60Hz)
         Monitor:   Monitor Max Res: 1600,1200
     Driver Name: igxprd32.dll
  Driver Version: 6.14.0010.4926 (English)
     DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 2/15/2008 13:12:06, 57344 bytes
     WHQL Logo'd: Yes
 WHQL Date Stamp: n/a
             VDD:          Mini VDD: igxpmp32.sys
   Mini VDD Date: 2/15/2008 13:12:06, 5854752 bytes
Device Identifier: {D7B78E66-64EE-11CF-A365-7227A2C2CB35}
       Vendor ID: 0x8086
       Device ID: 0x27AE
       SubSys ID: 0x0778152D
     Revision ID: 0x0003
     Revision ID: 0x0003
     Video Accel:
 Deinterlace Caps: n/a
        Registry: OK
    DDraw Status: Enabled
      D3D Status: Enabled


-------------
Sound Devices
-------------
           Description: Realtek HD Audio output
 Default Sound Playback: Yes
 Default Voice Playback: Yes
           Hardware ID:
HDAUDIO\FUNC_01&VEN_10EC&DEV_0269&SUBSYS_152D0778&REV_1000
       Manufacturer ID: 1
            Product ID: 100
                  Type: WDM
           Driver Name: RtkHDAud.sys
        Driver Version: 5.10.0000.5713 (English)
     Driver Attributes: Final Retail
           WHQL Logo'd: Yes
         Date and Size: 10/2/2008 19:01:00, 4878336 bytes
           Other Files:
       Driver Provider: Realtek Semiconductor Corp.
        HW Accel Level: Full
             Cap Flags: 0xF5F
   Min/Max Sample Rate: 8000, 192000
Static/Strm HW Mix Bufs: 33, 32
 Static/Strm HW 3D Bufs: 33, 32
             HW Memory: 0
      Voice Management: No
 EAX(tm) 2.0 Listen/Src: Yes, Yes
  I3DL2(tm) Listen/Src: Yes, Yes


---------------------
Sound Capture Devices
---------------------
           Description: Realtek HD Audio Input
 Default Sound Capture: Yes
 Default Voice Capture: Yes
           Driver Name: RtkHDAud.sys
        Driver Version: 5.10.0000.5713 (English)
     Driver Attributes: Final Retail
         Date and Size: 10/2/2008 19:01:00, 4878336 bytes
             Cap Flags: 0x41
          Format Flags: 0xFFF

-----------
USB Devices
-----------
+ | Vendor/Product ID: 0x8086, 0x27C9
| Matching Device ID: usb\root_hub
| Service: usbhub
| Driver: usbhub.sys, 4/14/2008 00:15:38, 59520 bytes
| Driver: usbd.sys, 4/15/2008 14:00:00, 4736 bytes


--------------
System Devices
--------------
    Name: Intel(R) 82801G (ICH7 Family) Ultra ATA Storage Controllers -
27DF
Device ID: PCI\VEN_8086&DEV_27DF&SUBSYS_0778152D&REV_02\3&B1BFB68&0&F9
  Driver: C:\WINDOWS\system32\DRIVERS\pciide.sys, 5.01.2600.0000 (Greek),
11/26/2001 22:57:54, 3456 bytes
  Driver: C:\WINDOWS\system32\DRIVERS\pciidex.sys, 5.01.2600.5512 (Greek),
4/14/2008 00:10:30, 24960 bytes
  Driver: C:\WINDOWS\system32\DRIVERS\atapi.sys, 5.01.2600.5512 (English),
4/14/2008 00:10:32, 96512 bytes

    Name: Intel(R) 82801G (ICH7 Family) SMBus Controller - 27DA
Device ID: PCI\VEN_8086&DEV_27DA&SUBSYS_0778152D&REV_02\3&B1BFB68&0&FB
  Driver: n/a

    Name: Device ID:
PCI\VEN_8086&DEV_27D8&SUBSYS_0778152D&REV_02\3&B1BFB68&0&D8
  Driver: C:\WINDOWS\system32\DRIVERS\hdaudbus.sys, 5.10.0001.5013
(English), 4/15/2008 14:00:00, 144384 bytes

    Name: Intel(R) 82801G (ICH7 Family) PCI Express Root Port - 27D4
Device ID: PCI\VEN_8086&DEV_27D4&SUBSYS_00000000&REV_02\3&B1BFB68&0&E2
  Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (Greek),
4/14/2008 21:32:16, 68480 bytes

    Name: Intel(R) 82801G (ICH7 Family) PCI Express Root Port - 27D2
Device ID: PCI\VEN_8086&DEV_27D2&SUBSYS_00000000&REV_02\3&B1BFB68&0&E1
  Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (Greek),
4/14/2008 21:32:16, 68480 bytes

    Name: Intel(R) 82801G (ICH7 Family) PCI Express Root Port - 27D0
Device ID: PCI\VEN_8086&DEV_27D0&SUBSYS_00000000&REV_02\3&B1BFB68&0&E0
  Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (Greek),
4/14/2008 21:32:16, 68480 bytes

    Name: Intel(R) 82801G (ICH7 Family) USB2 Enhanced Host Controller -
27CC
Device ID: PCI\VEN_8086&DEV_27CC&SUBSYS_0778152D&REV_02\3&B1BFB68&0&EF
  Driver: C:\WINDOWS\system32\drivers\usbehci.sys, 5.01.2600.5512
(English), 4/14/2008 00:15:36, 30208 bytes
  Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512
(English), 4/14/2008 00:15:38, 143872 bytes
  Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (Greek), 4/14/2008
22:00:10, 78848 bytes
  Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English),
4/14/2008 00:15:38, 59520 bytes
  Driver: C:\WINDOWS\system32\hccoin.dll, 5.01.2600.5512 (English),
4/15/2008 14:00:00, 7168 bytes

    Name: Intel(R) 82801G (ICH7 Family) USB Universal Host Controller -
27CB
Device ID: PCI\VEN_8086&DEV_27CB&SUBSYS_0778152D&REV_02\3&B1BFB68&0&EB
  Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512
(English), 4/14/2008 00:15:36, 20608 bytes
  Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512
(English), 4/14/2008 00:15:38, 143872 bytes
  Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (Greek), 4/14/2008
22:00:10, 78848 bytes
  Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English),
4/14/2008 00:15:38, 59520 bytes

    Name: Intel(R) 82801G (ICH7 Family) USB Universal Host Controller -
27CA
Device ID: PCI\VEN_8086&DEV_27CA&SUBSYS_0778152D&REV_02\3&B1BFB68&0&EA
  Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512
(English), 4/14/2008 00:15:36, 20608 bytes
  Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512
(English), 4/14/2008 00:15:38, 143872 bytes
  Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (Greek), 4/14/2008
22:00:10, 78848 bytes
  Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English),
4/14/2008 00:15:38, 59520 bytes

    Name: Intel(R) 82801G (ICH7 Family) USB Universal Host Controller -
27C9
Device ID: PCI\VEN_8086&DEV_27C9&SUBSYS_0778152D&REV_02\3&B1BFB68&0&E9
  Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512
(English), 4/14/2008 00:15:36, 20608 bytes
  Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512
(English), 4/14/2008 00:15:38, 143872 bytes
  Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (Greek), 4/14/2008
22:00:10, 78848 bytes
  Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English),
4/14/2008 00:15:38, 59520 bytes

    Name: Intel(R) 82801G (ICH7 Family) USB Universal Host Controller -
27C8
Device ID: PCI\VEN_8086&DEV_27C8&SUBSYS_0778152D&REV_02\3&B1BFB68&0&E8
  Driver: C:\WINDOWS\system32\drivers\usbuhci.sys, 5.01.2600.5512
(English), 4/14/2008 00:15:36, 20608 bytes
  Driver: C:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.5512
(English), 4/14/2008 00:15:38, 143872 bytes
  Driver: C:\WINDOWS\system32\usbui.dll, 5.01.2600.5512 (Greek), 4/14/2008
22:00:10, 78848 bytes
  Driver: C:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.5512 (English),
4/14/2008 00:15:38, 59520 bytes

    Name: Intel(R) 82801GBM/GHM (ICH7-M Family) Serial ATA Storage
Controller - 27C4
Device ID: PCI\VEN_8086&DEV_27C4&SUBSYS_0778152D&REV_02\3&B1BFB68&0&FA
  Driver: C:\WINDOWS\system32\DRIVERS\pciide.sys, 5.01.2600.0000 (Greek),
11/26/2001 22:57:54, 3456 bytes
  Driver: C:\WINDOWS\system32\DRIVERS\pciidex.sys, 5.01.2600.5512 (Greek),
4/14/2008 00:10:30, 24960 bytes
  Driver: C:\WINDOWS\system32\DRIVERS\atapi.sys, 5.01.2600.5512 (English),
4/14/2008 00:10:32, 96512 bytes

    Name: Intel(R) 82801GBM (ICH7-M/U) LPC Interface Controller - 27B9
Device ID: PCI\VEN_8086&DEV_27B9&SUBSYS_00000000&REV_02\3&B1BFB68&0&F8
  Driver: C:\WINDOWS\system32\DRIVERS\isapnp.sys, 5.01.2600.5512 (Greek),
4/14/2008 21:25:50, 38016 bytes

    Name: Mobile Intel(R) 945 Express Chipset Family
Device ID: PCI\VEN_8086&DEV_27AE&SUBSYS_0778152D&REV_03\3&B1BFB68&0&10
  Driver: C:\WINDOWS\system32\DRIVERS\igxpmp32.sys, 6.14.0010.4926
(English), 2/15/2008 13:12:06, 5854752 bytes
  Driver: C:\WINDOWS\system32\igxprd32.dll, 6.14.0010.4926 (English),
2/15/2008 13:12:06, 57344 bytes
  Driver: C:\WINDOWS\system32\igxpgd32.dll, 6.14.0010.4926 (English),
2/15/2008 13:12:06, 151040 bytes
  Driver: C:\WINDOWS\system32\igxpdv32.dll, 6.14.0010.4926 (English),
2/15/2008 13:12:16, 1670144 bytes
  Driver: C:\WINDOWS\system32\igxpdx32.dll, 6.14.0010.4926 (English),
2/15/2008 13:12:14, 2643968 bytes
  Driver: C:\WINDOWS\system32\igxpxk32.vp, 2/15/2008 12:38:38, 2096 bytes
  Driver: C:\WINDOWS\system32\igxpxs32.vp, 2/15/2008 15:09:18, 27024 bytes
  Driver: C:\WINDOWS\system32\hccutils.dll, 6.14.0010.4926 (English),
2/15/2008 12:45:44, 102400 bytes
  Driver: C:\WINDOWS\system32\igfxsrvc.dll, 6.14.0010.4926 (English),
2/15/2008 12:46:08, 48128 bytes
  Driver: C:\WINDOWS\system32\igfxsrvc.exe, 6.14.0010.4926 (English),
2/15/2008 12:46:06, 249856 bytes
  Driver: C:\WINDOWS\system32\igfxpph.dll, 6.14.0010.4926 (English),
2/15/2008 12:46:26, 204800 bytes
  Driver: C:\WINDOWS\system32\igfxcpl.cpl, 6.14.0010.4926 (English),
2/15/2008 12:46:28, 122880 bytes
  Driver: C:\WINDOWS\system32\igfxcfg.exe, 6.14.0010.4926 (English),
2/15/2008 12:48:06, 524288 bytes
  Driver: C:\WINDOWS\system32\igfxdev.dll, 6.14.0010.4926 (English),
2/15/2008 12:45:40, 208896 bytes
  Driver: C:\WINDOWS\system32\igfxdo.dll, 6.14.0010.4926 (English),
2/15/2008 12:46:16, 135168 bytes
  Driver: C:\WINDOWS\system32\igfxtray.exe, 6.14.0010.4926 (English),
2/15/2008 12:46:46, 135168 bytes
  Driver: C:\WINDOWS\system32\igfxzoom.exe, 6.14.0010.4926 (English),
2/15/2008 12:45:58, 163840 bytes
  Driver: C:\WINDOWS\system32\hkcmd.exe, 6.14.0010.4926 (English),
2/15/2008 12:46:46, 159744 bytes
  Driver: C:\WINDOWS\system32\igfxress.dll, 6.14.0010.4926 (English),
2/15/2008 12:45:28, 3293184 bytes
  Driver: C:\WINDOWS\system32\igfxpers.exe, 6.14.0010.4926 (English),
2/15/2008 12:46:18, 131072 bytes
  Driver: C:\WINDOWS\system32\igfxrara.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:24, 159744 bytes
  Driver: C:\WINDOWS\system32\igfxrchs.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:24, 110592 bytes
  Driver: C:\WINDOWS\system32\igfxrcht.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:24, 110592 bytes
  Driver: C:\WINDOWS\system32\igfxrdan.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:26, 172032 bytes
  Driver: C:\WINDOWS\system32\igfxrdeu.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:26, 192512 bytes
  Driver: C:\WINDOWS\system32\igfxrenu.lrc, 6.14.0010.4926 (English),
2/15/2008 12:45:40, 172032 bytes
  Driver: C:\WINDOWS\system32\igfxresp.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:28, 188416 bytes
  Driver: C:\WINDOWS\system32\igfxrfin.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:28, 176128 bytes
  Driver: C:\WINDOWS\system32\igfxrfra.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:28, 184320 bytes
  Driver: C:\WINDOWS\system32\igfxrheb.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:28, 155648 bytes
  Driver: C:\WINDOWS\system32\igfxrita.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:30, 188416 bytes
  Driver: C:\WINDOWS\system32\igfxrjpn.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:30, 131072 bytes
  Driver: C:\WINDOWS\system32\igfxrkor.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:32, 126976 bytes
  Driver: C:\WINDOWS\system32\igfxrnld.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:32, 188416 bytes
  Driver: C:\WINDOWS\system32\igfxrnor.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:32, 176128 bytes
  Driver: C:\WINDOWS\system32\igfxrplk.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:32, 180224 bytes
  Driver: C:\WINDOWS\system32\igfxrptb.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:32, 180224 bytes
  Driver: C:\WINDOWS\system32\igfxrptg.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:32, 180224 bytes
  Driver: C:\WINDOWS\system32\igfxrrus.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:34, 180224 bytes
  Driver: C:\WINDOWS\system32\igfxrsky.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:34, 176128 bytes
  Driver: C:\WINDOWS\system32\igfxrslv.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:34, 172032 bytes
  Driver: C:\WINDOWS\system32\igfxrsve.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:34, 172032 bytes
  Driver: C:\WINDOWS\system32\igfxrtha.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:34, 163840 bytes
  Driver: C:\WINDOWS\system32\igfxrcsy.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:26, 176128 bytes
  Driver: C:\WINDOWS\system32\igfxrell.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:28, 192512 bytes
  Driver: C:\WINDOWS\system32\igfxrhun.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:30, 180224 bytes
  Driver: C:\WINDOWS\system32\igfxrtrk.lrc, 6.14.0010.4926 (English),
2/15/2008 12:49:34, 172032 bytes
  Driver: C:\WINDOWS\system32\igfxext.exe, 6.14.0010.4926 (English),
2/15/2008 12:46:16, 163840 bytes
  Driver: C:\WINDOWS\system32\igfxexps.dll, 6.14.0010.4926 (English),
2/15/2008 12:46:18, 24576 bytes
  Driver: C:\WINDOWS\system32\iglicd32.dll, 6.14.0010.4926 (English),
2/15/2008 13:00:58, 2334720 bytes
  Driver: C:\WINDOWS\system32\igldev32.dll, 6.14.0010.4926 (English),
2/15/2008 13:01:04, 294912 bytes
  Driver: C:\WINDOWS\system32\igfxCoIn_v4926.dll, 2/15/2008 13:21:56,
147456 bytes

    Name: Mobile Intel(R) 945GME Express Processor to DRAM Controller -
27AC
Device ID: PCI\VEN_8086&DEV_27AC&SUBSYS_00000000&REV_03\3&B1BFB68&0&00
  Driver: n/a

    Name: Mobile Intel(R) 945 Express Chipset Family
Device ID: PCI\VEN_8086&DEV_27A6&SUBSYS_0778152D&REV_03\3&B1BFB68&0&11
  Driver: n/a

    Name: Device ID:
PCI\VEN_8086&DEV_2448&SUBSYS_00000000&REV_E2\3&B1BFB68&0&F0
  Driver: C:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.5512 (Greek),
4/14/2008 21:32:16, 68480 bytes

    Name: Realtek RTL8102E Family PCI-E Fast Ethernet NIC
Device ID: PCI\VEN_10EC&DEV_8136&SUBSYS_0778152D&REV_02\4&192AC53F&0&00E0
  Driver: C:\WINDOWS\system32\DRIVERS\Rtenicxp.sys, 5.698.0701.2008
(Greek), 7/1/2008 11:27:00, 108800 bytes
  Driver: C:\WINDOWS\system32\RtNicProp32.dll, 1.01.0716.2008 (English),
7/22/2008 00:14:00, 9728 bytes

---

### Post by mooware on 2010-03-08
Hi there.

It seems your noname-netbook is a rebranded Intel Classmate Convertible. I have one of these myself (though not rebranded) and it's running Ubuntu Netbook Remix 9.10 with wireless lan, touchscreen and display rotation working.

I used [this guide]("http://www.admindu.de/wordpress/?p=453") to get most of it running. It's in german, but I hope you get the gist of it (maybe google translate can help), because it would take some effort to explain everything here again.
The touchscreen input rotation still didn't work for me after following the guide, so I made my own little rotation tool, but YMMV.

The steps required to get the wireless lan working are quite easy:

Append the following lines to [FONT=Courier New]/etc/modules[/FONT]:
```
lp
rt3070sta
```[FONT=Courier New][FONT=Arial]

[/FONT][/FONT]Append the following lines to [FONT=Courier New]/etc/modprobe.d/blacklist.conf[/FONT][FONT=Courier New][FONT=Arial]:
[/FONT][/FONT]```
blacklist rt2×00usb
blacklist rt2×00lib
blacklist rt2800usb
blacklist rt2870sta
```Reboot. Now the wireless lan led should stop blinking frantically.

If you need any help with the rest of the guide, just contact me.

---

### Post by apavl on 2010-03-10
Thank you so much for your answer.

I followed the steps that were mentioned in the link (I had no trouble reading them via google translator) but unfortunately I had no luck, neither with the wlan, nor with the touch screen.

The wlan was recognized and enabled but it could not log in to my rooter.
The touchscreen didn't work, probably to a bad configuration of xorg.conf (I created one in /etc/X11/ as it was mentioned in the guide). I will give it a rest for a while and I'll get back to it shortly. 
I will post again my results.

Thanks again.

---

