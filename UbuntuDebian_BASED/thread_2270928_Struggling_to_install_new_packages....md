---
title: "Struggling to install new packages..."
date: 2015-03-26
forum: Ubuntu/Debian BASED
---

### Post by boblevien on 2015-03-26
New to Linux, so apologies if the title isn't very helpful.

Am running elementary OS on a pair USB sticks with persitance - periodically dd one to the other. Seems to be working ok. Have been having a struggle with installing new software.
If I use the Software Center the install seems to bog down at the end and eventually announces that it failed. BUT, the package appears to be installed and is running. Whetehr it's running properly, I can't say.

If I use the terminal I get a series of error messages:
So: sudo apt-get install or sudo apt-get autoremove
will start ok and then, at some point after "Running depmod." will announce:
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Then a series of error messages, which I will post if required, ending up with:
Errors were encountered while processing:
linux-image-3.2.0-77-generic
linux-image-generic
linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1) 

Can anybody talk me through this?

Thanks,
Bob

---

### Post by howefield on 2015-03-26
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

