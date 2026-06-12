---
title: "wierd dm- device error"
date: 2012-06-29
forum: Server Platforms
---

### Post by southerngeek on 2012-06-29
Ok, so i have a mdadm raid10 array humming away on top of 6 1TB drives, no problems at all with it. However, I rebooted yesterday, and the system hung and dropped to busybox, throwing an I/O error on device dm-3 (which I didn't know I had...), and also something about a duplicate raid45 device(?). After a few minutes md loaded my array, and I was able to boot. Now the system is periodically throwing the same I/O error. I checked on that device, and according to [FONT="Courier New"]dmsetup[/FONT] it is a 
```
Name:              isw_chjgbabhbd_Volume_0000_err_target
State:             ACTIVE
Read Ahead:        256
Tables present:    LIVE
Open count:        0
Event number:      0
Major, minor:      252, 3
Number of targets: 1
UUID: DMRAID-isw_chjgbabhbd_Volume_0000_err_target
```

So, does anyone have any idea what this thing is? I am not using dm-raid to run the fakeraid controller built into the board, it's all running strait md software raid. Doesn't seem to be causing any real problems, but i just don't know what this random device is :confused:

---

### Post by southerngeek on 2012-06-29
Weeeeeellll.... It would appear that there was some surviving fakeraid metadata on two of my drives in the array from when they served time in a Windoze server...therefore dmraid and mdadm were both trying to use those drives at the same time, and that's what was causing the error. Removing dmraid fixed the problem for now. But now I get to tear down the array so I can get rid of the offending metadata. (Unless anyone knows how I can do it without taking out the array?)#-o

---

