---
title: "USB-to-parallel printer cable configuration"
date: 2011-03-10
forum: System76 Support
---

### Post by Dave_L on 2011-03-10
[System76 Starling star3, Ubuntu 10.04]

I've connected an HP 722C Deskjet printer to a USB port on my star3, using a USB-to-parallel adapter cable. (The printer itself only has a parallel port.) 

I'm attempting to configure the printer using System >> Control Center >> Printing.

In the printer properties, what do I use for the Device URI? The default value is "parallel:/dev/lp0", but that's apparently for a parallel port.

---

### Post by isantop on 2011-03-10
I'd try that. I'm not very familiar with Parallel -> USB adapters, though, so it may be different.

---

### Post by Dave_L on 2011-03-10
More info:

```
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 050d:0002 Belkin Components 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
$ sudo lsusb -d 050d:0002 -v
Bus 003 Device 005: ID 050d:0002 Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x050d Belkin Components
  idProduct          0x0002 
  bcdDevice            2.02
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           78
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      1 Unidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               1
cannot read device status, Broken pipe (32)
```

I don't know if the diagostic "cannot read device status, Broken pipe (32)" is significant.

Based on that info, I tried setting the Device URI to "parallel:/dev/bus/usb/003/005"

When I initiate printing of a test page, the Printer State changes from "Idle" to "Processing", but nothing gets printed.

When configuring the printer, I chose the existing CUPS driver for the HP 722C printer.  Is it possible that a special driver is needed since the USB-to-parallel adapter cable is being used?

---

### Post by Dave_L on 2011-03-16
Any ideas on how I can make this work?

---

### Post by alfalfa55 on 2011-03-21
> **Dave_L said:**
> More info:

```
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 050d:0002 Belkin Components 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
$ sudo lsusb -d 050d:0002 -v
Bus 003 Device 005: ID 050d:0002 Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x050d Belkin Components
  idProduct          0x0002 
  bcdDevice            2.02
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           78
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      1 Unidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               1
cannot read device status, Broken pipe (32)
```I don't know if the diagostic "cannot read device status, Broken pipe (32)" is significant.

Based on that info, I tried setting the Device URI to "parallel:/dev/bus/usb/003/005"

When I initiate printing of a test page, the Printer State changes from "Idle" to "Processing", but nothing gets printed.

When configuring the printer, I chose the existing CUPS driver for the HP 722C printer.  Is it possible that a special driver is needed since the USB-to-parallel adapter cable is being used?


I have had problems with hplip as it uses the ghostview libraries.  I detect this issue by attempting a test page from the cups web interface ([http://localhost:631/](http://localhost:631/)) which yields a message about error in library.
This has shown itself in more than just the Ubuntu distribution.

---

### Post by Dave_L on 2011-03-21
> **alfalfa55 said:**
> I have had problems with hplip as it uses the ghostview libraries.  I detect this issue by attempting a test page from the cups web interface ([http://localhost:631/](http://localhost:631/)) which yields a message about error in library.
This has shown itself in more than just the Ubuntu distribution.

Thanks for the reply.

When I submit a test page using the web interface, I don't get an error message, but "nothing happens".

> HP-DeskJet-722C-17  	Test Page  	anonymous  	1k  	Unknown  	processing since
Mon 21 Mar 2011 06:46:11 PM EDT

The status merely says "processing".
 
Can you suggest any way to fix the problem?

---

### Post by isantop on 2011-03-22
I don't have any experience with Parallel connections, but here's a post that seems to detail how to set it all up:
[http://ubuntuforums.org/showpost.php?p=8620053&postcount=19](http://ubuntuforums.org/showpost.php?p=8620053&postcount=19)

---

### Post by Dave_L on 2011-03-22
isantop:

I couldn't find anything in that post that I hadn't already tried. It says to use parallel:/dev/usb/lp0 as the device URI.  I had already tried that, and it doesn't work. Actually, there's no "usb" subdirectory in /dev, which may explain why it doesn't work, but I don't know enough about Linux to be certain.

The cable came with a CD containing a Windows .exe, which I obviously can't use in Ubuntu.  I had thought the cable might already have enough "electronics" so that I wouldn't need a separate software driver, but perhaps that's not the case.

---

### Post by Flyers2391 on 2011-03-25
This probably isn't going to help your problem, but I had a Parallel to USB setup a while back that I connected to an old canon and it "just worked"  I had more issues with it on Windows, both with and without the driver.  Perhaps it is the printer driver that you should take a look at?

---

### Post by Samloops on 2011-08-20
With the cable and printer connected, check to see if there is a file or link created under /dev named usblp0. That's a zero at the end of that.  If so, set the URI of the printer to "parallel:/dev/usbpl0".  Worked for me.

---

### Post by voltsy on 2011-10-01
parallel:/dev/usb/lp0 worked for me: eeepc 701SD, USB-parallel adapter cable 0711:0302 (Magic Control Technology Corp. Parallel port) but probably works with the more common Paradise PL2305 067b:2305 as well...

I just used [http://localhost:631](http://localhost:631) CUPS add printer dialog: "Other Network Printers->LPD/LPR Host or Printer" (weird or what?), pasted "parallel:/dev/usb/lp0" into the "Connection" (URI) field and followed the prompts. Running Lucid 10.04 with all latest repository updates, CUPS version is 1.4.3

Believe it or not the printer was a Canon bj-200ex with foomatic bj200 driver.

PS I think parallel:/dev/usbpl0 might  be a typo....?

---

### Post by r0nni3 on 2011-10-19
No, I <guess> it's not a typo. 
I installed a Kyocera FS-3750 through an USB-par adapter using the device URI parallel:/dev/usblp0
Try that for a change. I saw that on a forum (can't remember which) PLUS the fact that after plugging the adapter in I used the dmesg command in the terminal and saw this :

[17740.672020] usb 7-1: new full speed USB device using uhci_hcd and address 2
[17741.016173] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x1A86 pid 0x7584

I guess that's a pretty good hint ;) :P

LE: try    usb://dev/usblp0   in case parallel://dev/usblp0   does not work. I suspect this can vary for different printers/adapters.

---

### Post by Chough39 on 2011-10-28
This might help someone with a Canon BJC 50 printer, this works well using the parallel port on a machine running Ubuntu 11.04. I need to use the printer with a laptop which only has USB. I have the following converter,  Prolific Technology Inc. PL2305 Parallel Port.
 I have tried the following URIs.
 

 
[LIST=1]
[*]usb:/dev/usblp0
[*]parallel:/dev/usblp0
[/LIST]
 

 They do  not work. However parallel:/dev/usblp0 when changed to parallel:/dev/usb/lp0 does work.
 I agree that it seems that there is a variation between printers and adapters.

---

