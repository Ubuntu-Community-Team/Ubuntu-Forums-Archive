---
title: "LCD Brightness Keys Not Working (Jaunty)"
date: 2009-05-11
forum: System76 Support
---

### Post by gpstar on 2009-05-11
On my Bonobo, ever since doing a fresh install of Jaunty, the FN + F8 or F9 for controlling the lcd backlight brightness no longer works. Tried the system76 driver restore option but still the same problem.

---

### Post by thomasaaron on 2009-05-11
I believe there was a fix for that in Intrepid that may not have been carried over to 9.04. I'll check with the driver maintainer. Stand by...

---

### Post by thomasaaron on 2009-05-11
OK. Confirmed. This will be fixed in a new version of the System76 driver, which will be released in a few days. I apologize for the inconvenience.

---

### Post by thomasaaron on 2009-05-12
OK, the driver with the fix has been released.

To install the System76 Driver, go to...

[http://planet76.com/repositories](http://planet76.com/repositories)

...and download the latest driver .deb package. The latest driver will always be the second link from the bottom. Save it to your Desktop.
Once it has downloaded, double-click the icon on your desktop and follow the prompts to install it.

Once installation is complete, go to System > Administration > System76 Driver > Restore (tab) > Restore (Button) to re-set your machine to factory standards (which may include some software downloads). If you only want to install drivers, select the 'Install' tab and the 'Install' button.

---

### Post by gpstar on 2009-05-12
it's working now. thanks.

---

### Post by gpstar on 2009-09-11
brightness keys no longer working again in 9.04 on a bonp2

also, webcam no longer works.

I ran the restore option on the latest system76 driver (2.3.7), but no changes.

It seems the FN+F8, FN+F9 and FN+F10 keys dont do anything. I can't get my webcam to turn on.

lsusb shows no changes when I press FN+F10 and do lsusb again, it's the same.

---

### Post by thomasaaron on 2009-09-11
Run your System76 Driver (System > Administration > System76 Driver > Install Tab > Install Button) and reboot.

---

### Post by gpstar on 2009-09-11
Just tried. Still same problems.

---

### Post by thomasaaron on 2009-09-14
OK. Please post the output of uname -r

Also, boot into a previous kernel and see if the problem exists there as well.

Also, what version of the System76 driver are you running? (Press the 'About' button in the driver.)

---

### Post by gpstar on 2009-09-14
2.6.28-11-generic for the kernel

2.3.7 of the system 76 driver.

---

### Post by thomasaaron on 2009-09-14
OK, something slightly strange is going on, and I don't quite have it figured out yet, but you are not running a fully updated computer. The output of 'uname -r' should be 2.6.28-15-generic. That is the current version.

Please go to System > Administratino > Update Manager and click the "Check" buttons to see if any more updates are available.

If they are not, please post the output of

> cat /boot/grub/menu.lst

Most likely the two problems are related, so we probably should figure this one out first.

---

### Post by gpstar on 2009-09-14
ok booted into the 2.6.28-15-generic kernel now.

re-ran the system76 driver and clicked on install. then rebooted.

same problem, nothing has changed.

lsusb before and after fn-f10 is still producing the same results. The webcam is not activated. Also the brightness keys are still not working.

results of lsusb (same result after fn-f10 as well)

```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 147e:2016  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by thomasaaron on 2009-09-15
I'm not sure, then.

We probably should send it in for repair. Shoot me an email at support---at---system76---dot---com.

---

### Post by gpstar on 2009-09-16
brightness keys appear to work just fine before bootup (in grub) and in vista. fn-f10 key works in vista, but the bison cam is not receving power as the led light for the camera never comes on. With a bit of searching online, 

[http://forum.notebookreview.com/showpost.php?p=2845543&postcount=22](http://forum.notebookreview.com/showpost.php?p=2845543&postcount=22)

I suspect a faulty wire that provides power to the webcam.

anyhow, firing off email to ya.

thanks.

---

### Post by thomasaaron on 2009-09-16
Got it. Thanks.

---

