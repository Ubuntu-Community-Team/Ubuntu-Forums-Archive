---
title: "huawei ec1260"
date: 2011-03-18
forum: Ubuntu Studio
---

### Post by xuniaw on 2011-03-18
Hi can anyone help me configure my modem(huawei ec 1260) to use in ubuntu.my local provider said it wasn't compatible. i plugged it in my computer and did lsusb and found it but i do not know how to connect to the internet with it:confused:

---

### Post by sgx on 2011-03-21
> **xuniaw said:**
> Hi can anyone help me configure my modem(huawei ec 1260) to use in ubuntu.my local provider said it wasn't compatible. i plugged it in my computer and did lsusb and found it but i do not know how to connect to the internet with it:confused:
Hi, some usb modems are supported by usbmodeswitch, and editing a new
wvdial.conf. There is a usb_modeswitch.conf containing a list of modem
configs that are commented out with # to start each line. If there are
for huawei, or rebranded twins, try them out.

use the command 

sudo wvdialconf

to generate a wvdial.conf in /etc and edit with your provider details.
Mine looks like this:

[Dialer Defaults]
Modem = /dev/ttyACM0
Baud = 460800
Stupid Mode = 1
Auto DNS = 1
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = USB Modem
Phone = 
FlowControl = Hardware (CRTSCTS)
Dial Command = ATDT
Username = 
Password = 

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) for more info

usb_modeswitch.conf also goes in /etc

These two .conf files can be dragged to /etc after new installs after
the apps themselves are installed.

Cheers

---

