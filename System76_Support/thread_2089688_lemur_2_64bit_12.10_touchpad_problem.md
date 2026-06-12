---
title: "lemur 2 64bit 12.10 touchpad problem"
date: 2012-11-30
forum: System76 Support
---

### Post by DNAtsol1 on 2012-11-30
I've installed 12.10 but my lemur2(64-bit) touchpad no longer works at all. 

does system76 have a specific driver I need or is there a setting I need to adjust?

---

### Post by isantop on 2012-11-30
> **DNAtsol1 said:**
> I've installed 12.10 but my lemur2(64-bit) touchpad no longer works at all. 

does system76 have a specific driver I need or is there a setting I need to adjust?

Make sure it isn't turned off by pressing Fn+F1 on your keyboard.

---

### Post by DNAtsol1 on 2012-11-30
Thanks, checked that already.
Does not seemed to be the issue.

---

### Post by DNAtsol1 on 2012-11-30
I'm actually wondering if the device is even present on the system. What file(s) contains could I view that contain configuration data. Where would I look to see what devices are on my machine and their current status. 

Thanks

---

### Post by DNAtsol1 on 2012-12-01
Pointer works when I plugged in a usb dell mouse

did a cat /proc/bus/input/devices

and got the following output. Notice it does not include a touchpad entry...

Am I on the right track here ?

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=413c Product=3200 Version=0110
N: Name="Dell Dell USB Mouse"
P: Phys=usb-0000:00:1d.0-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

---

### Post by DNAtsol1 on 2012-12-01
upgraded kernel and now solved.

---

