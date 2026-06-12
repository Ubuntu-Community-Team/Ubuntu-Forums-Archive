---
title: "[Ubuntu-Linaro] USB-UART FTDI not showing as ttyUSB"
date: 2017-09-22
forum: Ubuntu/Debian BASED
---

### Post by ariel6 on 2017-09-22
Hello,

I am running Linaro which is based in ubuntu. I have an USB-UART bridge that I must use, but I cannot see it in /dev as ttyusb. This is what I get:

```

root@linaro-ubuntu-desktop:~# dmesg 
[  333.790000] usb 1-1.1: new full-speed USB device number 4 using xusbps-ehci

```

```
root@linaro-ubuntu-desktop:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 003: ID 0603:00f2 Novatek Microelectronics Corp.
Bus 001 Device 004: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC


```

```
root@linaro-ubuntu-desktop:~# ls /dev/ | grep USB
root@linaro-ubuntu-desktop:~# lsmod | grep ftdi

```
As you can see, the device is being detected but I should be seeing it in /dev as ttyUSB and I see it as usbdev1.4. I made a test with putty to connect to it but of course the connection was not possible. Should I install something? I tried with FTDI Drivers Installation Guide for Linux - FTDI Chip but this did not work.

Thanks for any help.

[h=3][TDI Drivers Installation Guide for Linux - FTDI Chip]("http://www.ftdichip.com/Support/Documents/AppNotes/AN_220_FTDI_Drivers_Installation_Guide_for_Linux.pdf")[/h]

---

### Post by oldos2er on 2017-09-22
Moved to Other OS, Ubuntu/Debian BASED.

---

