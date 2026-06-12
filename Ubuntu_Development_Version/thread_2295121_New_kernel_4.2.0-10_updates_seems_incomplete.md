---
title: "New kernel 4.2.0-10 updates seems incomplete"
date: 2015-09-16
forum: Ubuntu Development Version
---

### Post by dino99 on 2015-09-16
Get that latest update; but only 3 of the 4 packages has received an upgrade
linux-headers-4.2.0-10 is still at version 4.2.0-10.11, not 12 as expected.
Wonder if it really matter, will know on the next cold boot.

---

### Post by ventrical on 2015-09-16
> **dino99 said:**
> Get that latest update; but only 3 of the 4 packages has received an upgrade
linux-headers-4.2.0-10 is still at version 4.2.0-10.11, not 12 as expected.
Wonder if it really matter, will know on the next cold boot.

I just updated my snappy personal (same kernel update) and it came up with failed - etc.. no space left on device!! and I have it on a 160GB hdd. I rebooted ..  will see what happened.

regards..

Edit:

 Nope .. it did not install 4.2.0-10   ..is still at 4.2.0-7

Ok .. I see where you are expecting -11. My bad... but it appears the process is busted here .. but still working.

---

### Post by rrnbtter on 2015-09-16
Greetings,
I've been running 4.2.0-10.12 for a few days. Just switched to the 4.3 kernel this morning.  Everything has been working ok here. 



ii  linux-image-4.3.0-040300rc1-generic                 4.3.0-040300rc1.201509160642               i386         Linux kernel image for version 4.3.0 on 32 bit x86 SMP

ii  linux-image-extra-4.2.0-10-generic                  4.2.0-10.12                                i386         Linux kernel extra modules for version 4.2.0 on 32 bit x86 SMP
ii  linux-image-4.2.0-10-generic                        4.2.0-10.12                                i386         Linux kernel image for version 4.2.0 on 32 bit x86 SMP

---

### Post by Cavsfan on 2015-09-16
I have the same thing, both 10 and 11 are mixed:
```
cavsfan@cavsfan-le-beast:~$ dpkg -l | grep -e "linux-generic" -e "linux-headers" -e "linux-image"
ii  linux-generic                                 4.2.0.10.10                              amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-10                        4.2.0-10.11                              all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-10-generic                4.2.0-10.11                              amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-7                         4.2.0-7.7                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-7-generic                 4.2.0-7.7                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.2.0.10.10                              amd64        Generic Linux kernel headers
ii  linux-image-4.2.0-10-generic                  4.2.0-10.11                              amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-7-generic                   4.2.0-7.7                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-10-generic            4.2.0-10.11                              amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-7-generic             4.2.0-7.7                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.2.0.10.10                              amd64        Generic Linux kernel image

```

---

### Post by dino99 on 2015-09-16
indeed this is only related to the "proposed" archive  :lolflag:

got the missing package update a few hours back. So the problem is solved

---

### Post by Cavsfan on 2015-09-17
Arch is not quite up to the 4.2 kernel but it never needs rebooting for anything no matter what. :lolflag:

 ```
[cavsfan@arch-install ~]$ uname -r
4.1.6-1-ARCH
```

I'll wait on the update to Wily. :p

---

### Post by Cavsfan on 2015-09-17
Enabled proposed and installed just the kernel parts and it looks like I have a mixture between 10 and 12 now, instead of 10 and 11.
Or maybe that's normal idk.

```
cavsfan@cavsfan-le-beast:~$ dpkg -l | grep -e "linux-generic" -e "linux-headers" -e "linux-image"
ii  linux-generic                                 4.2.0.10.10                              amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.2.0-10                        4.2.0-10.12                              all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-10-generic                4.2.0-10.12                              amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-7                         4.2.0-7.7                                all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-7-generic                 4.2.0-7.7                                amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.2.0.10.10                              amd64        Generic Linux kernel headers
ii  linux-image-4.2.0-10-generic                  4.2.0-10.12                              amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-7-generic                   4.2.0-7.7                                amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-10-generic            4.2.0-10.12                              amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-7-generic             4.2.0-7.7                                amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.2.0.10.10                              amd64        Generic Linux kernel image

```

---

### Post by oldos2er on 2015-09-18
> **dino99 said:**
> indeed this is only related to the "proposed" archive  :lolflag:

got the missing package update a few hours back. So the problem is solved

You can mark the thread 'Solved' under Thread Tools at the top of the page. Thanks!

---

