---
title: "USB to Serial not working Ubuntu 14.04"
date: 2014-03-02
forum: Ubuntu Development Version
---

### Post by bpowell2005 on 2014-03-02
Hello all.

I'm running a current Ubuntu 14.04.

I have an FTDI USB to Serial port adapter I'm trying to plug in for programming microcontrollers.

I *expect* to get a /dev/ttyUSB0 or something that I can then map to com1 in Wine for my program...but I'm not getting that dev/ttyUSB0.

Any ideas where I can look for this device?

Here is lsusb:
```

Bus 001 Device 002: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 008 Device 005: ID 0403:bd90 Future Technology Devices International, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Here is lsmod | grep ftdi:
```

ftdi_sio               48930  0 
usbserial              45014  1 ftdi_sio


```

---

### Post by QIII on 2014-03-02
[I]Moved to [B]Ubuntu +1


[/B][/I]14.04 is still in development.

---

### Post by rrnbtter on 2014-03-02
Greetings,
It is possible that usb-modeswitch is not working. usb-modeswitch allows the system to distinguish and switch between data drives such as flash media and devices such as modems, etc. This has been giving problems for a while. 
My suggestion is that you
1. sudo apt-get purge usb-modeswitch
2. sudo apt-get purge usb-modeswitch-data
3. delete both of these debs from /var/apt/cache/archives
I suggest that you have "proposed" enabled in your repositories. This should get you the latest fix. 
4. sudo apt-get update
5. sudo apt-get dist-upgrade
5. install usb-modeswitch from the software center.

That should fix it. But of course it will depend on if your "vendor/product" id's are included in the modeswitch data file. 
In the case listed in your post "Bus 008 Device 005: ID 0403:bd90 Future Technology Devices International, Ltd", the vendor would be 0x0403 and the product would be 0xbd90. We used to use "modprobe usbserial vendor=0xXXXX product =0xXXXX, but this is no longer supported. USB Serial is support by the kernel using the usb-modeswitch instead. 
Also, if the usb-modeswitch and usb-modeswitch-date debs don't match you will get an install error which will be unresolveable. In that case you will have to install a retro version from debian. Just google "usb-modeswitch debian", and install a matching set. You will have to purge what you have installed and again delete the debs from  the archives. 
This is the best I can do with this with my limited experience. Good luck.

---

### Post by rrnbtter on 2014-03-02
Greetings,
On second thought, you can check your installed versions with this....
1. apt-cache policy usb-modeswitch
You should get .....usb-modeswitch:
  Installed: 2.0.1+repack0-2
  Candidate: 2.0.1+repack0-2
2. apt-cache policy usb-modeswitch-data
You should get...
usb-modeswitch-data:
  Installed: 20131113-1
  Candidate: 20131113-1
If you get these results you should be OK, else use my previous post.

---

### Post by Lars Noodén on 2014-03-02
What does syslog say about things when you plug in the device?

---

### Post by bpowell2005 on 2014-03-02
> **rrnbtter said:**
> Greetings,
On second thought, you can check your installed versions with this....
1. apt-cache policy usb-modeswitch
You should get .....usb-modeswitch:
  Installed: 2.0.1+repack0-2
  Candidate: 2.0.1+repack0-2
2. apt-cache policy usb-modeswitch-data
You should get...
usb-modeswitch-data:
  Installed: 20131113-1
  Candidate: 20131113-1
If you get these results you should be OK, else use my previous post.

Hi rrnbtter: Here are my results:

```
apt-cache policy usb-modeswitch
usb-modeswitch:
  Installed: 1.2.3+repack0-1ubuntu3
  Candidate: 1.2.3+repack0-1ubuntu3
  Version table:
 *** 1.2.3+repack0-1ubuntu3 0
        500 http://mirrors.nl.eu.kernel.org/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
apt-cache policy usb-modeswitch-data
usb-modeswitch-data:
  Installed: 20120815-2
  Candidate: 20131113-1
  Version table:
     20131113-1 0
        500 http://mirrors.nl.eu.kernel.org/ubuntu/ trusty-proposed/main amd64 Packages
 *** 20120815-2 0
        500 http://mirrors.nl.eu.kernel.org/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```

As you can see, after adding "Proposed" there is a candidate for modeswitch-data, but it won't update without the update to modeswitch, which when I tried to download from Debian, started a chain of "unmet dependancies" ... that way leads to madness.

I should also note: I have a 13.10 box running, and it has the exact same versions of modeswitch and modeswitch-data...and it works just fine with this FTDI cable...if i had to guess, it's the ftdi_sio.ko module...but that's just a guess.

Thank you for your help!

---

### Post by bpowell2005 on 2014-03-02
> **Lars Noodén said:**
> What does syslog say about things when you plug in the device?

```
Mar  2 09:28:01 thameshouse kernel: [17972.532200] usb 8-1: new full-speed USB device number 24 using uhci_hcd
Mar  2 09:28:01 thameshouse kernel: [17972.722278] usb 8-1: New USB device found, idVendor=0403, idProduct=bd90
Mar  2 09:28:01 thameshouse kernel: [17972.722287] usb 8-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Mar  2 09:28:01 thameshouse kernel: [17972.722292] usb 8-1: Product: AXE027 PICAXE USB
Mar  2 09:28:01 thameshouse kernel: [17972.722297] usb 8-1: Manufacturer: Revolution
Mar  2 09:28:01 thameshouse mtp-probe: checking bus 8, device 24: "/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1"
Mar  2 09:28:01 thameshouse mtp-probe: bus: 8, device: 24 was not an MTP device

```

it's as if ftdi_sio never picks up or tries to link this device to a serial port...even if I try to modprobe ftdi_sio with the product and vendor info above.

Here is a different FTDI cable that DOES work...

```
Mar  2 09:29:58 thameshouse kernel: [18089.924187] usb 8-1: new full-speed USB device number 25 using uhci_hcd
Mar  2 09:29:59 thameshouse kernel: [18090.122190] usb 8-1: New USB device found, idVendor=0403, idProduct=6001
Mar  2 09:29:59 thameshouse kernel: [18090.122199] usb 8-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Mar  2 09:29:59 thameshouse kernel: [18090.122204] usb 8-1: Product: FT232R USB UART
Mar  2 09:29:59 thameshouse kernel: [18090.122209] usb 8-1: Manufacturer: FTDI
Mar  2 09:29:59 thameshouse kernel: [18090.122213] usb 8-1: SerialNumber: AD02CSHH
Mar  2 09:29:59 thameshouse kernel: [18090.130212] ftdi_sio 8-1:1.0: FTDI USB Serial Device converter detected
Mar  2 09:29:59 thameshouse kernel: [18090.130282] usb 8-1: Detected FT232RL
Mar  2 09:29:59 thameshouse kernel: [18090.130287] usb 8-1: Number of endpoints 2
Mar  2 09:29:59 thameshouse kernel: [18090.130292] usb 8-1: Endpoint 1 MaxPacketSize 64
Mar  2 09:29:59 thameshouse kernel: [18090.130297] usb 8-1: Endpoint 2 MaxPacketSize 64
Mar  2 09:29:59 thameshouse kernel: [18090.130302] usb 8-1: Setting MaxPacketSize 64
Mar  2 09:29:59 thameshouse kernel: [18090.132827] usb 8-1: FTDI USB Serial Device converter now attached to ttyUSB0
Mar  2 09:29:59 thameshouse mtp-probe: checking bus 8, device 25: "/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1"
Mar  2 09:29:59 thameshouse mtp-probe: bus: 8, device: 25 was not an MTP device
```

So, it seems ftdi_sio doesn't recognize my AXE027 cable...however, I *should* able able to modprobe and force it to work...as I do on my 13.10 box.

---

### Post by bpowell2005 on 2014-03-02
Here is a comparison of modinfo ftdi_sio between my 14.04 and 13.10 boxes..

14.04 (ftdi_sio does not work with AXE027 cable)
```
modinfo ftdi_sio
filename:       /lib/modules/3.13.0-14-generic/kernel/drivers/usb/serial/ftdi_sio.ko
license:        GPL
description:    USB FTDI Serial Converters Driver
author:         Greg Kroah-Hartman <greg@kroah.com>, Bill Ryder <bryder@sgi.com>, Kuba Ober <kuba@mareimbrium.org>, Andreas Mohr, Johan Hovold <jhovold@gmail.com>
srcversion:     5A0BA2EF703403D513F9624
alias:          usb:v0403p0011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p8E08d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pCFF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p8A28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0483p3747d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0483p3746d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20B7p0713d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p9868d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pA951d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF1Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF1Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF18d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAF9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1C0Cp0102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD578d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE729d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCA4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCA2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCA1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCA0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p937Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p937Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p9379d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p9378d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pED71d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pED73d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pED72d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pED74d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pA6D0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p9E90d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A79p6001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v165Cp0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1016d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1014d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p100Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p100Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p100Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0A1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0A0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C33p0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0FD8p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v9E88p9E8Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C6Cp04B2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04D8p000Ad*dc*dsc*dp*icFFiscFFip00in*
alias:          usb:v0456pF001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0456pF000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1CF1p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1CF1p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03EBp2109d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB99d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1BC9p6001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEF51d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEF50d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p1000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0F00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0E00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0D00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0C00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0B00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0A00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0900d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0700d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0500d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0400d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0107d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0105d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0104d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pED22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0584pB020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBDC8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCDAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCD9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCD8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBAF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1457p5118d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15BAp002Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15BAp0003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD739d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD738d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE700d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B91p0064d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE40Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEE18d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E6Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E69d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E68d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E67d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E66d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E65d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E64d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E63d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E62d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E61d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E60d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E59d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E58d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E57d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E56d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E55d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E54d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E53d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E52d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E51d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E50d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1781p0C30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDA74d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDA73d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDA72d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDA71d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDA70d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C7Dp0005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pCC4Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pCC49d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pCC48d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD678d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v128Dp0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFAF0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDD20d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p000Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p000Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p000Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p000Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pC1E0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pC991d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pC7D0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA88d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDC01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDC00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEA90d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF20d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D3Ap0300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D46p2021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D46p2020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF35d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF33d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF31d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:vDEEEp0303d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:vDEEEp0302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:vDEEEp0300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEC89d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEC88d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEEFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEEEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEEDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEECd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEEBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEEAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEE9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEE8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE548d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1342p0202d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD491d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD389d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD388d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF3C2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF3C1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF3C0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE520d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pBA02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC50d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC49d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC34d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC33d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC27d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC26d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC19d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC18d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06D3p0284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06CEp8311d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0647p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFD60d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v103Ep03E8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF460d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF680d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0F94p0005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0F94p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v093Cp0701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v093Cp0601d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFAD0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF44Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF44Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF44Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF449d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF448d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0EEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0EDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0ECd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0EBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0EAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0E9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0EFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0E8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF069d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF068d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB59d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE00Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B1FpC006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p8A98d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA33d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF39d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF38d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE6C8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB58d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE889d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE888d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE809d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE808d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC73d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC72d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC71d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC70d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF850d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA78d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B39p0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B39p0421d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0ACDp0300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52pA02Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52pA02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52pA02Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52pA02Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2883d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2873d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2863d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2853d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2843d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2833d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2823d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2813d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2882d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2872d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2862d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2852d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2842d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2832d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2881d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2871d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2861d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2851d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2841d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2831d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2443d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2433d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2423d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2413d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2442d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2432d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2422d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2412d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2441d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2431d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2421d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2411d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2223d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2213d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2222d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2212d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2221d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2211d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p9020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2104d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF857d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEBE0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF208d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF0C0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01EFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01EEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01EDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01ECd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01EBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01EAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01AFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01AEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01ADd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01ACd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01ABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01AAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0199d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0198d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0196d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0195d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0194d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0193d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0192d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0191d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0190d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0187d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0186d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0185d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0184d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0183d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0182d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0181d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0180d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0179d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0177d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0176d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0175d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0174d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0173d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0172d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0171d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0169d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0168d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0167d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0166d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0165d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0164d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0163d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0162d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0161d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0160d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0159d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0158d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0157d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0156d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0155d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0154d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0153d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0152d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0151d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0150d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0149d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0148d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0147d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0146d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0145d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0144d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0143d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0142d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0141d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0140d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0139d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0138d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0137d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0136d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0135d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0134d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0133d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0132d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0131d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0130d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0129d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0128d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0127d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0126d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0125d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0124d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0123d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0122d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0120d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0119d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0118d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0117d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0116d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0115d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0114d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0113d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0112d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0111d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0110d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0109d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0108d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0107d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0105d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0104d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB80d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA05d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA04d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFE38d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DCDp0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC8Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC8Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC82d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC08d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD780d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF0EEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF0E9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF0C8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1209p1006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1209p1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v104Dp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v104Dp3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v104Dp3000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFDDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFDCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFDBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFDAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFD9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFD8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pCAA0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6014d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFBFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p8372d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pC850d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC60d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF2D0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pB812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pB811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pB810d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD016d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD014d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pABB9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pABB8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p9F80d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFFA8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF60Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF608d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF7C0d*dc*dsc*dp*ic*isc*ip*in*
depends:        usbserial
intree:         Y
vermagic:       3.13.0-14-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D8:15:4E:5A:7F:10:87:36:C5:57:74:3D:27:44:13:0E:B1:BD:75:F4
sig_hashalgo:   sha512
parm:           ndi_latency_timer:NDI device latency timer override (int)
```

And here's 13.10...ftdi_sio DOES work with AXE027 cable (after modprobe)
```
modinfo ftdi_sio
filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/usb/serial/ftdi_sio.ko
license:        GPL
description:    USB FTDI Serial Converters Driver
author:         Greg Kroah-Hartman <greg@kroah.com>, Bill Ryder <bryder@sgi.com>, Kuba Ober <kuba@mareimbrium.org>, Andreas Mohr, Johan Hovold <jhovold@gmail.com>
srcversion:     118C2FFAFBDC88DB1344F66
alias:          usb:v0403p0011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p8E08d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pCFF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p8A28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0483p3747d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0483p3746d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20B7p0713d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p9868d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pA951d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF1Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF1Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF18d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAF9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDAF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1C0Cp0102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD578d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE729d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCA4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCA2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCA1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCA0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p937Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p937Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p9379d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p9378d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pED71d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pED73d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pED72d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pED74d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pA6D0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p9E90d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A79p6001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v165Cp0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1016d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1014d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p100Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p100Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p100Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1007d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A72p1000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0A1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0A0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C33p0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0FD8p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v9E88p9E8Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C6Cp04B2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04D8p000Ad*dc*dsc*dp*icFFiscFFip00in*
alias:          usb:v0456pF001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0456pF000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1CF1p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1CF1p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03EBp2109d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB99d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1BC9p6001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEF51d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEF50d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p8000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p1000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0F00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0E00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0D00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0C00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0B00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0A00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0900d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0700d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0500d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0400d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0107d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0105d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0104d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5050p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pED22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0584pB020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBDC8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCDAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCD9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBCD8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBAF8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1457p5118d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15BAp002Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15BAp0003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD739d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD738d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE700d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B91p0064d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE40Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEE18d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E6Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E69d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E68d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E67d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E66d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E65d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E64d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E63d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E62d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E61d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E60d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E5Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E59d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E58d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E57d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E56d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E55d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E54d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E53d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E52d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E51d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9E50d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2100p9001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1781p0C30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDA74d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDA73d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDA72d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDA71d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDA70d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C7Dp0005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pCC4Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pCC49d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pCC48d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD678d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v128Dp0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFAF0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDD20d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p000Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p000Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p000Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p000Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C26p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pC1E0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pC991d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pC7D0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA88d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDC01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDC00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEA90d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF20d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D3Ap0300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D46p2021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0D46p2020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF35d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF33d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF31d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF30d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pDF28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:vDEEEp0303d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:vDEEEp0302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:vDEEEp0300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEC89d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEC88d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEEFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEEEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEEDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEECd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEEBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEEAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEE9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEEE8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE548d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1342p0202d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD491d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD38Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD389d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD388d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF3C2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF3C1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF3C0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE520d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pBA02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC50d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC49d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC34d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC33d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC27d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC26d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC19d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC18d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0856pAC01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06D3p0284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06CEp8311d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0647p0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFD60d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v103Ep03E8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF460d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF680d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0F94p0005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0F94p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v093Cp0701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v093Cp0601d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFAD0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF9D0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF44Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF44Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF44Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF449d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF448d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0EEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0EDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0ECd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0EBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0EAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0E9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0EFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0E8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE0F0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF069d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF068d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB59d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE00Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B1FpC006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p8A98d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA33d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF3Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF39d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF38d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE6C8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF06Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB58d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB5Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE88Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE889d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE888d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE80Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE809d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pE808d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC73d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC72d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC71d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC70d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF850d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA78d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B39p0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B39p0421d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0ACDp0300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52pA02Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52pA02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52pA02Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52pA02Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2883d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2873d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2863d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2853d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2843d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2833d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2823d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2813d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2882d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2872d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2862d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2852d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2842d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2832d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2881d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2871d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2861d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2851d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2841d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2831d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2443d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2433d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2423d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2413d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2442d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2432d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2422d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2412d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2441d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2431d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2421d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2411d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2223d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2213d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2222d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2212d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2221d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2211d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p9020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2104d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0C52p2101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF857d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pEBE0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF208d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF0C0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01FAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01F0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01EFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01EEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01EDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01ECd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01EBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01EAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01E0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01DAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01D0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01CAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01C0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01BAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01B0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01AFd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01AEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01ADd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01ACd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01ABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01AAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp01A0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp019Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0199d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0198d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0196d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0195d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0194d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0193d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0192d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0191d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0190d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp018Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0187d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0186d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0185d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0184d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0183d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0182d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0181d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0180d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp017Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0179d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0178d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0177d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0176d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0175d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0174d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0173d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0172d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0171d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp016Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0169d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0168d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0167d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0166d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0165d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0164d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0163d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0162d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0161d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0160d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp015Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0159d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0158d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0157d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0156d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0155d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0154d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0153d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0152d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0151d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0150d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp014Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0149d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0148d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0147d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0146d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0145d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0144d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0143d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0142d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0141d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0140d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp013Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0139d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0138d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0137d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0136d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0135d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0134d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0133d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0132d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0131d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0130d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp012Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0129d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0128d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0127d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0126d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0125d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0124d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0123d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0122d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0120d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp011Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0119d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0118d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0117d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0116d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0115d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0114d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0113d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0112d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0111d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0110d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp010Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0109d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0108d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0107d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0106d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0105d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0104d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0102d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B3Dp0100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFB80d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA05d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA04d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFE38d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DCDp0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC8Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC8Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC82d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC0Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC08d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD780d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF0C8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1209p1006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1209p1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v104Dp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v104Dp3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v104Dp3000d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFDDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFDCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFDBd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFDAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFD9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pBFD8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFA10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pCAA0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6014d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFBFAd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p6001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p8372d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pC850d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFC60d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF2D0d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pB812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pB811d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pB810d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD016d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD014d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pD010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pABB8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403p9F80d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFFA8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pFF00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF60Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF608d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0403pF7C0d*dc*dsc*dp*ic*isc*ip*in*
depends:        usbserial
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           vendor:User specified vendor ID (default=0x0403) (ushort)
parm:           product:User specified product ID (ushort)
parm:           ndi_latency_timer:NDI device latency timer override (int)

```

Notice the bottom of this "good" version...parm lines for Vendor and Product...these are missing from the version that doesn't work...is this relevant?

---

### Post by bpowell2005 on 2014-03-02
If I can make some changes to the ftdi_sio.c and ftdi_sio.h files, and then recompile this module...I think I can fix my problem...however, I have no clue how to get the source for this module, and how to compile just the ftdi_sio.ko module...can anybody help with this?

Thanks!

---

### Post by Lars Noodén on 2014-03-03
Both ftdi_sio.c and ftdi_sio.h seem to be in the source for the kernel.  

```

$ find linux-3.13.0/ -name 'ftdi_sio*' -print
linux-3.13.0/drivers/usb/serial/ftdi_sio.c
linux-3.13.0/drivers/usb/serial/ftdi_sio_ids.h
linux-3.13.0/drivers/usb/serial/ftdi_sio.h


```

So you might try getting the source package and then building from that with your modifications.  If it works, be sure to submit a patch upstream.

---

### Post by rrnbtter on 2014-03-03
Greetings,
@bpowell2005.
Sorry for the delay in response. I work a 13.5 hour night shift. So out of touch till this morning. 
You can download a tar.gz file of both the old and new set from this link "www.fridaynitegang.com". 
My suggestion to get the new modeswitch working is to reinstall the old one with the older data file. 
Use Gdebi for the install and install the data file first since it is a depencency and the modeswitch won't 
install unless the dependency is present. 
You can make the process less confusing if you delete the entire contents of /var/apt/cache/archives and then update. 
This will prevent the installer from defaulting to already downloaded modules and dependencies.  After you get the older one 
reinstalled run a update/dist-upgrade and it should give you the newer version. The new version probably won't install if you
fail to empty your archive dir. I had the new version in my "held back" until I emptied the archive and then it automatically installed. 

Regarding the rest of your posts.... that is outside of my Linux skill set. Sorry!

---

### Post by bushidoka on 2014-09-06
I am having the same problem with a Garmin eTrex 20 - I'm expecting to get a /dev/ttyUSB0 device to show up, but am not getting it.   I have been at this for hours and am certain I have everything set up correctly.  I add the garmin_gps kernel module.   I get all sorts of nice things showing up in dmesg - just not a ttyUSB device.   lsusb shows my Garmin.

usb-devices has it show up as using the usb-storage driver, and I wonder if that is the issue.   Should it be using garmin-gps?  And how do I tell the system to force that?

T:  Bus=04 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#= 18 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=091e ProdID=2519 Rev=05.09
S:  SerialNumber=0000e61cc669
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


amckay@ubuntu-gig:~$ lsusb 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 005 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 022: ID 091e:2519 Garmin International eTrex 30
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Elfy on 2014-09-07
Thread from Trusty dev. If you've got issues with 14.04 after release this isn't the place for it, start a new thread in the general forum. Closed

---

