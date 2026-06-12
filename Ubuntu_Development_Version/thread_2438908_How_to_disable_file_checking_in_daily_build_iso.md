---
title: "How to disable file checking in daily build iso"
date: 2020-03-20
forum: Ubuntu Development Version
---

### Post by ping-wu on 2020-03-20
Recently when booting from USB containing a recent daily build iso, it takes much longer than before.  The reason was due to initrd doing file checking.  Is there any way to disable the file checking steps during booting from the LiveUSB?

---

### Post by guiverc on 2020-03-20
None have been documented (that I'm aware of, nor mentioned on [community.ubuntu.com]("https://discourse.ubuntu.com/t/defaulting-to-verify-the-image-integrity-before-installing-on-desktop/13472/") where the topic was raised).  I've found some flavors harder than others to skip (I've only achieved 'skip' once on Lubuntu for example out of loads of tries... yet have achieved it more than once on far fewer tries on ....)

---

### Post by ping-wu on 2020-03-20
> **guiverc said:**
> None have been documented (that I'm aware of, nor mentioned on [community.ubuntu.com]("https://discourse.ubuntu.com/t/defaulting-to-verify-the-image-integrity-before-installing-on-desktop/13472/") where the topic was raised).  I've found some flavors harder than others to skip (I've only achieved 'skip' once on Lubuntu for example out of loads of tries... yet have achieved it more than once on far fewer tries on ....)

Hit escape key during booting, one can see that [FONT=Ubuntu]media check is being executed.  Just burn a usb from a most recent daily build iso.  This and other warnings/error messages are also very discomforting.  There is no need to repeat here--just make a usb, boot from it, and hit the escape key.[/FONT]

---

### Post by him610 on 2020-03-20
>  it takes much longer than before
How much longer? Can you provide evidence of that statement?

---

### Post by guiverc on 2020-03-20
> **ping-wu said:**
> Hit escape key during booting, one can see that [FONT=Ubuntu]media check is being executed. [/FONT]

Thanks @ping-wu.  I had the latest Xubuntu 20.04 daily besides me, so it was easy to test

---

### Post by Frogs Hair on 2020-03-22
Moved to *Ubuntu Development Version*.

---

### Post by mc4man on 2020-03-23
Yeah, it's terrible. Relatively  speaking,  on my laptop 18.04 takes 35 secs, 20.04 recently  takes 3 min.
1st. time it started doing this thought I had a bad iso.

Edit: today's pending image takes 3:50..
If you hit s during the bootup it'll skip, exactly when don't know, just tap away for a bit.

---

### Post by corradoventu on 2020-03-27
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1867130](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1867130)

---

### Post by chrisretief on 2020-04-06
I'm glad error checking was enabled on the (first) 20.04 Beta iso I downloaded. I used a USB and booted up in live mode - all normal it seemed. I attempted to install it and half way through the install I got a error with a bug report request. Rebooting dropped me to the cursed 'GRUB>' prompt. Booted up again and checked the file checking reporting, and noticed one file error. I downloaded another ISO and installed normally with that. How can an ISO downloaded with Qtorrent give me a corrupted file, or does it get corrupted in the finalising process?

---

### Post by corradoventu on 2020-04-06
In the recent ISO at least after April 1st when You insert the USB to install you have a window showing the check progress and You have the choice to stop the check.

---

