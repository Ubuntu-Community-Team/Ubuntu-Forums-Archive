---
title: "Ubuntu phone not mounting"
date: 2015-03-22
forum: Ubuntu Phone and Tablet
---

### Post by davidricq87 on 2015-03-22
Hi,

I just reiceived the Aquaris E4.5 Ubuntu phone.
I'am really surprised, the Ubuntu phone is not detected by Ubuntu 14.04.........

I mean when I connect the phone with USB cable, I can connect with adb, but I can't browse phone folders with nautilus.


What's wrong ?




EDIT : 

Ok libmtp is outdated : I use this ppa [https://launchpad.net/~phablet-team/+archive/ubuntu/tools](https://launchpad.net/~phablet-team/+archive/ubuntu/tools) and solve my problem.

---

### Post by schankame on 2015-03-22
Did you have issues browsing files through the file management? Wondering if that is the problem I am having also.

---

### Post by davidricq87 on 2015-03-25
Hi Schankame,

I noticed nothing special when browsing throught file management.

What's happen exactly ?

---

### Post by mojo risin on 2015-03-27
I have the same problem, It doesnt mount at all, I cant see it in lsusb when it is plugged in.

---

### Post by davidricq87 on 2015-03-27
> **mojo risin said:**
> I have the same problem, It doesnt mount at all, I cant see it in lsusb when it is plugged in.

Can you post the output of lsusb ?

---

### Post by mojo risin on 2015-03-27
ok it does seem to register something but still nothing under mounted drives
with the phone
```
lsusb
Bus 002 Device 003: ID 05c8:0348 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 005: ID 2a47:2008  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

without
```
lsusb
Bus 002 Device 003: ID 05c8:0348 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I added the sources named at the top of the thread .

---

### Post by davidricq87 on 2015-03-27
BQ Aquaris correspond to 
Bus 002 Device 005: ID 2a47:2008 

On Ubuntu 14.04 constructor id are not set.
You must have information about device in "dmesg|grep -i usb"


Ok, if you add the ppa, upgrade packages, plug the phone.
The phone must be unlocked (on a scope for example) when you plug it.

---

### Post by mojo risin on 2015-03-27
ok it is found in the dmesg.

```
[  164.821882] usb 2-1.2: Product: Aquaris_E4.5
[  164.821887] usb 2-1.2: Manufacturer: BQ
[  164.821892] usb 2-1.2: SerialNumber: JU002788
[  577.411316] usb 2-1.2: USB disconnect, device number 5
[ 7587.156544] usb 2-1.2: new high-speed USB device number 6 using ehci-pci
[ 7587.249373] usb 2-1.2: New USB device found, idVendor=2a47, idProduct=2008
[ 7587.249384] usb 2-1.2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 7587.249391] usb 2-1.2: Product: Aquaris_E4.5
[ 7587.249395] usb 2-1.2: Manufacturer: BQ
[ 7587.249400] usb 2-1.2: SerialNumber: JU002788
[ 7648.720460] usb 2-1.2: USB disconnect, device number 6
[ 7651.703921] usb 2-1.2: new high-speed USB device number 7 using ehci-pci
[ 7651.796876] usb 2-1.2: New USB device found, idVendor=2a47, idProduct=2008
[ 7651.796888] usb 2-1.2: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 7651.796894] usb 2-1.2: Product: Aquaris_E4.5
[ 7651.796899] usb 2-1.2: Manufacturer: BQ
[ 7651.796904] usb 2-1.2: SerialNumber: JU002788
morri@morri ~ $ 


```

how do I get it to show up in the file manager? i dont have a micro SD in it yet but it has an internal memory as well that should be accessible.

---

### Post by davidricq87 on 2015-03-27
Normaly, if you install this ppa : [https://launchpad.net/~phablet-team/...e/ubuntu/tools]("https://launchpad.net/%7Ephablet-team/+archive/ubuntu/tools") then upgrade your system, it should appears in file manager (but be sure your phone is not lock when you connect)

```

[B]sudo add-apt-repository ppa:phablet-team/tools
sudo apt-get update && sudo apt-get upgrade
[/B]
```

Check if libmtp9 is intall on your system.

Maybe you need to reboot.

---

### Post by mojo risin on 2015-03-27
It is working now, thanks. I updated the distro(only refreshed the cache prev) and it fine now :)

---

