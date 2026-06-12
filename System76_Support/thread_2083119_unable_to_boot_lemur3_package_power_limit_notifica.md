---
title: "unable to boot lemur3: package power limit notification"
date: 2012-11-11
forum: System76 Support
---

### Post by layolayo on 2012-11-11
Just powered down and tried to reboot my lemur3 and am continually given the message: package power limit notification, for each cpu - total events = 1

The mouse is operational, I can access other tty but I cannot boot into unity...?

EDIT: 12.10 - Linux lemur 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Note I am able to boot into Unity without the error if I have no power connected to the laptop?

also (although this maybe a red-herring) I was unable to connect to my local wi-fi until I disconnected my power cable..

---

### Post by layolayo on 2012-11-11
The wifi issue is a red-herring.

I am still having booting issues however - system boots better with out the PSU connected - with the PSU connected I get the Package Power messages, sometimes it gets at far as booting with Low-Graphics Mode and other times just to Checking Battery Status...?

I've opened a support case with Sys76 - but if anyone has any ideas or any more info I should provide please let me know.

---

### Post by layolayo on 2012-11-12
First off BIG thanks to Mark at Sys76 support.

I was able to boot immediately into unity/Ubuntu after dropping to tty1 and running:

sudo /etc/init.d/lightdm restart

Did a full update, also reinstalled System76 drivers - rebooted - System76 Restore System - rebooted.

Tried rebooting 5 times so far and had no issues

---

