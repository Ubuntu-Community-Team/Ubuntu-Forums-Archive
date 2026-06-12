---
title: "Don't Use dd Before Your Morning Coffee"
date: 2016-03-08
forum: Ubuntu, Linux and OS Chat
---

### Post by buzzingrobot on 2016-03-08
Pretty much every time someone, including myself,  here explains how to use dd to burn an ISO image to a USB stick they caveat it with the warning to be certain it's pointed at the *right* device.  Because dd copies bits from "here" to "there" and does not care what "there" is.

The thing is, the identity of "there" can change.

This machine has two internal drives: /dev/sda and /dev/sdb.  An external USB backup drive is always attached and, normally, it is /dev/sdc.

So... plug in a USB stick and it's /dev/sdd. run "lslbk" and there it is: /dev/sdd.  Point dd at it and burn that image.

Except.... Reboot with that USB stick in place and it might not be /dev/sdd.  It might be /dev/sdc and that external backup drive might be /dev/sdd.

And that's what happened here this groggy, insufficiently caffeinated morning.  I didn't check with lsblk, but just reverted to habit and used /dev/sdd, overwriting that backup drive.

(I keep the most current backup on Dropbox, too, so the sky has not completely fallen.)

I've seen these device assignments silently shuffle around when a new USB device is attached, too. Always check.

(If you have the capability and patience, I've found burning an install image to a DVD obviously avoids  this issue as well as the other annoying quirks that can pop up using USB sticks. Plus, in Windows, you can do it with a right click on the file name.)

---

### Post by sudodus on 2016-03-08
I know. This is why I bothered to make ***mkusb***, to help avoid such problems. If you don't want to bother with a GUI, use ***mkusb-nox*** (No X)!

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

I was relieved, when I read that you have the extra backup on Dropbox :-)

---

### Post by sammiev on 2016-03-08
DD (Data Destroyer) strikes again.

I like to recommend mkusb to new comers because of this.

It's easy to make a mistake when you have different usb and storage devices all plugged in.

Glad for backups.

---

### Post by kansasnoob on 2016-03-08
Yep, it earned the moniker ***disk destroyer*** :frown:

---

### Post by help_me2 on 2016-03-08
At least it was just a backup. A few years ago I mistakenly wiped a drive with 35,000 mp3's on it and no backup. It took me years to amass that much music. I literally cried. Data Destroyer is an understatement. Life destroyer.

---

### Post by buzzingrobot on 2016-03-08
> **help_me2 said:**
> ...A few years ago I mistakenly wiped a drive with 35,000 mp3's on it and no backup.

Ouch. Very ouch.

Wandering off topic, a year or so ago I managed to zap a Gmail account I'd used since early in its beta. About 40,000 messages. Surprisingly easy to do:  Just a bare "Delete" checkbox on a page I'd wandered onto by mistake. Only I didn't know that. Silly me thought I was deleting a Google Apps account. Like dd, No "Are You Really Sure"?" warnings. Nada. Just click and it's gone.  Recovery efforts, online and with actual humans, went nowhere.

---

### Post by mikodo on 2016-03-08
> **buzzingrobot said:**
> 
Except.... Reboot with that USB stick in place and it might not be /dev/sdd.  It might be /dev/sdc and that external backup drive might be /dev/sdd.
Using LABELS persists over the other changes. Could you use that with dd?

I'm happy to hear you have "workable" other backups.

Thanks, for posting. We all need reminding.

---

