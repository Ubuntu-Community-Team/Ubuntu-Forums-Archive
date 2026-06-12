---
title: "meerkat 11.04 Serial port question"
date: 2011-05-13
forum: System76 Support
---

### Post by eightbits89 on 2011-05-13
Hello Ubuntu users,
I have a fairly new System76 meerkat pc running Ubuntu 11.04.
After executing the following Terminal mode command,
dmesg | grep tty
I get the following output:
[    0.000000] console [tty0] enabled
[    1.224539] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.370692] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.625347] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.646278] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
This seems to indicate to me that I have at least two UART's installed on the motherboard. There is no external
connection for a serial port, but the system does recognize a USB to Serial adapter and the same command
 "dmesg | grep tty" adds in the USB port assignment. (seen below).
[ 2801.560337] usb 5-1: FTDI USB Serial Device converter now attached to ttyUSB0  //This added for USB adapter.

I also find from an Internet search that there are a couple of serial I/O programs, Cutecom and minicon.
Both of these app's are in the Ubuntu Software Center site.

Does anyone have any experience in using either of these programs and has anyone used a USB to Serial adapter and 
able to get the serial port(s) to work.

As there are no external serial port connections it would seem that the USB converter could be configured to work with one of the just mentioned programs.

I am rather new to Linux and I am looking for a way to use the Ubuntu (System76) system to work similar to the
Windows Hyperterm program.

Thanks to any suggestions and/or advice. :)

---

### Post by Flyers2391 on 2011-05-16
Hi, I tried using minicom a bit in the past but wasn't completely happy with it.  The main thing I missed (and still miss) is being cable to copy and paste from a text file over my usb to serial cable.  Besides that, for the past few years I've been using a program called "serial port terminal" (gtkterm) in the software center.  

Install that and then just select Configuration > Port and choose USB from the drop down.  

The best part of the converter is, back in the days of Windows, I needed the driver for it to work.  Every once in a while I would (for some unknown reason) need to re-install the driver.  This was Very Bad if I was at a customer's and couldn't do my work because the driver disappeared again.  Now, it Just Works :)

---

