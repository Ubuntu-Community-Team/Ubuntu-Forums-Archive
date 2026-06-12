---
title: "JEOS 12.04 missing kernel modules"
date: 2012-09-27
forum: Server Platforms
---

### Post by esa007 on 2012-09-27
Hello,

i have installed a JEOS server 12.04 on my Ubuntu Hypervisor.

When i passtrough  a serrial USB-Device to the vm i can see the Device but there is no kernel module for this device.

The missing modules are:
usbserial 
ftdi_sio

```

root@vm2:/# lsusb
Bus 001 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
oot@vm2:/# 
root@vm2:/# usb-devices
  ....
  T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
  D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
  P:  Vendor=0403 ProdID=6001 Rev=06.00
  S:  Manufacturer=FTDI
  S:  Product=FT232R USB UART
  S:  SerialNumber=A4VPKI9K
  C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=250mA
  I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

root@vm2:/# lsmod
Module                  Size  Used by
psmouse                97362  0
serio_raw              13211  0
virtio_balloon         13108  0
lp                     17799  0
parport                46562  1 lp
floppy                 70365  0
root@vm2:/#
root@vm2:/#
 
root@vm2:/# modprobe ftdi_sio
FATAL: Module ftdi_sio not found.
   
root@vm2:/# modprobe usbserial
FATAL: Module usbserial not found

```So i can passtrough the USB-Device but i can not use it on JEOS because of the missing kernel modules.
Is it possible to download the missing modules and install it to JEOS
or do i have to install a full server-version on my vm...

some ideas....

---

