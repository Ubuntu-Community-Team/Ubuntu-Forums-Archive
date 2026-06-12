---
title: "Vmware &gt; Ubuntu 8.04 Host &gt; Windows XP Guest and Smart Card problems"
date: 2008-05-08
forum: Virtualisation
---

### Post by snafilter on 2008-05-08
I have Vmware 1.0.5 on Ubuntu 8.04 64 Bit with Windows XP as a guest machine.  

Within my XP installation I need to access the UBS GemPC Twin Smart Card, if I enable the card in my Guest Machine via VM > Removable Devices > USB Decvices the host os has problems: the logs to show this better:

This snippet is from when I first inset the USB into the the host without guest access:

```
00000371 hotplug_libusb.c:478:HPAddHotPluggable() Adding USB device: 005:006
00000017 readerfactory.c:1116:RFInitializeReader() Attempting startup of Gemplus GemPC Twin 00 00 using /usr/lib/pcsc/drivers/ifd-ccid.bundle/Contents/Linux/libccid.so.1.3.1
00000110 readerfactory.c:983:RFBindFunctions() Loading IFD Handler 3.0
00000271 ifdhandler.c:1239:init_driver() LogLevel: 0x0003
00000206 ifdhandler.c:1249:init_driver() DriverOptions: 0x0000
00000007 ifdhandler.c:77:IFDHCreateChannelByName() lun: 0, device: usb:08e6/3437:libusb:005:006
00000561 ccid_usb.c:233:OpenUSBByName() Manufacturer: Ludovic Rousseau (ludovic.rousseau@free.fr)
00000204 ccid_usb.c:243:OpenUSBByName() ProductString: Generic CCID driver v1.3.1
00000249 ccid_usb.c:249:OpenUSBByName() Copyright: This driver is protected by terms of the GNU Lesser General Public License version 2.1, or (at your option) any later version.
00000611 ccid_usb.c:397:OpenUSBByName() Found Vendor/Product: 08E6/3437 (Gemplus GemPC Twin)
00000009 ccid_usb.c:399:OpenUSBByName() Using USB bus/device: 005/006
00004726 ccid_usb.c:788:get_data_rates() declared: 10753 bps
00000013 ccid_usb.c:788:get_data_rates() declared: 14337 bps
00000005 ccid_usb.c:788:get_data_rates() declared: 15625 bps
00000005 ccid_usb.c:788:get_data_rates() declared: 17204 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 20833 bps
00000013 ccid_usb.c:788:get_data_rates() declared: 21505 bps
00000006 ccid_usb.c:788:get_data_rates() declared: 23438 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 25806 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 28674 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 31250 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 32258 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 34409 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 39063 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 41667 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 43011 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 46875 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 52083 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 53763 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 57348 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 62500 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 64516 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 68817 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 71685 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 78125 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 83333 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 86022 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 93750 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 104167 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 107527 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 114695 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 125000 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 129032 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 143369 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 156250 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 166667 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 172043 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 215054 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 229391 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 250000 bps
00000004 ccid_usb.c:788:get_data_rates() declared: 344086 bps
00007826 ifdhandler.c:841:IFDHPowerICC() lun: 0, action: PowerUp
00051019 Card ATR: 3B 7B 94 00 00 80 65 B0 83 01 01 74 83 00 90 00 
00051024 ifdhandler.c:271:IFDHGetCapabilities() lun: 0, tag: 0xFAE
00000037 ifdhandler.c:313:IFDHGetCapabilities() Reader supports 1 slot(s)
00000077 hotplug_libusb.c:433:HPEstablishUSBNotifications() End reload serial configuration
00000009 hotplug_libusb.c:430:HPEstablishUSBNotifications() Reload serial configuration
00000392 hotplug_libusb.c:433:HPEstablishUSBNotifications() End reload serial configuration
00000008 hotplug_libusb.c:430:HPEstablishUSBNotifications() Reload serial configuration
00000340 hotplug_libusb.c:433:HPEstablishUSBNotifications() End reload serial configuration
00000007 hotplug_libusb.c:430:HPEstablishUSBNotifications() Reload serial configuration
00000345 hotplug_libusb.c:433:HPEstablishUSBNotifications() End reload serial configuration
```

Now When I enable it in the Guest OS:

```
1193307205 ccid_usb.c:476:WriteUSB() usb_bulk_write(005/006): Device or resource busy
00000019 ifdwrapper.c:494:IFDStatusICC() Card not transacted: 612
00000008 eventhandler.c:316:EHStatusHandlerThread() Error communicating to: Gemplus GemPC Twin 00 00
00400095 ccid_usb.c:476:WriteUSB() usb_bulk_write(005/006): Device or resource busy
00000016 ifdwrapper.c:494:IFDStatusICC() Card not transacted: 612
00000007 eventhandler.c:316:EHStatusHandlerThread() Error communicating to: Gemplus GemPC Twin 00 00
00400057 ccid_usb.c:476:WriteUSB() usb_bulk_write(005/006): Device or resource busy
00000017 ifdwrapper.c:494:IFDStatusICC() Card not transacted: 612
00000006 eventhandler.c:316:EHStatusHandlerThread() Error communicating to: Gemplus GemPC Twin 00 00
00400058 ccid_usb.c:476:WriteUSB() usb_bulk_write(005/006): Device or resource busy
00000017 ifdwrapper.c:494:IFDStatusICC() Card not transacted: 612
00000007 eventhandler.c:316:EHStatusHandlerThread() Error communicating to: Gemplus GemPC Twin 00 00
00070517 hotplug_libusb.c:430:HPEstablishUSBNotifications() Reload serial configuration
00286094 hotplug_libusb.c:433:HPEstablishUSBNotifications() End reload serial configuration
00000018 hotplug_libusb.c:430:HPEstablishUSBNotifications() Reload serial configuration
00000386 hotplug_libusb.c:433:HPEstablishUSBNotifications() End reload serial configuration
00000009 hotplug_libusb.c:430:HPEstablishUSBNotifications() Reload serial configuration
00000348 hotplug_libusb.c:433:HPEstablishUSBNotifications() End reload serial configuration
00042685 ccid_usb.c:476:WriteUSB() usb_bulk_write(005/006): Device or resource busy
00000021 ifdwrapper.c:494:IFDStatusICC() Card not transacted: 612
00000007 eventhandler.c:316:EHStatusHandlerThread() Error communicating to: Gemplus GemPC Twin 00 00
00400075 ccid_usb.c:476:WriteUSB() usb_bulk_write(005/006): Device or resource busy
00000015 ifdwrapper.c:494:IFDStatusICC() Card not transacted: 612
00000006 eventhandler.c:316:EHStatusHandlerThread() Error communicating to: Gemplus GemPC Twin 00 00
00400097 ccid_usb.c:476:WriteUSB() usb_bulk_write(005/006): Device or resource busy
00000019 ifdwrapper.c:494:IFDStatusICC() Card not transacted: 612
00000007 eventhandler.c:316:EHStatusHandlerThread() Error communicating to: Gemplus GemPC Twin 00 00

```

My Card reader in the guest os states:

The card is available for use.  However, the card is not the one being requested, and cannot be used for the current operation.

Any help, yeah I know it's way out there, will be greatly appreciated.

---

### Post by ztirffritz on 2008-06-24
Did you ever figure this out?  I'm about to start experimenting with almost the exact same setup.  I'm using Ubuntu 8.04 64.  VMWare client is XP.  I'm using a Gemalto Smart Card reader.  I haven't tried anything yet, but I'm not expecting it to work at all.  We'll see what happens.

---

### Post by snafilter on 2008-06-24
I should have kept track of what I did, but it is working!  

I upgrade to the latest version of Vmware, all the updates from Ubuntu and crossed my fingers really....

The only quirk I have found is that at times, it doesn't like the USB port that it's in, so for example I'll start VMware and try to access the smart card and it won't find it.  I will, at that point, pick a different port and plug the physical device into it and re-enable it in VMware and it seems to work.

Let me know how it works out for you and if there is anything that I can help with, I'll let you know.

---

