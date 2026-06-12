---
title: "Ubuntu 10.04 Server w/ virtual kernel, USB device not working?"
date: 2011-01-04
forum: Virtualisation
---

### Post by samosamo on 2011-01-04
I have an ESXi 4.1 server with an Ubuntu 10.04 Server guest that was installed with the virtual kernel option.

I have an APC UPS plugged into the ESXi server via USB.  The device is then added to my Ubuntu guest using USB passthrough.  I have apcupsd installed via apt-get for use with the UPS.

apcupsd cannot see the UPS device.  It seems that the USB module is not loading.

Below is my steps to troubleshoot:

```

root@server:~# uname -a
Linux server 2.6.32-25-server #44-Ubuntu SMP Fri Sep 17 21:13:39 UTC 2010 x86_64 GNU/Linux

```
```
root@server:~# apctest


2011-01-04 23:34:53 apctest 3.14.6 (16 May 2009) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
apctest FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
apctest error termination completed

```
```
root@server:~# lsmod | grep usb
root@server:~#

```
```
root@server:~# dmesg | grep usb
[    0.690368] usbcore: registered new interface driver usbfs
[    0.690382] usbcore: registered new interface driver hub
[    0.690408] usbcore: registered new device driver usb
[    0.971509] usb usb1: configuration #1 chosen from 1 choice
[    0.972359] usb usb2: configuration #1 chosen from 1 choice
[    2.290201] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.297041] usb 2-1: configuration #1 chosen from 1 choice
[    3.419127] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    3.568716] usb 2-2: configuration #1 chosen from 1 choice

```
```
root@server:~# cat /sys/kernel/debug/usb/devices

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev= 2.06
S:  Manufacturer=Linux 2.6.32-25-server uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:02:01.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

[B]T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=051d ProdID=0002 Rev= 1.06
S:  Manufacturer=APC
S:  Product=Back-UPS ES 550 FW:843.K1 .D USB FW:K1 
S:  SerialNumber=3B1803X15914  
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  2mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   6 Ivl=10ms[/B]

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12  MxCh= 7
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0e0f ProdID=0002 Rev= 1.00
S:  Product=VMware Virtual USB Hub
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev= 2.06
S:  Manufacturer=Linux 2.6.32-25-server ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:02:02.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms
root@server:~# 

```

---

### Post by samosamo on 2011-01-06
ttt

---

### Post by samosamo on 2011-02-03
ttt

---

### Post by samosamo on 2011-02-13
I found a solution/workaround.  Rather than use the virtual kernel, I built a virtual machine with the server kernel.  Now it is working.

---

