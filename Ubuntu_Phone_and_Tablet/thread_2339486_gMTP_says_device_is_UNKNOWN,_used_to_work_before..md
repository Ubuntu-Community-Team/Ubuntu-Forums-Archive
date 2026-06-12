---
title: "gMTP says device is UNKNOWN, used to work before."
date: 2016-10-09
forum: Ubuntu Phone and Tablet
---

### Post by Joleen on 2016-10-09
Suddenly, after almost a year of collaboration, gmtp decided not to  recognise my phone. Here is the result I get from terminal, when I try  to connect to the phone.


```
Device 0 (VID=0bb4 and PID=2008) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team


```

the last time I tried it, has also added this "panic" lines -naybe because I reinstalled gvfs.

```
Device 0 (VID=0bb4 and PID=2008) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP PANIC: failed to open session on second attempt
Detect: Unable to open raw device?
LIBMTP PANIC: Trying to dump the error stack of a NULL device!
LIBMTP PANIC: Trying to clear the error stack of a NULL device!
```



 needless to say I have saved the phone details in vendor and attr lines to /etc/udev/rules.d/98-gtab.rule as advised in [http://forum.xda-developers.com/showthr ... ?t=1077377]("http://forum.xda-developers.com/showthread.php?t=1077377"). -**As I said, it used to work.**

USb debugging and error detection is and was disabled in my phone...Any suggestions?

thanks in advance..

---

