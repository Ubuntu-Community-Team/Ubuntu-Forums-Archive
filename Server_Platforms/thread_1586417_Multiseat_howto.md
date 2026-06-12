---
title: "Multiseat howto"
date: 2010-10-02
forum: Server Platforms
---

### Post by ubun2warrior on 2010-10-02
Hi

I am trying to build a multiseat linux system. I am posting some outputs

output of lspci | grep VGA
```
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

```
ls /dev/input/mouse*
```
/dev/input/mouse0  /dev/input/mouse1  /dev/input/mouse2
```

more /proc/bus/input/devices
```
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input4
U: Uniq=
H: Handlers=mouse1 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0001 Vendor=10ec Product=0888 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:05.0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c05a Version=0111
N: Name="Logitech USB Optical Mouse"
P: Phys=usb-0000:00:02.0-3/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.0/input/input6
U: Uniq=
H: Handlers=mouse2 event6 
B: EV=17
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=04d9 Product=1603 Version=0110
N: Name="  USB Keyboard"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=04d9 Product=1603 Version=0110
N: Name="  USB Keyboard"
P: Phys=usb-0000:00:02.0-4/input1
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=13
B: KEY=2000000 39fa d941d001 1e0000 0 0 0
B: MSC=10
```

I have connected two mouse and two keyboard (one PS/2 and the other USB). I have also connected two monitors and i am getting displays on both the screens. I am also able to move my cursor on both the screens.

I am having trouble in configuring xorg.conf. I am running Ubuntu 10.04 desktop on my PC and I have also installed kdm bcoz gdm does not support multiseat(is there a way to downgrade to gdm 2.20 or can i modify gdm 2.30 to support multiseat???). When i boot my PC i get the kdm login screen and then I boot into gnome session.. (is it ok ?? or do I need to install Kubuntu??)
Also, I have one onboard nvidia graphics 6150SE and I have put one nvidia 8400GS 512Mb in the 16X PCIe slot for the additional seat...

So kindly tell me what should I do now or what things are missing ?? For any further info abt my PC plz tell me to post outputs(specify the commands for the same..)

ubun2warrior

---

### Post by leodp on 2010-10-19
Hi warrior!
excuse me if I point you to a basic document, but you have not mentioned it: have you followed the multiseat HOWTO?
[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

BR
Leodp

---

