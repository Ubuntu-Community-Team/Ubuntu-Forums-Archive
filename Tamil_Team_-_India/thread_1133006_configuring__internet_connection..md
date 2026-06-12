---
title: "configuring  internet connection."
date: 2009-04-22
forum: Tamil Team - India
---

### Post by msidhard on 2009-04-22
guys
        here is the way to connect huawei with ubuntu . 
1. start terminal
2.lsusb
  now u can find wether ur modem is connected to ubuntu or not. if not then check ur loose connections.if there is no loose connection then ur modem is not supported for ubuntu.
3.if connected then dmesg | grep tty
 the output will say some thing like x is connected as /dev/ttyUSB0 or /dev/tty****
4.sudo gedit /etc/wvdial.config
5.just add Modem = /dev/tty****
then add the necessary details like phone username password etc and save and exit.
  now u configured wvdial.
6.sudo wvdialconfig
 this  will configure the modem setup it will Init in wvdial.conf never mind that.
7.sudo wvdial
this will connect to internet.
u can use this method for configuring  lot of modems not only huawei.

---

