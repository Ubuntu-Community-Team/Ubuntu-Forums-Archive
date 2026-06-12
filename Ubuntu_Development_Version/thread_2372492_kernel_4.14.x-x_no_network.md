---
title: "kernel 4.14.x-x no network"
date: 2017-09-25
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-09-25
No network on kernel 4.14.x-x.

---

### Post by Doug S on 2017-10-05
Someone else reported the same problem, over on the [4.14-rc? ]("https://ubuntuforums.org/showthread.php?t=2371638&p=13694540#post13694540")series thread.

---

### Post by Doug S on 2017-10-06
did you ever try kernel [4.14-rc1]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14-rc1/")? Or just 4.14-rc2? Do you see any apparmor errors in dmesg or /var/log/kern.log?
[My issues]("https://ubuntuforums.org/showthread.php?t=2371638&p=13694678#post13694678") (not network) seem to all be due to one commit from the big security changes that were delayed from 4.14-rc1 to 4.14-rc2.

---

### Post by Doug S on 2017-10-06
> **Doug S said:**
> did you ever try kernel [4.14-rc1]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14-rc1/")? Or just 4.14-rc2? Do you see any apparmor errors in dmesg or /var/log/kern.log?
[My issues]("https://ubuntuforums.org/showthread.php?t=2371638&p=13694678#post13694678") (not network) seem to all be due to one commit from the big security changes that were delayed from 4.14-rc1 to 4.14-rc2.O.K., never mind. I finally got my 17.10 desktop VM working, and have confirmed this "no network" issue is due to the same commit and dhclient have appormor issues.

---

### Post by ventrical on 2017-10-07
> **Doug S said:**
> O.K., never mind. I finally got my 17.10 desktop VM working, and have confirmed this "no network" issue is due to the same commit and dhclient have appormor issues.

Actually Doug I wiped that machine and re-installed.  Was too far gone. It was from early june ISO. Even booting into 4.13.n.-n was borked.

Regards..

---

### Post by Doug S on 2017-10-07
> **ventrical said:**
> Actually Doug I wiped that machine and re-installed.  Was too far gone. It was from early june ISO. Even booting into 4.13.n.-n was borked.

Regards..Are you saying that networking on a 17.10 desktop with kernel 4.14-rc2 or 4.14-rc3 is working for you now?

---

### Post by ventrical on 2017-10-07
> **Doug S said:**
> Are you saying that networking on a 17.10 desktop with kernel 4.14-rc2 or 4.14-rc3 is working for you now?

No. I'm using default 4. 13.x.x and gdm (on that machine) is still broke. It must be the hardware.

regards..

---

