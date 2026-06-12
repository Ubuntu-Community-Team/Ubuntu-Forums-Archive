---
title: "Consistent uncommanded reboot on Live DVD on Asus CM1630-06"
date: 2014-01-16
forum: Ubuntu Development Version
---

### Post by bcschmerker on 2014-01-16
I am in the process of assessing Ubuntu® Trusty Tahr&#8482; on my Asus® CM1630-06 due to a borked Security hive in Microsoft® Windows® 7.0.8001 (Kernel 6.1.7601), only to find that "Try Ubuntu" will not keep running.  As of 16 January 2014, the 13.12a1 Live DVD causes spontaneous reboots with the following hardware configuration:

Asus® M5A78LT-M/CSM system board (BIOS 0304; Advanced Micro Devices® 760G northbridge and SB700 southbridge; 2.8 GHz AMD® Athlon II® X2 220:  Stock for CM1630-06)
Asus® EAH6850DC/2D1S/1GD5 video display adapter (AMD® Radeon® HD&#8482; 6850 video system/Barts Pro GPU) - presumed supported by X.org, video-radeon
Asus® XONAR® Essence&#8482; STX&#8482; audio card (Asus® AV-100 audio DSP, mfd. by C-Media International Inc.) - presumed supported by ALSA, snd-virtuoso

The system does not stay up long enough before the uncommanded reboot to get data on the software component(s) involved.  The problem is always reproducible on my hardware set-up.

Has this problem of spontaneous reboots occurred on other systems with Ubuntu® 13.12a1; and if so, have fixes been released on subsequent nightlies?  (As of 16 January 2014, Ubuntu® 14.01a2 is not due out for nearly two weeks.)

---

### Post by grahammechanical on 2014-01-17
At what stage of loading does the live session reboot? We first get a purple screen with an icon of a human and a keyboard. Next comes a purple screen with the word Ubuntu in the centre and some white dots underneath. At this point the live session starts to detect what hardware we have. Is it after this point that the reboot comes?

Have you tried any of the F6 options? During the development cycle of 13.10 (or was it 13.04) there was a time when I could only get I live session running by using a combination of F6 options. And this is on older hardware that has never had any problems running a live session. Not since I first started using Ubuntu in 2007. Others did not seem to have this problem.

Regards.

---

### Post by bcschmerker on 2014-01-17
The CM1630-06 makes it as far as the GUI desktop prior to "zonking"; the loss of background occurs at the presumable start of the spontaneous-reboot sequence.  I recently read about a buggy driver for certain AMD® graphics-processing units in LinUX Kernel 3.13 resulting in panics and/or similar crashes.  Will therefore have to test in text-only mode (NoModeSet) to rule video-driver bugs in or out.

**Update:**  NoModeSet results in stable running in GUI mode at 1024x768.  Suspect a video-driver, rather than kernel, issue.

**Update 2:**  Similar "zonk" encountered with UbuntuGNOME 13.12a1 installation, same conditions. :-( Aborting conversion on the CM1630-06 for now - I was able to reinstall Microsoft® Windows® 7.0.8001 (Kernel 6.1.7601) from a backup disc image from 2011.

---

