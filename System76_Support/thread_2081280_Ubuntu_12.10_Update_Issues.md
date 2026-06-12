---
title: "Ubuntu 12.10 Update Issues"
date: 2012-11-06
forum: System76 Support
---

### Post by isantop on 2012-11-06
Many System76 users are experiencing issues with a new kernel update today. The root of the cause is that Ubuntu 12.10 doesn't include packages necessary for build kernel modules. This will cause issues with card readers, proprietary graphics, and other things.

If you're running 12.10, and have a system component other than Nvidia proprietary graphics that no longer works after an update, log in, then re-run the System76 Driver. This will solve your problems.

For Nvidia graphics, your screen resolution and desktop will be broken after the reboot. To fix them, log in to your system, then press Ctrl+Alt+T to open a terminal window. Then, run these commands:

```
sudo apt-get clean
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall nvidia-current-updates
sudo reboot
```

After this, you should be good to go. 

If anyone has any other questions, feel free to open a support ticket for your product by visiting [this page](https://www.system76.com/my-account), then clicking on "Open Support Case" underneath the computer in question.

---

### Post by jpv on 2012-11-06
Don't do this:
```
sudo apt-get install linux-headers-`uname -r`
```

That only works while `uname -r` remains current.  Do this instead, which always works:
```
sudo apt-get install linux-headers-generic
```

This works because "linux-headers-generic" is a meta-package that "...will always depend on the latest generic kernel headers..."

And if you have been doing it the bad way, you may want to go purge all the old header packages.

---

### Post by Bill Gates Foundation on 2012-11-25
this worked for me......

:guitar:
1gig nvida card desktop  with a reboot resolution problem....fixed

---

