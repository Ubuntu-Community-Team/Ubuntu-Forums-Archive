---
title: "Upgrade from Xubuntu 11 to 14 results in &quot;Video mode not supported&quot;"
date: 2014-01-17
forum: Ubuntu Development Version
---

### Post by coaxihuitl on 2014-01-17
I just recently tried upgrading from Xubuntu 11 to 14. There were no issues during the upgrade however ad soon as I rebooted I got the "video mode not supported" message upon boot - this is that floating message on the monitor after bios has completed. I can still enter BIOS. I can also enter grub and select the old version or new version both as regular or safe mode. However if I go this route it hits the splash screen and then goes to a non-responsive cursor instead of the video message. I tried a (improperly working) PCIe video card instead of the onboard video and it got to the splash screen and then acted like it usually does - stripes I colours. Running off the onboard video creates the problems I described in the start. The motherboard is an Asus F1A75-M Pro so the onboard video is an AMD Radeon 6000 series. Any idea what I can do to get my video back (well the video for the OS?). Thanks.

---

### Post by fantab on 2014-01-17
How did you upgrade from "Xubuntu 11 to 14"?
What graphics card do you have onboard?
Have you tried '[**nomodeset**]("http://ubuntuforums.org/showthread.php?t=1613132")' option?

---

### Post by coaxihuitl on 2014-01-18
Amazing - it didn't work when I added it but did when I deleted quiet splash (this as an option somewhere else I think). Thank you!

---

### Post by vasa1 on 2014-01-18
Until 14.04 is released you may like to post about 14.04 in the Ubuntu+1 subforum here: [http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

---

### Post by Bucky Ball on 2014-01-18
*Thread move to **Ubuntu+1**.* 

All posts regarding 14.04 LTS go here until release in April. 

Unless you know what you are doing, 14.04 is not a good place to start. It is still testing. I would advise a supported release, 12.04 LTS or 13.10, support until April 2017 and June this year respectively, both upgradeable to 14.04 LTS (five years support) in April.

The version you are using at the moment should be updated/upgraded everyday and you should report all faults here ... but don't expect a known, easy fix. As I say, it's still being tested.

You might help others by marking your thread as solved by following the link in my signature. Of course, it may break again after the next update. :-k

PS: If you're testing 14.04 intentionally, carry on and disregard this. ;)

---

### Post by coaxihuitl on 2014-01-18
No, upgrading to 14 was a mistake. I meant to upgrade to the most recent stable version but was working on two things at a time and didn't read carefully.

The nomodeset option I've found works fine for every boot but I can't make it permanent even usin the instructions given (thanks again btw). I guess that's okay for now.

To answer your questions:
I upgraded directly from 11.37 to 14.04 because I was having major issues with 11.53 (couldn't boot into it, had to keep selecting 11.37 from grub. I did it too quickly not realizing 13 is what I should have chosen.

As to video cards, the motherboard houses a 6550 Radeon while the "fried" external (PCIe) card was a Radeon HIS 6950.

---

### Post by Bucky Ball on 2014-01-18
There was no 11.37. You had 11.04 or 11.10, both of which reached end-of-life quite some time ago. Probably why you were having issues. I would advise a reinstall, but if you are going to stick with it, you better start the learning curve now:

Making 'nomodeset' permanent:

Open a terminal, then paste:

```
sudo cp /etc/default/grub /etc/default/grub.backup
```

This create a backup in case you screw up.

```
sudo nano /etc/default/grub 
```

Look for the line like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
```

If you don't have 'splash quiet, but just "" that is fine. Change that line to:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet nomodeset"
```

or, if you're not using 'splash quiet':

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

Hit ctrl+X, then 'y', reboot and see if that works ok.

---

### Post by coaxihuitl on 2014-01-18
My mistake - Xubuntu 11...I was thinking of the "Advanced options for Ubuntu" screen with "Linux 3.2.0-37" and the 57 version available in Grub (first bootable, second not) not the actual Xubuntu versions. Sorry.

---

### Post by Bucky Ball on 2014-01-18
You have marked this thread as solved. Please inform the community about what you did to fix the problem or what course of action you have decided to take. Thanks. (Forum etiquette. ;))

---

### Post by grahammechanical on 2014-01-18
Using nomodeset is a temporary fix that may or may not get us to a desktop. It runs the OS loading process without setting a video mode. Another option is Recovery Mode>Resume. Either way when getting to a desktop we then open System Settings>Software and Updates>Additional Drivers tab and experiment with video drivers. And it can sometimes be a bit of an experiment. I think that is what you need to do now to remove the need to add nomodeset at every boot.

Regards.

---

