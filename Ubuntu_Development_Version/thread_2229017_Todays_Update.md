---
title: "Todays Update"
date: 2014-06-10
forum: Ubuntu Development Version
---

### Post by sammiev on 2014-06-10
It's great to see things move forward. :)

Todays update after a reboot will not load the startup session after you enter in your password. Thought that may happen after I seen what was going to be removed and installed.

---

### Post by Cavsfan on 2014-06-11
> **sammiev said:**
> It's great to see things move forward. :)

Todays update after a reboot will not load the startup session after you enter in your password. Thought that may happen after I seen what was going to be removed and installed.

I wonder why. I got the updates and rebooted and everything is fine here.

---

### Post by sammiev on 2014-06-11
> **Cavsfan said:**
> I wonder why. I got the updates and rebooted and everything is fine here.

I will need a way to login some how and run an update. Ctrl + Alt + F1 seems not to work so far.

---

### Post by cariboo on 2014-06-12
> **sammiev said:**
> I will need a way to login some how and run an update. Ctrl + Alt + F1 seems not to work so far.

Can't you start in Recovery mode, then select Networking, once the partitions are mounted you should be able to drop to a root prompt and do any updates or repairs that are needed.

---

### Post by sammiev on 2014-06-12
> **cariboo907 said:**
> Can't you start in Recovery mode, then select Networking, once the partitions are mounted you should be able to drop to a root prompt and do any updates or repairs that are needed.

Yes I was able to do that last night but still getting the error startup session would not load. I took over 75 updates before I rebooted.

---

### Post by Cavsfan on 2014-06-12
> **cariboo907 said:**
> Can't you start in Recovery mode, then select Networking, once the partitions are mounted you should be able to drop to a root prompt and do any updates or repairs that are needed.

Right. The way I got through this previously was to enter Recovery mode, then select Networking, then drop to root shell and enter **mount -n -o remount,rw /** and then I could get the updates. 
Sudo would normally be required before that command but not in root shell mode.

---

### Post by rrnbtter on 2014-06-12
Greetings,
My suggestion is that you boot from a Install disk or other bootable device that you may have and run gparted and  verify that you still have a root partition. I your root partition is zapped hopefully you used a separate Home partition to protect your data. I know you are not a nooby but anyone can have a senior moment.

---

### Post by sammiev on 2014-06-12
> **rrnbtter said:**
> Greetings,
My suggestion is that you boot from a Install disk or other bootable device that you may have and run gparted and  verify that you still have a root partition. I your root partition is zapped hopefully you used a separate Home partition to protect your data. I know you are not a nooby but anyone can have a senior moment.

I can boot and I do see my user id and it accepts my password but then I get will not load the startup session. I can also update now using Ctrl + Alt + F1 and still the same error after I try a fresh reboot.

---

### Post by rrnbtter on 2014-06-13
For some systems the process is somewhat  broken. I was having the much the same problems. I could boot into Recovery mode, run disk repair and then choose to continue the boot process, and then reboot into normal mode and it would usually give me my desktop (but not always). Ultimately I had to reinstall over my current version using the 14.10 daily. I am up now but still having occasional visits of the aforementioned.

---

### Post by sammiev on 2014-06-13
Here's the exact error I was getting and wished I would have waited a few more hours before doing a fresh install as this problem was addressed in [this]("http://ubuntuforums.org/showthread.php?t=2229255&page=2") thread tonight.

---

