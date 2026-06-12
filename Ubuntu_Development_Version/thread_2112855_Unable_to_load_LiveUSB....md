---
title: "Unable to load LiveUSB..."
date: 2013-02-05
forum: Ubuntu Development Version
---

### Post by Baldrick_NZ on 2013-02-05
I was filled with anticipation to test run 13.04, so I downloaded the latest liveCD ISO and attempted to use 'Startup Disk Creator' to install the Live ISO onto my 8Gb USB stick to try out.

Yet everytime I try to boot into the USB, I only get as far as the purple background and the five red dots under the Ubuntu logo in the middle of the screen. It doesn't get to the login screen. The mouse icon freezes and nothing else happens. One time I left it in that state overnight, and it was still there in the morning. 

I've looked into the folder structure of the LiveUSB, and everything seems fine. I've tried re-downloading the ISO on different days, and installing to the USB, and still no joy.

Any ideas?

---

### Post by VinDSL on 2013-02-05
> **Baldrick_NZ said:**
> Any ideas?
I haven't had any luck, using Startup Disk Creator, in quite a while.

Have you tried UNetbootin?

Works every time, for me... ;)

---

### Post by cariboo on 2013-02-05
I use the classic geeky way of creating a usb device using dd:

```
sudo dd if=raring-desktop-amd64.iso of=/dev/sdc bs=1M
```

I haven't had a failure yet.

Regardless, the op's problem sounds like something else, have you pressed F6 at the initial boot screen, and tried some of the options like no modeset?

---

### Post by jerrylamos on 2013-02-06
> **cariboo907 said:**
> I use the classic geeky way of creating a usb device using dd:

```
sudo dd if=raring-desktop-amd64.iso of=/dev/sdc bs=1M
```

I have better luck with dd if I do this on the USB stick:
sudo gparted
only one partition
format to F32
no label
then do the dd which is pretty slow - don't forget to include the bs=1M or it will really crawl.
Another dodge, when running unstable development Ubuntu like 13.04, is always have backup partitions example 12.04.2 in case something is really unstable like startup disk creator.  For years that app has been very problematic on Ubuntu.  Makes no sense to me, get it right once, then don't change it.

---

### Post by grahammechanical on 2013-02-06
I can get a Raring live DVD to work only by adding the F6 option of acpi=off and then putting irqpoll before quiet splash in the boot parameters.

It gets me to a live session and from there I can install but choosing Install Ubuntu at the third screen even with those changes gets me to a Busybox prompt. I have not tried this on a USB but an Edubuntu image from last week installed fine with USB creator and loads. Once, I whip the BIOS into behaving as I want it to.

Regards.

---

### Post by ventrical on 2013-02-06
As I also said before .. I have a Maveric Install on one of my bigger (newer) hdds and have now migrated all my  zsync and startup disk proceedures to that partition.

  As for testing SDC  in Raring ?? How can we test something that is busted?

---

### Post by ventrical on 2013-02-06
> **grahammechanical said:**
> I have not tried this on a USB but an Edubuntu image from last week installed fine with USB creator and loads. Once, I whip the BIOS into behaving as I want it to.

Regards.

 BIOS settings and behaviour have become a very big performance factor during this cycle. I consider myself fortunate to have so many machines to work with. On my Intel based machines like my Dell Dimension 3100 and HP Pavilion (both Intel chipset) I have had little or no problems.

---

### Post by mc4man on 2013-02-06
> **ventrical said:**
> 
  As for testing SDC  in Raring ?? How can we test something that is busted?
SDC is fine now in raring, whether it works for all users is another question.

---

### Post by ventrical on 2013-02-06
> **mc4man said:**
> SDC is fine now in raring, whether it works for all users is another question.


Yes.. that is an affirmative. For how long though ???  (fingersXcrossed)   :)

---

### Post by Baldrick_NZ on 2013-02-07
Thanks guys, the F6 trick worked!

---

