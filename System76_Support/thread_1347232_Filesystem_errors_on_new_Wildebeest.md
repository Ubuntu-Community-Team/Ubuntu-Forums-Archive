---
title: "Filesystem errors on new Wildebeest"
date: 2009-12-05
forum: System76 Support
---

### Post by echo314 on 2009-12-05
Hi, on a new Wildebeest 64-bit. Been seeing some troubling signs...

First, having problems when re-plugging in hardware such as thumb drives, or CDs. The first is recognized, but if I put in another (such as plug in USB drive, unplug, plug in a second) the second will not be recognized. I am ejecting properly. Similar situation with the CD. May be related to the bug here, as I get the same error message [DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/355522"). As I use the computer now, there is a CD in the drive which I just used as a LiveCD, and now is not recognized. If I go to Places > Computer, it shows up as CD/DVD drive. Double clicking does not seem to accomplish anything. 

Second, and **much more worrying**, the FS seems to be having problems. While transferring files to and from the HD to a thumb drive, the computer froze. I waited about 30sec, and reset, where I was greeted by ```
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for (and some other stuff)
``` What followed was an automatic file system check, and after that I was able to log in. It took me a minute or two, but I found the log creator and attached the log. The data seems intact, but this really gives me second thoughts about this computer. Well I hope to hear from you Tom, I would like to get this figured out before the 30day guarantee period is over. I'm not quite satisfied yet, you understand! :)

EDIT: Some other symptoms. I instructed the computer to restart. Once the OS closed (just after the screen went black, or whatever it does right before starting up again) the computer made several beeping sounds. For about 1sec, it was a lot of rapid beeps, around 7/sec. Then, for about 2 or 3 seconds, one solid beep. About a second after, the regular startup beep, and the system started up, albiet much slower then normal. It took about 30sec waiting at the screen with the boot menu / bios options, and next to those options instead of flashing though a lot of letter/number combinations like usual, it froze on 5A. After that, it continued like normal, and I don't see any thing out of the ordinary. The second set of logs I just took, after the above mentioned. Currently, the CD drive does not show up in Computer. Perhaps I need to check the cables again?

---

### Post by jeamer on 2009-12-07
Hi, I thought I'd throw mine in here rather than starting a new thread, as they are a similar problem. Only thing is, the partition that can't mount in my boot is the swap, and b/c of this I can only boot into a recovery shell (which I am in right now). I am on a PanV3, Ubuntu 9.10.

As above, it says:

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
swap: waiting for UUID (then about a thirty digit number)

This happened yesterday, and I rebooted and things were ok. Today, I tried rebooting 4 times, no dice, then recovery shell. Loose cable?

Thanks.

---

### Post by thomasaaron on 2009-12-07
I had a similar situation to that (usb drives, et al), and it was due to a corrupted install (not an upgrade, but an install). Re-installing fixed it.

Did you re-image your machine? How about upgrade it?

As for the beeping, you might want to pop it open and make sure nothing got banged loose in shipping: memory cards, hard drive cables, etc...

---

### Post by echo314 on 2009-12-07
Thomas, would you recommend I use the same /home partition, or should I reformat that as well when reinstalling?

---

### Post by thomasaaron on 2009-12-08
Theoretically, keeping the same /home should be fine. Realistically, though, it contains a lot of invisible config files, and I'm not sure if one of them has anything to do with your problem. 

If it were me, I'd go ahead and just reformat it.

---

### Post by echo314 on 2009-12-08
I'm still having several problems. 

-After pressing F10 when booting up, the CD drive may show up, it may not. If I select the CD drive, it eventually just boots up the HD like normal (I have no indication something is wrong with the CD). In fact, it actually showed up for a little while when I booted up as the correct name (9.10 amd64, etc), but now its disappeared again since I clicked on it, receiving the error message mentioned earlier. One time, it actually brought me to the CD page, where I selected Install Ubuntu. The screen just displayed a blinking _, and did not continue with the install process. 

-Sometimes, after booting up to the HD (taking a long time at the splash again), it will show me the console tty1 login prompt, and then display a lot of "Buffer I/O error on device sr0, logical block 0 (and other numbers). After this, it seems to bring me to the GUI login page like normal. 

-Got the weird beeping error on a shutdown again. I've checked most of the cables, everything seemed OK, but some were very hard to get to. 

-The system froze one more time, about 30sec after booting up. Another log is attached, after the freeze. I looked briefly in the logs, and saw some more sr0 errors mentioned. 

I'm sorry this seems so disorganized, I'm not sure how to have this make sense, since I'm getting symptoms all over the place.

P.S. How long do I have to request a refund? I'm not sure if the 30 days starts from the order date, the shipping date, or the delivery date. I don't want to submit for the RMS number too late if I can't solve this. Thank you.

---

### Post by thomasaaron on 2009-12-09
OK, let's move this to support email so that we can gain some efficiency.
support...at...system76...dot...com

In the meantime, if you can manage to get the splash screen from the live CD and select "Test Memory", that would be good.

---

