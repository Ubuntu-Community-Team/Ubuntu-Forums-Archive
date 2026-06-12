---
title: "Install of 18.04 failed"
date: 2018-02-28
forum: Ubuntu Development Version
---

### Post by crcarson on 2018-02-28
Had the problem describe by the post "... stuck at 'Started gnome display manager" and since I couldn't recover any other way, downloaded the 18.04 daily build for 2/27.  Tried to install this build and the install process stops after completing the "Who are you" input.  No error messages or way to get control just hangs there.  Back on 17.10 and will try another daily build later.

---

### Post by crcarson on 2018-03-02
Downloaded daily build 3/1/18 and attempted install.  Just after collecting user data from the Who are You popup the install window closed and the install stopped.  Checked syslog and found the last message about [COLOR=#333333][FONT=Ubuntu]G_UDEV_IS_DEVICE (device)' failing.  Found possible new bug report for 1752091 which describes this error but doesn't indicate if this is an install problem. [/FONT][/COLOR][Edit]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1752091/+edit")

---

### Post by crcarson on 2018-03-02
Thinking the error was related to the USB device tried to install the same build level via a DVD.  Got the same stop after the Who are You screen but couldn't verify the syslog error since the install process was hung.

---

### Post by crcarson on 2018-03-05
Using daily build for 3/5/18 the above error does not occur.

---

### Post by technoshaman on 2018-07-17
I have this error. Installing ubuntu 18.04  from USB on an Acer Spin 1 notebook. Install hanging onconfiguring hardware with the message  G:UDEV_IS_DEVICE (failed) just after a message of upgrade available. Install just hangs, no change after an hour.

---

### Post by slickymaster on 2018-07-17
Ubuntu 18.04 is already released. Thread closed.
> **technoshaman said:**
> I have this error. Installing ubuntu 18.04  from USB on an Acer Spin 1 notebook. Install hanging onconfiguring hardware with the message  G:UDEV_IS_DEVICE (failed) just after a message of upgrade available. Install just hangs, no change after an hour.

Please start a new thread in [https://ubuntuforums.org/forumdisplay.php?f=333](https://ubuntuforums.org/forumdisplay.php?f=333) regarding your issue.

---

