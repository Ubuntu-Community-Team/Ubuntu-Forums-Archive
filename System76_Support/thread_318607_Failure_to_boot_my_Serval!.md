---
title: "Failure to boot my Serval!"
date: 2006-12-14
forum: System76 Support
---

### Post by Kaloma on 2006-12-14
Since yesterday (when I installed the latest Ubuntu 'edgy' kernel security update), my Serval Performance system has failed to boot several times.  This problem required a hard shutdown and reboot.

The first time this occurred, I tried booting into recovery mode, which seemed to work around the issue.

The second time, even recovery mode did not work; three times I attempting to boot without success.  Since I could see the boot status this time I noticed the message "BUG: soft lockup on CPU#0".  This did not sound very good to me.

Fortunately, I have just booted my system successfully again after flipping the wireless card switch on the chassis to the 'on' position.  I had previously turned it 'off' since I was not using it at the time and had noticed an apparent CPU bug whereby one of my cores was always at 100% frequency even when not in use according to the system monitor.

Anyhow, I don't know if the switch was the cause/cure or not, because when the problem first began I still managed to boot with the switch 'off' and so far I have only had one success with it 'on'.  (I need to do some important work before I can test this theory and risk not being able to boot again.)

Has anyone else heard of or experienced a similar problem?

-Matthew-

---

### Post by crichell on 2006-12-14
Hi Matthew - I have one other report of "BUG: soft lockup on CPU#0" although it was a different machine.  I'm trying to re-create the problem on a Serval now and will get back to you shortly.

---

### Post by hackmeister on 2006-12-14
> **Kaloma said:**
> Since yesterday (when I installed the latest Ubuntu 'edgy' kernel security update), my Serval Performance system has failed to boot several times.  This problem required a hard shutdown and reboot.


Perhaps it was caused by this?
[http://ubuntuforums.org/showthread.php?t=318206](http://ubuntuforums.org/showthread.php?t=318206)

---

### Post by crichell on 2006-12-14
Matthew - we're not experiencing the problem using nVidia's driver from the repos - does hackmasters thread look relevant?

---

### Post by Kaloma on 2006-12-18
I do have the driver version mentioned in that notice.  However, neither of the files noted are missing from /usr/lib/xorg/modules.  Also, my boot process was failing well before attempting to initialize X.  I now reinstalled the nvidia-glx package just in case.

Since flipping the wireless card switch back to the 'on' position, I have not had this problem.  I haven't yet tried switching it 'off' again to see if I can reproduce it.

Regarding the issue of one cpu core running at 100% frequency all the time, my best guess now is that it may not be related to the wireless card/driver.  I have recently noticed that it the issue seems to be related to coming out of hibernation.  If I boot my system fresh, I do not observe the behavior, but if I hibernate and resume then I notice it.

Many thanks to Carl and hackmeister for your help.  If you happen to discover any more information about the error message I initially posted, let me know.  Otherwise, I have my workaround for now.

-Matthew-

---

