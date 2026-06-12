---
title: "Getting a Steinberg CI1 USB audio interface to work"
date: 2011-02-27
forum: Ubuntu Studio
---

### Post by richarddevries on 2011-02-27
Hi all,

I have a MacBook 3,1 running Ubuntu 10.10 x86_64. I bought a Steinberg CI1 USB audio interface ([http://www.steinberg.net/en/products/hardware/ci1/ci1_start.html](http://www.steinberg.net/en/products/hardware/ci1/ci1_start.html)) which I can return if I can't get it to work in Ubuntu. Before the purchase I googled around a bit to see if anyone had tried this and came up with virtually nothing.

When I plug in the device, it shows up in lsusb as follows:
```
$ sudo lsusb -v -d 0x0499:0x1501

Bus 003 Device 013: ID 0499:1501 Yamaha Corp.
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 2.00
  bDeviceClass 255 Vendor Specific Class
  bDeviceSubClass 0
  bDeviceProtocol 255
  bMaxPacketSize0 8
  idVendor 0x0499 Yamaha Corp.
  idProduct 0x1501
  bcdDevice 1.00
  iManufacturer 1 Yamaha Corporation
  iProduct 2 Steinberg CI1
  iSerial 0
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 176
    bNumInterfaces 3
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0x80
      (Bus Powered)
    MaxPower 500mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 0
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 1
      bInterfaceProtocol 0
      iInterface 0
      ** UNRECOGNIZED: 0a 24 01 00 01 34 00 02 01 02
      ** UNRECOGNIZED: 0c 24 02 01 01 01 00 02 03 00 00 00
      ** UNRECOGNIZED: 09 24 03 02 01 03 00 01 00
      ** UNRECOGNIZED: 0c 24 02 03 03 06 00 02 03 00 00 00
      ** UNRECOGNIZED: 09 24 03 04 01 01 00 03 00
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 1
      bAlternateSetting 0
      bNumEndpoints 0
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 2
      bInterfaceProtocol 0
      iInterface 0
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 1
      bAlternateSetting 1
      bNumEndpoints 1
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 2
      bInterfaceProtocol 0
      iInterface 0
      ** UNRECOGNIZED: 07 24 01 01 01 01 00
      ** UNRECOGNIZED: 0e 24 02 01 02 03 18 02 44 ac 00 80 bb 00
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x01 EP 1 OUT
        bmAttributes 5
          Transfer Type Isochronous
          Synch Type Asynchronous
          Usage Type Data
        wMaxPacketSize 0x0126 1x 294 bytes
        bInterval 1
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 2
      bAlternateSetting 0
      bNumEndpoints 0
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 2
      bInterfaceProtocol 0
      iInterface 0
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 2
      bAlternateSetting 1
      bNumEndpoints 1
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 2
      bInterfaceProtocol 0
      iInterface 0
      ** UNRECOGNIZED: 07 24 01 04 01 01 00
      ** UNRECOGNIZED: 0e 24 02 01 02 03 18 02 44 ac 00 80 bb 00
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x82 EP 2 IN
        bmAttributes 5
          Transfer Type Isochronous
          Synch Type Asynchronous
          Usage Type Data
        wMaxPacketSize 0x0126 1x 294 bytes
        bInterval 1
Device Status: 0x0000
  (Bus Powered)
```

Linux sound architecture is a bit of a mystery to me, but I've tried a few things:

1. I noticed that the snd-usb-audio module wasn't loaded, so I did
```
sudo modprobe snd-usb-audio
sudo alsa force-reload
```
The snd-usb-audio module loaded, but the card still isn't listed in 'aplay -l', nor does it show up in alsamixer.

2. As a long shot, I installed some extra drivers from Medibuntu, which probably don't apply:
```
sudo apt-get install alsa-firmware alsa-firmware-loaders
```
I have no idea how to continue. I found the Sound Troubleshooting Procedure ([https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)), but I figured that wouldn't do any good as the card isn't recognized at all.
I'm just assuming this device should turn up as a soundcard, but maybe I'm dead wrong. I have until Monday to get this thing to work; if it isn't working by then, I'll return it and start shopping for something else. Any help would be much appreciated. Someone knowledgable saying that it won't work anyway would help as well.
Btw, I also posted my question on [answers.launchpad]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/147019").

---

### Post by sgx on 2011-02-27
Good grief, you bought hardware because you couldn't verify it works
in linux? :popcorn:

That's like dating a chic with 4 missing boyfriends, because nobody
has found the bodies :D

lsusb and usbview are useful to spot your device. Does it show up in
qjackctl setup page

Input Device  >
Output Device >

click the  >  widgets

Cheers
(To be honest, I once purchased a soundcard knowing for sure it was not yet supported in linux, and maybe never would be :wink: )

---

### Post by richarddevries on 2011-02-27
Thanks for your reply. It doesn't show up in jackctl, I've tried that in the meantime. I figure it needs drivers which won't be provided any time soon. So, I'll give up and return it tomorrow. If you have any recommendations for an audio interface that _is_ supported, I'd appreciate it.

---

### Post by sgx on 2011-02-27
[http://www.linuxstudiopro.com/#](http://www.linuxstudiopro.com/#)

this is a good site, wish I could visit with tons of cash :o

[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

This has links to many unsorted manufactures, click the brand to see supported cards.

Firewire may also be an option. There are several recent related topics if you search the older pages here, ffado is the current firewire keyword.

If you mention the requirements you have, people can chime in with experience in those areas 

Cheers

---

### Post by sgx on 2011-02-27
[http://getsatisfaction.com/energyxt/topics/what_linux_usb_audio_sound_card](http://getsatisfaction.com/energyxt/topics/what_linux_usb_audio_sound_card)

people happy with maudio in linux

---

### Post by AutoStatic on 2011-02-28
From the CI1 operation manual:> USB1.1, 44.1/48 kHz, 24bit, bus-poweredSo it's a standards compliant USB audio device and should work ootb on Ubuntu. But it does need a driver apparently according to the operation manual. Not sure what that driver does. Can you give the full output of both **lsusb** and **lspci** ?

Best,

Jeremy

---

### Post by richarddevries on 2011-02-28
sgx, thanks for your tips!

AutoStatic, the device is USB1.1. However, the line **bInterfaceClass 255 Vendor Specific Class** keeps showing up in lsusb -v, which probably means that the interface class is not one of the standard ones.
The full output of lsusb -v for the CI1 is in my first post, here is the full output of lsusb:```
$ lsusb
Bus 007 Device 003: ID 05ac:022a Apple, Inc. Internal Keyboard/Trackpad (MacBook Pro) (ISO)
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 009: ID 0499:1501 Yamaha Corp. 
Bus 003 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]
Bus 002 Device 002: ID 0d49:7410 Maxtor Mobile Hard Disk Drive (1TB)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```lspci:```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
04:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
```

---

### Post by AutoStatic on 2011-02-28
Ah, sorry for not examining your lsusb output a bit more thoroughly :( Everything else looks ok, maybe you could try installing the **linux-backports-modules-alsa-maverick-generic** package but I can't find anything about ALSA support for the CI1 though.

Best,

Jeremy

---

### Post by richarddevries on 2011-02-28
I've installed linux-backports-modules-alsa-maverick-generic and, to be sure, rebooted. Nothing changed. dmesg reports```
usb 3-2: new full speed USB device using uhci_hcd and address 5
```, no new device/channels in alsamixer, aplay -l or jackctl. I think I'll give up, return the device and look for something that has linux drivers or true USB1.1 compliance.

---

### Post by AutoStatic on 2011-02-28
:(
Bad luck then probably. Weird because most Yamaha soundcards seem to work (like the Audiogram series). I could ask on the [Linux Audio Users mailinglist]("http://linuxaudio.org/mailarchive/lau/"), maybe someone on there has experience with this card.

Best,

Jeremy

---

### Post by richarddevries on 2011-02-28
Thanks for your help, guys. I returned the CI1 and I'll be trying an M-Audio next, as soon as it's back in stock at the local store.

---

### Post by DaveCat on 2012-05-22
Hello! I've done the same stupid thing (bought a Steinberg C1 audio interface) but even more stupidly: cannot give it back!
Being not a programmer, I can't make myself a driver module to make it work, and I suppose nobody would do that job without having himself a C1.
However, if is there an hero or just a fool that could & would make a driver but cannot test the hardware, I could test it.
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

### Post by sgx on 2012-05-23
Hi, just cut your losses, and sell/trade it at Harmony Central,
Gearslutz, ebay, or other windows/Mac site.
Cheers

---

