---
title: "FTDI Communication problem"
date: 2014-04-02
forum: Ubuntu Application Development
---

### Post by David_Freese on 2014-04-02
I have a temperature and humidity monitor that uses a FTDI232 chip to communicate via USB.  I am running Ubuntu 12.04.  The device automatically loads the ftdi_sio module, and shows up as /dev/ttyUSB0.

```

miil@breast-daq ~$ dmesg | grep FTDI
[  456.477589] ftdi_sio 6-9:1.0: FTDI USB Serial Device converter detected
[  456.478035] usb 6-9: FTDI USB Serial Device converter now attached to ttyUSB0

```

```

miil@breast-daq ~$ lsusb
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 006 Device 002: ID 046b:ff01 American Megatrends, Inc. 
Bus 006 Device 006: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 004: ID 046b:ff10 American Megatrends, Inc. 

```

I have tested this out with minicom and gtkterm on OpenSuse, and have been able to get this to read no problem. However, when I open gtkterm, I receive no response from the device.  Trying to toggle the DTR or RTS lines in gtkterm results in a "Control signals read: Input/output error."  Does anyone have any thoughts as to why this might be the case?  I most likely will be able to unmount the ftdi_sio driver and use the ftdi2xx driver, however, I would like to avoid that if possible.

Additionally, I have been able to communicate with devices at /dev/ttyS0 on a standard serial port, and at /dev/ttyUSB1 when serial devices were attached by a usb to serial converter.

Thanks!

---

