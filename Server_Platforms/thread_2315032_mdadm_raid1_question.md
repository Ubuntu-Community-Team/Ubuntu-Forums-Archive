---
title: "mdadm raid1 question"
date: 2016-02-25
forum: Server Platforms
---

### Post by austin49 on 2016-02-25
So i have stepped into another persons mess and am trying to figure it all out. One thing i was wanting to do was simply pull a drive from the raid, put in a new one, rebuild it and then i have a "working" copy of the data. I was able to do this one 2 of the machines, however the other 2 are not working. When i pull the drive, install the new drive & restart, it does not start. It loads the grub screen and then nothing. If i put the old HD back in, it then starts.

I tested on one of the machines failing the drive and this then worked. If i fail the drive first i can then swap in a new drive. However i can not boot back to the failed drive at this point so it defeats the purpose.

Now onto the question at hand, WHY?

Why can i remove the drive in one machine and it boots fine, yet i am forced to fail the drive in another before i can remove it.

I have not done anything special to the mdadm install (no custom changes except setting boot_degraded=true) and both machines are the same install of 12.04 from the same install disk

Is there a flag or setting or something somewhere that allows it to boot without actually failing the drive?

Sorry if this is vague but im not sure what all information would be needed, considering it is 2 servers setup with the same ubuntu install, same mdadm and both are raid1 i would think they would act the same.

---

### Post by austin49 on 2016-02-26
Anyone have any ideas? Is this posted in the wrong section?

---

### Post by austin49 on 2016-02-29
Alright, well thanks for the assistance.. lol

---

### Post by Bucky Ball on 2016-02-29
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2016-02-29
If boot degraded is set to true, it should boot with only one disk without needing to fail it first. Do they have identical HW? The disks have identical flags?

Many boards were designed with windows in mind and some do not boot if they don't see a boot flag on any of the disks. So if only one disk has a boot flag and you pull it out sometimes the board might not boot just because there is no boot flag, even though linux doesn't need it and doesn't use it.

---

### Post by darkod on 2016-02-29
Do you use LVM over the raid? If you do, there seems to be a related bug in 12.04: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1077650](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1077650)

There is also more info and other bugs linked in there.

---

### Post by austin49 on 2016-02-29
Yes, both partitions have the boot flag on both machines and boot degraded flag is set on both machines. And no, LVM is not being used

The machines are identical, i can literally take a windows HD and swap them between the machines, and i'm pretty sure it is known that is not an easy task if anything is different.

The only difference is one machine has 2 partitions (md0 & md1 (swap is part of the raid on this machine)) where as the other only has one (md0)

---

### Post by darkod on 2016-02-29
Search more for known bugs for this situation. Even without lvm many people say they have found issues booting degraded.
On another note, are you considering upgrading to 14.04?

---

