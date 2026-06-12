---
title: "Booting with raid5 the partitions are lost"
date: 2009-02-19
forum: Server Platforms
---

### Post by alkisx on 2009-02-19
I followed the following example: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) , with method 2 on setting up a system with raid5, every step went fine without any problem, but on reboot it seemed that the partitions are not been initialized.

The main raid which lies on /dev/mapper is isw_ecbigjdjje_MAIN, and the partions are with the same name but with numbers on the end. 

So the first (/) partition is isw_ecbigjdjje_MAIN1, 
The second (/boot) partition is isw_ecbigjdjje_MAIN2 and so on.
The grub found it, and everything ok on menu.lst.
On boot, after system failure to find the partition, I am stocked with the initramfs. checking the directory /dev/mapper to see what is available, I see only tha main raid point (isw_ecbigjdjje_MAIN).
The partitions I mentioned above, are nowhere. checking the dev, I see that the devices are present.

Any idea on what went wrong?

---

### Post by alkisx on 2009-02-19
Any help please??

---

### Post by alkisx on 2009-02-19
Is seems that since no help appeared, I'm moving to mdadm. I will have to open a new thread on that.

---

