---
title: "Porting USB Wifi Adapter to VM"
date: 2011-04-23
forum: Virtualisation
---

### Post by slick666 on 2011-04-23
Dear Forum,

I think I might be working on something a little unique. I'm looking to use Virtualbox for some testing where I'm trying to simulate a system with a USB wifi adapter. I have an extra physical USB wifi adapter but I can't seem to get the configuration right. It seems all I need to do is

[LIST=1]
[*]Disable the adapter in the host OS
[*]Configure the USB device to be part of the VM.
[/LIST]

I'm thinking that after I complete task 1 it should be pretty standard to set up the USB pass through in Virtualbox. But I can't seem to get the system to ignore the device. Can someone please help point me in the right direction for this? Has anyone ever heard of doing this before?

Also I have installed the virtualbox guest extensions for USB support.

Thanks

---

### Post by slick666 on 2011-04-23
Ok, I was WAY over thinking this. All I had to do to keep the system from using the device is block the loaded of it's kernel modules. What I first did was find the kernel module that is used for the extra wifi adapter in my case was **rtl8187**. I figured this by looking at the dmesg data and taking a good guess based on my knowledge of the device. I added this to the end of my blacklist file located in **/etc/modprobe.d/blacklist.conf**.

```
...

blacklist rtl8187
```

I then rebooted but still found the device as busy according to virtualbox.

```
VBoxManage list usbhost
Host USB Devices:

...

UUID:               cdbaefc1-1beb-469f-9bcd-b79b4daac05d
VendorId:           0x0bda (0BDA)
ProductId:          0x8187 (8187)
Revision:           1.0 (0100)
Manufacturer:       Manufacturer_Realtek_RTL8187_
Product:            RTL8187_Wireless
SerialNumber:       00C0CA4F682B
Address:            sysfs:/sys/devices/pci0000:00/0000:00:0b.1/usb1/1-4//device:/dev/vboxusb/001/007
Current State:      Busy

...


```

I still had to plug and unplug the device before it cleared itself and became available. **A reboot is not enough!** The device had to loose power and be reloaded. After that it was standard VirtualBox methods for attaching the USB device to the VM.

---

