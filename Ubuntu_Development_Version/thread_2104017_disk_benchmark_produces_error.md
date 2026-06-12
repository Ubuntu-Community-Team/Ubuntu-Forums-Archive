---
title: "disk benchmark produces error"
date: 2013-01-11
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-01-11
The disk benchmarker produces an error when attempting a read access rate.

---

### Post by Doug S on 2013-01-12
Is there a corresponding entry or entries in /var/log/kern.log? If yes, could you post it / them. Also, in your screen shot the pop up window partly blocks the disk information in the background window. What is the disk type and size and such? Is your issue repeatable? If yes, is it always at the same spot, or random?

---

### Post by ventrical on 2013-01-12
> **Doug S said:**
> Is there a corresponding entry or entries in /var/log/kern.log? If yes, could you post it / them. Also, in your screen shot the pop up window partly blocks the disk information in the background window. What is the disk type and size and such? Is your issue repeatable? If yes, is it always at the same spot, or random?


There is no information in the background.

There is no infor added in /var/log/kern.log.

 I just upgraded this install yesterday .. so new Raring upgrade.

---

### Post by ventrical on 2013-01-12
attatch

---

### Post by cariboo on 2013-01-12
I tried running the benchmark yesterday when I saw this thread, I get a udisk error when trying to run it, I haven't investigated further as of yet.

---

### Post by ventrical on 2013-01-12
Thanks cariboo. There is nothing in the voluminous kernel logs but some quark activity with usb stuff etc...  basically the upgrade from quantal to raring on this machine  broke a few depends 'somewhere" because cheese web cam is not working either and I tired backgrading different kernels, but to no avail .. so I backed up all my pics , etc and will let it sit until some other big update comes along.

---

