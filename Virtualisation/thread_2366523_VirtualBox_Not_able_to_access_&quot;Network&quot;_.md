---
title: "VirtualBox Not able to access &quot;Network&quot; USB Device"
date: 2017-07-18
forum: Virtualisation
---

### Post by rich86 on 2017-07-18
Hi,

I am having problems with my Polar V650 bike computer when trying to access it as a USB device in VirtualBox running Win7 (which is the only OS which has the PolarFlow software to download the data), i know it is unlikely anyone has the same device but i hope that someone maybe able to help me with a solution.

When i plug in the device, it seems to be registered as a Network Device:

```
$ sudo dmesg
 
[  489.696539] usb 1-2: new high-speed USB device number 5 using xhci_hcd
[  489.826020] usb 1-2: New USB device found, idVendor=0da4, idProduct=0009
[  489.826026] usb 1-2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[  489.826030] usb 1-2: Product: Polar V650
[  489.826033] usb 1-2: Manufacturer: Polar Electro Oy
[  489.826037] usb 1-2: SerialNumber: Q8ONVCPRSGMB7TW8
[  489.922114] usbcore: registered new interface driver cdc_ether
[  489.933705] rndis_host 1-2:1.0 usb0: register 'rndis_host' at usb-0000:00:14.0-2, RNDIS device, 62:2f:90:cb:72:7f
[  489.933765] usbcore: registered new interface driver rndis_host
[  489.958056] rndis_host 1-2:1.0 enp0s20u2: renamed from usb0
[  490.004480] IPv6: ADDRCONF(NETDEV_UP): enp0s20u2: link is not ready
```

```
$ sudo lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b469 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 04ca:300b Lite-On Technology Corp. Atheros AR3012 Bluetooth
Bus 001 Device 005: ID 0da4:0009 Polar Electro Oy 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

In VirtualBox the device is not listed as a in connected USB devices. I am able to connect another USB GPS device and use in the VirtualBox Win7 without any problems.

It seems like Ubuntu is keeping the device and not allowing VirtualBox to access it, does anyone have any ideas how to stop this behaving as a network device in Ubuntu?

I did try ```
sudo RMMOD cdc_ether
``` but i the module was locked and it wasn't possible to run this command.

Thanks in advance.
Richard

---

### Post by &amp;KyT$0P# on 2017-07-18
What version of VirtualBox?
Do you have the Extension Pack installed?

Do you have VirtualBox Guest Additions installed in Windows 7?

On the host, are you in the [FONT=Courier New]vboxusers[/FONT] group?

---

### Post by rich86 on 2017-07-19
OK so i am an idiot, i checked and upgraded to the latest version and re-added myself to the vboxusers group and the device seems to be recognised in Win7 virtual machine now.

Sorry for wasting any ones times

---

