---
title: "ubuntu server 16.04"
date: 2016-06-20
forum: Server Platforms
---

### Post by Rui_Duarte on 2016-06-20
hello

I have had a ubuntu server 14.04 runing in a machine without any issues.

Yesterday I decided that was time for upgrade and fresh install ubuntu server 16.04

I am runing a machine with 2 hard drives...I installed via usb dont have a cd/dvd media.

First thing I notice is no login prompt after boot, only appears after CTRL+ALT+F1 after that i login etc

The problem is when I remove the graphic card because I dont want it there no need for that, and the system doesnt boot and I cant ssh nothing.

thanks in advance for the help

---

### Post by mastablasta on 2016-06-22
check dmesg and old logs in /var/log look for any erros and where the boot stops.

is the PC using UEFI secure boot?

what is the graphics card? does it use any extra drivers?

---

### Post by Rui_Duarte on 2016-06-22
hello,


this is a asus p5k-e  it doesnt have UEFI

In /var/log in boot.log I have this:

[https://www.dropbox.com/s/11nqfb9h7a4ahbw/P_20160622_194424.jpg?dl=0](https://www.dropbox.com/s/11nqfb9h7a4ahbw/P_20160622_194424.jpg?dl=0)
.
The graphic card is only to install the OS, i want it to work without it. I didnt install any driver.

---

