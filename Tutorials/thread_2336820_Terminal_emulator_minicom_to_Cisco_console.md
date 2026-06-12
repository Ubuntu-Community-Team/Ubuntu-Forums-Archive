---
title: "Terminal emulator minicom to Cisco console"
date: 2016-09-11
forum: Tutorials
---

### Post by Scott_Stumpf on 2016-09-11
Terminal emulator to access Cisco console port. Install the terminal emulator "minicom" and make operational a USB serial interface to Cisco console port. This example is accomplished using the terminal emulator minicom with Ubuntu. 
 
    1) Install the terminal emulator 
    get to a root command prompt 
    user:~$ sudo -i 
 
    install minicom 
    root:/# apt-get install minicom 
 
    2) To configre minicom some information is required. 
 
    make sure the cable connecting the computer to the Cisco console port is disconnected from the computer. 
    Enter this command   root:/# lsusb 
    here are the results: 
    Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
    Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
    Bus 003 Device 003: ID 08ff:2810 AuthenTec, Inc. AES2810  
    Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub  
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 
    3) Now plug the usb to console cable into the computer and Cisco device. 
    Enter this command root:/# lsusb 
    here are the results: 
    Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
    Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
    Bus 003 Device 003: ID 08ff:2810 AuthenTec, Inc. AES2810  
    Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub  
    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
    Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub  
    Bus 001 Device 003: ID 2478:2008 Tripp-Lite U209-000-R Serial Port  
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 
 
    4) Compare the two lists. The item in the second list that is not in the first list is the Cisco console device port. Seen here 
    Bus 001 Device 003: ID 2478:2008 Tripp-Lite U209-000-R Serial Port 
 
 
    5) The device ID is a hexadecimal number with two components. The first component is the vendor and the second is the product. These hexadecimal numbers are entered to configure the serial usb port (incase it has not been configured). Here is the command 
        root:/# modprobe usbserial vendor=0x2478 product=0x2008 
 
 
    6) To find the usb serial device connected to the Cisco console, enter the following command        root:/#dmesg | grep 2478 
 
    usb 1-2: New USB device found, idVendor=2478, idProduct=2008  
    usb 1-2: New USB device found, idVendor=2478, idProduct=2008 
 
 
    7) List the tty connections with the following command 
        root:/#dmesg | grep tty 
    console [tty0] enabled  
    ttyS4 at I/O 0xf0e0 (irq = 19, base_baud = 115200) is a 16550A  
    usb 1-2: pl2303 converter now attached to ttyUSB0  
    pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0  
    usb 1-2: pl2303 converter now attached to ttyUSB0  
 
    8) Results from list in step 6 the vendor code is visable and a new identifier "usb 1-2". Using the new identifier look in the list created in step 7. Find the new identifier. In the line item with the new identifier the tty device is provided. In this item it is ttyUSB0. Note minicom is case sensitive. tty is lower case and USB is upper case in this example. 
 
 
    9) Configure minicom 
minicom requires the USB serial port be configured so minicom may communicate with the Cisco console. command to run minicom 
    minicom -s 
 
    Arrow down to the line "Serial port setup" hit enter 
    enter A, then backspace to the first forward slash, looks like 
        /dev/ttyUSB3 
        /dev/ 
    now type   "ttyUSB0"   hit enter 
 
 
These settings are: 
   Baud rate: 9600 
   Data bits: 8 
   Parity: none 
   Stop bit: 1 
 
In minicom the above settings are item E are choosen by entering the associated letter: 
   baud rate 9600 enter C 
   Data bits enter V 
   Parirty enter L 
   Stop bit enter W 
 
   the above is a common interface, minicom has summerized this in letter Q

---

