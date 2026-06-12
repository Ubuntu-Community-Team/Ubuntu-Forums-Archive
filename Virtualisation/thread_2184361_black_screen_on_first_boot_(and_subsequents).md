---
title: "black screen on first boot (and subsequents)"
date: 2013-10-28
forum: Virtualisation
---

### Post by danielsender on 2013-10-28
I just installed saucy 13.10 as a guest system on a windows8 virtualbox host. The memory on the machine is 8GB so I gave 2GB to the 13.10 plus 60GB of disk space. The installation went fine w/o any problems. On the first reboot of the machine and after a couple of minutes I get the login prompt, typed the password and then the screen goes black. If I press ctl-alt-F1 I get the console where I can enter commands, but on return the screen will stay black. Any pointers?

Thanks.

---

### Post by houstonbofh on 2013-10-29
It is probably a failure in the accelerated 3D graphics that you don't really have.  Does Saucy still have a 2D mode?

---

### Post by danielsender on 2013-10-29
> **houstonbofh said:**
> It is probably a failure in the accelerated 3D graphics that you don't really have.  Does Saucy still have a 2D mode?

I don't know, but doesn't the use of 2D or 3D depend on which desktop environment I use?, e.g. KDE, unity, etc. Does that mean that if I install KDE I will be able to run saucy?

---

### Post by danielsender on 2013-10-29
yes, kubuntu works fine, it seems to be an unity issue.

---

