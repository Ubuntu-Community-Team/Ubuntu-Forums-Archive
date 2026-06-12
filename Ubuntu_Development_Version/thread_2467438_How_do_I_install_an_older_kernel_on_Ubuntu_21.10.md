---
title: "How do I install an older kernel on Ubuntu 21.10"
date: 2021-09-26
forum: Ubuntu Development Version
---

### Post by cyberhiker001 on 2021-09-26
Dell Latitude 7280 Intel® Core&#8482; i5-7300U CPU @ 2.60GHz × 4 

I began experiencing a kernel panic when Ubuntu upgraded to Kernel Linux 5.11.0-86-generic x86_64 a couple of months ago, and I was able to install the older kernel - I do not remember and I wiped it out installing Ubuntu 21.10. In the meantime, I had dual-boot (backup OS) installed Mint 20. and it has Kernel Linux 5.4.0-86-generic x86_64, which works.

Ubuntu 21.10 only has a few kernels in synaptic, 5.11 and 5.13.

How can I install an older kernel on Ubuntu 21.10?

It takes about ten minutes until the kernel panic, so I can do some installation work.

---

### Post by ajgreeny on 2021-09-26
*Thread moved to **Ubuntu Development Version**.* which is more appropriate and a better fit for this thread.

Don't forget 21.10 is still in development and not yet released so potential problems can still be anticipated, even though it's not too far away from being released.

Please run command ```
inxi -Fzx
``` to give us a lot more information on both your hardware and software.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by cyberhiker001 on 2021-09-26
Well, things didn't go so well. The cursor did not show up. I brought up a terminal and installed the INXS package and ran it, and it gave me a readout, but I did not know how to copy it without a cursor or arrow controls. Things may still be too buggy for my machine. If you have any way for me to get the info, I'll try, otherwise, I'll wait until the end of the month and try again with the stable release.

---

### Post by cyberhiker001 on 2021-09-26
A quick look around this board seems to indicate there are some similar problems. So, I am content to wait for the stable release. This is the first time I have tried an early Beta release. I'm using Mint - it is like an older desktop version of Ubuntu - it will do.

---

### Post by Dennis N on 2021-09-26
> **cyberhiker001 said:**
> Well, things didn't go so well. The cursor did not show up. I brought up a terminal and installed the INXS package and ran it, and it gave me a readout, but I did not know how to copy it without a cursor or arrow controls. Things may still be too buggy for my machine. If you have any way for me to get the info, I'll try, otherwise, I'll wait until the end of the month and try again with the stable release.

I suggest you login using Xorg, not Wayland (which is the default). See if that makes a difference for the cursor.

---

### Post by tea for one on 2021-09-26
> **cyberhiker001 said:**
>  In the meantime, I had dual-boot (backup OS) installed Mint 20. and it has Kernel Linux 5.4.0-86-generic x86_64, which works.

If you explore this site [http://old-releases.ubuntu.com/releases/20.04.1/](http://old-releases.ubuntu.com/releases/20.04.1/), you can find older Ubuntu ISO images together with a manifest of packages.

Ubuntu 20.04.1 has Kernel 5.4.0-42.

Maybe worth a look?

---

### Post by cyberhiker001 on 2021-09-26
Thanks - I'll try that

---

