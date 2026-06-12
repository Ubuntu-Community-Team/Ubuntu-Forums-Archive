---
title: "HOWTO:  install Brother printer drivers in Ubuntu 10.04 or later or Mint 11."
date: 2011-08-29
forum: Tutorials
---

### Post by robot_chicken_parm on 2011-08-29
[solved]  HOWTO:  install Brother printer drivers in Ubuntu 10.04 or later or Mint 11.


No worries.  With the help of some very nice people on IRC this was easy as pie  :)

edit:  i think i made some mistakes in my initial post, so i have updated it, and this way is simpler and worked for me no problem.

First off go to Brother Drivers for Linux® distributions at  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) and click on Printer Driver.  ctrl+F and search for your model of printer.  click on it, and download the "LPR" deb first and install it, then the "cupswrapper" deb package.

Go into your web browser and type [http://localhost:631/](http://localhost:631/) into the address bar.  Under the "PRINTERS" tab you should now find your printer..

  Mine is the Brother MFC-J410w, which is also a scanner, and if you need to add your scanner, read on.  Go back to Brother Drivers for Linux® distributions at [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)  and click on "scanner driver/scan-key tool".  ctrl+f search for your brother scanner and then whatever category it falls into, such as brscan2 or brscan3 etc., go up and downbload that driver for your partiucular system(32 bit, deb, for ex.).


After the install, there is one more step:

As it states on [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)  ,

Press ALT+F2 to run an application, and in the field paste:

```

gksudo gedit /lib/udev/rules.d/40-libsane.rules

```and add the following two lines to the end of the device list.   

```
[FONT=monospace]
[/FONT]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[FONT=Ubuntu]
[/FONT]
```[FONT=Ubuntu]

[/FONT]Restart your computer.  Viola!

Thanks go out to to Karsus and Rustyl_64 among others!

---

### Post by Sef on 2011-08-29
Moved to Tips & Tutorials.

---

### Post by robot_chicken_parm on 2011-08-30
thanks...  btw this is a gui tutorial... for the terminal, refer to [http://ubuntuforums.org/showthread.php?t=590793&page=31](http://ubuntuforums.org/showthread.php?t=590793&page=31)  and this should hopefully help.  i couldnt find my specifics in synaptic but the way i described worked fine and i can print and scan now

---

