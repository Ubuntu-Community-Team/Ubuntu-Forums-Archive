---
title: "Tascam 122 USB help"
date: 2008-07-20
forum: Ubuntu Studio
---

### Post by mbtigger on 2008-07-20
Hello all!

I have a Tascam 122 USB that I am trying to get to work under Hardy. I've never had it working before, 

I've installed the Alsa drivers 1.0.16, including the firmware section (which reads 1.0.15).

I've downloaded the usx2y-fw-0.1b folder. I know that the new firmware bits are supposed to be in /lib/firmware so I have been trying the following command to install the firmware. I've been trying this from the subdirectory that contains my ld2-ezusb.hex file...

 sudo fxload -s ld2-ezusb.hex -I /lib/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/003/005

i get the following error 

/lib/firmware/usx2yloader/us122fw.ihx: unable to open for input.


I do not see a /usx2yloader directory, nor do I see a us122.ihx file. Am I supposed to create them? am I supposed to get them from somwhere?

Any help would be appreciated!

thanks!

MB

---

### Post by Stochastic on 2008-07-21
Hi, I don't have my 122 running on my hardy system, but it looks like it's no different from getting it to work in previous versions (from your description).  First I should point out that it'd be nice next time to include a link to the original instructions you were following, which led you to the error.  But the error is fairly straightforward; I did a couple commands on my system to see if I could find your missing us122fw.ihx they were ```
locate us122fw.ihx
apt-file search us122*
``` and they both turned up nothing (this was after I installed the alsa-firmware-loaders package).  The first command simply searched for the file on my system.  The second command searches for packages that contain a file with the name us122.  The lack of any bone thrown, tells me that there really isn't a package in the repositories I can find with the required file.  From my days using a us122 I remembered downloading the firmware package from alsa's website [www.alsa.org](www.alsa.org) (infact it's linked to right on the top right of the page).

Once this compressed folder was opened by my compy, the required file was right there in /alsa-firmware-1.0.17/usx2yloader .  You may get lucky and only need to unzip the required file, then point to the location in that command you were using; you may need to compile the alsa-firmware (I'd try the first way first, then try to match version numbers 1.0.15 to what's used on the system).

Hope this helps.

---

### Post by mbtigger on 2008-07-21
Thank You Stochastic!


The 1.0.17 firmware had the correct file in it. Once I had the file downloaded and placed into my /lib/firmware directory I made a 55-tascam.rules folder and pasted the following into it 

>  BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us122fw.ihx'"
 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

As per thread [http://ubuntuforums.org/showthread.php?t=431066](http://ubuntuforums.org/showthread.php?t=431066)

Green light is now on the Tascam - all I need do is figure out how to get Ardour to recognize the USB input and I am home free!

MB

---

