---
title: "UbuntuStudio 8.10 multi cpu suggestion"
date: 2009-01-31
forum: Ubuntu Studio
---

### Post by Ouoertheo on 2009-01-31
I just wanted to let the ubuntustudio 8.10 users know that in the default kernel (2.6.27-3-rt) there is *no* support for multiple cpus as of this moment.

You can check to see if this is your case by checking the output of-
```
dmesg | grep "CPU"
```

If it states that only 1 cpu is being used, then you should switch back to the kernel version 2.6.24-23-rt.
This way you won't have to reinstall ubuntu if you want that extra boost.

Since I upgraded, and didn't do a clean install, my old kernel was already there (or is it installed by default?) and all I had to do was boot from it and reconfigure some xserver/video card stuff.
If that's not your case, then you should be able to find the kernel and headers by doing a little digging.

---

### Post by raboofje on 2009-02-01
Indeed a known (and serious) issue, track it at launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/290498)

not sure what the status of the bug is (what exactly causes it, does it also affect upstream, etc) and whether anyone is working on it.

---

### Post by Ng Oon-Ee on 2009-02-02
It will not be worked on, since Jaunty is already in active development. If 2.6.24-rt works for you, use that, if (like me) you're on a fresh install, then best to wait for Jaunty for now. Or reinstall Hardy, it IS LTS, after all.

---

### Post by imag1narynumber on 2009-02-02
Both of mine are running. Ubustu Intrepid here.

---

