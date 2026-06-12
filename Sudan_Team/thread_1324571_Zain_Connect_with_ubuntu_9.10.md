---
title: "Zain Connect with ubuntu 9.10"
date: 2009-11-12
forum: Sudan Team
---

### Post by Netcowboy on 2009-11-12
[CENTER][FONT="Comic Sans MS"][SIZE="5"][COLOR="Blue"]Hello there ,

I'm using zain connect , since i installed karmic my huawi zain connect stop working 

i think they said it's an issue with the kernel

this is temp fix untill they fix it in da updates

do this ::

1- plug your zain connect

2- wait for it to show as cd rom

3- right click then click on safely remove 

4- open terminal window and copy those commands
> sudo rmmod usb-storage

> sudo modprobe -r option

> udo modprobe usbserial vendor=0x12d1 product=0x1001

5- then go to your network-manager and you'll find it :)

not my own work i got help from a friend :)[/COLOR][/SIZE][/FONT][/CENTER]

---

### Post by zero-n on 2009-12-01
Thanks Netcowboy.

but i am using Canar Go and it works will in Karmic :P

---

### Post by mhmdfoss on 2009-12-08
thank you netcowboy

---

