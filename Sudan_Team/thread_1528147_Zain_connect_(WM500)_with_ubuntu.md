---
title: "Zain connect (WM500) with ubuntu"
date: 2010-07-10
forum: Sudan Team
---

### Post by khalidshraf on 2010-07-10
Hi all,
I am using zain connect (WM500) i.e "5Gbyte download limit" device which is obviously has
problems on working with linux (am using Ubuntu9.10 karmic koala).
There is nothing I had'nt try to figure and solve the problem.We all know that the basic idea is to:
1-Eject the media labled ZAIN_MODEM and unmount the usb_storage device if it appears.
2-Switch the device into usbserial mode.
3-Connect using wvdial or ppp(using terminal,kppp,umtsmon) or any program with the appropriate parameters.
But unfortunately steps above dont always work for me.
I tried >wvdialconf and it did'nt work (it points to /dev/ttyUSB1 as the modem which is obviously  not)
I tried changing /etc/wvdial.conf settings again not working!.
I tried installing "wine" and it works (sometimes)
eventually we can see that running the QsSetup.exe is a must but like I said installing wine to be able to run the .exe file not always working.
If anyone found a solution please let us know.;)

---

### Post by Adntu on 2010-07-10
Alsalam alikom Khalid
unfortunately, have no idea about your problem.
just wanted to welcome you here. I hope you will stay around after your problem is fixed.

---

### Post by khalidshraf on 2010-07-10
Thanx Adntu,
And about staying around dont worry cause m not planning to migrate from ubuntu.So u ll
find me here insha allah;)

---

### Post by zero-n on 2010-07-10
Hi [khalidshraf]("http://ubuntuforums.org/member.php?u=1110168"),
& welcome to this forum

I am using CanarGo without any problems ;) , but i think i can help you ( insha2 allah )

1- what you mean by:
```
2-Switch the device into usbserial mode.
```2- can you paste you wvdial.conf file here.

---

### Post by khalidshraf on 2010-07-11
I mean executing the commands
modprobe -r option
modprobe usbserial vendor=0x05c6 product=0x9000

---

### Post by yasir.elsharif on 2010-07-13
Salamat Khalid,

I am not using the same device, but did you tried **usbmodeswitch**?

---

### Post by khalidshraf on 2010-07-14
Hi Yassir,
I tried using usbmodeswitch also,but again did'nt work.I dont think this is the problem because I received (after switching the usb modem and running ppp) the error msg (No network protocol is running).The command wvdialconf identified two modems on /dev/ttyUSB1 and /dev/ttyUSB3.I believe that It's something related to modem initialization (running QsSetup.exe).I reinstalled wine (this time using ubuntu software center) 3 days ago to have QsSetup.exe running automatically when plugging in the modem and (till now) it works just fine.I think getting the binary source of the driver and modifying it to run under linux environment will solve the problem.

---

### Post by zero-n on 2010-09-21
Try to follow this steps:
```

sudo rmmod usbserial

``````

 sudo modprobe usbserial vendor=0x05c6 product=0x9000

``````

sudo ls -al /dev/ttyUSB*

```Then try :
```

sudo wvdialconf

```

---

### Post by zero-n on 2010-09-23
Sorry for writing two responses but i found the solution for Zain WM500 modem after my first repsonse.

check [this]("http://ubuntuforums.org/showthread.php?p=9867518#post9867518") guide.

i have tested it by my self.

good luck

---

