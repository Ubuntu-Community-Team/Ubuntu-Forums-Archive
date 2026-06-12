---
title: "Lucid RAID sysfs Timeout Problem"
date: 2010-12-17
forum: Server Platforms
---

### Post by duffboy on 2010-12-17
I have a dual processor, dual core Xeon machine with a sweet Adaptec 2120S RAID. I have successfully installed Lucid Server on this system a few times and continue to run into kernel panics when I SSH in. Playing from the actual computer seems to give me zero grief. After the panics, things go from bad to worse and I wind up reinstalling the OS. There may be a way to fix it after the panics, but since this is a fresh install I do not need to, I need to stop the panics. I tried getting the upgrades, successfully, for Lucid as well as the RAID controller with no luck.

After much research it seems that there is something to do with the timeout/recovery cycle being used by the RAID controller and the OS. My knowledge in such areas is very limited and I really am at a loss. From a couple of different sources, it looks as though the timeout for the system differs from the controller and I need to adjust the system's timeout to be lower than the controllers (the controller is probably about 30 seconds and Lucid maybe 45?)

I am really at a loss for how to proceed. Am I even on the right track? How can I change the sysfs value for the SCSI? 

Any help is very much appreciated.

Dave

---

### Post by duffboy on 2010-12-18
Polite bump.

I really just need to know how to change the sysfs value.

I can find the /lib/udev/rules.d folder, but my knowledge really breaks down as to what to do in there. Thanks again for any help.

Dave

---

### Post by duffboy on 2010-12-19
Well, it appears that I figured it out. Thought I would post what I did so that others who have this problem, although they may be few in number, would not have to endure the grief this problem has given me.

The problem really did turn out to be the difference in disk timeout between the controller card and Ubuntu. The card's timeout is at 30 seconds, while Linux's default, used by Ubuntu, is 45 seconds.

In the /etc/udev/rules.d I added the file '50-udev-default.rules' and put the following two lines in the file
```
SUBSYSTEM=="scsi" , SYSFS{type}=="0|7|14", RUN+="/bin/sh -c 'echo 29 > /sys/block/sda/device/timeout'"

KERNEL=="null", MODE="0666"

```

The first line writes a new timeout of 29 seconds to the /sys/block/sda/device/timeout file, previously 45.

The second line deals with a problem created by the first line where the /dev/null permissions were getting screwed up. It resets them to the default value, as laid out in /lib/udev/50-udev-default.rules.

After making the changes and throwing in a reboot, it seriously looks as though my problem has been solved.

I really do thank all of those people who viewed my post but were, for whatever reason, unable to help. Seeing the views and lack of replies leads me to think it really was a hard problem or, and more likely, I need to be more clear when describing a problem and asking for help.

On a somewhat related note, if somebody knows a reason why what I did is wrong or bad practice, please reply to that end. Thanks!

Dave

---

