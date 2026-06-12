---
title: "using SDC on daily auto ejects pendrive without notice?"
date: 2012-07-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-07-28
I just updated the daily quantal-desktop-i386.iso using Startup Disk Creator. All went well, but, after it was finsihed I did not find the proverial USB icon in the Unity panel.

---

### Post by mc4man on 2012-07-28
Whether intended or not, new behavior or not, (haven't paid the remembering kind of attention), seems to make sense.

The 2 most common actions after creating would be to remove thumb for later use, so being already ejected is good
or
reboot to the drive, in that case being ejected doesn't matter

---

### Post by ronacc on 2012-07-28
a new udisks2 came down today maybe thats it , I can't check SDC stopped making a bootable disk for me a few days ago ( again ) . It makes the disk installs the boot loader , marks it bootable but my bios don't see it as a bootable disk , SDC worked fine all the way through precise but went wonky at the start of precise then started working again and now out again , same stick all the way through .

---

### Post by ventrical on 2012-07-28
> **mc4man said:**
> Whether intended or not, new behavior or not, (haven't paid the remembering kind of attention), seems to make sense.

The 2 most common actions after creating would be to remove thumb for later use, so being already ejected is good
or
reboot to the drive, in that case being ejected doesn't matter

 I agree, makes sense .. but I am just slightly perplexed that there is usually no heads-up for this stuff.

 I find since precise release that I have to use -(Discarded on shutdown,unless you save them elsewhere) Option because  using in (stored  in reserved extra space) will most often fail.

 It is like going out on a limb because using  the first option can always lead to breakage in the pipes if the USB is pulled pre-maturely. In my old VAX-UNIX days we were always taught to make sure all files are closed before terminate a program . So , I just get concerned that there may be some flags left open on critical system files that can bork a newly created USB... it's just the downtime that's aggravating.

 So now there is  a complete 'undepends'  for the  newly created finished USB. Not having an indicator doesn't seem logical. so I may file a bug .. no USB indicator found in unity panel after finished SDC session.

---

### Post by mc4man on 2012-07-28
> **ventrical said:**
>  so I may file a bug .. no USB indicator found in unity panel after finished SDC session.

You may wish to check something 1st. I believe previous to unity-6.0 that when the usb disk deal was done the drive was in fact unmounted, it just wasn't removed being from the unity launcher

Maybe try on a 12.04 install & see (have a nautilus window open would be one way.

---

### Post by ventrical on 2012-08-01
> **mc4man said:**
> You may wish to check something 1st. I believe previous to unity-6.0 that when the usb disk deal was done the drive was in fact unmounted, it just wasn't removed being from the unity launcher

Maybe try on a 12.04 install & see (have a nautilus window open would be one way.

  After updating today (Quantal) the USB icon still disappears from the Unity Panel(bar) after SDC is completed. However, Nautilus reports the USB there  unmounted.

---

### Post by ventrical on 2012-08-01
> **mc4man said:**
> You may wish to check something 1st. I believe previous to unity-6.0 that when the usb disk deal was done the drive was in fact unmounted, it just wasn't removed being from the unity launcher


 I can see the perfect logic in this now because it follows up on the notification that is displayed after SDC is finished making a USB boot disk. You know ... "you are now ready to use  .. etc.."  and just pull it out.  So  there is some logical elimination of redundancy in notifications. I guess we  just have to find these things for ourselves and not depend on devs to come here and keep us apprised  of all the little changes.

---

