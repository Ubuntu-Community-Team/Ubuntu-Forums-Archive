---
title: "Sierra Wireless Direct IP driver for Raspian"
date: 2016-09-29
forum: Ubuntu/Debian BASED
---

### Post by gerbaum on 2016-09-29
Hi,

I got a Sierra Wireless 7710 LTE Modem. It is connected with USB to my up to date raspberry.
The modem runs in Direct IP mode, I changed that with via AT command.

My Problem is, the modem isnt shown in ifconfig.

Lsusb

```
Bus 001 Device 010: ID 1199:68a3 Sierra Wireless, Inc. MC8700 Modem
Bus 001 Device 003: ID 0424:ec00 Standard Microsystems Corp. SMSC9512/9514 Fast Ethernet Adapter
Bus 001 Device 002: ID 0424:9514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Dmesg

```

[    9.714199] smsc95xx 1-1.1:1.0 eth0: link up, 100Mbps, full-duplex, lpa 0x4DE1
[   10.982303] usb 1-1.4: new high-speed USB device number 4 using dwc_otg
[   11.083940] usb 1-1.4: config 1 has an invalid interface number: 12 but max is 5
[   11.083966] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   11.083978] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   11.083991] usb 1-1.4: config 1 has no interface number 4
[   11.084002] usb 1-1.4: config 1 has no interface number 5
[   11.085628] usb 1-1.4: New USB device found, idVendor=1199, idProduct=68a3
[   11.085647] usb 1-1.4: New USB device strings: Mfr=4, Product=3, SerialNumber=5
[   11.085657] usb 1-1.4: Product: MC7710
[   11.085668] usb 1-1.4: Manufacturer: Sierra Wireless, Incorporated
[   11.085678] usb 1-1.4: SerialNumber: 358888842674285
[   11.116176] usbcore: registered new interface driver usbserial
[   11.116275] usbcore: registered new interface driver usbserial_generic
[   11.116358] usbserial: USB Serial support registered for generic
[   11.120757] usbcore: registered new interface driver sierra
[   11.120986] usbserial: USB Serial support registered for Sierra USB modem
[   11.124401] cdc_ether 1-1.4:1.12 eth1: register 'cdc_ether' at usb-3f980000.usb-1.4, CDC Ethernet Device, 00:a0:c6:00:00:00
[   11.124583] sierra 1-1.4:1.0: Sierra USB modem converter detected
[   11.124613] usbcore: registered new interface driver cdc_ether
[   11.126449] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB0
[   11.126606] sierra 1-1.4:1.1: Sierra USB modem converter detected
[   11.128066] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB1
[   11.128242] sierra 1-1.4:1.2: Sierra USB modem converter detected
[   11.129210] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB2
[   11.129362] sierra 1-1.4:1.3: Sierra USB modem converter detected
[   11.130161] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB3
[   11.496152] random: nonblocking pool is initialized
[   13.895881] Bluetooth: Core ver 2.21
[   13.896111] NET: Registered protocol family 31
[   13.896139] Bluetooth: HCI device and connection manager initialized
[   13.896182] Bluetooth: HCI socket layer initialized
[   13.896208] Bluetooth: L2CAP socket layer initialized
[   13.896269] Bluetooth: SCO socket layer initialized
[   13.944034] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.944067] Bluetooth: BNEP filters: protocol multicast
[   13.944101] Bluetooth: BNEP socket layer initialized
[   16.380500] usb 1-1.4: USB disconnect, device number 4
[   16.381529] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[   16.381657] sierra 1-1.4:1.0: device disconnected
[   16.382589] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[   16.382715] sierra 1-1.4:1.1: device disconnected
[   16.387010] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[   16.387149] sierra 1-1.4:1.2: device disconnected
[   16.389326] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3
[   16.389464] sierra 1-1.4:1.3: device disconnected
[   16.389803] cdc_ether 1-1.4:1.12 eth1: unregister 'cdc_ether' usb-3f980000.usb-1.4, CDC Ethernet Device
[   24.042261] usb 1-1.4: new high-speed USB device number 5 using dwc_otg
[   24.143901] usb 1-1.4: config 1 has an invalid interface number: 12 but max is 5
[   24.143931] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   24.143949] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   24.143967] usb 1-1.4: config 1 has no interface number 4
[   24.143983] usb 1-1.4: config 1 has no interface number 5
[   24.145700] usb 1-1.4: New USB device found, idVendor=1199, idProduct=68a3
[   24.145721] usb 1-1.4: New USB device strings: Mfr=4, Product=3, SerialNumber=5
[   24.145754] usb 1-1.4: Product: MC7710
[   24.145771] usb 1-1.4: Manufacturer: Sierra Wireless, Incorporated
[   24.145786] usb 1-1.4: SerialNumber: 358888842674285
[   24.149012] sierra 1-1.4:1.0: Sierra USB modem converter detected
[   24.150269] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB0
[   24.151040] sierra 1-1.4:1.1: Sierra USB modem converter detected
[   24.162942] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB1
[   24.163681] sierra 1-1.4:1.2: Sierra USB modem converter detected
[   24.164704] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB2
[   24.165386] sierra 1-1.4:1.3: Sierra USB modem converter detected
[   24.166298] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB3
[   24.170762] cdc_ether 1-1.4:1.12 eth1: register 'cdc_ether' at usb-3f980000.usb-1.4, CDC Ethernet Device, 00:a0:c6:00:00:00
[   29.438025] usb 1-1.4: USB disconnect, device number 5
[   29.438842] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[   29.438966] sierra 1-1.4:1.0: device disconnected
[   29.439805] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[   29.439933] sierra 1-1.4:1.1: device disconnected
[   29.442809] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[   29.443037] sierra 1-1.4:1.2: device disconnected
[   29.444274] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3
[   29.444424] sierra 1-1.4:1.3: device disconnected
[   29.444931] cdc_ether 1-1.4:1.12 eth1: unregister 'cdc_ether' usb-3f980000.usb-1.4, CDC Ethernet Device
[   39.142257] usb 1-1.4: new high-speed USB device number 6 using dwc_otg
[   39.243865] usb 1-1.4: config 1 has an invalid interface number: 12 but max is 5
[   39.243913] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   39.243931] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   39.243949] usb 1-1.4: config 1 has no interface number 4
[   39.243965] usb 1-1.4: config 1 has no interface number 5
[   39.245628] usb 1-1.4: New USB device found, idVendor=1199, idProduct=68a3
[   39.245648] usb 1-1.4: New USB device strings: Mfr=4, Product=3, SerialNumber=5
[   39.245664] usb 1-1.4: Product: MC7710
[   39.245680] usb 1-1.4: Manufacturer: Sierra Wireless, Incorporated
[   39.245695] usb 1-1.4: SerialNumber: 358888842674285
[   39.248862] sierra 1-1.4:1.0: Sierra USB modem converter detected
[   39.250093] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB0
[   39.250983] sierra 1-1.4:1.1: Sierra USB modem converter detected
[   39.253084] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB1
[   39.253947] sierra 1-1.4:1.2: Sierra USB modem converter detected
[   39.254983] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB2
[   39.255720] sierra 1-1.4:1.3: Sierra USB modem converter detected
[   39.256684] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB3
[   39.261168] cdc_ether 1-1.4:1.12 eth1: register 'cdc_ether' at usb-3f980000.usb-1.4, CDC Ethernet Device, 00:a0:c6:00:00:00
[   44.543968] usb 1-1.4: USB disconnect, device number 6
[   44.544748] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[   44.544861] sierra 1-1.4:1.0: device disconnected
[   44.545637] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[   44.545752] sierra 1-1.4:1.1: device disconnected
[   44.546903] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[   44.547048] sierra 1-1.4:1.2: device disconnected
[   44.548150] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3
[   44.548295] sierra 1-1.4:1.3: device disconnected
[   44.548808] cdc_ether 1-1.4:1.12 eth1: unregister 'cdc_ether' usb-3f980000.usb-1.4, CDC Ethernet Device
[   53.742253] usb 1-1.4: new high-speed USB device number 7 using dwc_otg
[   53.843867] usb 1-1.4: config 1 has an invalid interface number: 12 but max is 5
[   53.843896] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   53.843914] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   53.843932] usb 1-1.4: config 1 has no interface number 4
[   53.843948] usb 1-1.4: config 1 has no interface number 5
[   53.845688] usb 1-1.4: New USB device found, idVendor=1199, idProduct=68a3
[   53.845726] usb 1-1.4: New USB device strings: Mfr=4, Product=3, SerialNumber=5
[   53.845742] usb 1-1.4: Product: MC7710
[   53.845758] usb 1-1.4: Manufacturer: Sierra Wireless, Incorporated
[   53.845773] usb 1-1.4: SerialNumber: 358888842674285
[   53.848934] sierra 1-1.4:1.0: Sierra USB modem converter detected
[   53.850144] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB0
[   53.851039] sierra 1-1.4:1.1: Sierra USB modem converter detected
[   53.862913] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB1
[   53.863677] sierra 1-1.4:1.2: Sierra USB modem converter detected
[   53.865018] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB2
[   53.865687] sierra 1-1.4:1.3: Sierra USB modem converter detected
[   53.866916] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB3
[   53.871980] cdc_ether 1-1.4:1.12 eth1: register 'cdc_ether' at usb-3f980000.usb-1.4, CDC Ethernet Device, 00:a0:c6:00:00:00
[   59.137915] usb 1-1.4: USB disconnect, device number 7
[   59.138703] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[   59.138801] sierra 1-1.4:1.0: device disconnected
[   59.139486] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[   59.139574] sierra 1-1.4:1.1: device disconnected
[   59.140226] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[   59.140314] sierra 1-1.4:1.2: device disconnected
[   59.141039] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3
[   59.141129] sierra 1-1.4:1.3: device disconnected
[   59.141416] cdc_ether 1-1.4:1.12 eth1: unregister 'cdc_ether' usb-3f980000.usb-1.4, CDC Ethernet Device
[   66.802267] usb 1-1.4: new high-speed USB device number 8 using dwc_otg
[   66.903794] usb 1-1.4: config 1 has an invalid interface number: 12 but max is 5
[   66.903822] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   66.903839] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   66.903857] usb 1-1.4: config 1 has no interface number 4
[   66.903873] usb 1-1.4: config 1 has no interface number 5
[   66.905630] usb 1-1.4: New USB device found, idVendor=1199, idProduct=68a3
[   66.905651] usb 1-1.4: New USB device strings: Mfr=4, Product=3, SerialNumber=5
[   66.905667] usb 1-1.4: Product: MC7710
[   66.905682] usb 1-1.4: Manufacturer: Sierra Wireless, Incorporated
[   66.905698] usb 1-1.4: SerialNumber: 358888842674285
[   66.908994] sierra 1-1.4:1.0: Sierra USB modem converter detected
[   66.910124] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB0
[   66.910940] sierra 1-1.4:1.1: Sierra USB modem converter detected
[   66.912259] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB1
[   66.913135] sierra 1-1.4:1.2: Sierra USB modem converter detected
[   66.914191] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB2
[   66.914922] sierra 1-1.4:1.3: Sierra USB modem converter detected
[   66.915889] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB3
[   66.920623] cdc_ether 1-1.4:1.12 eth1: register 'cdc_ether' at usb-3f980000.usb-1.4, CDC Ethernet Device, 00:a0:c6:00:00:00
[   72.195655] usb 1-1.4: USB disconnect, device number 8
[   72.196451] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[   72.196567] sierra 1-1.4:1.0: device disconnected
[   72.197362] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[   72.197478] sierra 1-1.4:1.1: device disconnected
[   72.198656] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[   72.198805] sierra 1-1.4:1.2: device disconnected
[   72.199882] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3
[   72.200045] sierra 1-1.4:1.3: device disconnected
[   72.200606] cdc_ether 1-1.4:1.12 eth1: unregister 'cdc_ether' usb-3f980000.usb-1.4, CDC Ethernet Device
[   79.602254] usb 1-1.4: new high-speed USB device number 9 using dwc_otg
[   79.703884] usb 1-1.4: config 1 has an invalid interface number: 12 but max is 5
[   79.703911] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   79.703928] usb 1-1.4: config 1 has an invalid interface number: 13 but max is 5
[   79.703946] usb 1-1.4: config 1 has no interface number 4
[   79.703962] usb 1-1.4: config 1 has no interface number 5
[   79.705660] usb 1-1.4: New USB device found, idVendor=1199, idProduct=68a3
[   79.705682] usb 1-1.4: New USB device strings: Mfr=4, Product=3, SerialNumber=5
[   79.705697] usb 1-1.4: Product: MC7710
[   79.705713] usb 1-1.4: Manufacturer: Sierra Wireless, Incorporated
[   79.705728] usb 1-1.4: SerialNumber: 358888842674285
[   79.708857] sierra 1-1.4:1.0: Sierra USB modem converter detected
[   79.710056] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB0
[   79.710880] sierra 1-1.4:1.1: Sierra USB modem converter detected
[   79.712456] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB1
[   79.713367] sierra 1-1.4:1.2: Sierra USB modem converter detected
[   79.714374] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB2
[   79.715120] sierra 1-1.4:1.3: Sierra USB modem converter detected
[   79.716067] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB3
[   79.720690] cdc_ether 1-1.4:1.12 eth1: register 'cdc_ether' at usb-3f980000.usb-1.4, CDC Ethernet Device, 00:a0:c6:00:00:00
[   84.997345] usb 1-1.4: USB disconnect, device number 9
[   84.998141] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[   84.998245] sierra 1-1.4:1.0: device disconnected
[   84.998912] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[   84.999001] sierra 1-1.4:1.1: device disconnected
[   84.999658] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[   84.999748] sierra 1-1.4:1.2: device disconnected
[   85.000469] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3
[   85.000560] sierra 1-1.4:1.3: device disconnected
[   85.000845] cdc_ether 1-1.4:1.12 eth1: unregister 'cdc_ether' usb-3f980000.usb-1.4, CDC Ethernet Device
[   86.252252] usb 1-1.4: new high-speed USB device number 10 using dwc_otg
[   86.354554] usb 1-1.4: New USB device found, idVendor=1199, idProduct=68a3
[   86.354580] usb 1-1.4: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[   86.354596] usb 1-1.4: Product: MC7710
[   86.354612] usb 1-1.4: Manufacturer: Sierra Wireless, Incorporated
[   86.354627] usb 1-1.4: SerialNumber: 358888842674285
[   86.356645] sierra 1-1.4:1.0: Sierra USB modem converter detected
[   86.357478] usb 1-1.4: Sierra USB modem converter now attached to ttyUSB0

```

There is a thread which links to a direct IP driver for the modem and describes how to install the driver till kernel 3.0.x

[https://mycusthelp.net/SIERRAWIRELESS/_cs/AnswerDetail.aspx?aid=44](https://mycusthelp.net/SIERRAWIRELESS/_cs/AnswerDetail.aspx?aid=44)

But it gives that error:

```
Compiling  sierra.c sierra_net.c
make[1]: *** /lib/modules/4.4.21-v7+/build: No such file or directory.  Stop.
Makefile:39: recipe for target 'default' failed
make: *** [default] Error 2

```

Also I found the driver till version 4.7 here:

[http://lxr.free-electrons.com/source/drivers/usb/serial/sierra.c](http://lxr.free-electrons.com/source/drivers/usb/serial/sierra.c)

But I dont know how to install it.

I hope you can help me out here, I'm just starting to get used to Linux.

Thx

---

### Post by QIII on 2016-09-29
Moved to Ubuntu/Debian BASED

---

