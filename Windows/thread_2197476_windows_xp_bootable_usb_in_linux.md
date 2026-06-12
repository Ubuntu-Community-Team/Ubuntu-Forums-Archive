---
title: "windows xp bootable usb in linux?"
date: 2014-01-03
forum: Windows
---

### Post by jhay2 on 2014-01-03
hello ubuntu fanatics .. :)


i currently installed xubuntu 13.10 in my old laptop

i read about winusb on linux but this winusb supports win 7 and 8 and vista , but not xp

i have an xp bootable iso. 

how can i create a bootable xp usb on linux ? 

thanks :)

---

### Post by Mark Phelps on 2014-01-04
> how can i create a bootable xp usb on linux ?

Which are you looking to do:
1) Create an XP installer USB stick
2) Boot and run XP from a USB stick

---

### Post by monkeybrain20122 on 2014-01-04
There is a thing called BartPE which allegedly can make a live Windows XP usb. Several of my friends (all Windows power users) spent hours trying and none was able to get it to work. :)

Why bother with XP anyway? It will reach end of life in April.

---

### Post by C.S.Cameron on 2014-01-04
There are a couple of ways to run XP from a flash drive, both painfully slow on USB2.

The Ngine method can be found here: [http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf](http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf)
The already modified files can be found elsewhere on the internet.

The second method works for XP, Vista, Win 7 & 8.
This is to do a full install of Ubuntu, (or Puppy, etc), Install Vbox into Ubuntu and then install Windows as a client.
The download from virtualbox.org works better than the one from download center.

Edit:
I have not been able to get the Ngine method to work with SP3, but then I have not tried very hard either.
I have been running XP SP3 for about a week now, from a 16GB USB2 Sandisk Cruzer Fit, and the speed is not all that bad, if you got lots of RAM.

---

### Post by jhay2 on 2014-01-05
create a bootable xp under linux ? is it possible ?

---

### Post by SeijiSensei on 2014-01-05
Yes, if the machine is powerful enough.  You can run [VirtualBox]("http://www.virtualbox.org/") and create a virtual machine into which you can install Windows.  I have a Win7 VM on a couple of Ubuntu desktops. While you can install VB from the Ubuntu repositories, I prefer to follow the approach outlined [here](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).

I wouldn't try to run both Windows and Ubuntu on a machine with much less than 1.5 GB of RAM.  768 MB is about the smallest memory space I'd allocate to either XP or a current Ubuntu distribution. CPU matters less than memory for most applications.  Don't expect to play graphics-intensive games in this setting, though.  The virtual machine writes to an emulated display rather than directly to the graphics hardware itself and thus cannot take advantage of all the optimizations the hardware might provide.

---

### Post by C.S.Cameron on 2014-01-05
For XP client with Ubuntu host on a flash drive I would recommend that everything is on the same flash drive, (16 GB is about minimum size).
If the VDI file is on a separate flash drive things get extremely slow.
It is not too bad if the VDI is on the internal drive though.
This is for USB2, I have not tried with a USB3 flash drive.

---

### Post by Timoteo32 on 2014-01-06
Piggybacking off a similar topic, which program would you guys recommend to create a Windows 7 install stick?  I have my iso, just need an app. I've seen the name WinUSB several times but I don't see it in the Ubuntu Software Center.

---

