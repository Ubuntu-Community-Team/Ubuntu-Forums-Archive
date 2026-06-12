---
title: "How to link a port"
date: 2009-02-13
forum: Wine
---

### Post by Doug11 on 2009-02-13
I found a loader program for my FTA which was built as a .deb package. After installing it, i noticed it only has com ports. My laptop does not have a serial port but uses a usb-serial adapter. I also have a Doze program that will run in wine but it also has only com ports. I want to know how i can point the wine loader to use my usb adapter. this is a screen shot of the linux loader,,also this is my output for  

doug@lappy:~$ dmesg | grep usb
[   22.921119] usbcore: registered new interface driver usbfs
[   22.921143] usbcore: registered new interface driver hub
[   22.928772] usbcore: registered new device driver usb
[   22.992873] usb usb1: configuration #1 chosen from 1 choice
[   23.152757] usb usb2: configuration #1 chosen from 1 choice
[   23.400484] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   23.412589] usb usb3: configuration #1 chosen from 1 choice
[   24.451891] usb 1-1: new full speed USB device using ohci_hcd and address 3
[   24.658918] usb 1-1: configuration #1 chosen from 1 choice
[   24.963606] usb 1-3: new low speed USB device using ohci_hcd and address 4
[   25.171631] usb 1-3: configuration #1 chosen from 1 choice
[   25.197612] usbcore: registered new interface driver hiddev
[   25.201718] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb1/1-3/1-3:1.0/input/input2
[   25.211524] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-3
[   25.216590] hiddev96hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-3
[   25.216607] usbcore: registered new interface driver usbhid
[   25.216611] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.362568] usbcore: registered new interface driver usbserial
[   41.362596] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   41.362634] usbcore: registered new interface driver usbserial_generic
[   41.362637] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   41.410507] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[   41.410706] usb 1-1: pl2303 converter now attached to ttyUSB0
[   41.410715] usbcore: registered new interface driver pl2303
[   41.410718] /build/buildd/linux-2.6.24/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver
doug@lappy:~$ 

Somehow i would like to link one of the com ports to the ttyUSB0 that is list above. A little guidance here would be greatly apreciated.

---

