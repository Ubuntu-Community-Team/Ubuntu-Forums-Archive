---
title: "Lexicon Omega problem"
date: 2008-10-01
forum: Ubuntu Studio
---

### Post by dillinger417 on 2008-10-01
I have a Lexicon Omega -what is supposed to be a plug-n-play ALSA supported USB recording device - and I have had some success using it in the past, but right now it doesn't seem to be recognized... when I plug it in the syslog shows:

```
Oct  1 19:56:51 user-desktop kernel: [  165.080770] usb 1-4: new full speed USB device using ohci_hcd and address 5
Oct  1 19:56:52 user-desktop kernel: [  165.292689] usb 1-4: configuration #1 chosen from 1 choice
Oct  1 19:56:52 user-desktop NetworkManager: <debug> [1222909012.179232] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3200_noserial'). 
Oct  1 19:56:52 user-desktop NetworkManager: <debug> [1222909012.228783] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3200_noserial_if0').
```

But its not listed in /proc/asound/cards... and it isn't an option in Jack for selecting input/output devices like it used to be.  I know it worked ok before on 7.04 w/o PulseAudio, now I have 8.04 w/ PulseAudio but can't say those changes did this -- It's something I pick up now and again w/ varying results and degrees of success. I would love some help, or some pointers to help to continue to debug the issue. :)

---

### Post by dillinger417 on 2008-10-14
Ok I really need some help here so I thought I would post more info.

This is from dmesg from normal boot:  Just picked the (imho) relevant usb stuff:

```
[   39.572286] usbcore: registered new interface driver usbfs
[   39.572356] usbcore: registered new interface driver hub
[   39.573688] usbcore: registered new device driver usb
[   39.575198] SCSI subsystem initialized
[   39.585483] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   39.585541] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 23 (level, low) -> IRQ 23
[   39.585848] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   39.585859] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   39.586303] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   39.586399] ehci_hcd 0000:00:02.1: debug port 1
[   39.586445] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   39.586519] ehci_hcd 0000:00:02.1: irq 23, io mem 0xfeb00000
[   39.586020] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   39.591506] libata version 3.00 loaded.
[   39.592212] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   39.592430] usb usb1: configuration #1 chosen from 1 choice
[   39.592499] hub 1-0:1.0: USB hub found
[   39.592551] hub 1-0:1.0: 10 ports detected
[   39.693184] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   39.693243] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, low) -> IRQ 22
[   39.693575] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   39.693582] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   39.693689] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   39.697273] ohci_hcd 0000:00:02.0: irq 22, io mem 0xd5003000
[   39.741934] Floppy drive(s): fd0 is 1.44M
[   39.750398] usb usb2: configuration #1 chosen from 1 choice
[   39.750472] hub 2-0:1.0: USB hub found
[   39.750525] hub 2-0:1.0: 10 ports detected
...
[   40.520521] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   40.714653] usb 2-1: configuration #1 chosen from 1 choice
[   40.978581] usb 2-2: new full speed USB device using ohci_hcd and address 3
[   41.180906] usb 2-2: configuration #1 chosen from 1 choice
[   41.310433] ata3: SATA link down (SStatus 0 SControl 310)
[   41.444637] usb 2-4: new full speed USB device using ohci_hcd and address 4
[   41.613472] ata4: SATA link down (SStatus 0 SControl 310)
[   41.656515] usb 2-4: configuration #1 chosen from 1 choice
[   41.660106] usbcore: registered new interface driver hiddev
[   41.666620] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input2
[   41.674734] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:02.0-1
[   41.674942] usbcore: registered new interface driver usbhid
[   41.674989] /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   54.944675] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7404
[   54.944753] usbcore: registered new interface driver usblp
[   56.520485] usb 2-4: new full speed USB device using ohci_hcd and address 7
[   56.627544] EXT3 FS on sda6, internal journal
[   56.731929] usb 2-4: configuration #1 chosen from 1 choice

```

sudo lsusb
```
Bus 002 Device 015: ID 0451:3200 Texas Instruments, Inc. 
Bus 002 Device 003: ID 03f0:7404 Hewlett-Packard 
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  

```

sudo lsusb -v ( for Lexicon Omega )
```
Bus 002 Device 015: ID 0451:3200 Texas Instruments, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0451 Texas Instruments, Inc.
  idProduct          0x3200 
  bcdDevice            0.00
  iManufacturer           1 USB Device - By Haim Eliyahu
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           18
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x40
      (Missing must-be-set bit!)
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
Device Status:     0x0001
  Self Powered

```

Then later
```
Oct 14 19:50:00 jared-desktop kernel: [  781.915308] usb 2-4: new full speed USB device using ohci_hcd and address 9
Oct 14 19:50:47 jared-desktop kernel: [  828.236438] usb 2-4: new full speed USB device using ohci_hcd and address 11
Oct 14 19:50:47 jared-desktop kernel: [  828.447533] usb 2-4: configuration #1 chosen from 1 choice
Oct 14 19:50:47 jared-desktop kernel: [  828.450421] usb 2-4: can't set config #1, error -62
Oct 14 19:50:47 jared-desktop kernel: [  828.450489] usb 2-4: USB disconnect, address 11
Oct 14 19:50:47 jared-desktop NetworkManager: <debug> [1224031847.401635] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3200_noserial'). 
Oct 14 19:50:47 jared-desktop NetworkManager: <debug> [1224031847.404920] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3200_noserial'). 
Oct 14 19:50:47 jared-desktop pulseaudio[6576]: module-hal-detect.c: Error getting capability: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_451_3200_noserial
Oct 14 19:51:19 jared-desktop kernel: [  860.094537] usb 2-4: new full speed USB device using ohci_hcd and address 12
Oct 14 19:51:19 jared-desktop kernel: [  860.304182] usb 2-4: configuration #1 chosen from 1 choice
Oct 14 19:51:19 jared-desktop NetworkManager: <debug> [1224031879.252968] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3200_noserial'). 
Oct 14 19:51:19 jared-desktop NetworkManager: <debug> [1224031879.302541] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3200_noserial_if0'). 
Oct 14 19:52:27 jared-desktop kernel: [  929.058973] usb 2-4: USB disconnect, address 12
Oct 14 19:52:27 jared-desktop NetworkManager: <debug> [1224031947.994401] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3200_noserial_if0'). 
Oct 14 19:52:27 jared-desktop NetworkManager: <debug> [1224031947.997526] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3200_noserial'). 
```

Unplugging, plugging
```
Oct 14 19:55:32 jared-desktop kernel: [ 1113.964266] usb 2-4: USB disconnect, address 14
Oct 14 19:55:32 jared-desktop NetworkManager: <debug> [1224032132.876225] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_02_0_if0_0'). 
Oct 14 19:55:32 jared-desktop NetworkManager: <debug> [1224032132.880157] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3200_noserial'). 
Oct 14 19:55:38 jared-desktop kernel: [ 1119.591788] usb 2-4: new full speed USB device using ohci_hcd and address 15
Oct 14 19:55:38 jared-desktop kernel: [ 1119.802904] usb 2-4: configuration #1 chosen from 1 choice
Oct 14 19:55:38 jared-desktop NetworkManager: <debug> [1224032138.717444] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_451_3200_noserial'). 
Oct 14 19:55:38 jared-desktop NetworkManager: <debug> [1224032138.765259] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_02_0_if0_0'). 
```

lspci -v|grep HCI
```

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])

```

   In the manual it notes that "The Omega is compatible with USB 2.0 ports, but the USB 2.0 bus will switch to the slower USB v1.1 to work with the Omega." 

I'm trying to learn as much as I can, but I still have a lot to learn about the kernel and debugging.  Let me know if I can provide more useful information.  ANY help would be greatly appreciated.  :)

---

### Post by dillinger417 on 2009-10-03
Hello-

  I've been meaning to come back to this post actually, but I've been busy.  The omega is supposed to 'just work' with snd-usb-audio( [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Lexicon]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Lexicon")).  No windows drivers are necessary.  The problem was actually the omega itself.  According to this thread [http://www.lexiconpro.com/Community/viewtopic.php?f=12&t=48&st=0&sk=t&sd=a&start=15]("http://www.lexiconpro.com/Community/viewtopic.php?f=12&t=48&st=0&sk=t&sd=a&start=15") its a known problem.  I actually sent it in for a warranty replacement and it has worked fine since.

---

