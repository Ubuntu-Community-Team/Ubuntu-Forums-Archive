---
title: "can not recognize 3rd-party usb"
date: 2022-08-16
forum: Virtualisation
---

### Post by dangal2022 on 2022-08-16
Hello, everyone.I have ubuntu running on a virtual machine and I want to plug in my third party device through the usb port and it works and runs fine on windows platform, on ubuntu when I type the lsusb command it is able to show that the device is there but I am unable to find a device file like ttyUSB* in /dev/tty. Is there a way to load the device shown by lsusb into /dev/tty so that my test demo program can run?Thanks
environment&#65306;
ubuntu hard drive size is 40GB
4GB of RAM
Number of processors: 2
USB port&#65306;3.0
OS: Ubuntu 16.04.5 LTS(amd64)

---

### Post by ajgreeny on 2022-08-16
What virtual system are you using?

If virtualbox, make sure you have the guest additions installed in the VM and that USB3 is chosen in the VM settings.

---

### Post by dangal2022 on 2022-08-16
I use VMWARE workstation pro 16.1&#65292;and I installed the vmtools

---

### Post by dangal2022 on 2022-08-16
```

szh@szh-virtual-machine:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 2f4b:2012  
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

my device is 2f4b:2012,but I use 'ls /dev/tty*', no **ttyUSB*** device found
```

szh@szh-virtual-machine:~$ ls /dev/tty*
/dev/tty    /dev/tty16  /dev/tty24  /dev/tty32  /dev/tty40  /dev/tty49  /dev/tty57  /dev/tty8       /dev/ttyS14  /dev/ttyS22  /dev/ttyS30
/dev/tty0   /dev/tty17  /dev/tty25  /dev/tty33  /dev/tty41  /dev/tty5   /dev/tty58  /dev/tty9       /dev/ttyS15  /dev/ttyS23  /dev/ttyS31
/dev/tty1   /dev/tty18  /dev/tty26  /dev/tty34  /dev/tty42  /dev/tty50  /dev/tty59  /dev/ttyprintk  /dev/ttyS16  /dev/ttyS24  /dev/ttyS4
/dev/tty10  /dev/tty19  /dev/tty27  /dev/tty35  /dev/tty43  /dev/tty51  /dev/tty6   /dev/ttyS0      /dev/ttyS17  /dev/ttyS25  /dev/ttyS5
/dev/tty11  /dev/tty2   /dev/tty28  /dev/tty36  /dev/tty44  /dev/tty52  /dev/tty60  /dev/ttyS1      /dev/ttyS18  /dev/ttyS26  /dev/ttyS6
/dev/tty12  /dev/tty20  /dev/tty29  /dev/tty37  /dev/tty45  /dev/tty53  /dev/tty61  /dev/ttyS10     /dev/ttyS19  /dev/ttyS27  /dev/ttyS7
/dev/tty13  /dev/tty21  /dev/tty3   /dev/tty38  /dev/tty46  /dev/tty54  /dev/tty62  /dev/ttyS11     /dev/ttyS2   /dev/ttyS28  /dev/ttyS8
/dev/tty14  /dev/tty22  /dev/tty30  /dev/tty39  /dev/tty47  /dev/tty55  /dev/tty63  /dev/ttyS12     /dev/ttyS20  /dev/ttyS29  /dev/ttyS9
/dev/tty15  /dev/tty23  /dev/tty31  /dev/tty4   /dev/tty48  /dev/tty56  /dev/tty7   /dev/ttyS13     /dev/ttyS21  /dev/ttyS3

```
[IMG]https://sm.ms/image/zQhel6vZtdRNsgI[/IMG][IMG]https://sm.ms/image/zQhel6vZtdRNsgI[/IMG]

---

### Post by tea for one on 2022-08-16
> **dangal2022 said:**
> I want to plug in my third party device through the usb port 
Is the name and description of this device a secret?

Also, you are using a very old version of Ubuntu?

Why not run a live session of Ubuntu 22.04 and see if this unspecified device is recognised?

---

### Post by dangal2022 on 2022-08-16
thanks.the name of device is Oceanhood XS11639 ,a usb-driven [spectrophotometer]("http://www.baidu.com/link?url=1Mxauf7iKjq96kn7dpBfd5okYTOmoqXA2VdQxe9PymfEA0lpxypaz5ZWqSH3lLODJAAmC1ikOO0aME4Uzyom7tUFtKdddn1AO_ibDoWmCuaHTcPZSjUIwnGswXE7WEeN").. It can be shown in Ubuntu22.04...
but It stills not to appear in '/dev/tty*', still no USB device found

---

### Post by sudodus on 2022-08-16
Please check with the manufacturer or vendor if there exists a  linux driver for your spectrophotometer. They should know.

If there is no linux driver, you have to use an operative system with a driver for it, Windows (or maybe MacOS).

---

### Post by QIII on 2022-08-16
Moved to Virtualisation.

I would like to echo this again:  You are using an old, unsupported version of Ubuntu.  Because you are no long receiving security updates, you place yourself -- and all of us -- at risk.  Your VM, if connected to the internet while running, is an easy target for those who create botnets.  This means that not only could your VM be compromised, it could also cause problems for others.

Before you do anything further, please install a supported version of Ubuntu.  I would suggest one of the two currently supported LTS versions:  20.04.x or 22.04.  With one of them installed, continue to seek support for the original issue.

---

### Post by dangal2022 on 2022-08-16
Hi,I installed the Ubuntu22.04 and the name of device can be shown in 'lsusb';
```

szh@szh-virtual-machine:/mnt/hgfs/SeaBreeze1/SeaBreeze/src/vendors/OceanOptics/devices$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 003 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
**Bus 003 Device 005: ID 2f4b:2012 XS11639  Oceanhood XS11639**
Bus 003 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0008 VMware, Inc. Virtual Bluetooth Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

and I also find the  device driver provided by vendor(XS11639.cpp)
```

szh@szh-virtual-machine:/mnt/hgfs/SeaBreeze1/SeaBreeze/src/vendors/OceanOptics/devices$ ls
Apex.cpp        HR4000.d         NIRQuest256.d              QE65000.o         STS.cpp          Ventana.d       XS11510.o    XV1000Plus.cpp
Apex.d          HR4000.o         NIRQuest256.o              QEPro.cpp         STS.d            Ventana.o       **XS11639.cpp**  XV1000Plus.d
Apex.o          Jaz.cpp          NIRQuest512.cpp            QEPro.d           STS.o            XR3000.cpp      XS11639.d    XV1000Plus.o
Blaze.cpp       Jaz.d            NIRQuest512.d              QEPro.o           Torus.cpp        XR3000.d        XS11639.o    XV700.cpp
Blaze.d         Jaz.o            NIRQuest512.o              RS785.cpp         Torus.d          XR3000.o        XS12666.cpp  XV700.d
Blaze.o         Makefile         Oceanhood3rdParty.cpp      RS785.d           Torus.o          XR3000Plus.cpp  XS12666.d    XV700.o
FlameNIR.cpp    Maya2000.cpp     Oceanhood3rdParty.d        RS785.o           USB2000.cpp      XR3000Plus.d    XS12666.o    XV700Plus.cpp
FlameNIR.d      Maya2000.d       Oceanhood3rdParty.o        SEED3000.cpp      USB2000.d        XR3000Plus.o    XS13496.cpp  XV700Plus.d
FlameNIR.o      Maya2000.o       OceanhoosSpectrometer.cpp  SEED3000.d        USB2000.o        XS10420.cpp     XS13496.d    XV700Plus.o
HR2000.cpp      Maya2000Pro.cpp  OceanhoosSpectrometer.d    SEED3000.o        USB2000Plus.cpp  XS10420.d       XS13496.o
HR2000.d        Maya2000Pro.d    OceanhoosSpectrometer.o    SEED3000Plus.cpp  USB2000Plus.d    XS10420.o       XS9214.cpp
HR2000.o        Maya2000Pro.o    OHGeneric.cpp              SEED3000Plus.d    USB2000Plus.o    XS11071.cpp     XS9214.d
HR2000Plus.cpp  MayaLSL.cpp      OHGeneric.d                SEED3000Plus.o    USB4000.cpp      XS11071.d       XS9214.o
HR2000Plus.d    MayaLSL.d        OHGeneric.o                Spark.cpp         USB4000.d        XS11071.o       XV1000.cpp
HR2000Plus.o    MayaLSL.o        QE65000.cpp                Spark.d           USB4000.o        XS11510.cpp     XV1000.d
HR4000.cpp      NIRQuest256.cpp  QE65000.d                  Spark.o           Ventana.cpp      XS11510.d       XV1000.o

```
but I still not find my device through the USB port
```

szh@szh-virtual-machine:/mnt/hgfs/SeaBreeze1/SeaBreeze/src/vendors/OceanOptics/devices$ ls /dev/tty*(no** ttyUSB*** found)
/dev/tty    /dev/tty16  /dev/tty24  /dev/tty32  /dev/tty40  /dev/tty49  /dev/tty57  /dev/tty8       /dev/ttyS14  /dev/ttyS22  /dev/ttyS30
/dev/tty0   /dev/tty17  /dev/tty25  /dev/tty33  /dev/tty41  /dev/tty5   /dev/tty58  /dev/tty9       /dev/ttyS15  /dev/ttyS23  /dev/ttyS31
/dev/tty1   /dev/tty18  /dev/tty26  /dev/tty34  /dev/tty42  /dev/tty50  /dev/tty59  /dev/ttyprintk  /dev/ttyS16  /dev/ttyS24  /dev/ttyS4
/dev/tty10  /dev/tty19  /dev/tty27  /dev/tty35  /dev/tty43  /dev/tty51  /dev/tty6   /dev/ttyS0      /dev/ttyS17  /dev/ttyS25  /dev/ttyS5
/dev/tty11  /dev/tty2   /dev/tty28  /dev/tty36  /dev/tty44  /dev/tty52  /dev/tty60  /dev/ttyS1      /dev/ttyS18  /dev/ttyS26  /dev/ttyS6
/dev/tty12  /dev/tty20  /dev/tty29  /dev/tty37  /dev/tty45  /dev/tty53  /dev/tty61  /dev/ttyS10     /dev/ttyS19  /dev/ttyS27  /dev/ttyS7
/dev/tty13  /dev/tty21  /dev/tty3   /dev/tty38  /dev/tty46  /dev/tty54  /dev/tty62  /dev/ttyS11     /dev/ttyS2   /dev/ttyS28  /dev/ttyS8
/dev/tty14  /dev/tty22  /dev/tty30  /dev/tty39  /dev/tty47  /dev/tty55  /dev/tty63  /dev/ttyS12     /dev/ttyS20  /dev/ttyS29  /dev/ttyS9
/dev/tty15  /dev/tty23  /dev/tty31  /dev/tty4   /dev/tty48  /dev/tty56  /dev/tty7   /dev/ttyS13     /dev/ttyS21  /dev/ttyS3

```

---

### Post by ajgreeny on 2022-08-17
Please do not add screenshot images of terminal output as you have done in two posts here. It is very difficult to read text in images and makes it more difficult to help you.

Please highlight then copy the text (ctrl + shift + c) and post it back here using Code-Tags.
See my signature below for a How-to.

---

### Post by dangal2022 on 2022-08-17
> **ajgreeny said:**
> Please do not add screenshot images of terminal output as you have done in two posts here. It is very difficult to read text in images and makes it more difficult to help you.

Please highlight then copy the text (ctrl + shift + c) and post it back here using Code-Tags.
See my signature below for a How-to.

sorry,I modified my post with screenshot replace by code tags.

---

### Post by ajgreeny on 2022-08-18
> **dangal2022 said:**
> sorry,I modified my post with screenshot replace by code tags.
Thank you so much!

I'm sure you can see now how much easier it is for everybody to help you.

---

### Post by tea for one on 2022-08-18
> **dangal2022 said:**
> and I also find the  device driver provided by vendor(XS11639.cpp)

Can you confirm that XS11639.cpp is a driver suitable for Ubuntu?
Have you installed it?

---

### Post by dangal2022 on 2022-08-19
> **tea for one said:**
> Can you confirm that XS11639.cpp is a driver suitable for Ubuntu?
Have you installed it?


XS11639.cpp is a c++ language file&#65292;can’t install,but it can compile a dynamic library in ubuntu...I compile it to generate a dynamic library(.so) , and my demo program can work, but I want to know why my usb device can't be shown in '/dev/' ?

---

### Post by tea for one on 2022-08-19
> **dangal2022 said:**
> my demo program can work, but I want to know why my usb device can't be shown in '/dev/' ?
Splendid news about the success with your program.

In post 9, you observed [COLOR="#0000FF"]ls /dev/tty*(no ttyUSB* found)[/COLOR].
ttyusb or tty/usb do not exist and I think that you have to look elsewhere.

Here is an example of the location of a removable usb device (in my case it is a dvb tv tuner).
(Probably a good idea to only have the relevant device attached to avoid confusion)
Open a terminal and run lsusb to identify the details:-
```
edited@edited-22-04:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 8087:0aaa Intel Corp. Bluetooth 9460/9560 Jefferson Peak (JfP)
Bus 001 Device 004: ID [COLOR="#0000FF"]07ca:850a AVerMedia Technologies, Inc. AverTV Volar Black HD (A850)[/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
edited@edited-22-04:~$ 
```
Then, enter ```
usb-devices
```
```
edited@edited-22-04:~$ usb-devices
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=[COLOR="#0000FF"]07ca[/COLOR] ProdID=[COLOR="#0000FF"]850a[/COLOR] Rev=01.01
S:  Manufacturer=[COLOR="#0000FF"]AVerMedia[/COLOR]
S:  Product=A850 DVBT
S:  SerialNumber=302705000939000
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=dvb_usb_af9015
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=84(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=85(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
edited@edited-22-04:~$ usb-devices
```
First line T: indicates the location of the the usb device.
Bus=01 – Navigate to /sys/bus/usb/devices/usb1/
Lev=01 – Navigate to /sys/bus/usb/devices/usb1/1-1/
Look for the files [COLOR="#0000FF"]idProduct idVendor manufacturer[/COLOR]
The content of these files will correspond to the output of both lsusb and usb-devices.

One last tip, if the device is not visible to usb-devices, then you may need to use a different usb port.
Finally, my example is from a bare-metal installation, I would hope that Windows host and Vmware will behave accordingly.

---

### Post by TheFu on 2022-08-19
Not all USB devices are shown as tty devices.  The device name is something the driver picks, usually with a trailing number, so that multiple devices can be used on the same system.

If the software is working, perhaps the manual for that software will list the device name?  OTOH, if it is working, is the device name important?  you could look for it using lsof. I'd pipe that output through grep to limit the results.

Or use **lshw** to see the driver and device name. For example:
```
$ lshw -C network |egrep '\*|logical name:'
WARNING: you should run this program as super-user.
  *-network
       logical name: enp3s0
  *-network:0
       logical name: enp7s0f0
  *-network:1
       logical name: enp7s0f1
  *-network:0
       logical name: enp8s0f0
  *-network:1
       logical name: enp8s0f1
  *-network:0 DISABLED
       logical name: virbr0-nic
  *-network:1
       logical name: vnet0
```

If you know the "class" of the device, like I knew "network", then reducing the output just to that class will make it shorter.  Without the class filter, lots of chips/subsystems/devices will be output.

---

### Post by dangal2022 on 2022-08-21
[LIST]
[*]Thank you all
[/LIST]

---

