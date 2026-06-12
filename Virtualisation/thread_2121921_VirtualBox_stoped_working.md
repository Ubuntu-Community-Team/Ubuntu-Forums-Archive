---
title: "VirtualBox stoped working"
date: 2013-03-03
forum: Virtualisation
---

### Post by BobW on 2013-03-03
I've been using VirtualBox for quite a while with no problems and it suddenly stopped working.

I have a 12.10 64bit Ubuntu host and am tryign to run a 12.10 32bit Ubuntu guest.

This was working fine previously bu no longer will boot up.

I even tried creatign a new guest. The install seems to all run correctly, but when I reboot at the end I get a blank screen.
There is an error message about compiz closing unexpectedly.

Has somethign changed in the latest code that doesn't play nice with VirtualBox?

---

### Post by Groodles on 2013-03-04
Virtualbox relies on DKMS to handle kernel updates, but in my experience it doesn't work all the time/every time.

If you have recently performed a kernel update, try running the following from the command line.

 ```
sudo /etc/init.d/vboxdrv setup
```

---

