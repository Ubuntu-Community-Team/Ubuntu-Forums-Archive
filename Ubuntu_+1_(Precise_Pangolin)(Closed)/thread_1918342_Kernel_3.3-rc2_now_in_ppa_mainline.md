---
title: "Kernel 3.3-rc2 now in ppa mainline"
date: 2012-01-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2012-01-31
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc2-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc2-precise/)

---

### Post by sammiev on 2012-01-31
> **paul_in_london said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc2-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-rc2-precise/)

Thanks Paul.

---

### Post by paul_in_london on 2012-01-31
> **sammiev said:**
> Thanks Paul.

No problem. nvidia 295.09 still working. :)

---

### Post by rodercot on 2012-01-31
I already installed in on my 10.04 system so far pretty good. did the asm fix and nvidia-current installed for me. alsa 1.0.25 built against it as well as lirc 0.9.0. 
 
 suspend and resume seem to be working ok on my Sandy Bridge test setup here. Lirc still was not working and I took a rest suspended the machine and watched a movie, resumed the machine and lirc started working. I am afraid to reboot now. I could get nothing on irw or ir-keytable -t prior to the suspend. So if I reboot and it does not work then suspend and resume and it does work I will be completely confused as all the modules are loaded, I can run a no daemon pid and watch lirc pick up the client and initialize the device but no irw response this is in bridge mode with the kernel drivers.

 Dave

---

