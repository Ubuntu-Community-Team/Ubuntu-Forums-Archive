---
title: "/dev/sda5 is not present in &quot;single user&quot; mode, although busy"
date: 2010-03-07
forum: Virtualisation
---

### Post by Cubytus on 2010-03-07
Hi to all, 

I want to use **zerofree**, which is an utility intended to zero all free space in an Ubuntu partition, primarily intended for virtual machines users, to allow compression of the virtual hard drive. 

As all this kind of utilities, it needs an unmounted partition, or one mounted read-only, which can be done in "single user" mode ("Recovery mode", in Ubuntu).

Hence, I rebooted in this mode from a root prompt (#) using the **telinit 1** command, then ran **mount -o ro,remount /dev/sda5**, sda5 being my Ubuntu partition.

Problem is, this doesn't work. I get "/ is busy" (/ being where /dev/sda5 is mounted), and, in addition, I can't see anything under /dev, there's no /sda5! Partition is busy, but not present!

Then of course, **zerofree /dev/sda5** doesn't run since it cannot find /dev/sda5.

Am I missing something essential here?

---

### Post by dcstar on 2010-03-08
> **Cubytus said:**
> Hi to all, 

I want to use **zerofree**, which is an utility intended to zero all free space in an Ubuntu partition, primarily intended for virtual machines users, to allow compression of the virtual hard drive. 

As all this kind of utilities, it needs an unmounted partition, or one mounted read-only, which can be done in "single user" mode ("Recovery mode", in Ubuntu).

Hence, I rebooted in this mode from a root prompt (#) using the **telinit 1** command, then ran **mount -o ro,remount /dev/sda5**, sda5 being my Ubuntu partition.

Problem is, this doesn't work. I get "/ is busy" (/ being where /dev/sda5 is mounted), and, in addition, I can't see anything under /dev, there's no /sda5! Partition is busy, but not present!

Then of course, **zerofree /dev/sda5** doesn't run since it cannot find /dev/sda5.

Am I missing something essential here?

If you want to work on unmounted partitions, boot the VM with an Ubuntu Install CD (exactly as you would with a "real" system).

---

### Post by Cubytus on 2010-03-08
Then, I rebooted using the Ubuntu DVD, unmounted the /dev/sda5 partition, and ran zerofree -v /dev/sda5. It seemed to work.

Still, no explanation as to why an unmounted partition disappears from the /dev (device) sub-tree ?

---

