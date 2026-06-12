---
title: "How to run Zain, Canar &amp; Sudani modems in Ubuntu"
date: 2010-09-20
forum: Sudan Team
---

### Post by zero-n on 2010-09-20
[CENTER][COLOR=Red][B]This guide is not a full guide yet it will be by your help ;)

[/B][/COLOR][/CENTER]

This guide is intended to be a full guide for USB,PCMCIA & phone modems for all Internet service provider in Sudan.

I don't have all kinds of different modems :???: , so if someone is interested to complete this guide with me He/She is welcome.



_[COLOR=Red]**For Ubuntu 10.10:**[/COLOR]_
usb_modeswitch is installed by default with the new Ubuntu release (  maverick meerkat ) so you can escape usb_modeswitch installation part.

_[COLOR=Red]**Note:**[/COLOR]_
_For this guide i am using:_
- Ubuntu 10.04 LTS.
- [usb-modeswitch]("http://www.draisberghof.de/usb_modeswitch/")
- [sakis3g]("http://www.sakis3g.org/").

**Installing usb-modeswitch:**
check [this]("http://ubuntuforums.org/showthread.php?p=9867386#post9867386") guide.

**Installing sakis3g:**
check [this]("http://ubuntuforums.org/showthread.php?p=9879795#post9879795") guide.[COLOR=Red][B]

Update 12/08/2011:[/B][/COLOR]
[GUI tools for Zain Connect and Sudani mDSL.]("http://ubuntuforums.org/showthread.php?p=11143885#post11143885")


**============================****====================**[INDENT][INDENT][INDENT][INDENT][INDENT][B]USB Modems
[/B] [/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]**============================****====================**





[B]==========================
1- Zain's Huawei E1692 USB modem[/B][B]:
======================[/B]**====**
[IMG]http://www.gambinoshop.it/shop/images/pccard_e1692.jpg[/IMG]
```

_**Zain Part 1: (defining the modem)**_
1- Add a configuration usb_modeswitch file for Huawei E1692 USB modem:
[code]
sudo gedit /etc/usb_modeswitch.d/12d1:1446

```2- Paste the following lines & save the file:
```

#---------------------
# Zain's Huawei E1692:
#---------------------

DisableSwitching=0
EnableLogging=0

DefaultVendor=  0x12d1
DefaultProduct= 0x1446

TargetVendor=   0x12d1
TargetProduct=  0x140c

MessageContent="55534243000000000000000000000011060000000000000000000000000000"

CheckSuccess=5

```3- Reboot your system



_**Zain **__**Part 2: (Editing connection**__** information**_[U][B])
[/B][/U]You can use your preferable program, i will use wvdial , check [this]("http://ubuntuforums.org/showthread.php?p=8523823#post8523823") guide for installing wvdial.

1- Run wvdial configuration tool:
```

sudo wvdialconf 

```You see output like this:
```

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
ttyUSB0<Info>: Device or resource busy
Modem Port Scan<*1>: USB0 
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB2.
Modem configuration written to /etc/wvdial.conf.
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```2- Edit wvdial.conf:
```

sudo gedit /etc/wvdial.conf

```enter any username & password as you like Zain connection have not username & password but wvdial will not accept blank user & password fields so we need to add another option which is [COLOR=Red]**Stupid Mode = 1**[/COLOR] & the file will be:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
New PPPD = yes
Modem = /dev/ttyUSB2
Username = zain
Password = zain
Baud = 9600

```[COLOR=Red]
**Note:**[/COLOR] ttyUSB2 is my modem this value may differ in your system (wvdialconf will add it automatically so never try to change it).



_**Zain **_[U][B]Part 3: (connect & disconnect)
[/B][/U]**connect:**
```

sudo wvdial

```[B]
disconnect:[/B]
```

press Ctrl+C

```[/code][B]==========================
2- Zain's WM500 USB modem[/B][B]:
======================[/B][B]====
[/B][B][IMG]http://i56.tinypic.com/142sp4y.jpg[/IMG]
[/B]```

_**Zain Part 1: (defining the modem)**_
1- Add a configuration usb_modeswitch file for WM500 USB modem:
[code]
sudo gedit /etc/usb_modeswitch.d/05c6:f000

```2- Paste the following lines & save the file:
```

#------------------------
# Zain's WM500 USB modem:
#------------------------

DefaultVendor=  0x05c6
DefaultProduct= 0xf000

TargetVendor=   0x05c6
TargetProduct=  0x9000

CheckSuccess=20

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"

```3- Make a shell script for loading specific modules need for the modem:
```

sudo gedit /etc/init.d/wm500

```4-paste the following & save the file:
```

#!/bin/sh
modprobe -v option
sleep 2
echo "0x05c6 0x9000" >/sys/bus/usb-serial/drivers/option1/new_id

```5- Give the script execution permission:
```

sudo chmod +x /etc/init.d/wm500

```6- Reboot you system.



_**Zain **__**Part 2&3: (Editing connection**__** information**__** + **__**connect & disconnect**__**)**_
I have tried to use wvdialconf without any luck it gave me this result:
```

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- ERROR
ttyUSB1<*1>: ATQ0 V1 E1 &C1 -- ERROR
ttyUSB1<*1>: ATQ0 V1 E1 &D2 -- ERROR
ttyUSB1<*1>: ATQ0 V1 E1 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: Alpha
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- OK
ttyUSB2<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- ERROR
ttyUSB2<*1>: ATQ0 V1 E1 &C1 -- ERROR
ttyUSB2<*1>: ATQ0 V1 E1 &D2 -- ERROR
ttyUSB2<*1>: ATQ0 V1 E1 +FCLASS=0 -- OK
ttyUSB2<*1>: Modem Identifier: ATI -- Manufacturer: Alpha
ttyUSB2<*1>: Speed 9600: AT -- OK
ttyUSB2<*1>: Max speed is 9600; that should be safe.
ttyUSB2<*1>: ATQ0 V1 E1 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB1.
Modem configuration written to /etc/wvdial.conf.
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 +FCLASS=0"
ttyUSB2<Info>: Speed 9600; init "ATQ0 V1 E1 +FCLASS=0"


```[COLOR=Red]**Notice: **[/COLOR]
ttyUSB2<*1>: ATQ0 V1 E1 S0=0 -- ERROR
ttyUSB2<*1>: ATQ0 V1 E1 &C1 -- ERROR
ttyUSB2<*1>: ATQ0 V1 E1 &D2 -- ERROR

& wvdial won't run successfully because of these errors.


so we need to use another tool [COLOR=Red]**Sakis3G**[/COLOR].

1- Install sakis3g using [this]("http://ubuntuforums.org/showthread.php?t=1580427") guide or any other guide.

2- From your terminal run sakis3g:
```

sudo sakis3g 

```3- From sagis3g menu select [COLOR=Red]**Connect with 3G**[/COLOR] & enter your PIN number normally it's 0000.

4- Select [COLOR=Red]**Reported by your modem (INTERNET)**[/COLOR].

5- Zain uses blank username & password but leave username field empty this will lead to close connection attempt & going back to sakis3g main window so enter **[COLOR=Red]APN_USER[/COLOR]** 
as your username & [COLOR=Red]**APN_PASS**[/COLOR] as your password.

Now if everything is ok you will see a message box contains:
```

WM500  connected to Zain SDN (63401)

```[/code][B]==========================
3- Zain's Huwaei E220 USB modem[/B][B]:
======================[/B]**====**
[IMG]http://i52.tinypic.com/dmy495.jpg[/IMG]
```

_**Zain Part 1: (defining the modem)**_
1- Add a configuration usb_modeswitch file for Huawei E220 USB modem:
[code]
sudo gedit /etc/usb_modeswitch.d/12d1:1003

```2- Paste the following lines & save the file:
```

#------------------------------------------------
# Zain's Huawei E220, E230, E270, E870 USB modem:
#------------------------------------------------

DefaultVendor= 0x12d1
DefaultProduct=0x1003

TargetClass=0xff

CheckSuccess=20

HuaweiMode=1

```3- Reboot you system.


_**Zain **__**Part 2: (Editing connection**__**)**_
You can use your preferable program, i will use wvdial , check [this]("http://ubuntuforums.org/showthread.php?p=8523823#post8523823") guide for installing wvdial.

1- Run wvdial configuration tool:
```

sudo wvdialconf 

```You see output like this:
```

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```2- Edit wvdial.conf:
```

sudo gedit /etc/wvdial.conf

```enter any username & password as you like Zain connection  have not username & password but wvdial will not accept blank user  & password fields so we need to add another option which is [COLOR=Red]**Stupid Mode = 1**[/COLOR] & the file will be:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
New PPPD = yes
Modem = /dev/ttyUSB0
Username = zain
Password = zain
Baud = 9600

```[COLOR=Red]
**Note:**[/COLOR] ttyUSB0 is my modem this value may differ in your  system (wvdialconf will add it automatically so never try to change it).

_**Zain **_[U][B]Part 3: (connect & disconnect)
[/B][/U]**connect:**
```

sudo wvdial

```[B]
disconnect:[/B]
```

press Ctrl+C

```[/code][B]  ==============================
4- Canar's C-motech CNU-680 USB modem[/B][B]:
=======================[/B][B]=======
[IMG]http://1.bp.blogspot.com/_SzZlNc2uTO0/S9PHPZr6HEI/AAAAAAAABak/og80q2c1P0w/s320/C-motech+CNU-680.JPG[/IMG]
[/B]```

_**Canar Part 1: (defining the modem)**_
1- Add a udev rules for the modem:
[code]
sudo gedit /etc/udev/rules.d/85-cmotech-qtmodem.rules 

```2- Paste the following lines & save the file:
```

# C-motech CNU-680 modem inserted before rdevchg
ACTION=="add", KERNEL=="sg*", SUBSYSTEMS=="usb", SYSFS{idVendor}=="16d8", SYSFS{idProduct}=="6803", RUN+="/usr/bin/cmotech-qtmodem-in -26627"

# C-motech CNU-680A modem data interface
KERNEL=="ttyACM*", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:v16D8p680A*", SYMLINK+="cmotechdata"

# C-motech CNU-680A modem data interface
KERNEL=="ttyUSB*", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{bInterfaceNumber}=="01", ATTRS{modalias}=="usb:v16D8p680A*", SYMLINK+="cmotechdata"

# C-motech CNU-680A modem inserted after rdevchg
ACTION=="add", KERNEL=="tty*", SUBSYSTEMS=="usb", SYSFS{idVendor}=="16d8", SYSFS{idProduct}=="680a", RUN+="/usr/bin/cmotech-qtmodem-in 26634"

# C-motech CNU-680A modem removed
ACTION=="remove", SUBSYSTEMS=="usb", ENV{PRODUCT}=="16d8/680a/0", RUN+="/usr/bin/cmotech-qtmodem-out 26634"

# C-motech CNU-680 modem data interface
KERNEL=="ttyACM*", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:v16D8p6803*", SYMLINK+="cmotechdata"

# C-motech CNU-680 modem data interface
KERNEL=="ttyUSB*", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{bInterfaceNumber}=="00", ATTRS{modalias}=="usb:v16D8p6803*", SYMLINK+="cmotechdata"

# C-motech CNU-680 modem dm interface
KERNEL=="ttyUSB*", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{bInterfaceNumber}=="01", ATTRS{modalias}=="usb:v16D8p6803*", SYMLINK+="cmotechdm"

# C-motech CNU-680 modem inserted
ACTION=="add", KERNEL=="tty*", SUBSYSTEMS=="usb", SYSFS{idVendor}=="16d8", SYSFS{idProduct}=="6803", RUN+="/usr/bin/cmotech-qtmodem-in 26627"

# C-motech CNU-680 modem removed
ACTION=="remove", SUBSYSTEMS=="usb", ENV{PRODUCT}=="16d8/6803/0", RUN+="/usr/bin/cmotech-qtmodem-out 26627"

# C-motech CNU-550 modem data interface
KERNEL=="ttyACM*", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:v16D8p5543*", SYMLINK+="cmotechdata"

# C-motech CNU-550 modem data interface
KERNEL=="ttyUSB*", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{bInterfaceNumber}=="01", ATTRS{modalias}=="usb:v16D8p5543*", SYMLINK+="cmotechdata"

# C-motech CNU-550 modem inserted
ACTION=="add", KERNEL=="tty*", SUBSYSTEMS=="usb", SYSFS{idVendor}=="16d8", SYSFS{idProduct}=="5543", RUN+="/usr/bin/cmotech-qtmodem-in 21827"

# C-motech CNU-550 modem removed
ACTION=="remove", SUBSYSTEMS=="usb", ENV{PRODUCT}=="16d8/5543/0", RUN+="/usr/bin/cmotech-qtmodem-out 21827"

# C-motech CNM-650 modem data interface
KERNEL=="ttyACM*", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{modalias}=="usb:v16D8p6533*", SYMLINK+="cmotechdata"

# C-motech CNM-650 modem data interface
KERNEL=="ttyUSB*", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{bInterfaceNumber}=="01", ATTRS{modalias}=="usb:v16D8p6533*", SYMLINK+="cmotechdata"

# C-motech CNM-650 modem dm interface
KERNEL=="ttyUSB*", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{bInterfaceNumber}=="03", ATTRS{modalias}=="usb:v16D8p6533*", SYMLINK+="cmotechdm"

# C-motech CNM-650 modem inserted
ACTION=="add", KERNEL=="tty*", SUBSYSTEMS=="usb", SYSFS{idVendor}=="16d8", SYSFS{idProduct}=="6533", RUN+="/usr/bin/cmotech-qtmodem-in 25907"

# C-motech CNM-650 modem removed
ACTION=="remove", SUBSYSTEMS=="usb", ENV{PRODUCT}=="16d8/6533/0", RUN+="/usr/bin/cmotech-qtmodem-out 25907"

# C-motech CGU628 modem inserted before rdevchg
ACTION=="add", KERNEL=="sg*", SUBSYSTEMS=="usb", SYSFS{idVendor}=="16d8", SYSFS{idProduct}=="628a", RUN+="/usr/bin/cmotech-qtmodem-in 25226"

# C-motech CGU628 modem data interface
KERNEL=="tty[AU]*", SUBSYSTEM=="tty", SUBSYSTEMS=="usb", ATTRS{bInterfaceNumber}=="00", ATTRS{modalias}=="usb:v16D8p628a*", SYMLINK+="cmotechdata"

# C-motech CGU628 modem inserted
ACTION=="add", KERNEL=="tty*", SUBSYSTEMS=="usb", SYSFS{idVendor}=="16d8", SYSFS{idProduct}=="628a", RUN+="/usr/bin/cmotech-qtmodem-in 25226"

# C-motech CGU628 modem removed
ACTION=="remove", SUBSYSTEMS=="usb", ENV{PRODUCT}=="16d8/628a/0", RUN+="/usr/bin/cmotech-qtmodem-out 25226"

```3- Make a shell script for loading specific modules need for the modem:
```

sudo gedit /etc/init.d/cmotech 

```4- paste the following:
```

#!/bin/sh

case "$1" in
start)
    modprobe sg
    modprobe usb-storage
    modprobe cdc_acm
    modprobe option
    echo -n "0x16d8 0x6803" > /sys/bus/usb-serial/drivers/option1/new_id
    echo -n "0x16d8 0x680a" > /sys/bus/usb-serial/drivers/option1/new_id
    echo -n "0x16d8 0x6533" > /sys/bus/usb-serial/drivers/option1/new_id
    echo -n "0x16d8 0x5543" > /sys/bus/usb-serial/drivers/option1/new_id
    ;;
esac

```5- Give the script execution permission:
```

sudo chmod +x /etc/init.d/cmotech

```6- Reboot you system.



_**Canar **__**Part 2: (Editing connection**__** information**__**)**_
You can use your preferable program, i will use wvdial , check [this]("http://ubuntuforums.org/showthread.php?p=8523823#post8523823") guide for installing wvdial.

1- Run wvdial configuration tool:
```

sudo wvdialconf 

```You see output like this:
```

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: C-MOTECH Co., Ltd.
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: USB2 

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```2- Edit wvdial.conf:
```

sudo gedit /etc/wvdial.conf

```add your username,password & phone number ( #777 )
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = yes
ISDN = 0
Modem Type = Analog Modem
Phone = #777
Modem = /dev/ttyUSB0
Username = *******@canar.go
Carrier Check = no
Password = ********
Baud = 9600

```[COLOR=Red]**Note:**[/COLOR] ttyUSB0 is my modem this value may differ in your system (wvdialconf will add it automatically so never try to change it).



_**C**_[U][B]anar Part 3: (connect & disconnect)
[/B][/U]**connect:**
```

sudo wvdial

```[B]
disconnect:[/B]
```

press Ctrl+C

```[/code][B]==========================
5- Sudani's ZTE AC8700 USB modem[/B][B]:
=======================[/B]**===**
[IMG]http://www.ztemt.com.cn/ennewzte/uploadimages/1199886659638.jpg[/IMG]
```

[U][B]Sudani Part 1: (defining the modem)
[/B][/U] No need for defining cause the device will be recognized as a modem, no CD or USB storage included.



_**Sudani **__**Part 2: (Editing connection information)**_
You can use your preferable program, i will use wvdial , check [this]("http://ubuntuforums.org/showthread.php?p=8523823#post8523823") guide for installing wvdial.

1- Run wvdial configuration tool:
[code]
sudo wvdialconf 

```You see output like this:
```

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: QUALCOMM INCORPORATED
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: USB2 

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```2- Edit wvdial.conf:
```

sudo gedit /etc/wvdial.conf

```add [COLOR=Red]sudani[/COLOR] as your username & password, the phone number is  #777
```

[Dialer Defaults]
Modem = /dev/ttyUSB0
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = Analog Modem
Phone = #777
New PPPD = yes
ISDN = 0
Username = sudani
Password = sudani
Baud = 9600

```[COLOR=Red]**Note:**[/COLOR] ttyUSB0 is my modem this value may differ in your system (wvdialconf will add it automatically so never try to change it).



_**Sudani**_[U][B] Part 3: (connect & disconnect)
[/B][/U]**connect:**
```

sudo wvdial

```[B]
disconnect:[/B]
```

press Ctrl+C

```[/code][B]==========================
6- Sudani's ZTE AC2726 USB modem[/B][B]:
======================[/B]**====**
[IMG]http://image.ec21.com/image/mai8crystal/simg_GC03982061_CA03982214/ZTE_AC2726_Modem.jpg[/IMG]
```

_**Sudani Part 1: (defining the modem)**_
1- Add a configuration usb_modeswitch file for ZTE AC2726 USB modem:
[code]
sudo gedit /etc/usb_modeswitch.d/19d2:fff5

```2- Paste the following lines & save the file:
```

#-------------------
# Zain's ZTE AC2726:
#-------------------

DefaultVendor= 0x19d2
DefaultProduct=0xfff5

TargetVendor=  0x19d2
TargetProductList="fff1,ffff"

MessageContent="5553424312345678c00000008000069f030000000000000000000000000000"

CheckSuccess=20

```3- Reboot your system



_**Sudani **__**Part 2: (Editing connection**__** information**_[U][B])
[/B][/U]You can use your preferable program, i will use wvdial , check [this]("http://ubuntuforums.org/showthread.php?p=8523823#post8523823") guide for installing wvdial.

1- Run wvdial configuration tool:
```

sudo wvdialconf 

```You see output like this:
```

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: QUALCOMM INCORPORATED
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
WvModem<*1>: Cannot get information for serial port.
ttyUSB4<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB4<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB4<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```2- Edit wvdial.conf:
```

sudo gedit /etc/wvdial.conf

```enter [COLOR=Red]sudani[/COLOR] as the username , [COLOR=Red]sudani[/COLOR] as the password & [COLOR=Red]#777[/COLOR] as the phone number the file will be:
```


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Phone = #777
Modem = /dev/ttyUSB0
Username = sudani
Password = sudani
Baud = 9600

```[COLOR=Red]
**Note:**[/COLOR] ttyUSB0 is my modem this value may differ in your system (wvdialconf will add it automatically so never try to change it).



_**Sudani **_[U][B]Part 3: (connect & disconnect)
[/B][/U]**connect:**
```

sudo wvdial

```[B]
disconnect:[/B]
```

press Ctrl+C

```[/code][B]==========================
7- Sudani's Huawei E1750 USB modem[/B][B]:
======================[/B]**====**
[COLOR=Red]No picture cause forum rules allows you to include 8 pictures only in one post but you can use the following link to see the picture:[/COLOR]
[http://i51.tinypic.com/f9o1y.jpg](http://i51.tinypic.com/f9o1y.jpg)
```

_**Sudani Part 1: (defining the modem)**_
1- Add a configuration usb_modeswitch file for Huawei E1750 USB modem:
[code]
sudo gedit /etc/usb_modeswitch.d/12d1:1446

```2- Paste the following lines & save the file:
```

#----------------------------
# Sudani's Huawei E1750 :
#----------------------------

DefaultVendor= 0x12d1
DefaultProduct=0x1446

TargetVendor=  0x12d1
TargetProductList="1001,1406,140b,140c,1412,141b,14ac"

CheckSuccess=20

MessageContent="55534243123456780000000000000011060000000000000000000000000000"

```3- Reboot your system



_**Sudani **__**Part 2: (Editing connection**__** information**_[U][B])
[/B][/U]You can use your preferable program, i will use wvdial , check [this]("http://ubuntuforums.org/showthread.php?p=8523823#post8523823") guide for installing wvdial.

1- Run wvdial configuration tool:
```

sudo wvdialconf 

```You see output like this:
```

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyUSB0<*1>: ATQ0 V1 E1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB0<*1>: Speed 9600: AT -- OK
ttyUSB0<*1>: Max speed is 9600; that should be safe.
ttyUSB0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyUSB1<*1>: ATQ0 V1 E1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 Z -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyUSB1<*1>: Modem Identifier: ATI -- Manufacturer: huawei
ttyUSB1<*1>: Speed 9600: AT -- OK
ttyUSB1<*1>: Max speed is 9600; that should be safe.
ttyUSB1<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttyUSB0.
Modem configuration written to /etc/wvdial.conf.
ttyUSB0<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
ttyUSB1<Info>: Speed 9600; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

```2- Edit wvdial.conf:
```

sudo gedit /etc/wvdial.conf

```enter [COLOR=Red]sudani[/COLOR] as the username , [COLOR=Red]sudani[/COLOR] as the password & [COLOR=Red]*99#[/COLOR] as the phone number the file will be:
```


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyUSB0
Username = sudani
Password = sudani
Baud = 9600

```[COLOR=Red]
**Note:**[/COLOR] ttyUSB0 is my modem this value may differ in your system (wvdialconf will add it automatically so never try to change it).



_**Sudani **_[U][B]Part 3: (connect & disconnect)
[/B][/U]**connect:**
```

sudo wvdial

```[B]
disconnect:[/B]
```

press Ctrl+C

```[/code]

---

### Post by moeyas on 2010-10-10
really nice topic zero-n,
thanks a lot fore your help
i have zain wm500, and i solved by installing ndiswrapper , then get the driver from my windows>program files> zain>driver> bssmd.inf & bsser.inf installed by the ndiswrapper from system>administration>windows wireless driver , then configure the connection through mobile wireless>add>>>>>>>>>>>> then follow up the steps . note  at the APN YOU SHOULD WRITE _PPP _
BTW I AM USING THE UBUNTO 10.10 RC
I AM SO GLAD TO FIND YOU SHABAB
C U ALL :P

---

### Post by zero-n on 2010-10-10
Thanks [moeyas]("http://ubuntuforums.org/member.php?u=1159427")

if you have experience with another modem (USB,PCMCIA)you can send how you manage to connect with Ubuntu in the post or email it to me, so manage to complete this guide to provide an easy to follow guide.

Salam

---

### Post by yasir.elsharif on 2010-11-24
Thanks [zero-n]("http://ubuntuforums.org/member.php?u=762650"),
As usual you are amazing, very well covered topic and very organized.
I just have a small question I would be very happy if you could help me on.
How to make a voice phone call using the zain modem or any modem, especially the usb ones, the way their own programs do that on windows. "their program let you make a call and send requests like *888# for checking credit"
Thanx in advance

---

### Post by zero-n on 2010-11-24
Thanks 

I have tried to do this but till now it didn't work, but i am still trying if you find out how to do it let me :)

i hope that you can help me to complete this guide too.

---

### Post by &#1605;&#1593;&#1575;&#1584; &#1575;&#1576;&#1606; &#1575;&#1604;&#1587;&#1608;&#1583;&#1575;&#1606; on 2010-12-07
&#1607;&#1584;&#1575; &#1608;&#1575;&#1604;&#1604;&#1607; &#1575;&#1601;&#1590;&#1604; &#1588;&#1585;&#1581; &#1575;&#1606; &#1588;&#1601;&#1578; &#1593;&#1606; &#1588;&#1585;&#1581; &#1578;&#1593;&#1585;&#1610;&#1601; &#1587;&#1608;&#1583;&#1575;&#1606;&#1610; &#1601;&#1610; &#1575;&#1576;&#1606;&#1578;&#1608; &#1608;&#1575;&#1604;&#1604;&#1607; &#1575;&#1606;&#1575; &#1605;&#1593;&#1580;&#1576; &#1580;&#1583;&#1575; &#1576;&#1607;&#1584;&#1575; &#1575;&#1604;&#1593;&#1605;&#1604; &#1575;&#1604;&#1605;&#1578;&#1602; &#1606; &#1608;&#1575;&#1604;&#1588;&#1575;&#1605;&#1604; &#1604;&#1603;&#1604; &#1575;&#1578;&#1608;&#1575;&#1593; &#1575;&#1604;&#1575;&#1578;&#1589;&#1575;&#1604; &#1576;&#1575;&#1604;&#1606;&#1578; &#1601;&#1610; &#1575;&#1604;&#1587;&#1608;&#1583;&#1575;&#1606; &#1608;&#1589;&#1583;&#1602; &#1575;&#1604;&#1605;&#1579;&#1604; &#1575;&#1604;&#1602;&#1575;&#1574;&#1604; [size="6"][color="red"][b][b][b]&#1575;[b[size="7"]&#1605;&#1575;&#1581;&#1603; &#1580;&#1604;&#1583;&#1603; &#1605;&#1579;&#1604; &#1592;&#1601;&#1585;&#1603;   
&#1580;&#1586;&#1575;&#1603;&#1605; &#1575;&#1604;&#1604;&#1607; &#1582;&#1610;&#1585;&#1575;[/size][/b][/b][/b][/b][/color][/size]

---

### Post by Dagash on 2010-12-11
**[COLOR=teal] [COLOR=sienna]for[/COLOR] Zain's WM500 USB modem[/COLOR]**
 
firstly , what exactly you write in the APN_USER & APN_PASS spaces ....??
 
i wrote APN_USER & APN_PASS .. then complete the instructions and get the code :
 
WM500  connected to Zain SDN (63401) 
 .... 
then again sakis3g appeare a window that want to choose an action for sakis3g script follow . what i should decide ? and after that how can i connect to the internet ?

---

### Post by zero-n on 2010-12-11
hi [Dagash]("http://ubuntuforums.org/member.php?u=1182595"),
& welcome to Ubuntu forums.


```
WM500  connected to Zain SDN (63401)
```means that your are now connected to the network, & sakis3g should show window that enables you to disconnect as i remember (i don't have a WM500 modem).

have you open your browser and checked if the internet is connected or not :D.

---

### Post by zazlox on 2010-12-13
Thanks a lot for sharing , useful topic

Allah bless you and reward you as well

---

### Post by toloykhan on 2011-08-11
**hello** **there** 
I just wana to add the newer zain connect GUI for linux .. it is just like the one for windows and very easy to install ...
first download the file below :
 
[http://www.4shared.com/file/p8ovWezb/zain_linux.html](http://www.4shared.com/file/p8ovWezb/zain_linux.html)
 
 
then from your terminal change the directory with the "**cd**" command to the downloaded linux directory 
**cd "path to source directory"**
then 
**type in the terminal : ./install**
**and all will go fine **
**when finsh close the terminal and go to your desktop and enjoy the zain connect GUI.**
 
**sorry I use your ****threat to post this zero-n, I don't wanna distruct users between threats.**
**regards**

---

### Post by zero-n on 2011-08-12
Hi [toloykhan]("http://ubuntuforums.org/member.php?u=1054960"),

Thanks for your contribution.

I need to know what modem models are supported by this  application. ;)

---

### Post by toloykhan on 2011-08-12
HI zero-n
I had just bought zain connect Hawawi E77 and found that files in it. but I think all Hawawi other modems are supported like E220, E169 and  E1690. But as I mentioned above I used E77 and it work just fine.

---

### Post by zero-n on 2011-08-12
Thanks [toloykhan]("http://ubuntuforums.org/member.php?u=1054960")

I've added a post included your package and another package for Sudani mDSL you can check it from [here]("http://ubuntuforums.org/showthread.php?t=1823480").

Salam.

---

### Post by fatharraxman on 2013-01-19
hi guys
am running ubuntu quental 12.10, just came by your nice thread, but i terribly need help with my c-motech canar modem it doesnt work what ever, it gives me the following message: arrahman@fatharrahman-HP-Mini-110-1100:~$ sudo apt-get install wvdialconf
[sudo] password for fatharrahman: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ sudo apt-get install ppp
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ sudo wvdialconf
sudo: wvdialconf: command not found
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ sudo kppp
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ sudo apt-get install wvdialconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wvdialconf
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ sudo apt-get install wvdial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  calligra-l10n-engb cdparanoia k3b k3b-data k3b-i18n kde-l10n-engb
  kde-l10n-zhcn kdevelop-l10n kdevelop-php-docs-l10n kdevelop-php-l10n
  language-pack-kde-en libdvdnav4 libdvdread4 libflac++6 libk3b6 libkcddb4
  libmpcdec6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libuniconf4.6 libwvstreams4.6-base libwvstreams4.6-extras
The following NEW packages will be installed:
  libuniconf4.6 libwvstreams4.6-base libwvstreams4.6-extras wvdial
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 870 kB of archives.
After this operation, 2,579 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://sd.archive.ubuntu.com/ubuntu/](http://sd.archive.ubuntu.com/ubuntu/) quantal/main libwvstreams4.6-base i386 4.6.1-5 [210 kB]
Get:2 [http://sd.archive.ubuntu.com/ubuntu/](http://sd.archive.ubuntu.com/ubuntu/) quantal/main libwvstreams4.6-extras i386 4.6.1-5 [454 kB]
Get:3 [http://sd.archive.ubuntu.com/ubuntu/](http://sd.archive.ubuntu.com/ubuntu/) quantal/main libuniconf4.6 i386 4.6.1-5 [129 kB]
Get:4 [http://sd.archive.ubuntu.com/ubuntu/](http://sd.archive.ubuntu.com/ubuntu/) quantal/main wvdial i386 1.61-4.1 [76.6 kB]
Fetched 870 kB in 1min 51s (7,816 B/s)                                         
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously unselected package libwvstreams4.6-base.
(Reading database ... 194814 files and directories currently installed.)
Unpacking libwvstreams4.6-base (from .../libwvstreams4.6-base_4.6.1-5_i386.deb) ...
Selecting previously unselected package libwvstreams4.6-extras.
Unpacking libwvstreams4.6-extras (from .../libwvstreams4.6-extras_4.6.1-5_i386.deb) ...
Selecting previously unselected package libuniconf4.6.
Unpacking libuniconf4.6 (from .../libuniconf4.6_4.6.1-5_i386.deb) ...
Selecting previously unselected package wvdial.
Unpacking wvdial (from .../wvdial_1.61-4.1_i386.deb) ...
Processing triggers for man-db ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://alumnit.ca/wiki/?WvDial](http://alumnit.ca/wiki/?WvDial)
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ sudo gedit /etc/wvdial.conf
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://alumnit.ca/wiki/?WvDial](http://alumnit.ca/wiki/?WvDial)
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://alumnit.ca/wiki/?WvDial](http://alumnit.ca/wiki/?WvDial)

any ideas?
please

---

### Post by zero-n on 2013-02-12
Hi [fatharraxman]("http://ubuntuforums.org/member.php?u=1176779")

wvdialconf is a tool that is included in wvdial package so you need to install wvdial package:
```
sudo apt-get install wvdial
```

connect your modem to any of USB port and run this command:
```
sudo wvdialconf
```

if it detects your modem then edit wvdial.conf file with your preferable editor like gedit or anything else:
```
gedit /etc/wvdial.conf
```
enter your connection information user name, password and dial number

---

### Post by FarisAlhoaba on 2013-03-13
Salam and *shukren jazeelen* :)

I have this CanarGo USB modem
I don't know if it is the same model for which  you have provided this very useful post,  but i gues it is because when i insert it the syslog gives this **NEW** info:

```
Farisalhoaba AptDaemon: INFO: Quitting due to inactivity
Mar 13 18:43:35 Farisalhoaba AptDaemon: INFO: Quitting was requested
Mar 13 18:45:55 Farisalhoaba kernel: [ 4177.236078] usb 5-1: new full-speed USB device number 5 using uhci_hcd
Mar 13 18:45:55 Farisalhoaba kernel: [ 4177.394993] usb 5-1: New USB device found, idVendor=16d8, idProduct=6803
Mar 13 18:45:55 Farisalhoaba kernel: [ 4177.395004] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Mar 13 18:45:55 Farisalhoaba kernel: [ 4177.395013] usb 5-1: Product: USB Mass Storage
Mar 13 18:45:55 Farisalhoaba kernel: [ 4177.395019] usb 5-1: Manufacturer: CMOTECH CO., LTD.
Mar 13 18:45:55 Farisalhoaba kernel: [ 4177.395025] usb 5-1: SerialNumber: 000000000002
Mar 13 18:45:55 Farisalhoaba kernel: [ 4177.397319] scsi8 : usb-storage 5-1:1.0
Mar 13 18:45:55 Farisalhoaba mtp-probe: checking bus 5, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1"
Mar 13 18:45:55 Farisalhoaba mtp-probe: bus: 5, device: 5 was not an MTP device
Mar 13 18:45:56 Farisalhoaba kernel: [ 4178.400567] scsi 8:0:0:0: CD-ROM            CMOTECH  Mass Storage     2.31 PQ: 0 ANSI: 0 CCS
Mar 13 18:45:56 Farisalhoaba kernel: [ 4178.409751] sr1: scsi3-mmc drive: 372x/372x caddy
Mar 13 18:45:56 Farisalhoaba kernel: [ 4178.410158] sr 8:0:0:0: Attached scsi CD-ROM sr1
Mar 13 18:45:56 Farisalhoaba kernel: [ 4178.413923] sr 8:0:0:0: Attached scsi generic sg2 type 5
Mar 13 18:45:56 Farisalhoaba kernel: [ 4178.559656] sr1: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
Mar 13 18:45:56 Farisalhoaba kernel: [ 4178.559689] sr: Sense Key : Hardware Error [current] 
Mar 13 18:45:56 Farisalhoaba kernel: [ 4178.559699] sr: Add. Sense: No additional sense information
Mar 13 18:45:56 Farisalhoaba usb_modeswitch: switching device 16d8:6803 on 005/005
Mar 13 18:48:36 Farisalhoaba kernel: [ 4337.936183] usb 5-1: USB disconnect, device number 5
Mar 13 18:48:36 Farisalhoaba kernel: [ 4337.938303] cdrom: issuing MRW background format suspend
Mar 13 18:48:36 Farisalhoaba udevd[3726]: failed to execute '/usr/bin/cmotech-qtmodem-out' '/usr/bin/cmotech-qtmodem-out 26627': No such file or directory
Mar 13 18:48:36 Farisalhoaba udevd[3729]: failed to execute '/usr/bin/cmotech-qtmodem-out' '/usr/bin/cmotech-qtmodem-out 26627': No such file or directory
```

I followed your steps to the letter in Part1, but when I use the command: 
```
sudo wvdialconf
```
I get this error message:
```
Scanning your serial ports for a modem
Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  



Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://alumnit.ca/wiki/?WvDial](http://alumnit.ca/wiki/?WvDial)
```.

I also tried to detect my modem in Gnome ppp but it says no modem was detected.
No need to mention that the modem works fine under Ms Windows
Any help?

---

### Post by zero-n on 2013-04-21
Alslam alaikom[COLOR=#000000] Faris, and welcome to Ubuntu forums

sorry for the late response

from this line and can assume that it Cmotech CNU-680:
[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]Mar 13 18:45:55 Farisalhoaba kernel: [ 4177.394993] usb 5-1: New USB device found, idVendor=16d8, idProduct=6803[/FONT][/COLOR]
```
and it seems that you have installed the application that comes with the modem for Linux could you please remove and then try again
[COLOR=#000000]
[/COLOR]

---

### Post by FarisAlhoaba on 2013-04-23
> **zero-n said:**
> Alslam alaikom[COLOR=#000000] Faris, and welcome to Ubuntu forums

sorry for the late response

from this line and can assume that it Cmotech CNU-680:
[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]Mar 13 18:45:55 Farisalhoaba kernel: [ 4177.394993] usb 5-1: New USB device found, idVendor=16d8, idProduct=6803[/FONT][/COLOR]
```
and it seems that you have installed the application that comes with the modem for Linux could you please remove and then try again
[COLOR=#000000]
[/COLOR]

&#1608;&#1593;&#1604;&#1610;&#1603;&#1605; &#1575;&#1604;&#1587;&#1604;&#1575;&#1605; &#1608;&#1585;&#1581;&#1605;&#1577; &#1575;&#1604;&#1604;&#1607; &#1608;&#1576;&#1585;&#1603;&#1575;&#1578;&#1607;
Thank you brother
Indeed it is because I had to revert back to Ubuntu 11.10 live session and the modem was detected out of the box as **Cmotech CNU-680** and all I had to do was to enter my account name and password.

I did install the application but after failing to make the modem work.

---

### Post by zero-n on 2013-04-24
I am glad that your problem is solved :popcorn:

feel free to ask here and members will help you if they can

slam

---

### Post by ghada on 2013-05-31
Hello ..
I'm new in using Linux I'm using openSuSE*
my question is does these steps work on all linux or only opunto ?

thanQ:D

---

### Post by zero-n on 2013-06-01
Hello [COLOR=#000000]ghada  and welcome to ubuntu forums.

Ubuntu uses usb_modeswitch to switch modems to their useful mode (modem) instead of (Zero-CD) and the latest OpenSUSE contains the package.

so i think this steps will work also with OpenSUSE expect packages installation because OpenSUSE uses (zypper) instead of (apt-get)[/COLOR]

---

