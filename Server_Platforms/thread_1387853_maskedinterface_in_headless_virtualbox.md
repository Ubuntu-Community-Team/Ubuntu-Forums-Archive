---
title: "maskedinterface in headless virtualbox"
date: 2010-01-22
forum: Server Platforms
---

### Post by 2handband on 2010-01-22
I've got virtualbox installed on a headless server and am trying to get a usb device enabled. Here's the device:

```
Host USB Devices:

UUID:               fb51fadf-cf5c-4d44-9490-442018019ce3
VendorId:           0x0403 (0403)
ProductId:          0x6001 (6001)
Revision:           4.0 (0400)
Manufacturer:       FTDI
Product:            USB <-> Serial
Address:            sysfs:/sys/devices/pci0000:00/0000:00:03.2/usb3/3-2//device:/dev/bus/usb/003/002
Current State:      Busy
```

Here's the command I'm using:

```
gene@robert:~$ VBoxManage usbfilter add 0 --target global --name homescan --action hold --active yes --vendorid 0403 --productid 6001 --revision 0400 --manufacturer FTDI --product "USB <-> Serial" --remote yes --serialnumber 4508a9f2-1431-4422-a480-2547277f9a26 --maskedinterfaces sysfs:/sys/devices/pci0000:00/0000:00:03.2/usb3/3-2//device:/dev/bus/usb/003/003

```

Here's my error message:

```
error: Failed to convert the --maskedinterfaces value 'sysfs:/sys/devices/pci0000:00/0000:00:03.2/usb3/3-2//device:/dev/bus/usb/003/003' to a number, rc=VERR_NO_DIGITS
```

To be honest I just made a guess at what to use for maskedinterfaces. I can't find a single piece of documentation online that explains what maskedinterfaces is or what you're supposed to put in it. I tried excluding it and was informed that I was missing a mandatory option. What do I need to plug in to get this usb device working?

---

