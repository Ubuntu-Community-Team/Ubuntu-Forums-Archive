---
title: "Kernel 5.13 broke my Ubuntu 21.10 on RPI4 8Gb"
date: 2021-09-08
forum: Ubuntu Development Version
---

### Post by nettobr on 2021-09-08
Hello all,

Ubuntu 21.10 on RPI4 and Kernel 5.13 broke my system only if I use a USB SSD install.

Lets see all steps:

I downloaded Ubuntu 21.10 desktop img from ubuntu daily builds and installed it on a USB SSD (about a month ago).

Every things were all wright an for me it was better than 21.04. I was very happy.

Until last week, when Update manager came with a kernel 5.13 version. As usual I applied all updates and rebooted.

Reboot took a long time and terminated in a character screen  and was written Busybox.....   initram... Type help for... For what??? I simply didn't know how to deal with that info.

Than I decide to install Ubuntu 21.04, but firefox latest version was 90 and I would be in trouble to recover firefox (90.0.2) data files form 21.10 and use it.

So I decide to give ubuntu 21.10 another try, and installed it on a SDcard. set up finished lets update it all and reboot. Reboot successfully and than I copied SDcard to my USB SSD using SD Card Copy from Raspberry PI OS.

Reboot took a long time and terminated in a character screen  and was written Busybox.....   initram... Type help for...

Oh my God, expending a weekend  to have a 21.10 working....

New try... Installed 21.10 again on RPI4 on USB SSD but... but in update manager UNMARKed all kernel 5.13 updates.

Now I am running Ubuntu 21.10 for 3 days but Kernel installed is 5.11.

I Hope this report could be useful for someone. And waiting for a fix.

Thanks,

---

### Post by mikewhatever on 2021-09-08
Not sure what you've expected. 21.10 has not been released yet, and things are expected to break.

Also, Firefox 91.0.2 is available in 21.04 for armhf: [https://packages.ubuntu.com/hirsute-updates/armhf/firefox/download](https://packages.ubuntu.com/hirsute-updates/armhf/firefox/download)

---

### Post by nettobr on 2021-09-08
I expect ubuntu to be fixed until release date.

But do be fixed someone must know about this crash. I Hope someone of developing team could see this report.

Knowledge is the Key.

Thanks,

---

### Post by QIII on 2021-09-08
The developers will not see this.  This is not a report.

The developers do not hang out here.  This is a peer-to-peer user support forum.

Please look [here]("https://help.ubuntu.com/stable/ubuntu-help/report-ubuntu-bug.html.en") for instructions on how to report bugs.

---

### Post by nettobr on 2021-09-08
Thanks QIII, I'll try.

---

### Post by VMC on 2021-09-09
What's the output of:```
ls -l /boot
```

---

### Post by nettobr on 2021-09-09
Hi VMC,

there is no /dev/sda1 mounted.

results on mount:

none on /
sysfs on /sys
proc on /proc
udev on /dev
devptsdevpts on /dev/pts
tmpfs on /run

This report is on launchpad and got "Confirmed" status. See here: [https://bugs.launchpad.net/ubuntu/+bug/1943097](https://bugs.launchpad.net/ubuntu/+bug/1943097)

Thanhs,

---

### Post by VMC on 2021-09-10
I just realized you have this on a Raspberry Pi.  Unsure of its architecture.

---

### Post by zebra2 on 2021-09-11
The kernel 5.13.0-16 in Proposed will crash. -14 is working ok for me. If you have a separate Home partition you can reformat root on reinstall and all of your installed applications will come back up perfect.

---

